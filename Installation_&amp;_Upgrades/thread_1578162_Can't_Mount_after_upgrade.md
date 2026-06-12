---
title: "Can't Mount after upgrade"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by bradydehart on 2010-09-20
This is the second time this has happened to me (after the first, i simply reinstalled but I would like to learn how to fix it). After a set of upgrades, when I restart, I get the following...



Killed
mount: mounting /dev on/root/dev failed: No such file or directory
mount: mounting /sys on/root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file ore directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


There are a string of numbers before this but I figure what I copied is the key material needed to find a solution. I am pretty new to Ubuntu, so I have no idea what to do from here. I have backed everything up through Ubuntu One so it isn't a huge deal to reinstall but if this is going to continue to happen, I would rather learn how to fix it. Thanks for any help you are willing to give!

---

### Post by dino99 on 2010-09-20
what kind of installation have you made ? you seem to use a chroot process.

---

### Post by bradydehart on 2010-09-20
I don't entirely know what you mean but I installed Ubuntu through the 10.04 disk. The upgrades simply came through direct download through the update manager.

---

