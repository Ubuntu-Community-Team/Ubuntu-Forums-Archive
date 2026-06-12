---
title: "Make sure you have a working Qt v4 qmake ?"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by erngab on 2010-02-23
I tried to install pyRadKDE
pyRadKDE Requires  PyQt4, PyKDE4

The latest stable version of PyQt4 is PyQt-x11-gpl-4.7
and here I am stuck
PyQt-x11-gpl-4.7$ python configure.py
Error: Make sure you have a working Qt v4 qmake on your PATH or use the -q
argument to explicitly specify a working Qt v4 qmake.

I also tried PyQt-x11-gpl-4.6.2 - same thing.
Some ideas we would welcome
Thanks in advance.

---

### Post by shameeram on 2010-08-31
Hello,

locate qmake

then use it after configure.py for eg :

python configure.py -q /usr/lib/qt4/bin/qmake

Good luck :D

---

### Post by prismctg on 2012-02-14
thnx its help me :)

---

### Post by oldos2er on 2012-02-14
Closed, necromancy.

---

