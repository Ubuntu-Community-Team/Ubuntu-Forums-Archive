---
title: "Installing Ubuntu 10.10 on 74gig drive along with 2 TB drives with RAID 1"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by elSpaniard on 2010-10-15
I am currently running Windows 7 on my primary 74 gig drive and have 2 TB drives in a RAID 1 setup as my secondary storage. I am planning to completely wipe out and install Ubuntu 10.10 on my primary drive. I would like to know if I need to do anything special with my ubuntu install to have it install and run properly.  I've been reading the fakeraid guides and I a bit confused. They all seem to assume that you are installing Ubuntu on a drive that is in a raid configuration. 

However, in my configuration, the only drives in a RAID set up are my two 1 TB drives that I plan to have hold all my personal data (music/pictures/code). My primary drive, which I intend to install Ubuntu on, is not. 

With my Windows 7 install, I had to install a driver that would recognize the RAID. Is their a similar driver that I need for my Ubuntu install?

Any information is greatly appreciated. This forum has been very VERY useful for my past Ubuntu issues.

Specs:
74 GB Drive 
(2) 1 TB (RAID 1)
Asus P5Q Pro Motherboard
Core 2 Duo E8500 Processor @ 3.16
6 GB Ram

---

### Post by ronparent on 2010-10-15
I would do a normal non-raid installation. Once the system is installed and running prior post indicate that dmraid (the software you need to see and access your raid partitions) may not be installed. To install it in a terminal simply enter 'sudo apt-get dmraid'. Once installed you should have full access to the raid. Have fun.

---

