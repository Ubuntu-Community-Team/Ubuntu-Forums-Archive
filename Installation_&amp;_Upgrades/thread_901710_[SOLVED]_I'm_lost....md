---
title: "[SOLVED] I'm lost..."
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by youknowwhat4q on 2008-08-26
So up until last night the Update Manager was working wonderfully, then out of the blue it started spitting out this message every time I attempt to update, or add programs.

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I'm completely lost, and almost tempted to get rid of ubuntu all together.

---

### Post by tamoneya on 2008-08-26
open up terminal (applications -> accessories -> terminal) and type:```
sudo dpkg --configure -a
```

---

### Post by youknowwhat4q on 2008-08-26
> **tamoneya said:**
> open up terminal (applications -> accessories -> terminal) and type:```
sudo dpkg --configure -a
```

Nevermind, 

When I attempted the code before it ignored it, tried again, it worked (I think).

---

