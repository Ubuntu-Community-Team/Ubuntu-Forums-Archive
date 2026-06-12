---
title: "GRUB hard disk error on fresh RAID install"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by dreamer.redeemer on 2008-01-28
Clean install of Gutsy Server, set up partitions manually for softwareRAID like so:
Drive 1: auto partitioned into 2 partitions, root and swap
drive 2: same as drive one
changed all 4 partitions to "use as physical volume for RAID"
disks 3 and 4: one partition, use for RAID.
set up RAID as RAID1, 3 different devices: 1 for root, 1 for swap(disks 1 and 2), 1 for home (on disks 3 and 4)
went back to partitioner, set raid device 1, which happened to be the home partition, to mount as /home
set raid device 2 to mount as /
set raid device 3 to mount as swap
wrote changes to disk, finished installation, and got the "GRUB hard disk error"

I know from googling that this means grub can't map the disk geometry, which isn't very suprising.
Booted into knoppix and both RAID devices are there, and root has all the stuff in it it's supposed to have.

Did i do something wrong? possibly RAIDing the swap is wrong? What do i do next?

Thanks!

---

### Post by dreamer.redeemer on 2008-01-28
I got ubuntu to load by unplugging the second hd in the array. Now, trying to edit the grub configuration, typing "device (hd0) /dev/sda" as well as sdb gives "Error 15: file not found"

any suggestions?

---

