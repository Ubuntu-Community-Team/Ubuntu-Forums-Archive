---
title: "Partition/Mounting gone wrong"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by Sunny Kraf on 2008-05-02
I am a new Ubuntu user. I just installed the 8.04 version on my Laptop. I have a DELL XPS M1330 with decent specs (T7500,3GB RAM,250GBetc...).

Also, divided my Laptop HDD into 3 partitions (1 for Vista, 1 for Ubuntu, and 1 for stuff like MP3s, videos which can be accessed by both Vista and Ubuntu). I kept the 3rd partition as NTFS as I plan to use Vista more.

I first installed Vista and then used gparted to resize that partition (I brought it down from 232 GB to 40 GB). Then I defragmented the 192 GB in Vista. Then I used the Ubuntu live cd for installation. Here there was some discrepancy as Ubuntu was showing the other partition as 202 GB(instead of 192GB). So, created a new 150 GB DATA partition out ot it in NTFS (mounted as /media/sda2, which turned out to be a mistake). Then i alloted 8 GB for swap and rest for linux.

Now the issues i have are as follows:

I am not able to read the DATA partition from ubuntu, the error i get from ubuntu is that i don't have the privileges to mount this drive.Also, windows is reading this partition but showing it as 143 GB. So, I went back to Gparted and saw that about 6 GB is unallocated ( I can't figure out why because I was using a calculator to calculate the exact MBs). I am thinking of deleting the 143 GB, so I'll have about 150 GB unallocated space, then create a full 150 GB NTFS partition from that.

Can i do that, and if i can where should i mount it? I am curious that i did not specify where to mount the vista partition but ubuntu still mounted it automatically and reading it fine. Should i do the same for the 150Gb partition (i.e not specify where to mount).

Another problem is that Vista is reading as follows:
Vista partition - 40GB
Data - 143GB
Ubuntu- 43Gb
Swap (not reading, saying it needs to be formatted)
is this normal?

Any help is appreciated.

---

### Post by Pumalite on 2008-05-02
You have to use Vista partitioner. You cannot use Gparted. Start from scratch.

---

