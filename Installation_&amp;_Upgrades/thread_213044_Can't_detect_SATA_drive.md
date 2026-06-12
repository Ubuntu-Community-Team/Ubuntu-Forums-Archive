---
title: "Can't detect SATA drive"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by foots2015 on 2006-07-10
I am trying to install the 64 bit version from the alternate cd.
The cd boots up fine. I then setup the installation to the point where it says that it is setting up the disk partitioner utility. 
After that all i have is a blue screen with a grey strip at the bottom.

My sysem has 1 SATA drive that i am hoping to dual boot with windows.

If I can't get it to istall, does anyone think that i could connect it over to the IDE cable, install it, then switch it back over to the SATA?

Please Help!

---

### Post by foots2015 on 2006-07-10
Anyone?

---

### Post by NewToasted on 2006-07-11
I have the exact same problem! 

My Kubuntu 6.06 AMD64 Desktop installer refuses as well to detect my Samsung SP2504C SATAII-harddrive. When I get to the step about partitioning I just stare at a grey window, which won't change in an hour.

I've done a little partitioning in QTparted from the Linux System Rescue CD, and there the partitions and harddrive look just fine. Also when I run fdisk in the SysRescueCD I find the drive and partitions, but in Kubuntu I can't find anything but my DVD-drive, which I by the way think is identified as "hda".

What can we do to get Ubuntu to find our harddrives?

Any help would be greatly appreciated, by both of us!

Best regards,

Simon

---

### Post by NewToasted on 2006-07-11
I think I may have discovered the solution to my problem!

It seems like the SATAII-controller of my ASRock 939Dual SATAII motherboard isnt compatible with the kernel of Ubuntu, so I have to plug the drive into one of the ordinary SATA-ports.

Ill let you know if I get it working.

---

### Post by foots2015 on 2006-07-11
On my mother board there is only SATAII (300 mps). My motherboard is also asus. 

I am about to give up on Ubuntu because i have been working on trying to install it for almost 2 weeks. 

Looks like it is time to try Mepis or maybe SUSE!!!

---

### Post by foots2015 on 2006-07-11
Did it fix the problem?

---

