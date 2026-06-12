---
title: "RAID fills entire disk leaving no room for individual boot or swap partitions"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by born1962 on 2011-01-13
I am installing the latest version of Ubuntu server 10. I have four 2Tb SATA drives and wish to set up a RAID 6 software array. On the first disk I set up 200 mb for the grub boot loader, and 32 gb for the swap file and the remaining area as a RAID partition. In the RAID partition I have 200 gb as ext4 for the root and the remainder btrfs for /home.

When I set up the RAID 6 most of the hard disk space on the other 3 disks are consumed, leaving no room to create the swap file and boot partitions. Is the expected behavior. Should I slot a small drive in devoted to boot/swap ? I am concerned that should disk 1 fail I will never get to start up the other drives.

---

### Post by born1962 on 2011-02-22
Got it. I was under the mistaken impression that the RAID setup would take care of the partition arrangements for the other disks in the set. The answer was provided by a youtube video that explained that you need to set up the other disks in exactly the same way as the master drive.

---

