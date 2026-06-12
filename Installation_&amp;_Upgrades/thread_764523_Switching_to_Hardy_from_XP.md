---
title: "Switching to Hardy from XP"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Yoguess on 2008-04-24
Hi guys,

I have been trying Ubuntu on my old laptop and as dual boot on my desktop.  I have finally decided to switch to Hardy 8.04.

I am no expert at linux so I want some help deciding. I have an old laptop (linux only, 40gb) for testing, a Thinkpad (XP will move to Vista and ubuntu dual boot later) and a Desktop (XP, for now switching to ubuntu) 

Currently I have removed my dual boot linux from desktop.  On the desktop I have 3 hdd with total of 4 partitions 200gb, 120gb, and 30/30gb(NTFS). 2 external drives 200gb (NTFS). When I switch to Hardy I will create a /Home on its own partition, how big should this partition be? and what about the rest of the partition?

As of now most of the drives are almost full so I can't move data to other drive to switch from NTFS to what ever.  Can Hardy read/write to NTFS or should I switch them later on?? If yes to what?? FAT32?? ext2?? 3??  I want to be able to read and write to this partition from ubuntu and XP or vista.

I ask bcuz I was able to look at the data from ubuntu while back but not read or write.

---

### Post by Monicker on 2008-04-24
> **Yoguess said:**
> Hi guys,

I have been trying Ubuntu on my old laptop and as dual boot on my desktop.  I have finally decided to switch to Hardy 8.04.

I am no expert at linux so I want some help deciding. I have an old laptop (linux only, 40gb) for testing, a Thinkpad (XP will move to Vista and ubuntu dual boot later) and a Desktop (XP, for now switching to ubuntu) 

Currently I have removed my dual boot linux from desktop.  On the desktop I have 3 hdd with total of 4 partitions 200gb, 120gb, and 30/30gb(NTFS). 2 external drives 200gb (NTFS). When I switch to Hardy I will create a /Home on its own partition, how big should this partition be? and what about the rest of the partition?

As of now most of the drives are almost full so I can't move data to other drive to switch from NTFS to what ever.  Can Hardy read/write to NTFS or should I switch them later on?? If yes to what?? FAT32?? ext2?? 3??  I want to be able to read and write to this partition from ubuntu and XP or vista.

I ask bcuz I was able to look at the data from ubuntu while back but not read or write.

When I installed Hardy Heron, the ntfs-3g package was there by default, which will allow you to read/write ntfs partitions from within ubuntu.  I've never experienced any problems using ntfs-3g in the past.

---

### Post by ChocoTuar on 2008-04-24
Feisty Fawn was unable to write to NTFS, but Gutsy and now Hardy are able to do so effectively.

I have a 100GB hard drive and I use a 19GB partition for Linux, with a 1GB swap (80GB for XP) and it seems to work really well. I don't tax it very much, so you'd have to factor that in as well. Linux just doesn't use the space like Windows OSs do.

It might be hard to repartition a drive that already has had lots of use on it, unless it has been THOROUGHLY defragged, because the partitioner will sheer that data right off, screwing up the entire file system. It's best to do a clean install of Windows on the entire drive, then come through immediately, partition, and put Linux on that.

---

### Post by Yoguess on 2008-04-24
Thanks Guys.
Now I just cant wait for the ISO to be up there.

---

