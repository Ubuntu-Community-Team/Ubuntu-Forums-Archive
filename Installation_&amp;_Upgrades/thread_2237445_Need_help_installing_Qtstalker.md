---
title: "Need help installing Qtstalker"
date: 2014-08-01
forum: Installation &amp; Upgrades
---

### Post by dunn2 on 2014-08-01
I have no idea why this doesnt want to install. :-s

---

### Post by claracc on 2014-08-02
More information is neede in order to help.

What are your harware specs?, and what ubuntu release are you running?, graphics card?. what way are you using to install the program and what is the error returning?

In ubuntu 12.04 package qtstalker is in repositories and can be installed from synaptic package manager or from xterm with command line ```
sudo apt-get install qtstalker
```.

---

### Post by dunn2 on 2014-08-02
> **claracc said:**
> More information is neede in order to help.

What are your harware specs?, and what ubuntu release are you running?, graphics card?. what way are you using to install the program and what is the error returning?

In ubuntu 12.04 package qtstalker is in repositories and can be installed from synaptic package manager or from xterm with command line ```
sudo apt-get install qtstalker
```.


E: Unable to locate package qtstalker

When i did that sudo line...............

I beleive i have an intel card.
 Ubuntu 14.04
4gb
duel core something 
d820

---

### Post by claracc on 2014-08-02
I think the software package qtstalker is in the universe repositories (at least in precise ubuntu).

Do you have the universe repository: free and open software maintained  by community enabled, in you software sources?

---

### Post by dunn2 on 2014-08-04
yea

---

### Post by ysy2 on 2014-11-13
I am using ubuntu 14.04lts (just switch to from windows vista). I am not experienced with linux based systems. i have been trying to install qtstalker0.36 from source, but no success. i have tried pretty much everything, mainly i have followed the guidance on this forum:

[http://ubuntuforums.org/archive/index.php/t-2107684.html](http://ubuntuforums.org/archive/index.php/t-2107684.html)

when i try to make qtstalker it gives me this output

> cd lib/ && make -f Makefile 
make[1]: Entering directory `/home/superman/Downloads/qtstalker/lib'
g++ -c -pipe -ffast-math -g -Wall -W -D_REENTRANT -fPIC -DQT_NO_COMPAT -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I/usr/local/include/ta-lib -I. -o QuotePlugin.o QuotePlugin.cpp
In file included from QuotePlugin.cpp:22:0:
QuotePlugin.h:26:30: fatal error: qnetworkprotocol.h: No such file or directory
 #include <qnetworkprotocol.h>
                              ^
compilation terminated.
make[1]: *** [QuotePlugin.o] Error 1
make[1]: Leaving directory `/home/superman/Downloads/qtstalker/lib'
make: *** [sub-lib-make_default] Error 2
superman@superman:~/Downloads/qtstalker$ g++
g++: fatal error: no input files
compilation terminated.




could someone please help?

---

