---
title: "PHP4 unmet dependency"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by Tyler Durden on 2005-03-09
Hi,
I've downloaded and installed Ubuntu Warty, but when i do a: ```
apt-get install php4
```
i get:
```
The following packages have unmet dependencies:
  php4: Depends: libmm13 but it is not installable
E: Broken packages
``` 
Anyone have this problem?
tanks,
 Tyler

---

### Post by Tyler Durden on 2005-03-09
Solved!
/etc/apt/sources.list missing parameters.

Thanks anyway

---

