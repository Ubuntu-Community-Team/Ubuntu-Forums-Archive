---
title: "Maximum Number of Partitions when trying to dual boot"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Zeenomorph on 2008-04-26
I just got a new computer with Ubuntu 7.10installed.  I want to dual boot with XP (for gaming) so I made a partition for it, and put in my windows disk. 

The problem happens when windows asks me to select a partition.  It says that there is the maximum number already.  

First is a small one that gparted says is the 'boot'
Next is the Linux swap one
Now is my big data one
and last is the spot that I wanted to put windows in

When I select that spot, I'm denied.  Any ideas?

---

### Post by obidose on 2008-04-26
I think windows has to go at the start of the disk from what I have heard. With that in mind maybe it would be easiest to install windows on the disk by formatting it completely.

Then you can get dl an ubuntu CD (the nice newer version than the one you have pre installed, updating to it would require just as much downloading)

You can use the automated installer on the cd to stick ubuntu on the disk with windows and it will set up grub to dual boot.

---

### Post by lemming465 on 2008-04-26
Include the output of "sudo fdisk -l" and we can give you more specific advice.

On DOS-style disk partitioning, which is what everything except Mac OS-X and Intel Itanium servers uses, you only get 4 "primary" partitions.  You can have up to 11 more logical partitions inside a single "extended" partition.  Both Linux and XP or Vista can run just fine from logical partitions, but the boot loaders like to have primary partitions.

If you have a 4th partition already intended for Windows, make sure the partition type is set to "7" (NTFS/HPFS).  Otherwise the windows installer won't see it, and if you don't have either an extended partition or spare disk space, it will be out of options.  You can do this by using the "t" (type) command in fdisk, among other ways.

---

