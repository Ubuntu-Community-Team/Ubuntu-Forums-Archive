---
title: "python-visual broke in Karmic?"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by amyst on 2010-01-07
I have been using python visual, and import visual package in Jaunty. After I upgraded to Karmic, python-visual stops working. I get the following error message: 

/usr/lib/python2.6/dist-packages/visual/__init__.pyc in <module>()
     57 
     58 import crayola as color
---> 59 import cvisual
     60 cvisual.init_numpy()
     61 from cvisual import (vector, mag, mag2, norm, cross, rotate, comp, proj,

AttributeError: 'Boost.Python.StaticProperty' object attribute '__doc__' is read-only

A search in google [https://bugs.launchpad.net/ubuntu/+source/python-visual/+bug/408663](https://bugs.launchpad.net/ubuntu/+source/python-visual/+bug/408663)
appears that someone has found an incompatibility between Karmic and libboost-python-dev back in August. I updated libboost-python-dev to 1.4 version, but the problem persists. 

Does anyone know a solution to this? I would prefer not going back to Jaunty :(

---

