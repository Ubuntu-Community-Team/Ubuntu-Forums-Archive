---
title: "help update manager problem"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by vrod222 on 2007-05-07
i keep getting this error,when I got and update:confused: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by taurus on 2007-05-07
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by vrod222 on 2007-05-07
thank you back to nolmal:guitar:

---

