---
title: "Ubuntu 7.04 with Windows XP"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by Games Goblin on 2007-05-30
ALL RIGHT!!! After much tinkering i finally got my USB modem to work with ubuntu...now that means i can proceed to the final step....installing!!

I have got Windows XP SP2 and i would like to dual boot with ubuntu

heres a map of my partitions:

C:\ - 39.0 GB
D:\ - 39.0 GB
E:\ - 39.0 GB
F:\ - 24.4 GB (Windows XP Pro SP2 is installed in this drive)
G:\ - 44.6 GB

My plan is to format C:\ (theres a faulty installation of vista in it) and then use partition magic to make a new 15 or 20 GB partition out of it and then install Ubuntu in the newely created partition....

so will this work? and should the ubuntu partition be FAT32 or some other file system? Will Ubunu set up a dual boot automatically?? 

Thanks!:KS

---

### Post by Vajra Vrtti on 2007-05-31
Are all those partitions in a single HD? Which are primary/secondary?

---

### Post by Yendor on 2007-05-31
Ubuntu will set up the dual boot automatically for you.

Are those separate drives, or multiple partitions on a single drive?  If your "drive C" is a separate physical drive, just run the Ubuntu installer and tell it to use that drive.  It will partition and format it for you.  If it's separate partitions, delete that partition and tell the Ubuntu installer to use the free space.

---

