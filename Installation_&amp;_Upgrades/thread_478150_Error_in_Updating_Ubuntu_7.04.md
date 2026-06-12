---
title: "Error in Updating Ubuntu 7.04"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by ozzyp9 on 2007-06-19
When I try and update Ubuntu 7.04 through the package manager i get an error that says 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


and then when i run "dpkg --configure -a" it says "dpkg: requested operation requires superuser privilege"

What should I do?

---

### Post by beatbros on 2007-06-19
hi,
try
```
sudo dpkg --configure -a
```

---

### Post by dayhawk4 on 2007-06-19
Directly running sudo dpkg would work, or you could open a super user shell by typing

sudo su -
dpkg .....

---

