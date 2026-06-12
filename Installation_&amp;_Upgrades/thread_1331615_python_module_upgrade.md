---
title: "python module upgrade"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by A Feyn Man on 2009-11-19
I am trying to upgrade my numpy python module from the repository version (1.2.1) to the latest version (1.3) and I am having trouble.
I used:
:~$ wget [http://sourceforge.net/projects/numpy/files/NumPy/1.3.0/numpy-1.3.0.tar.gz/download](http://sourceforge.net/projects/numpy/files/NumPy/1.3.0/numpy-1.3.0.tar.gz/download)
:~$ tar zxf numpy-1.3.0.tar.gz
:~$ cd numpy-1.3.0/
:~$ python setup.py install

and it ran fine and installed. When I used ipython to import numpy to see the version it was accessing and it was still the old 1.2.1 version. So I went to Synaptic to see if I could simply uninstall 1.2.1 but it said I would have to uninstall another module that is dependent on it and I can't lose the other module because I just want to switch version 1.3 with 1.2.1.

What do I do?
(PS I'm still with Jaunty)

---

### Post by A Feyn Man on 2009-11-19
Nevermind I worked it out

---

