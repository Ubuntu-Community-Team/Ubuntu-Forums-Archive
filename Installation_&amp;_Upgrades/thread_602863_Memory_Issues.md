---
title: "Memory Issues"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by mrmunkey on 2007-11-04
I've been using Linux for several years now.  I spent a year or so on Slackware, a year or so on SuSE and I've worked with plenty other distributions.  Mostly that's just a little background to establish a level of knowledge.  For whatever reason I hadn't gotten around to trying out Ubuntu until last weekend.

System:
--------
Abit AV-8 Motherboard

Western Digital IDE 80GB hda - Windows
Maxtor IDE 20GB hdb - Ubuntu
Western Digital SATA 120GB sda - Extra Windows drive

Dual booting, of course.

2 x 512MB : 1 GB Corsair memory
2 x 256MB : 512 MB some off-brand I don't remember  Both PC3200 400MHz Clock
--------

I'm trying to replace my Windows gaming computer so that I don't have to have Windows anymore.  I only play a few games anyway (Enemy Territory, and ET: Quake Wars) and those games have native Linux clients.

When I first tried installing, everything went quite well, until I tried restarting.  I got a GRUB error.  I think it was 17, but I don't remember.  It turned out I needed to update the BIOS to support booting off of the slave IDE drive.

Now I try to install and I keep getting a bunch of errors saying that the packages were corrupted (MD5 mismatches), or sometimes all the programs will end up crashing (Adept, the installer, etc.) and I can't even attempt an install.  Once I did get it to install, but then I ran into the same instability issues after rebooting.

I looked around and found out it might be related to the memory.  I ran a memcheck and there were errors.  

I replaced the Corsair memory with the same brand and model of memory from another computer (Corsair).  I still had the same problem.

After a lot of trial and error (and 10+ versions of Ubuntu and Kubuntu) I finally figured out that the only memory configuration is to have the off-brand memory in DIMMs 3 and 4.  Any other configuration will either lock up after booting, or just not boot at all.  Even if I put the off-brand memory in DIMMs 1 and 2.

Now that I've gone through all of this, my question is... does anyone else have this issue?  I've never had such problems with a distro before.  SuSE worked just fine on this same computer, Windows worked, Slackware worked, but not Ubuntu except with this goofy memory configuration.  I'd really like to have more than 512MB of memory in my gaming computer.

Could the BIOS upgrade have caused an issue with the memory controller?

---

