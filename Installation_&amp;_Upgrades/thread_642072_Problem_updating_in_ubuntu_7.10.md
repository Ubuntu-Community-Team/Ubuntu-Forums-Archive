---
title: "Problem updating in ubuntu 7.10"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by dwaynefuller on 2007-12-16
Whenever I try to update using the update manager it stalls and gives this error message. 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do I do?

---

### Post by Sef on 2007-12-16
Applications > Accessories > Terminal

then type or copy and paste this code:

```
sudo dpkg --configure -a
```

That should fix your problem.

---

