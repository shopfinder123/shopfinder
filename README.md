index.html
<!DOCTYPE html>
<html>
<head>
  <title>ShopFinder</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      margin: 0;
      font-family: sans-serif;
      background: linear-gradient(#0f172a, #1e293b);
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .card {
      background: #1e293b;
      padding: 25px;
      border-radius: 15px;
      width: 300px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0,0,0,0.5);
    }

    input {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      border-radius: 8px;
      border: none;
    }

    button {
      margin-top: 10px;
      width: 100%;
      padding: 10px;
      border-radius: 8px;
      border: none;
      background: #6366f1;
      color: white;
      font-weight: bold;
    }

    .searchBtn {
      background: #22c55e;
    }

    .logout {
      background: red;
    }

    .logo {
      width: 90px;
      margin-bottom: 10px;
    }

    .small {
      font-size: 12px;
      opacity: 0.7;
    }
  </style>
</head>

<body>

<div id="app"></div>

<script>
  let step = "login";
  let address = "";

  function render() {
    const app = document.getElementById("app");

    if (step === "login") {
      app.innerHTML = `
        <div class="card">
          <img src="https://i.ibb.co/8ggt05j7/file-000000002ddc7207ac954089ca8441d9.png" class="logo">
          <h2>ShopFinder</h2>
          <p class="small">Find any shop near you</p>

          <input id="addr" placeholder="Enter your address">

          <button onclick="goHome()">Continue</button>
        </div>
      `;
    }

    if (step === "home") {
      app.innerHTML = `
        <div class="card">
          <img src="https://i.ibb.co/8ggt05j7/file-000000002ddc7207ac954089ca8441d9.png" class="logo">
          <h3>Hi 👋</h3>
          <p class="small">${address}</p>

          <input id="search" placeholder="Search (medical, grocery, salon...)">

          <button class="searchBtn" onclick="search()">Search Nearby 🔍</button>

          <button class="logout" onclick="logout()">Logout</button>
        </div>
      `;
    }
  }

  function goHome() {
    address = document.getElementById("addr").value;
    if (!address) return alert("Enter address");
    step = "home";
    render();
  }

  function search() {
    const q = document.getElementById("search").value;
    if (!q) return alert("Type something");

    const text = q + " near me";
    window.open("https://www.google.com/maps/search/" + encodeURIComponent(text));
  }

  function logout() {
    step = "login";
    render();
  }

  render();
</script>

</body>
</html>
