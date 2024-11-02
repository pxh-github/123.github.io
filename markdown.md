# JavaScript 中 `var`、`let` 和 `const` 的区别

在JavaScript中，`var`、`let` 和 `const` 是声明变量的三个关键字，它们之间有几个关键的区别：

## 1. 作用域（Scope）
- **`var`**：函数作用域。即使在函数内部声明，`var`声明的变量也会提升到函数的顶部，并且如果函数内部没有相应的作用域，它将被认为是全局作用域的一部分。
- **`let` 和 `const`**：块级作用域。它们只在声明它们的块（如`if`语句、`for`循环等）内部可见。

## 2. 变量提升（Hoisting）
- **`var`**：变量被提升到它们所在的作用域的顶部，但只有声明被提升，赋值不会提升。
- **`let` 和 `const`**：不会像`var`那样被提升。如果在声明之前访问它们，会引发`ReferenceError`错误。

## 3. 重复声明
- **`var`**：在同一作用域内可以重复声明同一个变量。
- **`let` 和 `const`**：在同一作用域内不能重复声明同一个变量，否则会抛出错误。

## 4. 常量性（Mutability）
- **`var` 和 `let`**：可以重新赋值。
- **`const`**：一旦声明并初始化后，其值不能被改变。尝试修改`const`变量的值会导致错误。

## 5. 初始值
- **`var`**：可以声明时不赋值，之后在代码的任何地方都可以赋值。
- **`let` 和 `const`**：声明时必须赋值，否则会抛出错误。

## 6. 代码块（Block Scope）
- **`var`**：不适用于代码块，例如在`for`循环中，`var`声明的变量在循环外部也是可见的。
- **`let` 和 `const`**：适用于代码块，例如在`for`循环中，`let`和`const`声明的变量只在循环内部可见。

## 示例代码

```javascript
// var 示例
var x = 1;
if (true) {
  var x = 2; // 同一个变量x，函数作用域
  console.log(x); // 输出 2
}
console.log(x); // 输出 2

// let 示例
let y = 1;
if (true) {
  let y = 2; // 块级作用域，不同的变量y
  console.log(y); // 输出 2
}
console.log(y); // 输出 1

// const 示例
const z = 1;
// z = 2; // 错误：Assignment to constant variable.

if (true) {
  const z = 2; // 块级作用域，不同的变量z
  console.log(z); // 输出 2
}
// console.log(z); // 输出 1