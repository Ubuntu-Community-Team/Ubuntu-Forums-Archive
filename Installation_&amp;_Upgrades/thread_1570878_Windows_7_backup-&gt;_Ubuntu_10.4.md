---
title: "Windows 7 backup-&gt; Ubuntu 10.4"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by TKTAB911 on 2010-09-08
Just wondering... Im running ubuntu 10.4.1 or w/e on a usb drive--off my windows 7 computer. Im backing up everything under my personal folder: Music, Videos, Pictures, Documents. Is there going to be a problem at all copying the windows 7 backup to ubuntu? Im going to format my whole hard-drive and remove the partition on it [then]->Install ubuntu off of my USB Drive-to my hard drive. After that im going to copy the backup file(s) back to the hard drive. Is there anything I should do before/after doing it? the backup is about halfway done and its been an hour at least. 

As far as I can predict, It should be just as easy as copy-and-paste OR downloading a backup/restore utility that works with ubuntu. Am i right or wrong?

---

### Post by Mark Phelps on 2010-09-09
From personal experience, I've found it a BAD idea to mismatch filesystems with OSs.  Backups made of MS Windows OSs are best stored on NTFS partitions; of Linux, on Ext3/Ext4 Partitions.

Why? Because the permissions infrastructures are totally different between the OSs.

So, I would not migrate your Win7 backup to any Linux-formatted partitions.

Just a personal observation.

---

