---
title: "Dual boot with suse pro 9.3"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by django_xl on 2005-11-01
Hi folks,
I have a amd64 3000+ system running suse 9.3 and I would like to install Breezy on it as a dual boot system.

I already have downloaded the iso image and burned it, but I wanted to know if this could be done easily.

My harddisk is currently being used solely by suse and has the reiserfs filesystem.

What do I have to do to install breezy on it such that I can dual boot?

Thanks in advanced,
Robert

---

### Post by MrCheese on 2005-11-01
Very quick howto :

first you need to make room for Breezy - either shrink the existing Suse system using qtparted, Partition Magic, etc, or fit a new hdd for it. If Breezy is being installed on the same hdd as SuSE, set up the partitions in the newly freed-up space to suit as normal and let it install. If you choose to create just "/" & "/home" the /boot stuff will live in /boot in the root partition, the system should also identify the existing swap partition and allow you to use it. 

Grub should scan the hdd and find the SuSE setup as well so will offer you dual-boot. If you use lilo with SuSE you can abort grub setup (or write the loader to a floppy) and add an entry into the SuSE lilo config.

---

