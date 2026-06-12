---
title: "AMD64 on Linux 64bit - Install fail"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by Nxqd3051990 on 2008-10-28
I've AMD64 X2 4600+ (SOcket 940) and I can't install ubuntu amd64 on it. 
It shows that my professor is not compatible :confused::confused:

Can you people tell me why ?

---

### Post by Sef on 2008-10-28
With Ubuntu, type in this command:  ```
uname -m
```.   It should say X86_64.  If it does not, then you have a 32-bit system, which a 64-bit system cannot be installed to.

---

