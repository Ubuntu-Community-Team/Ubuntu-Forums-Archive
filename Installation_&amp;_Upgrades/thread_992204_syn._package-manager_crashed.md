---
title: "syn. package-manager crashed"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by Kerato on 2008-11-24
when i try to start syn. package manager it says:

an error occured

the following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please help

---

### Post by taurus on 2008-11-24
Close synaptic package manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by Kerato on 2008-11-24
thanx it worked :D

---

