---
title: "If I move my SWAP partitition, will Ubunto keep booting"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by metramo on 2006-09-24
Need to move my SWAP partitition to obtain some space for an XP NTTFS partition on my harddisk. I installed Ubunto identifying the partition where it is now.

Will Ubunto be able to boot after? Will I have to modify something for Ubunto to find the new location?

By the way. I use Norton Partition Magic to do these modifications, but I
suppose it's impossible to modify/move the Ubuntu partition using this tool.
Would someone know a Partition managing tool (within or outside Ubuntu), which will be able to handle Linux partition and, better yet, BTFS partitions, and, better yet, be as user friendly as Norton PM?

---

### Post by bernied on 2006-09-24
If you move the swap partition, ubuntu will not be able to find it until you tell it where you put it. This information should be in /etc/fstab. If you move the partition that contains the bootloader (grub), then you will get an error at boot time, as the first part of the boot process (grub stage 1), which resides in the first 512 bytes on your first hard drive, references directly to the position on the disk of the rest of the boot files (grub stages 1_5 and 2). So, if you do move that partition you will have to reinstall grub - you can do this with the live-cd (I think). If you change the numbering of partitions (by inserting one between two pre-exisitng partitions, then you may need to change boot options for the kernel in the /boot/grub/menu.lst file ('boot=/dev/...'), and also possibly /etc/fstab entries as well.

Proceed with care.

---

### Post by bernied on 2006-09-24
I should have said that ubuntu will probably still boot without that swap space, unless you are low on RAM - 256M should be plenty enough for boot, maybe even less.

And the linux repartitioning tools are parted (command line) and gui relatives (gparted, qtparted, and I think cfparted). And fdisk is a more basic partitioning utility - it doesn't resize.

---

