# Full Stack Development-II – Lab Experiments

## Experiment 1: Introduction to Modern JavaScript and DOM

### 1(A) Link a JavaScript file with an HTML page

**File: `index.html`**

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Experiment 1A</title>
</head>
<body>
    <h2>Experiment 1A: Linking JavaScript File</h2>
    <p id="msg">Hello</p>

    <script src="script.js"></script>
</body>
</html>
```

**File: `script.js`**

```javascript
document.getElementById("msg").innerHTML = "Hello JavaScript!";
```

**Output:** Hello JavaScript!

### 1(B) Select elements using DOM selectors

**File: `index.html`**

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Experiment 1B</title>
</head>
<body>
    <h2>Experiment 1B: DOM Selectors</h2>
    <h3 id="heading">Hello World</h3>
    <p class="para">Welcome to JavaScript</p>

    <script>
        document.getElementById("heading").style.color = "blue";
        document.querySelector(".para").style.color = "red";

        document.querySelectorAll("p").forEach(function(p) {
            p.style.fontSize = "20px";
        });
    </script>
</body>
</html>
```

**Output:** Heading appears blue. Paragraph appears red with 20px font size.

### 1(C) Implement event listeners

**File: `index.html`**

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Experiment 1C</title>
</head>
<body>
    <h2>Experiment 1C: Event Listeners</h2>
    <p id="msg">Click the button</p>
    <button id="btn">Click Me</button>

    <script>
        document.getElementById("btn").addEventListener("click", function() {
            document.getElementById("msg").innerHTML = "Button Clicked!";
        });
    </script>
</body>
</html>
```

**Output:** Clicking the button changes the paragraph to "Button Clicked!".

### 1(D) Handle click events for HTML buttons

**File: `index.html`**

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Experiment 1D</title>
</head>
<body>
    <h2>Experiment 1D: Button Click Events</h2>
    <button onclick="showMessage()">Click Me</button>
    <p id="result"></p>

    <script>
        function showMessage() {
            document.getElementById("result").innerHTML = "Welcome!";
        }
    </script>
</body>
</html>
```

**Output:** Clicking the button displays "Welcome!".

### 1(E) Implement three types of JavaScript functions

**File: `index.html`**

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Experiment 1E</title>
</head>
<body>
    <h2>Experiment 1E: Types of JavaScript Functions</h2>
    <p id="result"></p>

    <script>
        // 1. Function Declaration
        function add(a, b) {
            return a + b;
        }

        // 2. Function Expression
        const multiply = function(a, b) {
            return a * b;
        };

        // 3. Arrow Function
        const subtract = (a, b) => a - b;

        document.getElementById("result").innerHTML =
            "Addition = " + add(10, 20) + "<br>" +
            "Multiplication = " + multiply(5, 4) + "<br>" +
            "Subtraction = " + subtract(20, 10);
    </script>
</body>
</html>
```

**Output:**
- Addition = 30
- Multiplication = 20
- Subtraction = 10

---

## Experiment 2: React JS

**Objective:** To create simple React programs using class components, functional components, events, conditional rendering and string literals.

### Initial React Setup

Run these commands in the terminal:

```bash
npm create vite@latest exp2 -- --template react
cd exp2
npm install
npm run dev
```

### Common File: `index.html`

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>React Lab Experiments</title>
</head>
<body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
</body>
</html>
```

### Common File: `src/main.jsx`

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";

ReactDOM.createRoot(document.getElementById("root")).render(
    <React.StrictMode>
        <App />
    </React.StrictMode>
);
```

### 2(A) Counter using React Class Components

**File: `src/App.jsx`**

```jsx
import React, { Component } from "react";

class App extends Component {
    constructor() {
        super();
        this.state = { count: 0 };
    }

    render() {
        return (
            <div>
                <h2>Experiment 2A: Counter using Class Component</h2>
                <h3>Count: {this.state.count}</h3>

                <button onClick={() => this.setState({
                    count: this.state.count + 1
                })}>
                    Click Me
                </button>
            </div>
        );
    }
}

export default App;
```

**Output:** Counter starts at 0 and increases by 1 each time the button is clicked.

### 2(B) Counter using React Functional Components

**File: `src/App.jsx`**

```jsx
import { useState } from "react";

function App() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <h2>Experiment 2B: Counter using Functional Component</h2>
            <h3>Count: {count}</h3>

            <button onClick={() => setCount(count + 1)}>
                Click Me
            </button>
        </div>
    );
}

export default App;
```

**Output:** Counter starts at 0 and increases by 1 each time the button is clicked.

### 2(C) Handle button click events in a Functional Component

**File: `src/App.jsx`**

```jsx
function App() {
    function showMessage() {
        alert("Button Clicked!");
    }

    return (
        <div>
            <h2>Experiment 2C: Button Click Events</h2>
            <button onClick={showMessage}>Click Me</button>
        </div>
    );
}

export default App;
```

**Output:** Clicking the button displays an alert saying "Button Clicked!".

### 2(D) Conditionally render a component

**File: `src/App.jsx`**

```jsx
import { useState } from "react";

function App() {
    const [show, setShow] = useState(false);

    return (
        <div>
            <h2>Experiment 2D: Conditional Rendering</h2>

            <button onClick={() => setShow(!show)}>
                Show / Hide
            </button>

            {show && <h3>Hello React!</h3>}
        </div>
    );
}

export default App;
```

**Output:** The button displays or hides "Hello React!".

### 2(E) Display text using String Literals

**File: `src/App.jsx`**

```jsx
function App() {
    const name = "JavaScript";
    const message = "Welcome to React";

    return (
        <div>
            <h2>Experiment 2E: Displaying Text using String Literals</h2>
            <h3>{message}</h3>
            <p>Learning {name}</p>
            <p>{"Hello World!"}</p>
        </div>
    );
}

export default App;
```

**Output:**
- Welcome to React
- Learning JavaScript
- Hello World!

**Note:** For each sub-experiment, replace the contents of `src/App.jsx` with the respective program. The common files remain unchanged.

---

## Experiment 3: React useState Hook

**Objective:** To implement a counter button using the React useState Hook.

**Note:** Use the same React project setup and common files from Experiment 2.

### 3(A) Counter button using useState Hook

**File: `src/App.jsx`**

```jsx
import { useState } from "react";

function App() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <h2>Experiment 3A: Counter using useState Hook</h2>
            <h3>Count: {count}</h3>

            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
        </div>
    );
}

export default App;
```

**Output:** Initially, Count: 0. Each click on Increment increases the count by 1.

---
