---
title: "Failure to implement CMake when installing software from GIT Hub."
date: 2023-03-06
forum: Installation &amp; Upgrades
---

### Post by GwibberFooey on 2023-03-06
There is custom software on GIT Hub, whose main project page is found at ["]https://github.com/UniStuttgart-INS/INSTINCT]("https://github.com/UniStuttgart-INS/INSTINCT). By following the installation instructions from that webpage, I have reached the point where:

```

ugk@sfon:~/INSTINCT$ cmake -Bbuild/Release -S. -DCMAKE_BUILD_TYPE=Release -DENABLE_MAIN=ON -DENABLE_TESTING=OFF -DENABLE_DOXYGEN=OFF -DENABLE_CLANG_TIDY=OFF -DENABLE_CPPCHECK=OFF -DLOG_LEVEL=INFO
CMake Error at /usr/share/cmake-3.22/Modules/CMakeDetermineCXXCompiler.cmake:48 (message):
  Could not find compiler set in environment variable CXX:

  clang++.

Call Stack (most recent call first):
  CMakeLists.txt:16 (project)


CMake Error: CMAKE_CXX_COMPILER not set, after EnableLanguage
-- Configuring incomplete, errors occurred!
See also "/home/ugk/INSTINCT/build/Release/CMakeFiles/CMakeOutput.log".

```

For the record, the contents of that "CMakeOutput.log" file is:

```
The system is: Linux - 5.15.0-67-generic - x86_64
```

I admit this is very much a begginer's question for compiling custom software from C++ or C on GNU. I have used Linux and Python for a long time, and I have basic capabilities at Bash scripting and using Emacs in LisP Interaction mode. My question is whether somebody would please guide or help me to find the most practical possible work-around or solution to the error message displayed above. My system is Ubuntu Mate 22.04.

---

### Post by TheFu on 2023-03-06
Did you install a C++ compiler and linker?
The CMakefile is assuming the name of the compiler or the CXX variable inside it is incorrect.

---

### Post by MAFoElffen on 2023-03-06
That code assumes you have clang installed. If you had, then the result of 'which clang' would return '/usr/bin/clang' and the result of 'which clang++' would return '/usr/bin/clang++'...

'clang' is not a default installed package. If ,for instance, you wanted to install the clang compiler for Ubuntu 22.04, then :
```

sudo apt install llvm build-essential clang-14

```

---

