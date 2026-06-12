---
title: "Dual Boot XP/Ubuntu 7.04 w/ dual drives"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by RomanCross001 on 2007-09-29
I wish to create a dual boot system on my PC. I have XP installed and running on Primary Drive 0 IDE and Ubuntu installed but not currently running on separate SCSI Drive 0. Ubuntu drive was taken from a dedicated Linux PC and added to the dedicated Windows PC. Now I wish to edit the boot loader, etc. to enable me to see the Ubuntu drive and run either operating system of choice. A third SCSI drive contains my Windows PageFile in a NTFS partition and shared data on a FAT32 partition. Has anyone setup and configured a system similarly? Can you advise on the procedure to follow? Thank you.

---

### Post by logos34 on 2007-09-30
[Dual boot on dual drives]("http://ubuntuforums.org/showthread.php?t=179902")

You'll have to edit grub from the Feisty live cd, [changing the ubuntu root lines and adding XP entry.]("http://users.bigpond.net.au/hermanzone/p15.htm")

Then [install Grub to the windows drive MBR]("http://ubuntuforums.org/showthread.php?t=224351").

[Add windows (fat32, ntfs) partitions to linux fstab.]("http://www.psychocats.net/ubuntu/mountwindows")

---

