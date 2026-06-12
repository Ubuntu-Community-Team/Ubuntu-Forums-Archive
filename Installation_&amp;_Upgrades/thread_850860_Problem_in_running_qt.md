---
title: "Problem in running qt"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by adityakiran on 2008-07-06
i am trying to run qt in ubuntu........i think i installed all the libraries..but on tying to run, i am getting the following error
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o hello.o hello.cpp
hello.cpp:1:24: error: QApplication: No such file or directory
hello.cpp:2:18: error: QLabel: No such file or directory
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:5: error: ‘QApplication’ was not declared in this scope
hello.cpp:5: error: expected `;' before ‘app’
hello.cpp:6: error: ‘QLabel’ was not declared in this scope
hello.cpp:6: error: ‘label’ was not declared in this scope
hello.cpp:6: error: expected type-specifier before ‘QLabel’
hello.cpp:6: error: expected `;' before ‘QLabel’
hello.cpp:8: error: ‘app’ was not declared in this scope
hello.cpp: At global scope:
hello.cpp:3: warning: unused parameter ‘argc’
hello.cpp:3: warning: unused parameter ‘argv’
make: *** [hello.o] Error 1

can anyone help?

---

### Post by Bubba64 on 2008-07-06
You say you have installed all the libraries, I don't think anybody will know what that means, some may be able to read the errors and deduce something, but try this link and see if it changes anything.
[http://ubuntuforums.org/showthread.php?t=766683&highlight=reassuringly+offensive](http://ubuntuforums.org/showthread.php?t=766683&highlight=reassuringly+offensive)

---

### Post by nimes on 2008-07-06
hi, 

  export QTDIR=/usr
  export QMAKESPEC=/usr/share/qt4/mkspecs/linux-g++

try this ^^ before qmake

---

