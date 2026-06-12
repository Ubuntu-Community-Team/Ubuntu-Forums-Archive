---
title: "Dual boot advise... Gentoo &amp; Ubuntu"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by Aerodyne on 2005-06-16
Hi all,

Okay have not done this before ... so your help and advice would be appreciated.

Installed on the machine is Gentoo 2004 (2.6.10-gentoo-r4)... I have not got root access to it though!  I want to install Ubuntu as a dual boot option (but Gentoo boots by defualt), is it possible to do this with out screwing up Gentoo's installation & be able to select it from the Grub menu?

How easy is Ubuntu installation process/system? (i.e. is every thing configured for you).

-------------------
System spec:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md1              61430440   6372188  55058252  11% /
/dev/md2              40948120   7717644  33230476  19% /home
/dev/md3              30715088   1113308  29601780   4% /opt
none                    452356         0    452356   0% /dev/shm
/dev/cdroms/cdrom0      600886    600886         0 100% /mnt/cdrom

/dev/md1 is the root filesystem (according to Control Center)
VGA card nVidia
2 HDD RAID...albiet I don't need Ubuntu to use RAID, just installed to 1 hdd
2 iiyama monitors (dual monitor)

TIA & much obliged all.

---

### Post by Xian on 2005-06-16
[QUOTE=Aerodyne]Installed on the machine is Gentoo 2004 (2.6.10-gentoo-r4)... I have not got root access to it though!  I want to install Ubuntu as a dual boot option (but Gentoo boots by defualt), is it possible to do this with out screwing up Gentoo's installation & be able to select it from the Grub menu?

How easy is Ubuntu installation process/system? (i.e. is every thing configured for you).[/QUOTE]
The easiest way to do this would be to install Ubuntu and let it auto-detect your Gentoo partition, which will then add its bootloader (/boot/grub/menu.lst) parameters to what Ubuntu sends to the MBR, and then you will be able to choose either one on your initial boot after installation.

---

