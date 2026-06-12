---
title: "Partitioning HDD to Install Dual boot Ubuntu/Win XP"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by HishamAraji on 2007-10-12
I am a long time Windows user and have never used Linux before.  I am planning to dual boot Ubuntu/Win XP when Gutsy comes out in the next couple of days.  My system specs:

BenQ 24" Widescreen Monitor
Intel Core 2 Duo E6600
2 GB RAM
nVidia 8800 GTS 640 Mb
Sound Blaster X-FI Xtreme Music

and my hard drives:
150 GB Western Digital Raptor 10000 RPM (For OS, games, and programs)
500 GB Seagate Barracuda 7200 RPM (for file storage)


I plan to partition my 150 GB Raptor drive so I can have one partition for Ubuntu, and one partition for Win XP.  I am currently thinking that my final outcome will be

150 GB drive
      - Partition 1: Win XP
      - Partition 2: Ubuntu

500 GB drive:
      - Storage for music, movies, pictures, etc.


I will be doing a clean install of the OS's.  How should I partition my 150 GB drive for the OS's?  What size should each partition be?  Should I include a 3rd partition on that drive or just stick with 2?  How should I format the 500 GB drive (NTFS or FAT32)?  I do not plan on installing Gutsy until I have the optimal partition configuration figured out, and I appreciate any help you guys can give me.  

BTW, I've never dual-booted before, so I'm not sure how you select OS during start up?

---

### Post by phr0ze on 2007-10-12
If you are starting fresh, create your XP partition and install XP, leave the rest of the space unpartitioned. When you install ubuntu, choose the option to 'Use largest unpartitioned space'

Thats it.

Just make sure you install XP first. Even if you don't leave unpartitioned space, Ubuntu can make it for you.

---

### Post by phr0ze on 2007-10-12
> **HishamAraji said:**
> BTW, I've never dual-booted before, so I'm not sure how you select OS during start up?

Forgot to answer this one. When you boot, you will see a menu to pick the OS you wish to start. It will auto-start the default OS if you don't push any keys within a time limit.

---

### Post by HishamAraji on 2007-10-12
Thanks Phr0ze.  Do you have any recommendations on partition sizes given my HDD drive size?

  I've seen some dual boot guides that recommend a 3rd shared FAT32 partition.  Do you think that would be necessary since I will have a second HD dedicated entirely to file storage?

---

### Post by HishamAraji on 2007-10-12
You recommend I use the 'Use largest unpartitioned space' option.  Will this also create a partition for the swap file, or do I have to manually do that?

---

### Post by HishamAraji on 2007-10-12
I plan to use the Linux Recovery CD to create the partitions.  What size should I make the Ubuntu partition?   Since I will be creating the Ubuntu partition using the Linux Recovery CD, will Ubuntu automatically create a swap partition during installation?

---

