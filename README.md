# Pycom: A Python Compiler

## Usage

> ./pycom.py (flags) [source file]

### Flags
* -i (bool):\
    Print additional information about compilation (such as time taken). Defaults to off.

* -r (bool):\
    Run the generated executable automatically after compilation. Defaults to off.

* -rd (bool):\
    Run the generated executable automatically after compilation, and then delete it. Defaults to off.

* -o [output] (string):\
    The string specified after the flag will be the name of the generated executable. Defaults to the name of the Python file that was passed in.

* -fm | --fastmath (bool):\
    Perform aggressive optimisations speed on calculations at the cost of some precision. Defaults to off.

## What is Pycom?

Pycom is effectively a compiler for Python code, bringing it down to a native executable with C++ as 'intermediate representation'. It supports all of the BASIC-like syntax of Python along with a lot of the standard library and inbuilt functions. To see what is currently supported and not supported, check the 'Examples' section below.

## Why and when use Pycom?

Python is slow. While many optimisations and new implementations of it have vastly improved its speed, generating native code that can run as a standalone executable from Python code has never really been done. As a result, no matter what, Python code has never hit levels of speed and portability that C/C++. Pycom aims to tackle this.

Due to Pycom (currenly) not supporting all Python features from all versions, you should only really use it if you want to run simple applications that require high speed (again, check 'Examples')

## Examples

What Pycom supports and is good at:

High iteration loops:

```
def main():
    for i in range(1, 1000001):
        if i % 3 == 0:
            print(i)

    return 0
```

## Speed benchmarks and comparisons

| Benchmark | CPython | Pycom | Pycom with --fastmath | pypy | 
| ----------- | ----------- | ----------- | ----------- | ----------- |
| Multiples of 3 and 5 | 9.383s | 0.133s | 0.106s | 0.495s |
| Primes | 17.127s | 4.441s | 3.994s | 4.577s |
| Stack Operations | 8.857s | 2.132s | 1.992s | 3.113s |

(All of these can be found under ./benchmarks/)