---
title: "Hard Drive Order Problems"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by broth420 on 2008-08-11
I am trying to install Ubuntu 8.04 Server on a system with 1 250GB SATA hard drive as the primary drive and a 3ware 9650 array as a storage drive.  There are 4 500GB drives attached to the 3ware controller running RAID5.  Parition is simple; on the 250GB drive, I have swap, /, /var, and /home.  On the array I have one large partition mounted as /usr an running the XFS file system.
Most of the time when I try to rebuild the system, for some reason the array shows up as scsi0 (sda) and the 250GB single drive shows up as scsi1 (sdb), but randomly.  If I build the system with the array as sda with the above paritions, everything installs ok, but when I reboot, I get an error 22, unknown parition. If I get lucky and the 250GB drive shows up as sda, everything works fine.  What in the heck is causing this behavior and how can I change it?  I have set the first drive in the BIOS to be the 250GB drive, and the second drive is set to be the array, but that made no difference.

---

