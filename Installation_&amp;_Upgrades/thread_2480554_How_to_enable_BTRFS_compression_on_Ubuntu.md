---
title: "How to enable BTRFS compression on Ubuntu"
date: 2022-11-02
forum: Installation &amp; Upgrades
---

### Post by siliconmagician on 2022-11-02
**[SIZE=4]Solved my own problem... lol[/SIZE]**I just had the regular ubuntu installer (im using ubuntu MATE now) use btrfs for / using the something else button, then once installed i edited the /etc/fstab file to enable zstd compression, then ran a defrag command on / with -r -czstd as the flags. on my 16gb emmc on a minimal ubuntu mate 22.04 install with no new programs installed other than chrome, i have 9.7 gigs free, before i had like 5, and that would fill up rather quickly. I may later experiment with higher compression levels but im not sure my Celeron N2840 would allow higher compression without major performance penalties. For anyone whos wondering im using an HP ChromeBook 14 G4 running the MrChromeBox firmware, it has 4gb of ram and a 16GB EMMC module on the board which as far as i know is not upgradeable. 


I am trying to figure out how to enable BTRFS compression for my lubuntu root partition, reason being im running the operating system on a old Chromebook that has been modified to be able to run standard x86-64 operating systems, but im trying to get the most of the 16GB of soldered ssd storage. I am not plannng to use snapshots or any of the other BTRFS features, just using compression to save space. If anyone knows of another rootfs file system that has transparent compression thats supported in the installer, let me know.

---

