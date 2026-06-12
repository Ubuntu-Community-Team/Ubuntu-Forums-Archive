---
title: "Can't install texmaker (LaTex Editor)"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-03-30
I downloaded and extracted the texmaker LaTex Editor.
I am a bit confused about the part where I have to Enter PREFIX. I just entered "/usr".

When I try to install it I get the following errors...hope someone can help!!





root@ubuntu:/home/johs/texmaker/texmaker-1.11 # sudo sh BUILD.sh
Texmaker compilation :
----------------------------------------
Enter path to QT3 (/usr/lib/qt3 or ...):
/usr/lib/qt3
Enter PREFIX (/usr , /usr/local or /opt) :
/usr
Enter SYSTEM (1: UNIX ; 2: MACOSX) :
1
g++ -c -pipe -Wall -W -O2  -DPREFIX=\"/usr\" -DQT_NO_DEBUG
-I/usr/share/qt3/mkspecs/default -I. -I/usr/share/qt3/include -I.ui/
-I.moc/ -o .obj/addoptiondialog.o addoptiondialog.cpp
In file included from addoptiondialog.cpp:12:
addoptiondialog.h:15:21: qdialog.h: No such file or directory
addoptiondialog.h:16:23: qlineedit.h: No such file or directory
addoptiondialog.h:17:25: qpushbutton.h: No such file or directory
In file included from addoptiondialog.cpp:12:
addoptiondialog.h:24: error: parse error before `{' token
addoptiondialog.h:28: error: destructors must be member functions
addoptiondialog.h:29: error: syntax error before `*' token
addoptiondialog.h:32: error: syntax error before `*' token
addoptiondialog.cpp:13:21: qlayout.h: No such file or directory
addoptiondialog.cpp:15: error: `QWidget' was not declared in this scope
addoptiondialog.cpp:15: error: `parent' was not declared in this scope
addoptiondialog.cpp:15: error: parse error before `char'
addoptiondialog.cpp:16: error: invalid use of undefined type `class
   AddOptionDialog'
addoptiondialog.h:23: error: forward declaration of `class AddOptionDialog'
addoptiondialog.cpp: In constructor `AddOptionDialog::AddOptionDialog(...)':
addoptiondialog.cpp:16: error: class `AddOptionDialog' does not have any
field
   named `QDialog'
addoptiondialog.cpp:16: error: `parent' undeclared (first use this function)
addoptiondialog.cpp:16: error: (Each undeclared identifier is reported only
   once for each function it appears in.)
addoptiondialog.cpp:16: error: `name' undeclared (first use this function)
addoptiondialog.cpp:18: error: `setCaption' undeclared (first use this
   function)
addoptiondialog.cpp:19: error: `QGridLayout' undeclared (first use this
   function)
addoptiondialog.cpp:19: error: `gbox' undeclared (first use this function)
addoptiondialog.cpp:19: error: parse error before `(' token
addoptiondialog.cpp:20: error: `fontMetrics' undeclared (first use this
   function)
addoptiondialog.cpp:22: error: `lineEdit' undeclared (first use this
function)
addoptiondialog.cpp:22: error: parse error before `(' token
addoptiondialog.cpp:27: error: `buttonOk' undeclared (first use this
function)
addoptiondialog.cpp:27: error: parse error before `(' token
addoptiondialog.cpp:32: error: `buttonCancel' undeclared (first use this
   function)
addoptiondialog.cpp:32: error: parse error before `(' token
addoptiondialog.cpp:36: error: `clicked' undeclared (first use this
function)
addoptiondialog.cpp:36: error: `SIGNAL' undeclared (first use this function)
addoptiondialog.cpp:36: error: `accept' undeclared (first use this function)
addoptiondialog.cpp:36: error: `SLOT' undeclared (first use this function)
addoptiondialog.cpp:36: error: `connect' undeclared (first use this
function)
addoptiondialog.cpp:37: error: `reject' undeclared (first use this function)
addoptiondialog.cpp:39: error: `Qt' undeclared (first use this function)
addoptiondialog.cpp:39: error: parse error before `::' token
addoptiondialog.cpp:40: error: parse error before `::' token
addoptiondialog.cpp:42: error: `setFocusProxy' undeclared (first use this
   function)
addoptiondialog.cpp: At global scope:
addoptiondialog.cpp:46: error: invalid use of undefined type `class
   AddOptionDialog'
addoptiondialog.h:23: error: forward declaration of `class AddOptionDialog'
make: *** [.obj/addoptiondialog.o] Error 1
g++ -c -pipe -Wall -W -O2  -DPREFIX=\"/usr\" -DQT_NO_DEBUG
-I/usr/share/qt3/mkspecs/default -I. -I/usr/share/qt3/include -I.ui/
-I.moc/ -o .obj/addoptiondialog.o addoptiondialog.cpp
In file included from addoptiondialog.cpp:12:
addoptiondialog.h:15:21: qdialog.h: No such file or directory
addoptiondialog.h:16:23: qlineedit.h: No such file or directory
addoptiondialog.h:17:25: qpushbutton.h: No such file or directory
In file included from addoptiondialog.cpp:12:
addoptiondialog.h:24: error: parse error before `{' token
addoptiondialog.h:28: error: destructors must be member functions
addoptiondialog.h:29: error: syntax error before `*' token
addoptiondialog.h:32: error: syntax error before `*' token
addoptiondialog.cpp:13:21: qlayout.h: No such file or directory
addoptiondialog.cpp:15: error: `QWidget' was not declared in this scope
addoptiondialog.cpp:15: error: `parent' was not declared in this scope
addoptiondialog.cpp:15: error: parse error before `char'
addoptiondialog.cpp:16: error: invalid use of undefined type `class
   AddOptionDialog'
addoptiondialog.h:23: error: forward declaration of `class AddOptionDialog'
addoptiondialog.cpp: In constructor `AddOptionDialog::AddOptionDialog(...)':
addoptiondialog.cpp:16: error: class `AddOptionDialog' does not have any
field
   named `QDialog'
addoptiondialog.cpp:16: error: `parent' undeclared (first use this function)
addoptiondialog.cpp:16: error: (Each undeclared identifier is reported only
   once for each function it appears in.)
addoptiondialog.cpp:16: error: `name' undeclared (first use this function)
addoptiondialog.cpp:18: error: `setCaption' undeclared (first use this
   function)
addoptiondialog.cpp:19: error: `QGridLayout' undeclared (first use this
   function)
addoptiondialog.cpp:19: error: `gbox' undeclared (first use this function)
addoptiondialog.cpp:19: error: parse error before `(' token
addoptiondialog.cpp:20: error: `fontMetrics' undeclared (first use this
   function)
addoptiondialog.cpp:22: error: `lineEdit' undeclared (first use this
function)
addoptiondialog.cpp:22: error: parse error before `(' token
addoptiondialog.cpp:27: error: `buttonOk' undeclared (first use this
function)
addoptiondialog.cpp:27: error: parse error before `(' token
addoptiondialog.cpp:32: error: `buttonCancel' undeclared (first use this
   function)
addoptiondialog.cpp:32: error: parse error before `(' token
addoptiondialog.cpp:36: error: `clicked' undeclared (first use this
function)
addoptiondialog.cpp:36: error: `SIGNAL' undeclared (first use this function)
addoptiondialog.cpp:36: error: `accept' undeclared (first use this function)
addoptiondialog.cpp:36: error: `SLOT' undeclared (first use this function)
addoptiondialog.cpp:36: error: `connect' undeclared (first use this
function)
addoptiondialog.cpp:37: error: `reject' undeclared (first use this function)
addoptiondialog.cpp:39: error: `Qt' undeclared (first use this function)
addoptiondialog.cpp:39: error: parse error before `::' token
addoptiondialog.cpp:40: error: parse error before `::' token
addoptiondialog.cpp:42: error: `setFocusProxy' undeclared (first use this
   function)
addoptiondialog.cpp: At global scope:
addoptiondialog.cpp:46: error: invalid use of undefined type `class
   AddOptionDialog'
addoptiondialog.h:23: error: forward declaration of `class AddOptionDialog'
make: *** [.obj/addoptiondialog.o] Error 1
root@ubuntu:/home/johs/texmaker/texmaker-1.11 #

---

### Post by Leif on 2005-04-08
I'd suggest using the method described here :

[http://ubuntuforums.org/showthread.php?t=9986&highlight=texmaker](http://ubuntuforums.org/showthread.php?t=9986&highlight=texmaker)

as said, download the rpm, convert and install it. You might also consider using Kile instead, which I think is more fully-featured, and is in the repositories.

---

### Post by kleeman on 2005-04-08
The method works for Hoary. I prefer texmaker at times because it isn't as bloated as kile - it loads much faster and looks very nice in hoary with the kubuntu work!

---

