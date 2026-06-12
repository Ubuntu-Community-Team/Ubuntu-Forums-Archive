---
title: "Problem with installing on a RAID0 configuration."
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by asdlinux on 2008-04-17
Hi.

I have a Gigabyte GA-MA78GM-S2H motherboard that i have 2x250GB SATA drives in RAID0 configuration. I do run windows in a 100gb partion that works without problems on the RAID. I have been running LINUX for many years and i really miss it but i have this problem when i try to install. This is also first time i use RAID. All is well if you run a live cd (i have tried kubuntu 7.10 and ubuntu 8.04 and other distro cd with all same result) but my RAID gets broken, one of (second one) my disks will go offline and will not come online until powering the system down. I am aware that this chipset is very new (I got this motherboard the same week ATI released the chipset) so it might be a driver problem in the kernel. Also because i new to RAID i can be doing something wrong. 

Is there anyone that have an idea how to fix this or have some hints :)

Thanks
Magnus

---

### Post by wkulecz on 2008-04-17
Since you have a windows partition on the raid, read up on "fakeraid"  I think by default things are setup to use "dmraid" which is incompatible with windows.

At best, you'll need the alternate install cd and a good bit of knowledge to override the defaults.

Probably easiest to install a third non-raid drive and install Ubuntu to it, but you may still have issues with GRUB breaking your raid, the windows tools *might* fix it.

I've come to the conclusion that raid is more trouble than its worth.  Raid0 alledgedly offers more disk speed, but at the price of greatly increased system fragility.  I gave up on raid0 with w2k for this reason, although my legacy w2k box still uses raid1 for the boot drive and raid5 for data (photoshop and video editing).

--wally.

---

### Post by asdlinux on 2008-04-22
I have looked at linux software raid and I'm not sure if it is the solution for me. I need the speed that the raid gives in windows because i work with large data files. I need to be able to use my windows partions because of work. 

Is it possible to keep my raid and install a normal IDE drive to install ubuntu, How would GRUB react to that kind of configuration. I read everywhere that GRUB gives you lots of problems i these cases. Would it be possible to install GRUB on the IDE and use it as boot device?

Thanks
Magnus

---

