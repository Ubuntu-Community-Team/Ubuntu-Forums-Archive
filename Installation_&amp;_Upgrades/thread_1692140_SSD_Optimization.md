---
title: "SSD Optimization"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by sch-chris on 2011-02-21
I am building a new MiniITX system and would like some help on partitioning/mounting points for SSD optimization.

The majority of / will be on the SSD, but files that are written to often shouldn't be there as the high write operations will diminish the lifetime of the SSD.

I will also have a 450G SATAIII drive where I believe that directories like /tmp and /home should be.

I also like the idea of a RamDisk for browser/etc files.  

Can anyone point me in the direction of some links that discuss the above mentioned points?  Thanks a ton in advance.

Intended system:
MoBo: [Minix 890GX-USB3]("http://www.jwele.com/motherboard_detail.php?949")
CPU: AMD Phenom II X4 910e Deneb
RAM: G.SKILL 8GB (2 x 4GB) DDR3 1333 (PC3 10666)
HDA: SSD Corsair SATAIII 2.5" 128GB 
HDB: Western Digital SATAIII 2.5" 450GB
PSU: [Pico 160W PSU]("http://www.mini-box.com/picoPSU-160-XT")
Case: [MiniBox M350]("http://www.mini-box.com/M350-universal-mini-itx-enclosure")
OS: Ubuntu (with Win7 in VM or DualBoot)

---

### Post by deconstrained on 2011-02-21
Yes, you can mount /tmp and /var/run as tmpfs or ramfs and have these temporary files (which are deleted every reboot anyway) stored in memory. It may just be a proverbial drop in the bucket in terms of reducing the number of writes, but it's something. 

I believe further optimization can be done via aligning the partition's beginning to a number of 512b sectors that's a multiple of 8 (or rather, a round number of 4kb regions)...Which, in spite of the archaic nature of such a choice/standard, may well be how your drive is manufactured. 4 kb, because mkfs.ext4 and many other filesystem creation utilities will by default use blocks of that size...

"fdisk -l" should give you some useful information on the drive, in particular, the sector size.

I read this once:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

