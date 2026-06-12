---
title: "How to avoid RAID during installation?"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by tomcatf14 on 2007-10-17
Another problem occurred, the disk is RAIDED before. Now i am reinstall Ubuntu on the same disk. On the disk partition menu, i have removed all the RAID (MD) and ensure that the partition is only use for ext2 and swap (not raid). However, after the installation completed i saw RAID is installed!! How could that be? How do i avoid this? I want a new installation w/o RAID

---

### Post by kidders on 2007-10-18
Hi there,

The ability to handle RAID devices is a core part of the operating system ... you can't remove it, unless you are willing to recompile your kernel.

The same goes for PS/2 mouse support, SATA interface support, USB support, and hundreds of other things. In addition, Ubuntu automatically installs software for a huge variety of display adapters, and so on ... no user could possibly make use of *all* supported hardware. Normally though, this is seen as a good thing; people who don't need RAID support simply don't use it.

You *can* remove RAID support if your really want to, but the gain would be a negligable amount of disk space and (theoretically) an imperceptibly small increase in performance.

---

### Post by psusi on 2007-10-18
He isn't talking about removing raid [i]support[i], but just destroying the existing raid configuration of the disks.  You need to run sudo mdadm --zero-superblock /dev/sda, assuming sda is one of the drives in the array.  Repeat for each drive in the array.

---

