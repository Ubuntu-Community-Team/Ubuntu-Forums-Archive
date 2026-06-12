---
title: "Help with updating"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by sk8jpg on 2008-02-10
Hey guys,
I just installed 7.10 and I want to update everything but whenever i go to the Update Manager and click *Install Updates* this messgae pops up....


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do I do?

---

### Post by Partyboi2 on 2008-02-10
Opened a terminal (Applications>Accessories>Terminal)
and 
```
sudo dpkg --configure -a
```If you have not already done so.

---

