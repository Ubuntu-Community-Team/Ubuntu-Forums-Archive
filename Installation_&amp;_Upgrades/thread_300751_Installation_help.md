---
title: "Installation help"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by vaultrik on 2006-11-16
Hi, I have downloaded a xubuntu 6.10 alternate cd and want to install. The problem is, I have WIN fat16 installed.
I use pata disk with 3 partitions. hda3=win ; hda2=ext3,empty ; hda1=linux swap. I used Knoppix.
When I get to partitioning during the installation of xubuntu (with win already installed) I don't know what to do. I of course want to leave win partition without changes, as well as MBR. GRUB I'd like to have in hda2 partition, with the need of booting from floppy.
To which partition should I set bootable flag? Currently it is set on hda3=win. And is there an understandable possibility to put grub on hda2 instead of MBR?
Thank you very much:)

---

### Post by cotcot on 2006-11-16
With the alternate install CD you have the possibbility to install the bootloader on a floppy. When you pop in the floppy (supposing your bios is configured that it is the first boot device) and boot you will have ubuntu. With the floppy out tyou will have XP.
Leave the boot flag on your XP partition.

---

