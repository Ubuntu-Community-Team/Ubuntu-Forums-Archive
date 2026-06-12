---
title: "error on installation interrupted help"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by ayet on 2008-07-10
how do you resolve this error on synaptic package manager

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to 
correct the problem. 
E: _cache->open() failed, please report.

---

### Post by iaculallad on 2008-07-10
> **ayet said:**
> how do you resolve this error on synaptic package manager

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to 
correct the problem. 
E: _cache->open() failed, please report.

As the error message says: Do the command below using your terminal

```
sudo dpkg --configure -a
```

---

### Post by ayet on 2008-07-10
tnks. problem solved

---

