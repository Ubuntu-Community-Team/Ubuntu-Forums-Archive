---
title: "grub2 says no such partition for other os"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by Aliano on 2009-11-19
I've installed 9.10 and at the end of the install it looks for other os and finds my PCLinuxOS on sdb7. When I reboot and select PCLinuxOS is gives message no such partition. I tried command line to update grub and it finds pclos alright but the results are the same. I've tried to find if anyone else has come across this and it looks like it's just me............Aliano

---

### Post by lemming465 on 2009-11-21
Could we see the output of *sudo head -n 1000 /etc/fstab /proc/partitions /boot/grub/menu.lst /boot/grub/grub.cfg; sudo blkid*?

Do you know if PCLinuxOS was mounting swap space by partition device (e.g. /dev/sdb8) or by UUID?  The reinstall may have reformatted a swap partition being shared by the two OS's.

---

