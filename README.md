# Mini Java Code Analyzer

A Java desktop application that performs basic lexical, syntax, and semantic analysis on a limited subset of Java code. Built using Java Swing and regular expressions, the application provides an interactive environment for writing, examining, and identifying errors in simple Java variable declarations.

This project demonstrates fundamental concepts of source code analysis, object-oriented programming, and desktop application development.

> **Note:** This is an educational code analysis tool, not a complete Java compiler. It supports simplified code validation and does not generate bytecode or execute Java programs.

## Features

### Code Analysis

- **Lexical Analysis:** Uses regular expressions to recognize basic Java data types, identifiers, assignment operators, literals, and delimiters.
- **Syntax Analysis:** Validates the structure of simple variable declarations and assignments.
- **Semantic Analysis:** Performs basic data-type compatibility checks and reports mismatched values.
- **Analysis Pipeline:** Runs lexical, syntax, and semantic checks sequentially, stopping when an earlier stage reports an error.

### Desktop Interface

- Java Swing graphical user interface with a code editor and analysis results panel.
- Individual controls for lexical, syntax, and semantic analysis.
- Run button for executing the complete analysis sequence.
- File selection and loading for existing source files.
- Editing operations including undo, redo, cut, copy, paste, and select all.
- Adjustable editor font size through menu controls and Ctrl + mouse wheel.

## Technologies Used

- **Java:** Core application logic and object-oriented programming.
- **Java Swing:** Desktop graphical user interface.
- **Regular Expressions (Regex):** Pattern matching for code recognition and validation.
- **Java I/O:** Reading source files from the local filesystem.

## Project Structure

```text
mini-java-compiler/
├── src/
│   ├── actions/
│   │   ├── CodeRunner.java
│   │   ├── FileLoader.java
│   │   ├── LexicalAnalyzer.java
│   │   ├── SemanticAnalyzer.java
│   │   └── SyntaxAnalyzer.java
│   ├── common/
│   │   └── Token.java
│   ├── main/
│   │   └── MiniJavaCompiler.java
│   └── ui/
│       ├── EditorPage.java
│       └── WelcomePage.java
└── README.md
```

### Core Components

| Component | Responsibility |
|---|---|
| `MiniJavaCompiler` | Launches the Swing application |
| `WelcomePage` | Provides the initial application window |
| `EditorPage` | Manages the code editor, controls, and results display |
| `CodeRunner` | Coordinates the analysis sequence |
| `LexicalAnalyzer` | Recognizes supported tokens and reports invalid input |
| `SyntaxAnalyzer` | Checks the structure of basic variable declarations |
| `SemanticAnalyzer` | Performs simplified data-type validation |
| `FileLoader` | Loads source files into the editor |
| `Token` | Represents a token using type and value attributes |

## Installation and Setup

### Prerequisites

- Java Development Kit (JDK) 8 or later
- Git (optional, for cloning the repository)

Java Swing is included with the standard JDK. No additional third-party libraries are required.

### 1. Clone the repository

```bash
git clone https://github.com/rnjhnd/mini-java-compiler.git
cd mini-java-compiler
```

### 2. Compile the application

From the repository root, run:

```bash
javac -d bin -sourcepath src src/main/MiniJavaCompiler.java
```

### 3. Launch the application

```bash
java -cp bin main.MiniJavaCompiler
```

The application opens a welcome screen with a **Start** button. Select it to access the code editor.

## How to Use

1. Launch the application and select **Start**.
2. Enter a simple Java variable declaration or open an existing source file.
3. Use **Lexical Analysis** to inspect recognized code elements.
4. Use **Syntax Analysis** to check the declaration's structure.
5. Use **Semantic Analysis** to check basic type compatibility.
6. Alternatively, select **Run** to execute the analysis stages sequentially.
7. Review diagnostic messages in the results panel.

The Run button performs analysis only. It does not compile or execute the entered Java code.

## Example Validation Scenarios

The examples below illustrate the limited syntax supported by the application. Results depend on the current regular-expression rules.

### Example 1: Valid Declaration

```java
int age = 21;
```

**Expected behavior:**

- Lexical analysis recognizes the data type, identifier, assignment operator, literal, and delimiter.
- Syntax analysis accepts the declaration structure.
- Semantic analysis accepts the integer value.

### Example 2: Syntax Error

```java
int age 21;
```

**Expected behavior:**

- Lexical analysis may recognize the individual declaration elements.
- Syntax analysis rejects the statement because the assignment operator is missing.

### Example 3: Type Mismatch

```java
int age = 21.5;
```

**Expected behavior:**

- Lexical analysis recognizes the declaration elements.
- Syntax analysis accepts the basic assignment structure.
- Semantic analysis rejects the decimal value as incompatible with the declared integer type.

### Example 4: Unrecognized Input

```java
int age = 5 @ 10;
```

**Expected behavior:**

- Lexical analysis reports the statement as containing unrecognized input.
- The sequential analysis pipeline stops before subsequent stages.

## Current Limitations

This application is intended to demonstrate introductory source code analysis rather than fully implement the Java language.

Current limitations include:

- Supports only a restricted subset of Java declarations and assignments.
- Does not parse complete Java classes, methods, loops, or conditional statements.
- Relies on regular expressions rather than a complete Java grammar and parser.
- Implements simplified type checking without comprehensive Java language rules.
- Does not generate Java bytecode or execute source programs.
- Does not provide full symbol-table management or variable scope analysis.
- Some valid Java expressions and declarations may not be recognized.

## Potential Improvements

Future enhancements could include:

- Expanding support for Java expressions and statement types.
- Implementing a proper tokenizer and parser.
- Introducing structured diagnostic results with error locations.
- Improving numeric range and type validation.
- Separating analysis logic more completely from the user interface.
- Adding automated unit tests for valid inputs, invalid syntax, and edge cases.
- Improving editor responsiveness and error highlighting.

## Learning Outcomes

Developing this project provided practical experience with:

- Applying object-oriented programming concepts in Java.
- Organizing application logic into separate classes and packages.
- Implementing simplified lexical, syntax, and semantic analysis.
- Using regular expressions for pattern recognition.
- Building event-driven desktop interfaces with Java Swing.
- Handling local files and displaying diagnostic feedback.

## Project Purpose

The Mini Java Code Analyzer was developed as an educational project to explore how programming language analysis works at a fundamental level.

It focuses on recognizing source code elements, validating simple syntax, and identifying basic type mismatches while providing a graphical interface for interacting with the analysis process.
