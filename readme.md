# Valgrind Exercise
This exercise explores the valgrind tool to improve code quality during development and testing.

Valgrind helps detect several types of code issues:

- Undefined behavior
- Function and memory profiling
- Data-race detection
- Memory leak detection


## Installation guide via command-line
```
git clone --branch valgrind_exercise https://github.com/dpiet/cpp-boilerplate valgrind_exercise
cd valgrind_exercise
mkdir build
cd build
cmake ..
make
Run tests: ./test/cpp-test
Run program: ./app/shell-app
```
## Add remote repository
 - Pushing git cloned repository as own on Github: [here](https://dev.to/dance2die/push-git-cloned-repository-to-your-own-on-github-1ili)

## Building guide for code coverage
```
sudo apt-get install lcov
cmake -D COVERAGE=ON -D CMAKE_BUILD_TYPE=Debug ../
make
make code_coverage
```
This generates a index.html page in the build/coverage sub-directory that can be viewed locally in a web browser.


# Valgrind
More on Valgrind: [here](http://maintainablecode.logdown.com/posts/245425-valgrind-is-not-a-leak-checker)

Commands: 
```
- valgrind --leak-check=full ./build/app/shell-app &> initial_valgrind_report.txt

- valgrind --tool=callgrind build/app/shell-app

- kcachegrind callgrind.out.42023 

```
Resolved defects in the code:

1. Misuse of uninitialized values: resolved by initializing boolean variable in main.cpp
2. Memory Leak: resolved by deleting the smart pointer in AnalogSensor.cpp

Outputs:

- Initial Valgrind Report: [here](/initial_valgrind_report.txt)
- Final Valgrind Report: [here](/final_valgrind_report.txt)
- Screenshot of KCachegrind: [here](/KCachegrind_screenshot.png)