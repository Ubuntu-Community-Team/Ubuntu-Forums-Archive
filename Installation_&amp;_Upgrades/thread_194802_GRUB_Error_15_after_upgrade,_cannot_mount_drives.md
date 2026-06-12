---
title: "GRUB Error 15 after upgrade, cannot mount drives"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by mdd4696 on 2006-06-11
Hi all,

I'm hoping someone here can help me out. I have a server that I tried to upgrade to Dapper (from Breezy) that's not booting anymore. All I know is that I upgraded using the Update Manager and that after I rebooted, Ubuntu won't load. I'm getting a GRUB Error 15.

The system has two identical SATA drives with improperly set up RAID1. I had been running in degraded mode for a while--I couldn't figure out how to get the drives to sync up. Each drive has four partitions:

/dev/sda1 - ext2, bootable (I think)
/dev/sda2 - swap
/dev/sda3 - ext2
/dev/sda4 - ext2

When I tried to reinstall Dapper with the CD, I couldn't get past the partitioning phase. I thought I set up everything correctly, but it wouldn't do anything when I hit enter on "Write changes to disk".

I tried loading a live CD, but when I mount a disk all that show up are some weird files in an Access directory. Why can't I see all my normal files?

Help!

---

### Post by mdd4696 on 2006-06-11
A quick note: I have a ton of data on /dev/sdb I don't want to lose. Since /dev/sda wasn't synced properly, I could probably erase that drive.

If possible, I would like to do a fresh install, but first I want to verify that my data is in tact on /dev/sdb.

So, I suppose that my main question would be how I can look at the data on /dev/sdb before I go and reformat /dev/sda...

---

