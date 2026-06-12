---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by nosjunkie on 2008-09-11
I can't update/install packages anymore...I keep getting this warning.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Anyone know how to fix that??

---

### Post by Oldsoldier2003 on 2008-09-11
> **nosjunkie said:**
> I can't update/install packages anymore...I keep getting this warning.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Anyone know how to fix that??

```
sudo dpkg --configure -a
```The error message doesn't mention you need to run as superuser.

---

### Post by cdtech on 2008-09-11
I run both "sudo dpkg --configure -a && sudo apt-get -f install" at the same time.

---

### Post by Sef on 2008-09-11
> I run both "sudo dpkg --configure -a && sudo apt-get -f install" at the same time.


Sometimes just the former will work just fine.   Best to do one at a time to see if the latter is needed or not.

---

