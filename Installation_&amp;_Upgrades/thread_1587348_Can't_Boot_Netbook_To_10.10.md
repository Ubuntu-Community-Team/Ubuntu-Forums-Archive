---
title: "Can't Boot Netbook To 10.10"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by ..::| Dave89 |::.. on 2010-10-03
I have an Acer Aspire One netbook, that used to have Windows 7 Starter one it.  I downloaded Ubuntu 10.10 Netbook RC and created a LiveUSB, but upon installing, it won't boot, just keeps saying something like bootable disk not found.  I've tried 4 times, using both the advanced partitioning and install alongside existing OS, the only time I had it booting was when I used the advanced partitioner and accidentally installed GRUB to the USB stick I was installing from.  I've tried telling the install to install bootloader to sdb1 (root partition) but no luck. The only other partition I have is a 11.9 GB Windows restore partition that I want to keep.  I deleted my Android and "System Reserved Partition", which I think was to do with the Windows bootloader.  That kept trying to boot Windows even though it wasn't there any more, which is why I deleted it.  I created the LiveUSB with Linux Live USB Creator, which was the only way I could successfully make a bootable one.

EDIT:  It appears to have installed GRUB to the USB stick, even though last time I used the install alongside existing OS.  I'm going to attempt to install GRUB to the root partition, so I don't need the USB stick to boot.

EDIT #2:  Found a nice tutorial at [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD and managed to install GRUB to the HDD.  Now works perfectly.

---

