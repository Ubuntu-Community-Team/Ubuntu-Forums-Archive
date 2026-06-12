---
title: "Dpkg error 100; can't upgrade"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by phobophilia on 2010-09-22
Having some troubles with updating here; aptitude won't work and ends on a dpkg error of sh: ```
dpkg: permission denied
``` (something like that.) I searched previous topics, and have tried the following:
```
sudo: dpkg --configure -a
sudo: dpkg: command not found
```

I've tried rasslin' with aptitude, but to no avail. Help?

EDIT: Scratch that- ```
 chmod 755 /usr/bin/dpkg 
```
Fixed it in a jiffy. Yay for archives!

---

### Post by Darkness Des on 2010-09-22
The command you are thinking of is *sudo*, as opposed to *sudo:*

This appears to be your only problem. Tell me if that works, at all.

---

