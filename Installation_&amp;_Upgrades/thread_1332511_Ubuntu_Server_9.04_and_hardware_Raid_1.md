---
title: "Ubuntu Server 9.04 and hardware Raid 1"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by evayroberto on 2009-11-20
Hi. I'm trying to install Ubuntu Server 9.04 on a Dell Poweredge R200 with a hardware SAS 6/IR card, and configure RAID 1 (real hardware Raid).
Raid 1 are configured in card bios, Ubuntu installation seems fine (it detects only one hdd, so I suppose raid 1 is configured). When I do the partitions, I select one primary bootable partition with ext3 file system, and other primary non bootable partition for swap.
Installation finish, and Ubunty boots fine.
Now...I want to check if Raid1 is working properly, so I disconnect second hdd and systems works. Then, i connect it again and disconnect the first hdd...and BOOM! Linux begins to show errors and system cant continue working.
I reboot computer and it shows Raid inconsistency and begins to sync both drives.
My doubt is: RAID 1 must permit to work with one or another hdd connected???? Had I a bad understood of RAID 1 concept?
Thanks in advance

---

### Post by evayroberto on 2009-11-20
Nobody can help me????

---

