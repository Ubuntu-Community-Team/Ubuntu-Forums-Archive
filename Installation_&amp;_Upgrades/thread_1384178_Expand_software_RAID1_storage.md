---
title: "Expand software RAID1 storage"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by klockren on 2010-01-18
I am running ubuntu on 2x500GB SATA drives configured as Linux software RAID1 (mirroring). Configuration as below:
/dev/md0  = root partition
/dev/md1  = swap
/dev/md2  = /usr/local (400GB)

Now I want to change my 2x500GB disks to 2x2TB disks. All extra space shall be allocated to /dev/md2. I guess that I'll have to change one disk at a time and rebuild the raid after each new disk, but how do I expand the /dev/md2 partition?

---

