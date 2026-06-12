---
title: "How to? Rebuild the installer with SATA drivers?"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by eriklou on 2007-02-13
Alright, so I've been using 6.06 for a server, totaly better then RH9, and I have yet to come up with a problem I couldent figureout myself. Today thats diffrent. I just receved a new server with an SATA Raid controler built on the MB with two drives in a raid 0 config. Problem is that when I try to install 6.06 it detects both disks, not the one raid drive that I had setup on the hardware level using the same two drives... I was able to find a copy of the drivers from the MB site but they were for RH9 (rpm.) so I converted that to a deb file. My question is this, is there anyway to load these drivers before the Ubuntu install? Or do I have to rebuild the installer, I don't know where to even start looking for that info, Any help on the matter would be really great.

---

### Post by Delta_Farce on 2007-02-13
Hi,

I think you need to use dmraid. I've previously used this to install Gentoo, but not Ubuntu. I found you a guide which you can follow using the Dapper Live CD [here.]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")

There's a server version guide [here too.]("http://www.howtoforge.com/ubuntu_dapper_raid_system")

And another guide from the [Ubuntu Wiki.]("https://help.ubuntu.com/community/FakeRaidHowto")

It seems that you have to install the dmraid prior to partitioning, so have a look through the guides to see if you have any luck. I ended up getting rid of my raid array so I can't really offer any more info than this sorry.

Cheers,

Mark

---

