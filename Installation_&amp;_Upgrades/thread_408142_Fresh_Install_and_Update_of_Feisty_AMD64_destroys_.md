---
title: "Fresh Install and Update of Feisty AMD64 destroys root partition!"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by muncrief on 2007-04-13
Yikes!!!

I have been using Feisty AMD64 for about a month now with very few problems. However I needed to do a fresh reinstall this evening and was amazed that after the update the root partition was actually destroyed. Luckily I know to keep my root partition seperate from my data or this could really have been an unforseen disaster.

So here's exactly what I did, and I'll give you my system hardware configuration below. I simply booted up the Feisty 7.04 CD and installed Feisty as I've done before and everything was fine. When I clicked on the orange update icon it said there were 344 available updates, and I let it update everything.

When I rebooted I received a kernel panic, so I booted into Windows XP and found that the entire root partition was gone (I have a Windows program called Ext2IFS that allows me to mount ext2/ext3 drives). However all my other partitions, including my /home partition, are fine.

So as of tonight, if you have my hardware and just do a straight install/update of Feisty AMD64, it appears your root partition will be destroyed. 

Since root was destroyed I have no logs to provide, but I'm going to back up all my data and try it again with proposed and backport repositories enabled and see what happens.

Here's my hardware:

Gigabyte GA-K8N Pro-SLI Motherboard (Nvidia nForce 4 based)
Athlon 64 3000+
3GB Dual Channel PC3200 DRAM
Maxtor 6V200E0 Sata hard drive (sda, 120GB)
WDC WD1200JS-00MHB0 Sata hard drive (sdb, 200GB)
LITE-ON LH-18A1P DVD R/W drive
Sony CDU5221 CD-ROM drive
Nvidia 7800GT Video card
Hauppage WinTV-Go TV card

Drive partitioning:

sda1 - 20GB - Windows NTFS partition
sda2 - 2GB - Linux swap
sda3 - 20GB Linux ext3 / (this is the partition that was destroyed after the update)
sda4 - 70GB Linux ext3 /home
sdb1 - 95GB Linux ext3 /virtual (for virtual machines)
sdb2 - 95GB Linux ext3 /storage (data archive)


So the bottom line is that if your messing with Fesity AMD64 back up your data! I don't know what's going on, or what hardware it effects, but this is sure a bad bug so soon before release. I'm sure the Ubuntu developers will fix it soon though. I sure wish I could give them some type of logs ...

---

