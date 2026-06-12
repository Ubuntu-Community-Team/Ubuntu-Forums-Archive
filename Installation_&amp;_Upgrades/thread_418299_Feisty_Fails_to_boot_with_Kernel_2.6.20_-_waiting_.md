---
title: "Feisty Fails to boot with Kernel 2.6.20 - waiting for root filesystem"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2007-04-22
After  downloading the alternate boot cd for Feisty 7.04 and installing in text mode, feisty still fails to boot with kernel 2.6.20.

The boot process starts normally then halts with waiting for root filesystem.  -  no further boot activity takes place, I cant login at an alternate console but can press ctrl-alt-delete to reboot my system.


I have narrowed this problem down to a couple of things:-
kernel 2.6.20
the configuration of the Feisty kernel
or the fact that I have  Solaris and FreeBSD also as primary partitions.

I have had the same problem with knoppix when testing out 2.6.20, but as yet have not had time to recompile the kernel.

The /etc/fstab in Ubuntu Feisty tries to mount all filesystems, on boot so am wondering if its the ufs2 or solaris bf partitions that are causing this problem.


To get Feisty to work I have installed a kernel and llib/modules from another linux system, so this now has to be a kernel or kernel config related issue.

Is there any way  to load the Edgy kernel back to use with Feisty, the repositories only contain 2.6.20. Thanks in advance or help or suggestions with this problem.

---

### Post by visik7 on 2007-04-22
paste your /etc/fstab and /boot/grub/menu.lst

---

