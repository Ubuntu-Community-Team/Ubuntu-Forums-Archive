---
title: "Creating a Raid 1 on a already running system"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by mistagetitright on 2014-08-21
Can I get someone to help me out on this issue.  I have tried several tutorials but I am having an issue somewhere along the line.  I just brought another 1TB hard-drive and installed it in my system.  Because I already had Ubuntu running on the hard-drive installed I couldn't use the motherboard raid.  So I started the path of trying to use the Ubuntu Raid.  All tutorials that I have tried just doesn't work out for me a some point and I am guess its because my hard-drive is partitioned as follows:
 

 
 Partition 1 /dev/sda1 EXT4 Mounted at Filesystem Root
 Partition 2 /dev/sda2 Extended  and with in this container there is:
                                     Partition 5 /dev/sda5 Linux swap I believe its /dev/mapper/cryptswap1 as this is showing under other devices but its the same size 8 GB
                                     Partition 6 /dev/sda6 W95 FAT32 mounted at /windows
 Partition 3 /dev/sda3 EXT4 mounted at /media/mistaquade/VMHOST
 Partition 4 /dev/sda4 EXT4 not mounted

Any help is greatly appreciated.

---

