---
title: "Ubuntu setup on an already-partitioned Windows 7 computer"
date: 2014-09-13
forum: Installation &amp; Upgrades
---

### Post by cyberpunk3 on 2014-09-13
The computer already has 4 partitions:
sda1 - Windows 7 (NTFS)
sda2 - data partition (NTFS)
sda3 - ext4 (currently empty)
sda4 - linux swap (currently empty)

I prepared sda3 and sda4 a while ago to put Linux there, using gparted live. I booted Ubuntu 14.04.1, went straight to install, chose "something else" (or something like that) to choose the partition myself... but it doesn't seem to like my layout. It says "no root filesystem is defined". Where do I go from here? I assumed it would be straightforward with sda3 holding system and sda4 for swap.

---

### Post by fantab on 2014-09-13
You have to setup the moutpoints from the installer.
Select the partition, /dev/sda3 and click 'Change'...
Setup your partition as follows:
Use As = Ext4 journaling system
Mountpoint = /
Format = yes

For SWAP:
Use As = linux-SWAP
format = yes

Make sure your the boot-loader 'GRUB' is installed to /dev/sda, the HDD and not the Partition, like /dev/sda3.

---

