---
title: "installation fails to detect MPT-Fusion hardware"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by molafish on 2008-05-20
During 8.04 LTS Server installation, disk detection fails for me on a system with 1 SCSI drive on a LSI Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI adapter (PCI vendor ID 0x1000 device ID 0x0030).

I tried selecting the mptscsih driver, as well as megaraid-mbox. These were based on guidance from:

[http://ubuntuforums.org/archive/index.php/t-201858.html](http://ubuntuforums.org/archive/index.php/t-201858.html) (post by zagadka)
[http://cateee.net/lkddb/web-lkddb/FUSION_SPI.html](http://cateee.net/lkddb/web-lkddb/FUSION_SPI.html)

According to Ubuntu v5 release notes and the corresponding problem description for that release ([http://ubuntuforums.org/archive/index.php/t-13647.html](http://ubuntuforums.org/archive/index.php/t-13647.html) (post by Thibaut Varene)), issues with HW detection with MPT-Fusion were fixed way back then.

I opened the ash shell from the installer and tried modprobe mptscsih, but disk detection still fails with "No disk drive was detected" and a driver selection screen.

I know that the drive and adapter work by using another OS.

What am I missing, how do I proceed?

---

