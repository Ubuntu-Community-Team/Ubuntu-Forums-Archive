---
title: "error when trying to update"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by rob89ert on 2008-07-04
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by iaculallad on 2008-07-04
> **rob89ert said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

As the error displays, do the command below in your terminal:

```
sudo dpkg --configure -a
```

---

### Post by rob89ert on 2008-07-04
thanks! for the advice

---

