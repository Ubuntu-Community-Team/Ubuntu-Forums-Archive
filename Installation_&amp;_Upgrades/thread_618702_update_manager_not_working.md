---
title: "update manager not working"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by ubanchaos on 2007-11-20
well i dont kno whats wrong and it just comes up with some things about


 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by taurus on 2007-11-20
Close down Add/Remove, synaptic, or whatever window you have when you get that error message.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by wolfger on 2007-11-20
> **taurus said:**
> Close down Add/Remove, synaptic, or whatever window you have when you get that error message.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

Error on the first step:
```
wolfger@bravo:~$ sudo dpkg --configure -a
[sudo] password for wolfger:
Setting up xcwcp (2.3-6) ...
dpkg: error processing xcwcp (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 xcwcp

```

---

