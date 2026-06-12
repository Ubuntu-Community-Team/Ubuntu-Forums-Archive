---
title: "Partitioner doesn't recognize RAID"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by someguywhoneedshelp on 2007-04-19
Hi, I'm trying to install Fiesty from the AMD64-Server CD onto a machine with hardware RAID 1.

The previous OS (Fedora Core 6) recognized the RAID and saw it as one disk, however the Ubuntu installer sees two identical SCSI disks:
```
SCSI1 (0,0,0) (sda) - 500.1 GB ATA HDC WD5000KS-00M
            #1 primary    10.5 GB B K ext3                   /media/sda1
            #2 primary     1.0 GB   F swap                  swap
            #3 primary   488.6 GB   K xfs                   /media/sda3
                 pri/log   8.2 MB         FREE SPACE
SCSI3 (0,0,0) (sdb) - 500.1 GB ATA HDC WD5000KS-00M
            #1 primary    10.5 GB B K ext3                   /media/sdb1
            #2 primary     1.0 GB   F swap                  swap
            #3 primary   488.6 GB   K xfs                   /media/sdb3
                 pri/log   8.2 MB         FREE SPACE
```
Is there anything I can do about this? I would very much like to give Ubuntu a go on this box.

---

### Post by askreet on 2007-04-19
It's probably a software raid controller that's not supported by Ubuntu.  Do you know what kind of controller it is?

---

### Post by someguywhoneedshelp on 2007-04-19
Thanks for the reply.

It's a hardware controller with an Intel ICH8R chipset.

---

