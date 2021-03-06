# Production
## Definition
> [产生式](https://en.wikipedia.org/wiki/Production_(computer_science)): 在计算机中指 Tiger 编译器将源程序经过词法分析（Lexical Analysis）和语法分析（Syntax Analysis）后得到的一系列符合文法规则（Backus-Naur Form，BNF）的语句
> 
> [终结符](https://zh.wikipedia.org/wiki/%E7%B5%82%E7%B5%90%E7%AC%A6%E8%88%87%E9%9D%9E%E7%B5%82%E7%B5%90%E7%AC%A6)： 最终在代码中出现的字符
> 
> [巴科斯诺尔范式](https://zh.wikipedia.org/wiki/%E5%B7%B4%E7%A7%91%E6%96%AF%E8%8C%83%E5%BC%8F)：即巴科斯范式（英语：Backus Normal Form，缩写为 BNF）是一种用于表示上下文无关文法的语言，上下文无关文法描述了一类形式语言。它是由约翰·巴科斯（John Backus）和彼得·诺尔（Peter Naur）首先引入的用来描述计算机语言语法的符号集。


- Symbol
- Terminal Symbol: 不是由其他符号定义的符号，不会出现在产生式的左边
- Non-Terminal Symbol: 其他符号经过“与”、“或”等逻辑组成的符号
- 语言定义: 语言可以由一个 Non-Terminal Symbol 和他的产生式定义
- 语法树: 把一段具体的语言文本，根据产生式以树形结构来表示

## Writing
- [BNF](https://en.wikipedia.org/wiki/Backus%E2%80%93Naur_form): Backus–Naur form
- [EBNF](https://en.wikipedia.org/wiki/Extended_Backus%E2%80%93Naur_form): Extended Backus–Naur form

## Exercise
### 10以内数字四则运算
- 乘除优先 递归
- 加法递归，由乘法定义

```
<四则运算表达式> ::= <加法算式>
<加法算式> ::= (<加法算式> ("+" | "-") <乘法算式>) | <乘法算式>
<乘法算式> ::= (<乘法算式> ("*" | "/") <数字>) | <数字>
<数字> ::= { "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" }
```

### 整数四则运算
- 第一位不为0

```
<四则运算表达式> ::= <加法算式>
<加法算式> ::= (<加法算式> ("+" | "-") <乘法算式>) | <乘法算式>
<乘法算式> ::= (<乘法算式> ("*" | "/") <数字>) | <数字>
<数字> ::= { "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" } ｜ { "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" }
```

### 四则运算，允许小数
- 第一位不为0
- “点” 及其后面数字可选

```
<四则运算表达式> ::= <加法算式>
<加法算式> ::= (<加法算式> ("+" | "-") <乘法算式>) | <乘法算式>
<乘法算式> ::= (<乘法算式> ("*" | "/") <数字>) | <数字>
<数字> ::= { "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" } ｜ { "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" } ["."{ "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" }]
```

### 四则运算，允许括号
- 第一位不为0
- “点” 及其后面数字可选
- 括号优先级最高
- 括号内是加法算式 或者 乘法算式

```
<四则运算表达式> ::= {<括号算式>}
<括号算式> ::= "("<加法算式> | <乘法算式>")"
<加法算式> ::= (<加法算式> ("+" | "-") <乘法算式>) | <乘法算式>
<乘法算式> ::= (<乘法算式> ("*" | "/") <数字>) | <数字>
<数字> ::= { "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" } ｜ { "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" } ["."] [{ "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" }]
```