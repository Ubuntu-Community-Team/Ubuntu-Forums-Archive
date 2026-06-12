---
title: "Qjoypad install problems."
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by RaptorJay on 2011-11-26
I keep getting this and I can't seem to move forward. ~/Downloads/qjoypad-4.1.0/src$ make
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o axis.o axis.cpp
make: g++: Command not found
make: *** [axis.o] Error 127
 
I am trying to install Qjoypad. Its when i try to do the make and make install. I am running 10.04 LTS.

---

