---
title: "Promise FastTrak100 Tx2 RAID prevents install"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by jpb on 2006-03-30
I have an Athlon system with AMD-760 chipset running Windows 2k with two regular EIDE drives plus a Promise FastTrak100 TX2 PCI card with two 80 GB EIDE drives set up as RAID 0.  All this works fine under Win2k.

I tried booting from an Ubuntu 5.10 install DVD but I could not run it as a live filesystem or install the system. Either way, the process would just hang soon after bootup, with no particular warning or error message. I guessed the problem might be that the Promise RAID is not supported. I removed the Promise RAID pci card from the system. After that I was able to install 10.5 with no problems, so I believe the Promise card was indeed the problem.

I don't have time or inclination to troubleshoot this issue further. I'm just posting this here in case it is helpful to others with the same problem.

---

