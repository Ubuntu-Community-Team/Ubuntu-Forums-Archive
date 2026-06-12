---
title: "SATA RAID 0 Dual Boot AMD64"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by manosazules on 2005-04-16
I am buiding an AMD64 System with 2 74gb sata HDisks in a hardware Raid 0 configuration and trying to dual boot windows 64 wand Ubuntu 64. Does someone knows of a step-by-step guide for doing this?

I think I'm going to have problems with the raid 0 configuration. I need advise with partitions too, specially with the extended partition. Sorry, but its the first time Im trying to install a linux distro with dual boot. If I can make both OSs to work properly its going to be like magic! \\:D/ 

Thanks,

Alex

---

### Post by flipy on 2005-04-17
same here... i can't understand why ubuntu installer do not use dmraid to detect raid metadata and run dmsetup with that.. i'm stucked at the installation, and any help would be appreciated

---

### Post by sman on 2005-06-15
[QUOTE=manosazules]I am buiding an AMD64 System with 2 74gb sata HDisks in a hardware Raid 0 configuration and trying to dual boot windows 64 wand Ubuntu 64. Does someone knows of a step-by-step guide for doing this?

I think I'm going to have problems with the raid 0 configuration. I need advise with partitions too, specially with the extended partition. Sorry, but its the first time Im trying to install a linux distro with dual boot. If I can make both OSs to work properly its going to be like magic! \\:D/ 

Thanks,

Alex[/QUOTE]

I am in a similar situation. Any tackers on this? I real want to dual boot windows and Linux but only have a raid 0 array. Ubuntu sees them as two separate drives. 

Anyone out there who can help??

---

### Post by alastair on 2005-06-16
I saw your other post.

I suggest, unless things have changed recently, trhat you forget about "motherboard" RAID. XP might have drivers, but the manufacturers don't do Linux drivers. So, TWO seperate disks it is and you will have to re-arrange your installation. I don't think even NVidia support Linux with their NVRAID option. This is no big deal for Linux - because m/board RAID is s/w RAID essentially, and we do that very well already.

---

