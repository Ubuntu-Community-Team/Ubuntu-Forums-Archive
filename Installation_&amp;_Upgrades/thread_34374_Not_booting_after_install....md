---
title: "Not booting after install..."
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by andrew-Q on 2005-05-14
I installed u5.04 into hdd, my 2nd IDE disk. I answered not to install grub to the mbr as I want to keep the xp bootloader intact. When I choose this disk for boot in the BIOS, it shows a boot menu with kernel, mem tests etc and even xp. However nothing boots from these menu choices and I'm obliged to use the BIOS to boot from and use my xp install. At no moment during the Ubuntu install was it possible to create a floppy!

Is it worthwhile trying a 3rd party boot manager to get Ubuntu booted?

Any ideas?

---

### Post by nad on 2005-05-14
Grub appears to be installed to your second drive, however, its' configuration files may not be pointing to the correct location.

Open the file /boot/grub/menu.lst and confirm that the #groot line points to (hd1,0) if your /boot partition/directory is the first of your second drive, and that all the root entries point here also if this is the location of your / file system.

Using a third party boot manager is only asking for additional problems.

---

