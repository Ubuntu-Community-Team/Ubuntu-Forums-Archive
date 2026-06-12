---
title: "Swap Partition becomes unknow file system on restarting Ubuntu 14.04"
date: 2015-09-20
forum: Installation &amp; Upgrades
---

### Post by mabilalmirza on 2015-09-20
I installed Ubuntu v14.04 with 16GB swap partition (sda2). On reboot, system showed "The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present". Then I tried steps given in this blog ([http://punygeek.blogspot.nl/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html](http://punygeek.blogspot.nl/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html)). Everything worked fine and system showed correct results with "free -m" and "swapon -s" commands. But when restarted the system, system shows same message. After logging in, gparted shows File System "unkonwn" for sda2. I tried the steps several times with same result. I even reinstalled Ubuntu it didn't work.

Please help to figure out what's going on and what to do to resolve the issue.

I have HP Probook 4530s with 4GB RAM, 1GHz Processor, and around 620 GB Hard Disk.

---

