---
title: "Create live usb with dynamic list OS"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by Brantner on 2012-03-12
Hello!

I decide a problem - there is a live usb, which have 2 OS: Ubuntu and Debian (Ubuntu - OS for work, Debian contains Clonezilla). Loader - SYSLINUX.
There are 2 profiles in the syslinux.cfg, to boot each OS. I am coding a program, which will work on Ubuntu. It should be able to add a profile in syslinux.cfg (for example, start clonezilla with certain parameters). In Debian will be a script, that deletes the added profile of syslinux.cfg (after Clonezilla work).

Question - is it possible to modify the syslinux.cfg, as we have already loaded in one of the OS (and, if so - how to get there?)

I will be happy with any ideas, until changing the boot loader.

---

