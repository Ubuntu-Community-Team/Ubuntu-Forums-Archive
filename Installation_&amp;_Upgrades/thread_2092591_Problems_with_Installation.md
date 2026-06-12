---
title: "Problems with Installation"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by URL4n0t4found on 2012-12-08
Hi everyone,

i bought myself an HTPC and I thought Ubunutu would be the best OS to run it.

When I boot the installation routine (no options set) after some time it freezes with "ata8: hard resetting link". When switch from AHCI to IDE in the UEFI or start the installation with the option ahci=off the system boots but the installation routine says that there is not enough space on the disk - it doesn't see the harddisk. In gparted it doesn't show up as well. The disk is a SSD btw. I boot the installation from USB with a stick made with Universal-USB-Installer-1.9.1.8. 

Windows (7 and 8) installed fine on the machine.

Thx for the help and so long,
404

---

### Post by oldfred on 2012-12-08
Is it just one SSD or one of these Intel SRT that is both a HD & SSD? Those use some sort of RAID that causes issues.

Also if you created partitions in Windows you may have converted from basic partitions to dynamic if in BIOS mode? Dynamic partitions is proprietary to Windows and does not work with Linux.

Post this:

       sudo parted /dev/sda unit s print

---

