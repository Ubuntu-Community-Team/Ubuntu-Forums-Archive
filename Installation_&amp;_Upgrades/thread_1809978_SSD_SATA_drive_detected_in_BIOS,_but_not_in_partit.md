---
title: "SSD SATA drive detected in BIOS, but not in partition manager"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by erind on 2011-07-22
Hi,

I'm trying to do a fresh install of Ubuntu on a SSD SATA drive and the PC ( Gateway GT5220 ) has only this drive inside, but the partition manager does not see the drive, whereas the BIOS detects it. Also, just out of curiosity, tried Win 7 but that too does not see the SSD drive. 
I've had the same problem before, but with a regular SATA hard drive and somehow I managed to install Ubuntu on it using alternate install CD. But this time I'm really stuck.
*The other thing is that I'm able to do a full format/install of OS when I insert this drive in a laptop, but not in the desktop*, which tells me that this is some sort of missing SATA drivers. I've found the same issue from my searches so far on the web regarding support for SATA drives, but not a real solution for my case. Also BIOS does not have any 'ahci' option to disable.

Is there any other way I can get this to work ?

Thanks.

---

### Post by Quackers on 2011-07-22
Is it using SATA 3? Try SATA 2 ports.

---

### Post by erind on 2011-07-22
The PC is about 4 years old, so I think it's either SATA 1 or SATA 2, and it has 4 ports. I've also tried inserting the SSD in each of the 4 ports, but no luck.

Thanks.

---

### Post by Quackers on 2011-07-22
Have you done any partitioning on that drive?

---

### Post by erind on 2011-07-22
No, it's a new empty drive; I formatted it EXT4 when I insert it in my laptop.

Thanks Quackers.

---

