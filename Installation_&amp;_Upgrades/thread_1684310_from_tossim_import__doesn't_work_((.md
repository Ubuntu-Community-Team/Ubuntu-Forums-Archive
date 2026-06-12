---
title: "from tossim import * doesn't work :(("
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by ig71 on 2011-02-08
Hello all, i am new in Ubuntu and TinyOS, currently i want to try tossim simulator using Blink app. When i tried to command 'make micaz' or 'make micaz sim' is work, but when i tried to run simulator using python, an error was appeared. Here's an error was :

ig71@Agi-VAIO:~$ python
Python 2.6.6 (r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from tossim import *
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named tossim
>>> 

OR

>>> from TOSSIM import *
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named TOSSIM
>>> 

I am using python version 2.6.6 and i've already set python path to : 
PYTHONPATH=/opt/tinyos-2.1.1/support/sdk/python

And here's file(s) on /opt/tinyos-2.1.1/support/sdk/python/tinyos/tossim :
__init__.py
__init__.pyc
TossimApp.py
TossimApp.pyc
TossimNescDecls.py
TossimNescDecls.pyc
Any files was missing ???

Pleaseeee anyone help meee, i'm soo stuck whit those errors :frown:
Please.. Thanks
Ps : Sorry for my bad english

---

### Post by deceaseddolphin on 2011-03-09
type: locate libpython
and check where your python library files are located. also check the versions in sim.extra, sim-sf.extra, sim-fast.extra files under /opt/tinyos-2.1.1/support/make folder

---

