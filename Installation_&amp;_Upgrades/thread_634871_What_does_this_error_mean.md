---
title: "What does this error mean?"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by NobleRooster on 2007-12-08
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct
the problem. 
E: _cache->open() failed, please report.


I have no idea what this means.  It says it everytime I try to install something.

---

### Post by PmDematagoda on 2007-12-08
It means that you stopped a package managing process uncleanly.

To fix it, do:-

```
sudo dpkg --configure -a
```

---

