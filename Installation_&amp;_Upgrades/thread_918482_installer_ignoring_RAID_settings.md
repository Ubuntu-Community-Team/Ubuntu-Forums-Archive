---
title: "installer ignoring RAID settings"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by Mookinator on 2008-09-13
i'm trying to install 8.04 onto a machine with a 3 drive RAID0. the RAID0 has two partitions on it. one with 100Gb onto which winXP was installed and it working fine. the other 730Gb partition i wanted to install Ubuntu. The problem is that Ubuntu refuses to recognise that it's a RAID partition, it only sees 3 individual drives. i even created a ext3 partition and preformatted it with no luck. it doesn't acknolwedge that there's a 730Gb partition created and ONLY sees 3 unpartitioned drives. i've tried guided and manual partitioning modes, and it'll go through with the install, installing to the 230GB partition on the 1st drive and leave the second and third drives empty. (it also will not boot once installed, giving me a GRUB Error: 2) why is it doing this? i had no problem installing Ubuntu onto my server which as also running a RAID drive. any advice appreciated.

~Mike

EDIT: nevermind. i found what i was looking for. my "RAID" controller is built into the mobo and is a "fakeraid" system. so what i'm trying to do will basically never work.

---

