---
title: "error 21 solutions (a.k.a. GRUB MADNESS!)"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by Inferno3000 on 2005-08-25
It seems that more people have suffered, or suffer, from the so-called "GRUB-madness".
After installing the first stage of Ubuntu, it seems that the computer cannot boot ubuntu, nor Windows.
Error 21 is an error that occurs when GRUB cannot "find the disk"... Meaning that it cannot load the multiboot app from a specified harddisk.

The problem is quite uncommon as GRUB itself is an intelligent piece of software that finds its way itself, BUT:

due to:

1) A bad installation of GRUB might give an error like this.
1a) Solution: Try reinstalling GRUB (just follow the installation as usual, keep on clicking on continue until you reach the partitioner, choose for a manual partition and proceed as usual (do _NOT_ format the harddisk) and just ignore all the errors, after reinstalling, just reboot the PC)

2) A problem with the wiring of the harddisks might give an error like this (usually when you have more than 2 harddisks)
2a) GRUB only works if you install it on a master/slave of the same sort... Meaning that if you have a harddisk HD0 (Windows installation harddisk, or c:\ to speak in windows terms), a HD1 (let's call it d:\) and a HD"2" (e:\), and HD0 + HD1 being the respectively primary master and primary slave, it isn't possible to install Ubuntu on a secondary master or slave (HD"2").
My solution was to rewire the harddrives, making HD3 the slave of HD1 and HD2 the secondary slave of the CDrom drive (might change that in the future... But for the time being this is my solution).
Make sure you set the jumpers correctly.
After rewiring, follow the steps at 1(a). If that doesn't work.. Reinstall Ubuntu completely.

Unsure about what the primary or secondary masters/slaves are? Watch the bootscreen of your pc, or enter the bios (setup) by pressing "del" or "f1" during boot, and look in the CMOS or the HDD section.

Good luck, and if you need any help: post!

---

