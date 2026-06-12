---
title: "Partition for Windows"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by gowings83 on 2012-09-30
Ok hopefully some genius in here can help.  On my laptop I have a 750gb HDD.  I have ubuntu taking up the whole drive.  It has about 300gb of data (movies music ect.), what I want to do is make a NTFS partition for XP to use for games.  GParted says I have to unmout the drive to resize.  I'd like to be able to use these music, movies, whatever within XP instead of rebooting if I left the laptop on, which I rarely do.  So what I'm looking at is a full 750gb in ext4, which windows won't see.  I need to basically take say 350gb (have 388 available) in to a NTFS, transfer the files after dual booting with windows then extend the 350 to 650 within windows (partition magic probably).  I wish I had the resources to just move it all to another drive and start over, lol.  I already have a 500gb HDD full.  So how can I do this without messing up either OS.  All I want is to resize this darn thing.  :confused:

---

### Post by Mark Phelps on 2012-09-30
You can't resize a partition while it's in use, so you will have to reboot from USB or CD and use GParted to do the resizing.  But be aware, resizing a partition that big is likely to take a LONG time -- several hours, at least.

Also, while it's OK to have an NTFS "data" partition shared between MS Windows and Ubuntu, sharing an "OS" partition is a bad idea.

So, your best bet would be to have two NTFS partitions -- a small one for holding XP, and a large one for holding your shared data.

---

### Post by coffeecat on 2012-09-30
+1 to what Mark Phelps said, and to add...

You implied that you don't have spare backup capacity, but doing a resize of a partition with valuable data in situ risks data loss. Something could go wrong with the resize. If you possibly can, backup all your files first. I would not even attempt manipulating another partition on the same drive, let alone a partition with my data in it, without making sure I had adequate backups first.

---

### Post by darkod on 2012-09-30
Wow, that is a lot of repartitioning that can sometimes go wrong. And since you alredy say you have nowhere to copy the data (make backup), be aware that if it goes wrong, you can lose it all or a lot of it.

Basically you can use Gparted from the ubuntu live cd (booted in live mode with the cd), or a Gparted live cd (a bootable cd only with Gparted).

The ubuntu live mode mounts the swap partition, so you will probably need to right-click it in Gparted and select Swapoff. After that any existing locked symbols (the keys symbol next to the partitions) should be gone and you can manipulate the partitions.

Also if any of the partitions are logical inside an extended partition, make a difference between resizing the logical partition first and then the extended.

Also take into account that XP will need primary partition to install so you have to be able to create one new primary partition.

I would say what you are planning is very risky. You are talking about not one, but two big resize operations that take very long time and with that have higher risk something to go wrong. But the choice is yours.

---

### Post by gowings83 on 2012-09-30
Alright thanks guys.  I knew the risks but after seeing how much of a pain it is to just get xp and ubuntu dual booted with ubuntu installed first I think I'll wait until the extra space to backup everything is available.  Backup, wipe the drive, put in XP then ubuntu, SO much easier.

---

### Post by darkod on 2012-09-30
The problem here is not that ubuntu is installed first but that you want to move too much data. If you only want to create a 10-15GB partition for XP, that involves less risk because the partitioner needs to do less work. But moving hundreds of GBs is a different story and that has nothing to do with which OS is installed first.

On a new disk the benefit is that you install one OS with the size you want to allocate to it, and then the second one with the size you want to allocated to it too. No resizing needed. That is the main benefit of starting fresh, not the order in which the OSs are installed. On the new disk you can also install first ubuntu then XP and it will still be much easier than the operation you are considering now.

---

