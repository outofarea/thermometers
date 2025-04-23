[<!DOCTYPE html>
<html lang="nl">
<head>
  <meta charset="UTF-8">
  <title>Donatie Thermometers</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: space-around;
      padding: 20px;
      background-color: #f5f5f5;
    }
    .thermometer {
      text-align: center;
      width: 150px;
      background-color: white;
      border-radius: 10px;
      padding: 10px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    .bar-container {
      width: 50px;
      height: 300px;
      border: 2px solid #000;
      margin: 10px auto;
      position: relative;
      background-color: #eee;
      border-radius: 8px;
      overflow: hidden;
    }
    .bar-fill {
      position: absolute;
      bottom: 0;
      width: 100%;
      background-color: #e74c3c;
      transition: height 0.5s;
    }
    input, button {
      margin: 5px;
      padding: 5px;
      width: 90%;
    }
    h3 {
      font-size: 16px;
      margin-bottom: 5px;
    }
  </style>
</head>
<body>

<div class="thermometer">
  <h3>Hit voor een gebit</h3>
  <div class="bar-container">
    <div class="bar-fill" id="fill1" style="height: 0%"></div>
  </div>
  <div>Doel: €1500</div>
  <div id="value1">€0</div>
  <input type="number" id="input1" placeholder="Bedrag">
  <button onclick="donate(1, 1500)">Doneer</button>
</div>

<div class="thermometer">
  <h3>Reguliere donaties</h3>
  <div class="bar-container">
    <div class="bar-fill" id="fill2" style="height: 0%"></div>
  </div>
  <div>Doel: €2000</div>
  <div id="value2">€0</div>
  <input type="number" id="input2" placeholder="Bedrag">
  <button onclick="donate(2, 2000)">Doneer</button>
</div>

<div class="thermometer">
  <h3>Reisinschrijvingen</h3>
  <div class="bar-container">
    <div class="bar-fill" id="fill3" style="height: 0%"></div>
  </div>
  <div>Doel: 25 personen</div>
  <div id="value3">0 personen</div>
  <input type="number" id="input3" placeholder="Aantal">
  <button onclick="donate(3, 25)">Inschrijven</button>
</div>

<script>
  const totals = [0, 0, 0];

  function donate(index, goal) {
    const input = document.getElementById('input' + index);
    const value = parseFloat(input.value);
    if (!isNaN(value) && value > 0) {
      totals[index - 1] += value;
      const percent = Math.min(100, (totals[index - 1] / goal) * 100);
      document.getElementById('fill' + index).style.height = percent + '%';
      document.getElementById('value' + index).innerText =
        index === 3 ? Math.round(totals[index - 1]) + ' personen' : '€' + totals[index - 1].toFixed(2);
      input.value = '';
    }
  }
</script>

</body>
</html>](https://github.com/outofarea/thermometers.git)
