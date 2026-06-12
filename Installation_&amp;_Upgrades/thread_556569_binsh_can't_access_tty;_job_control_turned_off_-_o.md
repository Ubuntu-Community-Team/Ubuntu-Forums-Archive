---
title: "/bin/sh: can't access tty; job control turned off - one solution"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by dj_deef on 2007-09-21
one solution to this problem (when it comes after the installation) is to set root=UUID=yourhduuid in menu.lst (grub) and set the device mount by UUID in fstab

I think the error come out because sometimes kernel assings a different name to a device.
i.e. we expect /dev/sda and the kernel calls it /dev/sdb

---

### Post by Pumalite on 2007-09-21
Add your solution to the thread with the same name.

---

