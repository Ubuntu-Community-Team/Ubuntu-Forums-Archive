---
title: "Partitioning Question"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by shawn_duggan on 2006-10-29
Hi - I am trying to make my XP machine into a dual boot with Ubuntu. I plan to do an alternate install because I do not want to install grub to my MBR.  I will instead use BootPart to alter my windows boot.ini.

My machine is a (Compaq SR1750NX, AMD64 3500+ 2.2GHz, 1 GB RAM) and I will be installing Edgy to a second 30 GB hard drive.  If I remember correctly the alternate install makes me decide the partition sizes.  Any advice what to use?  

Thanks!
Shawn

---

### Post by AndyCooll on 2006-10-29
REad the link in my signature. IT is a well-respected HOWTO about dual-booting, and should answer your queries.

:cool:

---

### Post by Coelocanth on 2006-10-29
maybe 1 GB for swap (that will be plenty), then you can just go with the rest for /. Or, if you want to have your /home on a separate partition, go with maybe 10 GB for / and the rest for /home. It's really dependent on what you want to do with your system though.

---

### Post by shawn_duggan on 2006-10-29
I found the Dual Boot Guide and it is informative.  It also linked to Aysiu's site which has a lot of great info on partitioning.  I was more or less wondering the actual sizes to use.

I think I will go with 1 GB /swap, 10 GB / and 19 GB /home based on your inputs and what I read.

Thank you both for the replies and info.  This is a great forum.  I've been surfing distros now for several months (Fedora, Suse).  Part of the reason I've come back is simply because of the quality of these forums.  Help for Fedora and SuSe is no where near as accessible IMO.

---

