---
title: "Grub fails during dual boot install"
date: 2017-12-23
forum: Installation &amp; Upgrades
---

### Post by jaganadhg on 2017-12-23
Hi
I am trying to install Ubuntu 16.4 in Dell Inspiron 15 7000. It gives grub instllation failure error. Any clue on how tonreaolve it

---

### Post by oldfred on 2017-12-23
UEFI or BIOS install.
What is specific error.
If system is UEFI and Windows is UEFI, and you install Ubuntu in BIOS mode without the bios_grub partition, you get grub install errors. Better to have Ubuntu in UEFI mode, anyway.
Sometimes the FAT32 partition that is the ESP - efi system partition needs repair and then you get grub errors on UEFI installs.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

