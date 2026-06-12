---
title: "PyQt4 installation ubuntu"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by jaybstory on 2010-01-05
I'm new to pyqt I'm having trouble with installation on ubuntu 9.10 (64 bit).  I followed this tutorial from this website

[http://www.cs.usfca.edu/~afedosov/qttut/]("http://www.cs.usfca.edu/%7Eafedosov/qttut/")

and correctly installed python with qt3 framework, then implemented the sample project and it worked correctly.  

For a project I am working on for school, I need to use pyqt4 instead of pyqt3 however, I'm having trouble installing pyqt4.  

I first removed python-qt3 and qt3 designer via sudo apt-get remove and I've installed python-qt4 & qt4 designer via sudo apt-get install.  However, when I try to test out my project that I created in qt3 designer, it gives me this error

     From qt import *
  Import error: no module named qt


Does this mean that I don't have the correct packages of qt4 installed? Also, am I getting this error because I created the project via qt3 and I am trying to run it using qt4?


Basically, I want to know exactly which packages I need to install via the ubuntu command line to make pyqt4 work properly on ubuntu (and qt4 designer), because I seem to be doing something wrong here.  Thank you.

---

### Post by s.kushan on 2011-01-07
hi,
use this:

from PyQt4.QtGui import *

---

