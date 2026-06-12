---
title: "Partitioning after Installing Ubuntu"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by smokeysaysno on 2006-07-13
Hi, I'm a new linux/ubuntu user.  
This week I installed Ubuntu and had my hard drive partitioned so that I could run a dual boot system.  I figured that I would just wipe out my windows install and reinstall it at a later date when I had some time.  After spending a couple of days in Ubuntu, I've found that it can do everything that I wanted windows to do, and do it better.  I have a 30 gig partition on my hard drive that is in NTFS format.  Is it possible for me to reclaim that space and add it to my current ubuntu disc partition without reinstalling?

---

### Post by az on 2006-07-13
How big is your ubuntu partition?

You can extend or shrinik a partitoin from the end, but not the beginning.  Assuming the NTFS partition comes before the ext3 one, if your linux partition is less than 30 gigs, you can move it to where the current ntfs partition is and then just delete the original ext3 partition and then extend it.

You will need to change your fstab and /boot/grub/menu.list to point to the correct partition.

---

### Post by smokeysaysno on 2006-07-13
My ubuntu partition is 45 gigs.  My hard drive is 80 gigs with the Ext3 partition coming before the blank ntfs partition.  There's also a swap partition but I don't know where that is.  I'm not sure why I allocated it the way I did.  Like I said, I'm definately a new user and have no partition experience.  Is there a partition GUI that I could use?  I don't quite understand how to extend my ubuntu partition to the end of the drive so any help in easy steps would be awesome.

---

### Post by az on 2006-07-13
> **smokeysaysno said:**
> My ubuntu partition is 45 gigs.  My hard drive is 80 gigs with the Ext3 partition coming before the blank ntfs partition.  There's also a swap partition but I don't know where that is.  I'm not sure why I allocated it the way I did.  Like I said, I'm definately a new user and have no partition experience.  Is there a partition GUI that I could use?  I don't quite understand how to extend my ubuntu partition to the end of the drive so any help in easy steps would be awesome.

Use a live cd with gparted.  Delete the ntfs partition and resize the ext3 partition to occupy the freed space.

Since you say the ext3 partition comes before the NTFS one, it should not be a hassle.

---

