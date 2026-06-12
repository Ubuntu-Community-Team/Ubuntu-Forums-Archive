---
title: "gcc-version-check failed"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by dentaku on 2005-11-21
So far, it worked a dozen times but as I'm upgrading to breezy, installation fails with "gcc-version-check failed" 

> 
The compiler used to compile the kernel was gcc 3.4; the current compiler is gcc 4.0 


When I ignore this and continue, the following error appears after built:

> 
Unable to load kernel module 'nvidia.ko'. This is most likely because the kernel module was built using wrong kernel source files. 


WHat can I do to solve this problem?

---

### Post by 23meg on 2005-11-21
Reinstall the Nvidia drivers using the official 7667 package, entering ```
CC=gcc-3.4
export CC
```
before starting installation.

---

### Post by dentaku on 2005-11-21
Yup - that worked - thanks! Finally, GNOME is back. But now, many applications don't work anymore: "speicherzugriffsfehler" (english: memeory access error=, e.g. OpenOffice, Xine, etc.

---

### Post by 23meg on 2005-11-21
Which apps exactly, and what are the exact errors you get when you try to run them from terminal? Maybe you should open a new thread since this is unrelated with gcc version check / nvidia drivers.

---

