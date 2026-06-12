---
title: "BOOT ubuntu failed (grub also)"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by drunkez on 2007-10-08
Hi all
I have two disks
hd0 with winXP there
hd1 with two partitions hd1,0 where I just install ubuntu 7.04 and hd1,1 which is NTFS data partition
problem is
that when is system comes up i expect GRUB with OS chooser
but grub loads to some BASH like mode with command line like this

GRUB>

so what is the problem
thanks

---

### Post by Temik on 2007-10-08
Hmmmm I do not really know what is wrong with the grub menu. But in most cases you can fix any bootloader issues with SuperGrub disc.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
It helped me a lot. Hope it helps you too. ;-)
The best part about it is that you can load the kernel image directly from this disk without any bootloaders installed...

---

### Post by drunkez on 2007-10-08
ok i will try.....thanks

---

### Post by drunkez on 2007-10-08
just one question this supergrub is loader or tool to check mbr or what

---

### Post by Temik on 2007-10-08
It is an autoloader cd. It is a tool to reinstall , restore, backup and edit MBR Lilo and grub...

---

