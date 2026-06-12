---
title: "qt4 fails on 'make'"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by bartkl on 2007-02-18
Helle everybody,

I am trying to install QT4, and I thought it was correct to choose qt-x11-opensource-src-4.2.2,tar.gz for installation. 
So I read the INSTALL text file and correctly (I guess? by apt-get and Synaptic Package manager) installed gcc++, make and gcc. 

./configure  works fine, but when I type 'make' it gives me the following error after a big while of (seemingly) good stuff:

```

                 from kernel/qapplication.cpp:55:
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:50:22: error: X11 /Xlib.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:55:23: error: X11 /Xutil.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:56:21: error: X11 /Xos.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:63:23: error: X11 /Xatom.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:248: error: ‘Colo rmap’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:249: error: ISO C ++ forbids declaration of ‘Visual’ with no type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:249: error: expec ted ‘;’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:258: error: ‘Time ’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:259: error: ‘Wind ow’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:260: error: ‘Wind ow’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:282: error: ‘Wind ow’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:285: error: ‘Wind ow’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:286: error: ‘Wind ow’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:286: error: ‘Atom ’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:287: error: ‘Atom ’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:288: error: ‘Wind ow’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:288: error: ‘Atom ’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:299: error: expec ted ‘,’ or ‘...’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:299: error: ISO C ++ forbids declaration of ‘XSelectionRequestEvent’ with no type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:301: error: ‘Atom ’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:302: error: ‘Atom ’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:304: error: ‘Atom ’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:305: error: ‘Atom ’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:306: error: ‘Atom ’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:307: error: ‘Atom ’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:307: error: ‘Atom ’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:308: error: ‘Atom ’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:308: error: templ ate argument 1 is invalid
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:309: error: ‘Atom ’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:310: error: ‘Atom ’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:365: error: ISO C ++ forbids declaration of ‘Atom’ with no type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:365: error: expec ted ‘;’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:367: error: ISO C ++ forbids declaration of ‘Window’ with no type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:367: error: expec ted ‘;’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:369: error: ‘Wind ow’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:375: error: ‘Time ’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:376: error: ‘Time ’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:402: error: ISO C ++ forbids declaration of ‘Visual’ with no type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:402: error: expec ted ‘;’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:403: error: ‘Colo rmap’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:563: error: ‘Atom ’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:573: error: ‘Focu sOut’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:574: error: ‘Focu sIn’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:575: error: ‘KeyP ress’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:576: error: ‘KeyR elease’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:577: error: ‘None ’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:578: error: ‘Reve rtToParent’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:579: error: ‘Gray Scale’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:580: error: ‘Curs orShape’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:595: error: ‘XPoi nt’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:595: error: templ ate argument 1 is invalid
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:596: error: ‘XRec tangle’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:596: error: templ ate argument 1 is invalid
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:597: error: ‘XCha r2b’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:597: error: templ ate argument 1 is invalid
make[2]: *** [.obj/release-shared/qapplication.o] Error 1
make[2]: Leaving directory `/tmp/qt-x11-opensource-src-4.2.2/src/gui'
make[1]: *** [sub-gui-make_default] Error 2
make[1]: Leaving directory `/tmp/qt-x11-opensource-src-4.2.2/src'
make: *** [sub-src-make_default-ordered] Error 2

```

What's gone wrong? Thanks :)

---

### Post by willc0de4food on 2007-02-18
why dont you have apt install it for you?

> sudo apt-get update
sudo apt-get install synaptic
sudo synaptic
(once it opens) ctrl+f, qt4

select the packages you want installed for qt4 and you should be good to go..

---

### Post by bartkl on 2007-02-18
Thanks for the tip, :) but Synaptic gives 0 search results. I did see some qt3 items, but those aren't sufficient. On top of that, I'm still interested in what's gone wrong in my compiling process.



So, anybody else perhaps? Thanks

---

### Post by sky18 on 2007-02-20
Hi,

I was just trying to compile it also, and got the same message. I've found out that installing this package was solving the trouble :
xorg-dev

Hope it helps

---

