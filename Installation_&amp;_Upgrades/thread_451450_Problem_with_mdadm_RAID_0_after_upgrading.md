---
title: "Problem with mdadm RAID 0 after upgrading"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by kaijuu on 2007-05-22
I have three HDs in my PC: one for Ubuntu install, and two 250GB drives for storage that I had made into a RAID 0 array using mdadm. When I upgraded Ubuntu recently, the RAID (/dev/md0) is no longer available, though both drives still show up as Linux Raid Members. I tried to reassemble (-A) with mdadm, but it errors out on the first drive (/dev/hdc) saying the device is busy and there is a problem with the superblock. Any ideas?

---

