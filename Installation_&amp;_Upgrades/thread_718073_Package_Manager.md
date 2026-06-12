---
title: "Package Manager"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by jnee8871 on 2008-03-07
Can some one help me resolve this message i get trying to use Package manager?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thank you

---

### Post by taurus on 2008-03-07
Close the package manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

