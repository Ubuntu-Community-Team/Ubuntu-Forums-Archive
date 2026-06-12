---
title: "RAID install?"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by pwaldo on 2006-06-15
Hi all,

I'm trying to install from the Alternate CD.  I used Manual Partition to create two RIAD partitions:
/boot RAID 1
/ RAID 5

The install fails on writing the GRUB bootloader, so I go to the next step, writing LILO to /dev/md0.  When the install is done and I reboot, LILO starts to load then dies with this message:

L 99 99 99 ...

Any ideas?  Thanks in advance!

---

