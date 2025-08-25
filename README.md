<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ร้านขายของ</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>ร้านขายของออนไลน์</h1>
    <nav>
      <a href="cart.html">ไปที่ตะกร้า 🛒</a>
    </nav>
  </header>

  <main>
    <section class="products">
      <div class="product">
        <img src="https://via.placeholder.com/200" alt="สินค้า 1">
        <h2>สินค้า 1</h2>
        <p>ราคา: 100 บาท</p>
        <button onclick="addToCart('สินค้า 1', 100)">หยิบใส่ตะกร้า</button>
      </div>

      <div class="product">
        <img src="https://via.placeholder.com/200" alt="สินค้า 2">
        <h2>สินค้า 2</h2>
        <p>ราคา: 200 บาท</p>
        <button onclick="addToCart('สินค้า 2', 200)">หยิบใส่ตะกร้า</button>
      </div>

      <div class="product">
        <img src="https://via.placeholder.com/200" alt="สินค้า 3">
        <h2>สินค้า 3</h2>
        <p>ราคา: 300 บาท</p>
        <button onclick="addToCart('สินค้า 3', 300)">หยิบใส่ตะกร้า</button>
      </div>
    </section>
  </main>

  <script src="script.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ตะกร้าสินค้า</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>ตะกร้าสินค้า</h1>
    <nav>
      <a href="index.html">กลับไปซื้อสินค้า</a>
    </nav>
  </header>

  <main>
    <section class="cart">
      <ul id="cart-items"></ul>
      <p id="cart-total">รวมทั้งหมด: 0 บาท</p>
    </section>
  </main>

  <script src="script.js"></script>
</body>
</html>
body {
  font-family: 'Prompt', sans-serif;
  background-color: #fdf6f9;
  margin: 0;
  padding: 0;
  color: #333;
}

header {
  background: #ffd6e8;
  padding: 20px;
  text-align: center;
  border-bottom: 3px solid #ffb3c6;
}

header h1 {
  margin: 0;
  color: #d63384;
}

nav a {
  text-decoration: none;
  color: #d63384;
  font-weight: bold;
  margin: 0 10px;
}

.products {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin: 30px;
}

.product {
  background: #fff0f6;
  border: 2px solid #ffb3c6;
  border-radius: 12px;
  padding: 20px;
  width: 200px;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.product img {
  max-width: 100%;
  border-radius: 8px;
}

button {
  background: #ff85a1;
  color: white;
  border: none;
  padding: 10px;
  border-radius: 8px;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  background: #d63384;
}

.cart {
  padding: 20px;
  max-width: 500px;
  margin: auto;
  background: #fff0f6;
  border: 2px solid #ffb3c6;
  border-radius: 12px;
}
function addToCart(name, price) {
  let cart = JSON.parse(localStorage.getItem("cart")) || [];
  cart.push({ name, price });
  localStorage.setItem("cart", JSON.stringify(cart));
  alert(name + " ถูกเพิ่มเข้าตะกร้าแล้ว!");
}

function loadCart() {
  let cart = JSON.parse(localStorage.getItem("cart")) || [];
  let cartItems = document.getElementById("cart-items");
  let cartTotal = document.getElementById("cart-total");
  let total = 0;

  if (cartItems) {
    cartItems.innerHTML = "";
    cart.forEach((item, index) => {
      let li = document.createElement("li");
      li.textContent = `${item.name} - ${item.price} บาท`;
      cartItems.appendChild(li);
      total += item.price;
    });
    cartTotal.textContent = "รวมทั้งหมด: " + total + " บาท";
  }
}

// โหลดตะกร้าตอนเปิด cart.html
window.onload = loadCart;
