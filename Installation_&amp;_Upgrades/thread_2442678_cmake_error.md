---
title: "cmake error"
date: 2020-05-06
forum: Installation &amp; Upgrades
---

### Post by jacobetch2 on 2020-05-06
Hi guys, i have ubuntu 20.04 and going to install: [https://github.com/DanielOgorchock/joycond](https://github.com/DanielOgorchock/joycond) i could not. This error:
```
nozeco@asus:~/joycond$ cmake .
-- The C compiler identification is GNU 9.3.0
-- The CXX compiler identification is GNU 9.3.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found PkgConfig: /usr/bin/pkg-config (found version "0.29.1") 
-- Checking for module 'libevdev'
--   No package 'libevdev' found
CMake Error at /usr/local/share/cmake-3.15/Modules/FindPkgConfig.cmake:458 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/local/share/cmake-3.15/Modules/FindPkgConfig.cmake:637 (_pkg_check_modules_internal)
  CMakeLists.txt:7 (pkg_check_modules)


-- Configuring incomplete, errors occurred!
See also "/home/nozeco/joycond/CMakeFiles/CMakeOutput.log".
```

CMakeOutput.log: [https://pastebin.com/ggK2gB4h](https://pastebin.com/ggK2gB4h)

thanks

---

### Post by Impavidus on 2020-05-07
Install libevdev. As this is for compiling, you probably need the development version with header files:```
sudo apt install libevdev-dev
```

---

