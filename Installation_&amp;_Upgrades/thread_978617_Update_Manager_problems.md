---
title: "Update Manager problems"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by kreeten9996 on 2008-11-11
Hey, I'm new to this Linux thing and I've been trying to download updates from the update manager but every time I click install updates I get a message saying.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

The downloads were working before, but then i had to close it before it could finish. Can someone help me?

---

### Post by taurus on 2008-11-11
Close the update window manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

