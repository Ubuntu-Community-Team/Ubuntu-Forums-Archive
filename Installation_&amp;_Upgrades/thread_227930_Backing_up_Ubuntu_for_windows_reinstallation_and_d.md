---
title: "Backing up Ubuntu for windows reinstallation and dual boot"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by dcohen on 2006-08-02
Hey all, I recently started fiddling with ubuntu and initially I had it dual-booting with windows.  This was working fine, except I found that I needed a bit more space on my ubuntu partition, so I resized my windows partition with partition magic.  Unfortunately when windows restarted grub loaded into ubuntu (well I forgot to select windows) and it messed up my windows partition.  I didn't really have anything important on there and simply didnt feel like messing around to get it working again so i just deleted the partition.  Not long after, I did something that prevented me from booting into ubuntu and so I decided to just do a full reinstall.  

Since I didn't have the windows install CD on me I decided to just load ubuntu and mess around with it till I got my CD.  After a few days I've gotten the system to a nicely working state, and I would like to reinstall windows.  I understand that from an installation standpoint it's much easier to load windows first and then ubuntu so I want to just go that route.

My question is, what would be the best way to backup my ubuntu partition for reinstallation?  I have some program installed from  automatix that gives me the option for backup/restore (simple backup config, simple restore config) so should i just back up my root partition (nothing important on home)? Also, if I formatted my xp partition as FAT32 would I be able to read/write to it easily (i know ntfs write support is somewhat shakey though read support works fine.  Was just curious since it doesnt make much difference to me)?  Also I will probably be fiddling with the partitions a bit, would that effect grub at all?  

Thank you.

---

### Post by dcohen on 2006-08-02
I'd like to back it up to DVD btw.  The root partition is currently about 4.4 gigs total, though I'm sure there's some stuff on there that's unimportant.

---

