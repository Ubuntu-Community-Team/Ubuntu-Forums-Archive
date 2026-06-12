---
title: "having problems with updates"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by Tehal on 2008-02-29
When I try to install this is what error i get


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I dont understand this what can i do


Thanks

---

### Post by zvacet on 2008-02-29
Applications>accessories>terminal type


```
sudo dpkg --configure -a
```

---

### Post by Pumalite on 2008-02-29
sudo dpkg --configure -a (at the terminal)
Post the output here.

---

### Post by Tehal on 2008-02-29
Working now


Thanks

---

