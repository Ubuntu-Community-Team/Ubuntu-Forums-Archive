---
title: "Error when try to update"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by ghoracek on 2008-01-10
Using GutsyGibbon 7.1 on a laptop and I note there are 15 updates  to install.  Going through the process and I get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Which is totally Greek.  I tried opening a terminal to type in ´sudo dpkg --configure -a´, but that is clearly not what is intended.  

What am I supposed to do?

glh

---

### Post by taurus on 2008-01-10
Close synaptic or Add/Remove.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by ghoracek on 2008-01-10
Worked!! Cool. 

glh

---

