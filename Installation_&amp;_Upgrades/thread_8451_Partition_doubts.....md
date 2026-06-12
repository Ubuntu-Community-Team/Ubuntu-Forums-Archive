---
title: "Partition doubts...."
date: 2004-12-17
forum: Installation &amp; Upgrades
---

### Post by fuchetj on 2004-12-17
Hi
I want to install Ubuntu, but I have some doubts regarding partitions. 
I have two SATA HD of 160 GB each. I have one for XP, with several partions(one for OS, one for pagefile, one  for Apps, one for Docs and one for P2p storage(All NTFS)).
In the second HD I got Mandrake and the disk has four partitions(one for /, one for swap, one for /home and anotherone in FAT32 to interchange files between linux and win) and +100GB of unpartitinated space.

I'm wondering if a can share the swap and the /home partitions between Mandrake and Ubuntu. Can I?

I already have the liveCD and it seems to pick up the swap partition automaticaly(please correct me if i'm mistaken).

So my question is if I can create a new partition using the unparitionated space and share the home and swap partitions. 
When running liveCD I notice that I can open some file and folders of the home partiton from Ubuntu, however, I cannot do so with others, which seems to be blocked and it tells me that I have not rights to access them.

THanke you in advance

Fuche

---

### Post by nemin on 2004-12-17
[QUOTE=fuchetj]Hi
I want to install Ubuntu, but I have some doubts regarding partitions. 
I have two SATA HD of 160 GB each. I have one for XP, with several partions(one for OS, one for pagefile, one  for Apps, one for Docs and one for P2p storage(All NTFS)).
In the second HD I got Mandrake and the disk has four partitions(one for /, one for swap, one for /home and anotherone in FAT32 to interchange files between linux and win) and +100GB of unpartitinated space.

I'm wondering if a can share the swap and the /home partitions between Mandrake and Ubuntu. Can I?
[/QUOTE]
You absolutely can :)
[QUOTE=fuchetj]
I already have the liveCD and it seems to pick up the swap partition automaticaly(please correct me if i'm mistaken).

So my question is if I can create a new partition using the unparitionated space and share the home and swap partitions. 
[/QUOTE]
Very good idea, this is exactly the way I did it :)

---

### Post by liberal_tugboat on 2004-12-17
sharing swap is perfectly fine, sharing /home im not sure about... never tried it before
any one have any problems with sharing a /home partition between to different distros?
I would recommend backing up your /home before trying it, just in case

---

### Post by nemin on 2004-12-17
[QUOTE=liberal_tugboat]sharing swap is perfectly fine, sharing /home im not sure about... never tried it before
any one have any problems with sharing a /home partition between to different distros?
I would recommend backing up your /home before trying it, just in case[/QUOTE]
Of course it's always a good idea to have recent backups of all important data, before doing something like partitioning. For me, everything worked fine, but of course it's all at your own risk ;)

---

### Post by fuchetj on 2004-12-17
Thank you.
I will try it tomorrow. I'll made a backup and see what happen.

Fuche

---

