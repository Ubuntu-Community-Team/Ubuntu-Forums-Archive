---
title: "Before I spend money on hard drives...."
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by digilink on 2007-07-16
I'm looking for some advice. I've googled and searched the forums here, but didn't really come up with anything that I'm looking for, so I'm hoping someone that has this board or has worked with one can answer my questions. 

I just built a new Core 2 Duo system, upgrading from my old Athlon 64 s754 based setup. I am running only a single 160gb SATAII drive at the moment, and I want to move on to a RAID 5 or RAID 0+1 setup using 3 drives (3x 160gb)

I have a Gigabyte GA-965P-DS3 motherboard, and I want to build a RAID 5 array, but as I understand it, it only supports RAID 0/1 using the onboard controller. 

So I think my options are:

1. Get a supported PCI card that will do RAID 5 (suggestions?)
2. Use the onboard controller to do RAID 0+1 (if it will do it, I still need to RTFM)

Will the onboard SATA RAID controller work with Feisty?

---

### Post by Pumalite on 2007-07-16
Check all this before you go ahead:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://kerneltrap.org/node/7020](http://kerneltrap.org/node/7020)

[http://kerneltrap.org/node/7077](http://kerneltrap.org/node/7077)

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61342](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61342)

Good luck.

---

