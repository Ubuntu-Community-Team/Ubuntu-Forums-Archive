---
title: "update error"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by simonlugi on 2008-09-07
When trying to download updates I get the following error message 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can someone let me know how to fix this.

---

### Post by forger on 2008-09-07
open up Applications > Accessories > Terminal and execute the following commands:
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
```

---

### Post by simonlugi on 2008-09-07
Thanks that sorted the problem

---

