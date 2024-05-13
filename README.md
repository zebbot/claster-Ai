<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Online Shop</title>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
  <style>
    .product {
      border: 1px solid #ccc;
      padding: 20px;
      margin-bottom: 20px;
    }
  </style>
</head>
<body>

<div class="container">
  <h2>Online Shop</h2>
  <div class="row">
    <div class="col-md-4">
      <div id="product1" class="product">
        <h3>Product 1</h3>
        <p>Price: <span id="price1">100</span>$</p>
        <p>Quantity: <input type="number" id="quantity1" value="1" min="1"></p>
        <button class="btn btn-primary" onclick="addToCart(1)">Add to Cart</button>
        <button class="btn btn-success" onclick="buyNow(1)">Buy Now</button>
        <div id="timer1"></div>
      </div>
    </div>
    <div class="col-md-4">
      <div id="product2" class="product">
        <h3>Product 2</h3>
        <p>Price: <span id="price2">150</span>$</p>
        <p>Quantity: <input type="number" id="quantity2" value="1" min="1"></p>
        <button class="btn btn-primary" onclick="addToCart(2)">Add to Cart</button>
        <button class="btn btn-success" onclick="buyNow(2)">Buy Now</button>
        <div id="timer2"></div>
      </div>
    </div>
    <div class="col-md-4">
      <div id="product3" class="product">
        <h3>Product 3</h3>
        <p>Price: <span id="price3">200</span>$</p>
        <p>Quantity: <input type="number" id="quantity3" value="1" min="1"></p>
        <button class="btn btn-primary" onclick="addToCart(3)">Add to Cart</button>
        <button class="btn btn-success" onclick="buyNow(3)">Buy Now</button>
        <div id="timer3"></div>
      </div>
    </div>
  </div>
</div>

<script>
  // Function to add to cart
  function addToCart(productId) {
    var price = document.getElementById("price" + productId).innerText;
    var quantity = document.getElementById("quantity" + productId).value;
    var productName = "Product " + productId;
    console.log("Added to cart: " + productName + ", Quantity: " + quantity + ", Price: " + (price * quantity));
  }

  // Function to buy now
  function buyNow(productId) {
    var price = document.getElementById("price" + productId).innerText;
    var quantity = document.getElementById("quantity" + productId).value;
    var productName = "Product " + productId;
    console.log("Buy now: " + productName + ", Quantity: " + quantity + ", Price: " + (price * quantity));
    // Here you can redirect to the checkout page or process the purchase
  }

  // Countdown timer
  function countdown(endDate, timerId) {
    var timer = setInterval(function() {
      var now = new Date().getTime();
      var distance = endDate - now;

      var days = Math.floor(distance / (1000 * 60 * 60 * 24));
      var hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      var minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      var seconds = Math.floor((distance % (1000 * 60)) / 1000);

      document.getElementById(timerId).innerHTML = days + "d " + hours + "h " + minutes + "m " + seconds + "s ";

      if (distance < 0) {
        clearInterval(timer);
        document.getElementById(timerId).innerHTML = "EXPIRED";
      }
    }, 1000);
  }

  // Set countdown timers for each product
  var endDates = [
    new Date("2024-05-15T00:00:00Z").getTime(), // Product 1 end date
    new Date("2024-05-15T00:00:00Z").getTime(), // Product 2 end date
    new Date("2024-05-15T00:00:00Z").getTime()  // Product 3 end date
  ];

  countdown(endDates[0], "timer1");
  countdown(endDates[1], "timer2");
  countdown(endDates[2], "timer3");
</script>

</body>
</html>
