<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simple Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: #f4f4f4;
    }
    .calculator {
      background-color: #222;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0,0,0,0.2);
    }
    .display {
      background: #fff;
      padding: 15px;
      font-size: 2em;
      text-align: right;
      margin-bottom: 10px;
      border-radius: 5px;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 60px);
      gap: 10px;
    }
    button {
      font-size: 1.5em;
      padding: 15px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      background: #444;
      color: #fff;
      transition: 0.3s;
    }
    button:hover {
      background: #666;
    }
    .operator {
      background-color: #f39c12;
    }
    .equal {
      background-color: #27ae60;
      grid-column: span 2;
    }
    .clear {
      background-color: #e74c3c;
      grid-column: span 2;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div class="display" id="display">0</div>
    <div class="buttons">
      <button onclick="appendNumber('7')">7</button>
      <button onclick="appendNumber('8')">8</button>
      <button onclick="appendNumber('9')">9</button>
      <button class="operator" onclick="chooseOperation('/')">/</button>

      <button onclick="appendNumber('4')">4</button>
      <button onclick="appendNumber('5')">5</button>
      <button onclick="appendNumber('6')">6</button>
      <button class="operator" onclick="chooseOperation('*')">*</button>

      <button onclick="appendNumber('1')">1</button>
      <button onclick="appendNumber('2')">2</button>
      <button onclick="appendNumber('3')">3</button>
      <button class="operator" onclick="chooseOperation('-')">-</button>

      <button onclick="appendNumber('0')">0</button>
      <button onclick="appendNumber('.')">.</button>
      <button class="equal" onclick="compute()">=</button>
      <button class="operator" onclick="chooseOperation('+')">+</button>

      <button class="clear" onclick="clearDisplay()">C</button>
      <button class="clear" onclick="deleteLast()">DEL</button>
    </div>
  </div>

  <script>
    let currentOperand = '';
    let previousOperand = '';
    let operation = undefined;

    const display = document.getElementById('display');

    function appendNumber(number) {
      if (number === '.' && currentOperand.includes('.')) return;
      currentOperand = currentOperand.toString() + number.toString();
      updateDisplay();
    }

    function updateDisplay() {
      display.innerText = currentOperand || '0';
    }

    function chooseOperation(op) {
      if (currentOperand === '') return;
      if (previousOperand !== '') {
        compute();
      }
      operation = op;
      previousOperand = currentOperand;
      currentOperand = '';
    }

    function compute() {
      let result;
      const prev = parseFloat(previousOperand);
      const curr = parseFloat(currentOperand);
      if (isNaN(prev) || isNaN(curr)) return;
      switch (operation) {
        case '+':
          result = prev + curr;
          break;
        case '-':
          result = prev - curr;
          break;
        case '*':
          result = prev * curr;
          break;
        case '/':
          result = curr === 0 ? 'Error' : prev / curr;
          break;
        default:
          return;
      }
      currentOperand = result.toString();
      operation = undefined;
      previousOperand = '';
      updateDisplay();
    }

    function clearDisplay() {
      currentOperand = '';
      previousOperand = '';
      operation = undefined;
      updateDisplay();
    }

    function deleteLast() {
      currentOperand = currentOperand.toString().slice(0, -1);
      updateDisplay();
    }
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simple Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: #f4f4f4;
    }
    .calculator {
      background-color: #222;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0,0,0,0.2);
    }
    .display {
      background: #fff;
      padding: 15px;
      font-size: 2em;
      text-align: right;
      margin-bottom: 10px;
      border-radius: 5px;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 60px);
      gap: 10px;
    }
    button {
      font-size: 1.5em;
      padding: 15px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      background: #444;
      color: #fff;
      transition: 0.3s;
    }
    button:hover {
      background: #666;
    }
    .operator {
      background-color: #f39c12;
    }
    .equal {
      background-color: #27ae60;
      grid-column: span 2;
    }
    .clear {
      background-color: #e74c3c;
      grid-column: span 2;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div class="display" id="display">0</div>
    <div class="buttons">
      <button onclick="appendNumber('7')">7</button>
      <button onclick="appendNumber('8')">8</button>
      <button onclick="appendNumber('9')">9</button>
      <button class="operator" onclick="chooseOperation('/')">/</button>

      <button onclick="appendNumber('4')">4</button>
      <button onclick="appendNumber('5')">5</button>
      <button onclick="appendNumber('6')">6</button>
      <button class="operator" onclick="chooseOperation('*')">*</button>

      <button onclick="appendNumber('1')">1</button>
      <button onclick="appendNumber('2')">2</button>
      <button onclick="appendNumber('3')">3</button>
      <button class="operator" onclick="chooseOperation('-')">-</button>

      <button onclick="appendNumber('0')">0</button>
      <button onclick="appendNumber('.')">.</button>
      <button class="equal" onclick="compute()">=</button>
      <button class="operator" onclick="chooseOperation('+')">+</button>

      <button class="clear" onclick="clearDisplay()">C</button>
      <button class="clear" onclick="deleteLast()">DEL</button>
    </div>
  </div>

  <script>
    let currentOperand = '';
    let previousOperand = '';
    let operation = undefined;

    const display = document.getElementById('display');

    function appendNumber(number) {
      if (number === '.' && currentOperand.includes('.')) return;
      currentOperand = currentOperand.toString() + number.toString();
      updateDisplay();
    }

    function updateDisplay() {
      display.innerText = currentOperand || '0';
    }

    function chooseOperation(op) {
      if (currentOperand === '') return;
      if (previousOperand !== '') {
        compute();
      }
      operation = op;
      previousOperand = currentOperand;
      currentOperand = '';
    }

    function compute() {
      let result;
      const prev = parseFloat(previousOperand);
      const curr = parseFloat(currentOperand);
      if (isNaN(prev) || isNaN(curr)) return;
      switch (operation) {
        case '+':
          result = prev + curr;
          break;
        case '-':
          result = prev - curr;
          break;
        case '*':
          result = prev * curr;
          break;
        case '/':
          result = curr === 0 ? 'Error' : prev / curr;
          break;
        default:
          return;
      }
      currentOperand = result.toString();
      operation = undefined;
      previousOperand = '';
      updateDisplay();
    }

    function clearDisplay() {
      currentOperand = '';
      previousOperand = '';
      operation = undefined;
      updateDisplay();
    }

    function deleteLast() {
      currentOperand = currentOperand.toString().slice(0, -1);
      updateDisplay();
    }
  </script>
</body>
</html>
