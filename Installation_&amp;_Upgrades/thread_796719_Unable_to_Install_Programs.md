---
title: "Unable to Install Programs"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by Landscapeman on 2008-05-16
It keeps telling me that two software manager tools at the same time. I check update manager and try to update and got this message

An error occured
the following details are provided:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by atomkarinca on 2008-05-16
Open up a terminal (Applications > Accessories > Terminal) and type these:

```
sudo dpkg --configure -a
```

---

### Post by Landscapeman on 2008-05-16
Thank You

---

### Post by atomkarinca on 2008-05-16
No problem.

---

