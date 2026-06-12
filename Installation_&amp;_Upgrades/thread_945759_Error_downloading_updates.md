---
title: "Error downloading updates"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by paddy1 on 2008-10-12
The following is the error I get when downloading updates;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I then opened terminal and ran sudo dpkg --configure -a to repair

This is the result;


user@user-desktop:~$ sudo dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory

Any suggestions pleaseÉ

---

