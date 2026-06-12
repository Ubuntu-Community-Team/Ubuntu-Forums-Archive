---
title: "drives detected as scsi (sda, sdb, etc)"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by laughing_at_you101 on 2007-06-04
hello, when i run the ubuntu 7.04 disk from livecd, it detects all my drives as scsi, i go to run the install and it fails to install grub (i've only tried this once). i have looked in the forums, and havn't found anything. one of my friends said they had the same problem. i have installed, ubuntu 6.10 flawlessly, so i don't know why 7.04 isn't working, i know the cd is good because i got them from shipit. and none of my drives are scsi.

---

### Post by arkham on 2007-06-07
Your drives are probably SATA - which is also a serial drive interface and uses similar drivers to SCSI in Linux.  SCSI was around first, long before SATA, so you till have a lot of assumptions that these drives are SCSI rather than saying SCSI/SATA.

It's doubtful that this is the source of your problem, more info on the grub error would be helpful.

---

