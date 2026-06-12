---
title: "Update and Program Installation Problem in Hardy"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by Roundel on 2008-07-31
Hi,

I'm using Hardy on an HP ZD7000. After months without problems, I am suddenly unable to install anything using the package manager.  I get the following error in the terminal, synaptic window, update manager, etc.

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've tried running the suggested command in the terminal and nothing happened.  Any suggestions?

Thank you in advance!

-Roundel

---

### Post by Potatoj316 on 2008-07-31
```
sudo dpkg --configure -a
```

---

