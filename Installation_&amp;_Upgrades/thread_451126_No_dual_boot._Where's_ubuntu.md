---
title: "No dual boot. Where's ubuntu?"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by benst on 2007-05-22
Hi all,

I just installed Ubuntu 7.04 using a live CD. I followed the instructions on the Community Docs site for a dual boot installation, but Ubuntu didn't detect a windows installation so it didn't modify the mbr if I'm not mistaken, and it just boots straight into WinXP without prompting me to choose an OS.

The first hard disk is a 250GB SATA, with a 100GB partition for windows XP, and I used Ubuntu to create a 30GB partition (and I checked the logical drive option) for the root partition and a 2GB swap partition, all on the first hard disk.

I can see the new partitions under WinXP as "unknown but healthy" partitions.
Is it possible to set up a dual boot once ubuntu has been installed like this?

Any help would be greatly appreciated.

---

### Post by confused57 on 2007-05-22
> **benst said:**
> Hi all,

I just installed Ubuntu 7.04 using a live CD. I followed the instructions on the Community Docs site for a dual boot installation, but Ubuntu didn't detect a windows installation so it didn't modify the mbr if I'm not mistaken, and it just boots straight into WinXP without prompting me to choose an OS.

The first hard disk is a 250GB SATA, with a 100GB partition for windows XP, and I used Ubuntu to create a 30GB partition (and I checked the logical drive option) for the root partition and a 2GB swap partition, all on the first hard disk.

I can see the new partitions under WinXP as "unknown but healthy" partitions.
Is it possible to set up a dual boot once ubuntu has been installed like this?

Any help would be greatly appreciated.

Boot up the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

There is a way to install grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Post the output of "sudo fdisk -l" before you attempt to install grub.  Do you get any prompt during bootup of your computer to press "Esc" to enter grub?

---

