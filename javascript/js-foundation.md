## JavaScript Engine Workflow

Workflow
---

<img src="../images/js-engine-workflow.png" alt="lexical-scope-and-prototypes-chain" width="500px"/>

1. JS file pass through Lexical analysis (Parser)
    - Breaks the code into token
2. Token generates a AST (Abstract Syntax Tree)
    - go to https://astexplorer.net
3. Pass the AST to Interpreter and output is binary

### What can be problematic for JavaScript Engine

- eval()
- arguments()
- for..in
- with
- delete
 
Tips: always write optimize code that is predictable!

#### Memory Heap vs Call Stack

`Memory Heap`: where the memory allocation happens - allocate memory, use memory, release memory
`Call Stack`: keep track where we are in the code so that we can run the codes in order

#### How does garbage collection actually works in JavaScript?

- Use [**Mark-and-Sweep**](https://www.geeksforgeeks.org/mark-and-sweep-garbage-collection-algorithm/) algorithm

<img src="../images/mark-and-sweep-algo.png" alt="mark-and-sweep-algo" width="400px"/>

#### What is Memory Leaks?

When `Memory Heaps` is full  (no `garbage collection` is happening, it is called **Memory Leaks**. When memory leaks happens the browser will be crashed!

```js
let array = [];

// infinite loop, memory leaks
for (let i = 2; i > 1; i++) {
  array.push(i);
}

// Event listeners
const element = document.getElementById("button");
element.addEventListener("click", onClick);
// if we back and forth specially in single page application and don't remove event listeners
// then it causes memory leaks

// setInterval
setInterval(() => {
  // referencing  objects...
})

```