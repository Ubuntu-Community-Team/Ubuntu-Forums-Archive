---
title: "Feisty / SW Raid5 / LVM install fails to install LILO"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by cmreigrut on 2007-07-20
First, some background:  I have an old machine (formerly running Windows 2003) that I'm rebuilding into an internal server.  It has an Adaptec ARO-1000 (RAIDport III) card for RAID  but there doesn't seem to be any support for it, so my plan was to skip it and do software RAID5 across the three SCSI drives.  I actually have a fourth, but intend to use it as a cold spare.

Anyway, when installing from the alternate CD, I've partitioned everything as follows:
sda/sdb/sdc are configured as bootable logical partitions for RAID
one MD device (RAID5) using all three of the above
one LVM group using the MD device with three logical volumes: BOOT (ext2 /boot), SWAP (swap) and ROOT (ext3 /)

Life is good, and the install continues right up until it tries to install LILO (on /dev/md0), which seems to install but then fails when running /sbin/lilo (error code 1).  Skipping the LILO installation leaves me with an Operating System Not Found at the reboot.

What am I missing here?  Do I actually have to partition each of the three physical drives into three partitions(for boot, swap and root) , and then create three MD devices (from the three boots, swaps and roots, respectively)?  That sounds painful (especially when I have to fix things later if a drive fails).  Any other ideas?

---

