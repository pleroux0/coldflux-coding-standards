# Coding standards

The coding standards are set and are as follows:

## Consistency

Existing libraries have existing requirements for code formatting and quality. If extensions to an existing tool/library are made, the existing libraries' coding standards are followed.

## Code formatting

New tools developed will have a consistent coding format. The code format will be enforced by a tool to ensure consistent code formatting. Non-automated coding formats are hard to enforce and even harder to validate. The automated approach allows developers to independently and effortlessly follow the coding format. If the coding format was not followed, it could be instantly correct by reformatting the code using the automated formatting tool.

### Python

New developments will be formatted by *black* [1,2], the uncompromising Python code formatter. All settings will be left as the default as set by *black*.

### C/C++

New developments will be formatted using *clang-format* [3]. The following settings file, `.clang-format`, will be used:

```yaml
BasedOnStyle: LLVM
AlwaysBreakTemplateDeclarations: true
BreakBeforeBraces: Custom
BraceWrapping:
  AfterStruct: true
  AfterClass: true
  AfterFunction: true
  SplitEmptyRecord: false
BreakConstructorInitializers: AfterColon
ConstructorInitializerAllOnOneLineOrOnePerLine: true
FixNamespaceComments: true
ReflowComments: true
AllowShortFunctionsOnASingleLine: Empty
AllowShortBlocksOnASingleLine: true
IndentWidth: 4
```

The documentation for what these settings mean can be found at the official website [4].

## Code quality

The code quality will be enforced by a linter to ensure consistent code formatting. A code linter is not a replacement for code review, but due to time constraints, code review is not practical. A code linter can catch a significant amount of code quality issues without requiring additional working hours and without introducing wait times into the development cycle.

### C/C++

New developments will be checked with *clang-tidy* [5]. The following settings file, `.clang-tidy`, will be used:

```yaml
Checks: '
  clang-diagnostic-*,
  clang-analyzer-*,
  performance-*,
  modernize=*,
  misc=*,
  llvm-namespace-comment,
  llvm-header-guard
'
```

The documentation for what these settings mean can be found on the official website [6]. A large portion of the checks can also be automatically fixed with *clang-tidy*.

### Python

New developments will target at least python 3.6 or newer.

Mypy [7] will be used to check the correctness of the optionally annotated types.

We are still in the process of setting up a *pylint* [8] settings file that will be used across the new developments.

## References

[1] https://black.readthedocs.io/en/stable/

[2] https://github.com/psf/black

[3] https://clang.llvm.org/docs/ClangFormat.html

[4] https://clang.llvm.org/docs/ClangFormatStyleOptions.html

[5] https://clang.llvm.org/extra/clang-tidy/

[6] https://clang.llvm.org/extra/clang-tidy/checks/list.html

[7] http://mypy-lang.org/

[8] https://www.pylint.org/