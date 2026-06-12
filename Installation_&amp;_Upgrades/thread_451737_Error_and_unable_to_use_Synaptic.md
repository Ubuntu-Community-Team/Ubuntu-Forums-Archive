---
title: "Error and unable to use Synaptic"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by jazzybob on 2007-05-22
I get a messageage every time I try to install any package - I have run the specified command and the error still remains.  I am running an AMDAthalon 64.  

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any help would be gratefully welcome.

---

### Post by taurus on 2007-05-22
Open a terminal and run these commands to see what happens next.

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

