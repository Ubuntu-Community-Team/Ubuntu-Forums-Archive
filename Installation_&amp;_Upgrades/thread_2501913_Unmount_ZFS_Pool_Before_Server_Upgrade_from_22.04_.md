---
title: "Unmount ZFS Pool Before Server Upgrade from 22.04 -&gt; 24.04"
date: 2024-10-25
forum: Installation &amp; Upgrades
---

### Post by wgilthorpe on 2024-10-25
The TL;DR here is should I somehow unmount my ZFS Pools before I upgrade or not?

I have a Ubuntu Server that I use for general backup and as a media server.  

The OS (22.04) is on an old fashioned MD RAID 1 (I am familiar with this) and has 2 ZFS pools of ~14TB each.  I have heard good things about ZFS, so I converted my old RAID 6 arrays to ZFS Pools.  I have been pretty satisfied with the stability and performance.  

However, I am running Jellyfin and wanted to be able to transcode on the fly.  My upload is only 30Mb/s and the videos buffer if I am watching remotely.  So, I just got an Intel Arc GPU to transcode and, of course, the Kernel in 22.04 does not have the drivers built in.  However, I have read that the 24.04 kernel does have these drivers built in.

I was already planning on upgrading to 24.04 soon, but I am now more motivated to do so.

Do any of you experts out there know,  should I unmount my zpools before I upgrade the OS or is it relatively safe to go ahead with the upgrade with the system as is?  

Not sure if it makes much difference, but I installed the OS on the RAID 1, then got the zpools up and running.  One is used to backup my entire dropbox locally and all of my other boxes and the second is used for my media server.  However, all software is running off of the 128GB Raid 1 array where root and home partitioned.

As I said, I am old head with Ubuntu (7 or 8) and MD RAID,  but I am very new to ZFS.  In my older systems, I would just unmount the RAID arrays and removed them from the FSTAB until the upgrade was complete, then re-added them.

Any advice is much appreciated.

---

