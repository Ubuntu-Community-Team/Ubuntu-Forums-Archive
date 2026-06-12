---
title: "&quot;Unable to find a medium containing a live file system.&quot;"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by zygrot24 on 2010-10-04
Hi folks, long time lurker and Ubuntu tinkerer.

I've got a huge problem installing Ubuntu on a hobby computer. It's an old HP Pavillion a1223w, 3.0 P4, 1GB PC3200 (4x256MB), SATA Seagate 80GB with XP MCE currently installed, PATA LITEON DVD burner.

I get the titled error with every version, every disc and every configuration I've tried. I have had Ubuntu 9.4 and 9.1 installed on this computer at one point or another before. The OS on this computer changes frequently, it's a hobby computer for tinkering. I put Windows MCE back onto it because a friends Motherboard died and he needed a loaner. I got it back from him and wanted to try 10.04 on it. I cannot get 10.04, or any version, to install now. 

I've tried:

9.04, 9.1, 9.04 alternate install CD, 10.04, 10.04 alternate, 10.04 off a thumb drive, Kubuntu 10.04 on CD and thumb. I've checksum'd all my images and all have checked fine, and I've burned each version to at least 2 discs each. I even tried the 10.04 that came with my Ubuntu 5th Edition book.

I've also tried:

A known working DVD drive spare, a known working DVD burner on SATA, changing SATA/PATA controller modes (mixed/enhanced), different channels and master/slave configurations, all-generic-ide, and no acpi.

I don't want to resign myself to a mobo problem, because the computer still boots windows MCE perfectly, and will boot to install menus for live CDs, but will not boot or install Ubuntu/Kubuntu. 

Any ideas would be appeciated.

---

### Post by mörgæs on 2010-10-04
Hi, welcome to the forum. 

First of all thanks for trying several options before posting. If only more people would do that...

It seems to be a known error. If it also happens on 10.10 on your machine, could you maybe confirm this error and mention your findings in the bug report? 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543875](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543875)

---

