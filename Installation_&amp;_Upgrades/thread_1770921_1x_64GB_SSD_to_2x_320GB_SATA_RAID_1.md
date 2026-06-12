---
title: "1x 64GB SSD to 2x 320GB SATA RAID 1"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by Zeon100 on 2011-05-29
Hey guys,
My server running Ubuntu 11.04 is currently on a single 64GB SSD. it's too small so we have ordered 2x 320GB SATA hard drives we wish to use in RAID 1. I'm just wondering what people suggest as the best mgiration path? I presume this is the best way:
- Install both 320GB HDD and use mdadm to create a RAID1 array with them
- Clone the SSD to the new RAID 1
- Remove the SSD

Does this sound right? This is the first time I'm doing anything like this and the system has been setup with the default partitioning. Any recommended reading on things I will need to know about for this transition?

---

