---
title: "Can't install updates/programs"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by bokorpop on 2007-06-17
For reasons I do not understand, whenever I try to install updates or new programs, the following error message comes up.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. "

I have no idea what this means in plain english, somebody please help me.

---

### Post by zvacet on 2007-06-18
```
sudo dpkg --configure -a
```

---

