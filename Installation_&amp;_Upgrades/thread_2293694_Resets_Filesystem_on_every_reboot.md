---
title: "Resets Filesystem on every reboot"
date: 2015-09-06
forum: Installation &amp; Upgrades
---

### Post by Konstantin_Velitch on 2015-09-06
I have tried almost everything. 

Using Gparted I set up my SSD like this

First set a partition table gpt
_____________________

SDA1- 1024 MiB linux-swap swap space
SDA2- ~100 GiB  ext4 linux
SDA3- 512 MiB ext4 bootloader with the flag bios_grub

I then restart and go into my elementaryOS USB. 

From there I choose to partition my computer and set the linux partition mount point to '/'
It installs smoothly and I get a prompt to restart. 
As always once I restart it opens up the familiar message: Operation System Not Found

This happens every single time since removing the gnome-session package from my arch setup. 
I even tried installing Windows 7 but I get some whacked message about /boot/bcd and tells me to use a cd but I can't because the repair doesn't detect anything.

---

### Post by Konstantin_Velitch on 2015-09-07
Figured it out, no idea why it was breaking but after installing KXStudio it magically fixed itself.

---

