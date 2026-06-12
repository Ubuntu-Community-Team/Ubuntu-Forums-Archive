---
title: "[SOLVED] Grub menu maintenance"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by ithaka on 2007-09-07
All,


After being about half a year on Ubuntu I am wondering if it is not possible to get rid of removing the entries that are added over the time in the grub menu.

I know, minor inconvenience, but I am not (yet) a real linux adept, so I am not really keen on editing quite critical configuration files.

Or do I have to take this for granted?


Thanks for any feedback,

Olivier

---

### Post by erfahren on 2007-09-07
if you haven't done this, instead of completely removing entries just limit the number that actually show in the boot menu (I put 3). look for:
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=3

---

### Post by aidanr on 2007-09-07
```
gksudo gedit /boot/grub/menu.lst
```
and remove the old entries

---

### Post by ithaka on 2007-09-07
Thanks, will give this a try. Looks like what I 'need'.


> **erfahren said:**
> if you haven't done this, instead of completely removing entries just limit the number that actually show in the boot menu (I put 3). look for:
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=3

---

### Post by ithaka on 2007-10-18
Thanks, this indeed does the trick.

---

