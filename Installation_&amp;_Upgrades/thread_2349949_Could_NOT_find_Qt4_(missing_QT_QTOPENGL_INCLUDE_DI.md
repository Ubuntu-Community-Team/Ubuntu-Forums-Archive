---
title: "Could NOT find Qt4 (missing: QT_QTOPENGL_INCLUDE_DIR QT_QTOPENGL_LIBRARY)"
date: 2017-01-20
forum: Installation &amp; Upgrades
---

### Post by smallcat9603 on 2017-01-20
Dear all,  I am using ubuntu 16.04. I encountered a strange problem when installing viva. I can install viva successfully via sudo apt-get install viva, but by git clone I get the following error message. It says    Could NOT find Qt4 (missing: QT_QTOPENGL_INCLUDE_DIR QT_QTOPENGL_LIBRARY)  but I am sure I have installed libqt4-dev and libqt4-opengl.   Any help is appreciated!  output:  ```
 git clone https://github.com/schnorr/viva.git &#65288;no error&#65289; cd viva && mkdir -p build_graph && cd build_graph && cmake ../ -DTUPI_LIBRARY=ON -DVIVA=ON -DCMAKE_INSTALL_PREFIX=$HOME  CMake Error at /usr/share/cmake-3.5/Modules/FindPackageHandleStandardArgs.cmake:148 (message):   Could NOT find Qt4 (missing: QT_QTOPENGL_INCLUDE_DIR QT_QTOPENGL_LIBRARY)   (found version "4.8.7") Call Stack (most recent call first):   /usr/share/cmake-3.5/Modules/FindPackageHandleStandardArgs.cmake:388 (_FPHSA_FAILURE_MESSAGE)   /usr/share/cmake-3.5/Modules/FindQt4.cmake:1333 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)   CMakeLists.txt:91 (FIND_PACKAGE)   -- Configuring incomplete, errors occurred! See also "/home/smallcat/viva/build_graph/CMakeFiles/CMakeOutput.log". See also "/home/smallcat/viva/build_graph/CMakeFiles/CMakeError.log". 
```

---

### Post by Yellow Pasque on 2017-01-20
> libqt4-opengl
Do you have libqt4-opengl**-dev** ?
If you do, maybe this will shed more light on it:
```
sudo apt-get build-dep viva
```

---

### Post by steeldriver on 2017-01-20
nevermind . . .

---

