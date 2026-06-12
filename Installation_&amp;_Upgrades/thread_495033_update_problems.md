---
title: "update problems"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by zac07 on 2007-07-07
when I try to update it tells me:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

what do I need to do ?

                                               Thanks, 
                                                           Zac

---

### Post by taurus on 2007-07-07
Try

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by zac07 on 2007-07-07
thanks it works now

---

