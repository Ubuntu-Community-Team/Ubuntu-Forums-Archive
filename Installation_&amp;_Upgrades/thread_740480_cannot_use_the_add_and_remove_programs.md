---
title: "cannot use the add and remove programs"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by girlleo19 on 2008-03-30
i was trying to install audicty and other programs from the add and remove programs but everytime I try to add some programs.. i get this message....

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


help i'm a total noobie in linux help!!!!!!!!!!!!!!!!!!!!!!!!!111

---

### Post by scragar on 2008-03-30
open up a terminal and copy/paste the line:
```
sudo dpkg --configure -a
```
the terminal lies under applications > accessories

---

