---
title: "Lenovo u510"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by Zortwil on 2012-12-26
Hi, 
I'm currently on a pretty sluggish Dell N7010, and am looking to upgrade to the Lenovo u510.
Has anyone had any experience with Ubuntu on this machine?
Two questions:
1. Will multi touch gestures work?
2. Can I install the OS on the 24/32gb ssd and have home on the hdd? If so, how would I configure and partition the hard drives?

Thanks! Any help is appreciated.

---

### Post by 2F4U on 2012-12-26
> 2. Can I install the OS on the 24/32gb ssd and have home on the hdd? If so, how would I configure and partition the hard drives?

This would be independent from the brand of the machine. You would have to do manual partitioning and create a / root partition on the SSD and /home on the hdd. You may also wish to create separate partitions for swap, /tmp and /var on the hdd, since these contain temporary files.

---

