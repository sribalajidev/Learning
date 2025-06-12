

### Question 
What is a closure?
---

### Explanation
A closure is a function that is returned from another function and retain access to the variable of its outer function even after the outer function is executed.

For example, if we have a outerFunction() that defines a count variable and returns an innerFunction() that increments count and logs it. Then even the outerFunction() has executed the innerFunction() can still access and modify it.

```
function outerFunction() {
  let count = 0;
  return function innerFunction() {
    count++;
    console.log(count);
  };
}

const counter = outerFunction();

counter(); // 1
counter(); // 2
counter(); // 3
```
---

### Question 
What is a event bubbling and how does it works in HTML?
---

### Explanation
Event bubbling is a mechanism in the DOM where an event starts at the target element [The element that triggered the event] and propagates upwards to its parent element and eventually to the document.

To stop the event bubbling - if you want to prevent the event from propagation to parent element, you can use event.propagation() method

Eg: Dropdown menu with sub dropdown menu

* Event Listener : Event Listener is a mechanism used to listen for specific event [like click, keydown, keyup etc.,] on specific element in DOM.

* Event Handler : Event Handler is the actual function or code that executed when event listener detects an event.

```
Syntax for event listener

const button = document.querySelector('button');
button.addEventListener('click', function(){
   console.log('button clicked');
})
```
---

### Question 
Why Use Event bubbling in Real Time?
---

### Explanation
Instead of adding event listener to each child elements we can attach single event listener to parent element and detect the child which was clicked. This improves performance and also ensures the newly added child elements also works.

---

### Question 
What is hoisting in javascript?
---

### Explanation
Hoisting in javascript's default behaviour of moving the variable and function declaration to the top scope before execution.

Function declaration are fully hoisted i.e we can call function before defining them. However variable declaration using keyword - var are initialized with undefined, whereas let and const remains in temporal deadzone untill they are initialized, causing reference error. Variable declaration are not fully hoisted so calling them before initialization results in typerror.

---

### Question 
Difference between var, let and const?
---

### Explanation
In javascript let, var and const are used to declare variables but they have different behaviour. 
The key difference are var keyword is function scoped which can be reassigned, redeclared and also can be accessiable outside function. let keyword is block scoped which can be reassigned but we cant able to redeclare it and also it cant be accessiable outside its function. const keyword is also block scoped, which must be assigned during declaration and it cant be reassigned or redeclared.

---

### Question 
What is difference between '==' and '===' in javascript?
---

### Explanation
== is the loose equality operator. It compares values after type coercion.

=== is the strict equality operator. It compares both value and type without any coercion.

```
5 == '5';    // true  → because '5' is coerced to number
5 === '5';   // false → different types (number vs string)
null == undefined; // true
null === undefined; // false

What is NaN == NaN?
False — because NaN is never equal to anything, including itself.
```

---

### Question 
What is Es6? What are the new features introduced in Es6?
---

### Explanation
Es6 is a major update to Javascript that introduced features like let/const, arrow functions, promises, modules and classes. These features improve readability, performance and maintainability. In react, Es6 is widely used in functional components, state updates, and module imports.

```
const greet = (name = "Guest") => {
  console.log(`Hello, ${name}`);
};
greet(); // Hello, Guest
```

---

### Question 
What are async and await?. How are they different from promise?
---

### Explanation
Both async/await and Promises are used to handle asynchronous operations in JavaScript.

A Promise represents the eventual completion (or failure) of an async operation and returns a value.

An async function always returns a Promise. Inside it, we can use the await keyword to pause execution until the awaited Promise is resolved or rejected.

The key difference is in syntax and readability:
async/await makes asynchronous code look more like synchronous code, which is easier to write, read, and debug.

When using await, errors should be handled with try/catch blocks inside the async function.

```
// Using Promise
fetchData()
  .then(response => console.log(response))
  .catch(error => console.error(error));

// Using async/await
async function loadData() {
  try {
    const response = await fetchData();
    console.log(response);
  } catch (error) {
    console.error(error);
  }
}
```

---

### Question 
What is the difference between Authentication and Authorization?
---

### Explanation
Authentication is the process of verifying a user's identity — confirming who the user is using credentials like username and password.

Authorization is the process of determining what actions or resources a user is allowed to access after they are authenticated.

### Example on Amazon:

When a user logs in with their credentials — that’s authentication.

When the system restricts access so only admins can view the admin dashboard — that’s authorization.

---

### Question
Why is 1 < 2 < 3 true but 3 > 2 > 1 false in JavaScript?
---

### Explanation
**Expression 1:**
```
console.log(1 < 2 < 3); // true
```
Why?
This is evaluated left to right:

1 < 2 → true

So it becomes: true < 3

Now JavaScript coerces true into a number:
```
true => 1
```
So now it's:
```
1 < 3 → true ✅
```

**Expression 2:**
```
console.log(3 > 2 > 1); // false
```
Why?
Again, it's evaluated left to right:

3 > 2 → true

So it becomes: true > 1

Coercion again:
```
true => 1
```
So now it's:
```
1 > 1 → false ❌
```

In chained comparisons like 1 < 2 < 3, JavaScript evaluates from left to right, and intermediate results may be coerced into numbers (e.g., true → 1). To avoid confusion, use logical && or split expressions.

---

### Question 
Some coding questions
---

### Explanation
**Combine Two Arrays**
```
const a = [1, 2, 3];
const b = [4, 5, 6];

const combined = [...a, ...b];
console.log(combined); // [1, 2, 3, 4, 5, 6]
```

Explanation: We use the spread operator (...) to merge arrays.

**Combine and Remove Duplicates**
```
const a = [1, 2, 3, 4];
const b = [4, 5, 6];

const merged = [...a, ...b];
const unique = [...new Set(merged)];
console.log(unique); // [1, 2, 3, 4, 5, 6]
```

Explanation: Set removes duplicates, and we spread it back into an array.

**Reverse an Array**
```
const a = [1, 2, 3, 4];

const reversed = [...a].reverse();
console.log(reversed); // [4, 3, 2, 1]
```
Note: We use [...a] to clone the array so that the original a is not modified. reverse() mutates arrays.

**Remove a Specific Index (e.g., third element)**
```
const a = [1, 2, 3, 4];

// Remove 3rd element (index 2)
const updated = a.filter((_, index) => index !== 2);
console.log(updated); // [1, 2, 4]
```
Explanation: filter() skips the element at the specified index.

**Find Max/Min in Array**
```
const arr = [10, 5, 8, 20];
const max = Math.max(...arr); // 20
const min = Math.min(...arr); // 5
```
**Flatten a Nested Array**
```
const nested = [1, [2, [3, 4]], 5];
const flat = nested.flat(Infinity);
// Output: [1, 2, 3, 4, 5]

```

**Reverse a String**
```
const str = "hello";
const reversed = str.split('').reverse().join('');
// Output: "olleh"
```

---

### Question 
Difference between the DOM and virtual DOM?
---

### Explanation
The DOM (Document Object Model) is the actual structure of the webpage that browsers render.

The Virtual DOM is a lightweight copy of the real DOM used by React to optimize performance.

Instead of updating the real DOM directly, React updates the Virtual DOM first. It then uses a process called "diffing" to compare the new Virtual DOM with the previous one and applies only the necessary changes to the real DOM.

This makes updates faster and more efficient, especially in large, dynamic UIs.

---

### Question 
What are hooks? Name a few common ones.
---

### Explanation
Hooks let you use state and lifecycle features in functional components:
* ```useState``` – for managing local component state

* ```useEffect``` – for handling side effects like API calls or subscriptions

* ```useRef``` – for accessing and persisting DOM references or values across renders

* ```useContext``` – for accessing context values without using <Consumer>

* ```useMemo``` – for memoizing expensive computations

* ```useCallback``` – for memoizing function references to avoid unnecessary re-renders

---

### Question
What is useState in React?
---

### Explanation
```useState``` is a Hook in React that lets you add state to functional components.

It returns a state variable and a function to update that state.

```
const [state, setState] = useState(initialValue);
```

* ```state```: the current state value

* ```setState```: function to update the state

* ```initialValue```: the default value for the state

**Example :**
```
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

---

### Question
What’s the difference between useEffect and useLayoutEffect in React?
---

### Explanation
Both useEffect and useLayoutEffect are React Hooks used to run side effects in functional components — such as data fetching, DOM manipulation, or subscriptions.

The main difference is in when they run during the component lifecycle.

**useEffect**
* Runs after the render is committed to the screen.

* It’s asynchronous in nature.

* Non-blocking — the browser paints the UI first, then runs useEffect.

* Ideal for: API calls, event listeners, analytics, etc.

```
useEffect(() => {
  console.log("useEffect - runs after paint");
});
```

**useLayoutEffect**
* Runs synchronously after all DOM mutations, but before the browser paints.

* Blocking — it pauses painting until the effect is done.

* Ideal for: reading layout, measuring DOM elements, or synchronous DOM updates.

```
useLayoutEffect(() => {
  console.log("useLayoutEffect - runs before paint");
});
```

---

### Question
What are Props and State in React? How are they different?
---

### Explanation
In React, both props and state are used to control data within components, but they serve different purposes and have different behavior.

**Props (short for "properties")**
* Props are read-only inputs to a component.

* They are passed from a parent to a child component.

* Used to configure or customize components.

* Cannot be modified by the receiving component.

```
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

<Greeting name="Sri" />
```
Here, name is a prop passed from the parent to the Greeting component.

**State**
* State is data managed within a component.

* It is mutable and allows components to respond to user interaction or other events.

* Defined using the useState hook (in functional components).

```
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

Props are like function arguments passed from parent to child.
State is like a component’s internal memory that can change over time.

---

### Question
What is .map() in React.js and how is it used?
---

### Explanation
In React, .map() is commonly used to render lists of elements dynamically from arrays.

It is not a React-specific function but a standard JavaScript Array method that creates a new array by applying a callback function to each item in the original array.

**Syntax**
```
array.map((item, index) => {
  // return new item (typically JSX in React)
});
```

**React Use Case**
.map() is often used in React to dynamically render multiple components or HTML elements based on an array of data.

```
const fruits = ['Apple', 'Banana', 'Cherry'];

function FruitList() {
  return (
    <ul>
      {fruits.map((fruit, index) => (
        <li key={index}>{fruit}</li>
      ))}
    </ul>
  );
}
```

**Why use .map() in React?**
* To render lists without repeating code manually

* To generate components dynamically based on data (e.g., API responses)

* Helps keep your JSX clean and declarative

---

### Question
What is a key in ReactJS and why is it important?
---

### Explanation
In React, a key is a special string attribute you must include when creating lists of elements using .map() or similar methods.

Keys help React identify which items have changed, are added, or are removed. They improve performance and ensure proper re-rendering of list components.

**Why are keys important?**
* React uses keys to track elements between renders.

* Keys help React avoid unnecessary re-renders and maintain component state correctly.

* Without keys, React may misbehave or re-render inefficiently, especially with dynamic content.

```
const users = [
  { id: 1, name: 'John' },
  { id: 2, name: 'Alice' },
];

function UserList() {
  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

In this example:

* key={user.id} ensures each <li> is uniquely identified across renders.

---

### Question
What is React Router? How does Routing work in React?
---

### Explanation
React Router is a standard library for routing in React. It enables navigation between different components/pages in a single-page application (SPA) without refreshing the entire page.

It helps in:

* Defining multiple routes in the app

* Mapping URLs to components

* Navigating using links/buttons

* Handling dynamic paths, redirects, nested routes, etc.

**Install package**
```
npm install react-router-dom
```

**Define Route in the component**
```
// App.js
import React from 'react';
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom';
import Home from './Home';
import About from './About';
import Product from './Product';

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link> | <Link to="/product/101">Product</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/product/:id" element={<Product />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

**Route Components**
```
// Home.js
export default function Home() {
  return <h2>Home Page</h2>;
}

// About.js
export default function About() {
  return <h2>About Page</h2>;
}

// Product.js
import { useParams } from 'react-router-dom';

export default function Product() {
  const { id } = useParams();
  return <h2>Product ID: {id}</h2>;
}
```

**Redirect after login using useNavigate**
```
import { useNavigate } from 'react-router-dom';

function Login() {
  const navigate = useNavigate();

  const handleLogin = () => {
    // do login...
    navigate('/dashboard');
  };

  return <button onClick={handleLogin}>Login</button>;
}
```

**Nested Routes**
```
<Route path="/dashboard" element={<Dashboard />}>
  <Route path="settings" element={<Settings />} />
  <Route path="profile" element={<Profile />} />
</Route>

Accessed as:
/dashboard/settings
/dashboard/profile
```

---

### Question
What are the ways to create components in React?
---

### Explanation
In React, components are the building blocks of UI. You can create components in 3 main ways
* Functional Components
* Class Components
* Higher-Order Components (HOC)

---

### Question
What is functional component in react?
---

### Explanation
These are plain JavaScript functions that return JSX.
They are the most common and modern way to build components, especially with Hooks.

```
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```
OR using arrow function:
```
const Greeting = ({ name }) => <h1>Hello, {name}!</h1>;
```

---

### Question
What is Class Components in React?
---

### Explanation
Used in earlier versions of React before Hooks.
They include a render method and can hold state using this.state.

```
import React, { Component } from 'react';

class Greeting extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}
```

---

### Question
What are Higher-Order Components (HOCs) in React?
---

### Explanation
A Higher-Order Component (HOC) is a function in React that takes a component as input and returns a new component with added behavior or props.

It’s a pattern used to reuse component logic — like authentication, logging, or fetching data — across multiple components without repeating code.

**Syntax**
```
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

Logging Props with a HOC
```
function withLogger(WrappedComponent) {
  return function EnhancedComponent(props) {
    console.log('Props passed:', props);
    return <WrappedComponent {...props} />;
  };
}

// Usage:
const UserComponent = (props) => <div>Hello, {props.name}</div>;
const LoggedUserComponent = withLogger(UserComponent);
```
Now when you render LoggedUserComponent, it logs the props and then renders the original component.

A Higher-Order Component is just a function that enhances a component.
It’s like a wrapper that adds reusable features while keeping the component clean and focused.

---

### Question
What is memoization?
---

### Explanation
Memoization is an optimization technique where the result of a function call is cached, so if the function is called again with the same arguments, the cached result is returned instead of recalculating.

In JavaScript/React, memoization helps avoid expensive computations or unnecessary re-renders when inputs haven’t changed.

**Example**
```
function expensiveCalculation(num) {
  console.log('Calculating...');
  return num * 1000;
}

console.log(expensiveCalculation(5)); // Logs: Calculating... then 5000
console.log(expensiveCalculation(5)); // Logs: Calculating... again (no memoization)

```
**With memoization:**
```
const cache = {};
function memoizedCalc(num) {
  if (cache[num]) return cache[num];
  console.log('Calculating...');
  const result = num * 1000;
  cache[num] = result;
  return result;
}
```

---

### Question
What is useMemo in React and when should you use it?
---

### Explanation
useMemo is a React Hook that memoizes the result of a computation so it is recalculated only when its dependencies change.

```
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```
* Avoids re-running expensive functions unless dependencies (a or b) change.

* Useful for expensive calculations, transforming props, or filtering/sorting large lists.

**Example: useMemo to optimize expensive computation**
```
import React, { useState, useMemo } from 'react';

function ExpensiveComponent({ number }) {
  const expensiveResult = useMemo(() => {
    console.log('Running expensive calculation...');
    let total = 0;
    for (let i = 0; i < 1e7; i++) total += number;
    return total;
  }, [number]);

  return <div>Result: {expensiveResult}</div>;
}
```
Without useMemo, the calculation would run on every render, even if number didn't change.

---

### Question
Connect with api and render content in react
---

### Explanation
Create React Component – ```ProductList.js```

```
// ProductList.js

import React, { useEffect, useState } from 'react';

function ProductList() {
  const [products, setProducts] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch('https://fakestoreapi.com/products')
      .then(res => {
        if (!res.ok) throw new Error('Network response failed');
        return res.json();
      })
      .then(data => {
        setProducts(data);
        setLoading(false);
      })
      .catch(err => {
        setError(err.message);
        setLoading(false);
      });
  }, []);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error}</p>;

  return (
    <div className="product-list">
      {products.map(product => (
        <div className="card" key={product.id} style={styles.card}>
          <img src={product.image} alt={product.title} style={styles.image} />
          <h3>{product.title}</h3>
          <p><strong>${product.price}</strong></p>
          <p style={styles.desc}>{product.description.slice(0, 80)}...</p>
        </div>
      ))}
    </div>
  );
}

const styles = {
  card: {
    width: '200px',
    padding: '1rem',
    margin: '1rem',
    border: '1px solid #ddd',
    borderRadius: '8px',
    boxShadow: '0 2px 5px rgba(0,0,0,0.1)',
  },
  image: {
    width: '100%',
    height: '150px',
    objectFit: 'contain',
  },
  desc: {
    fontSize: '12px',
    color: '#666',
  }
};

export default ProductList;
```

Use it in your ```App.js```

```
//App.js

import React from 'react';
import ProductList from './ProductList';

function App() {
  return (
    <div>
      <h1>Fake Store</h1>
      <ProductList />
    </div>
  );
}

export default App;
```

I used ```useEffect``` to fetch data on mount, and ```useState``` to store and manage the product list. I also added basic error and loading state handling. I used ```.map()``` to dynamically render each product as a card with image, title, price, and a short description.

---

