---
title: "I just made a really big mistake!"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by xelapond on 2007-06-17
I was t a lan party with my gaming computer, dual booted with ubuntu 7.04 and windows XP.  I think I was using GRUB, but it was whichever one comes with ubuntu.  The Windows XP was not working properly for playing the games, so i reinstalled it.  I only reformatted its partition, but now i can not get into ubuntu.  I would just reinstall it but there was some stuff in there i would like to keep.

An advice on what I should do?  Is there a simple way to fix the ubuntu?

Also, in the end I do not care what bootloader i end up using.

---

### Post by Kubunteando on 2007-06-17
You can get a Ubuntu Live CD and reinstall GRUB.
It is really useful in case you have boot problems.

When you reinstall windows it overwrites the boot sector, so grub needs to be reinstalled.
Check the "grub-install" command.

---

### Post by Pumalite on 2007-06-17
> **Kubunteando said:**
> You can get a Ubuntu Live CD and reinstall GRUB.
It is really useful in case you have boot problems.

When you reinstall windows it overwrites the boot sector, so grub needs to be reinstalled.
Check the "grub-install" command.

Check this too:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

