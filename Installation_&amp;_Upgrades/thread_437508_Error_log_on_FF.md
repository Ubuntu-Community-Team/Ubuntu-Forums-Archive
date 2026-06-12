---
title: "Error log on FF"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by Confyzone on 2007-05-08
Just upgraded to FF now when i run my update manager and try to install the updates i get this error. Also I get the same error when I run Package Manager.....so when i try to run this command in my terminal is says user with superuser privelages required....wtf does that mean? this is the error i get

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please repor"

---

### Post by zvacet on 2007-05-09
```
sudo dpkg --configure -a
```

---

