---
title: "Quick question about installing Dapper with XP"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by e4tmyl33t on 2006-09-12
Hey all. New to the forums here, i've messed around with Linux before but have never been able (nor skilled enough) with some of my older installs to properly do a good dual-boot.

I've got 2 potential dualboot systems I want to put ubuntu on, and both of them have the same problems.

1: Older Athlon 600, 448 MB ram, 15GB main IDE drive, 120GB Storage drive (both NTFS, WinXP Pro on the 15 GB drive), with added-on Ethernet and Belkin wireless cards. About half the 15 GB drive is free, and it's the one i'd like to use.

2: HP zv6233nr laptop, Ath64 3200+, 512 MB Ram, 100GB HDD with about 40 GB free, again, all NTFS. Has a Broadcom wireless chipset.

I got my CDs in the mail and booted the laptop with the x64 disk, wouldn't mount the windows drive. I read in another post about the pmount not allowing ntfs by default, which I'll get to later. (same thing happens on the desktop) Now, what i'm wondering is:

a) The wireless cards are SEEN by Ubuntu, but don't seem to operate. I do get some sort of bcm_xxxx error message during the boot process (i don't have it on-hand, unfortunately, but if i decide to try again i'll write it down for you.)

b) I've tried to use the Ubuntu installer partitioner, and it kicks back some error when trying to partition the drive. Ive tried a non-windows based version of Partition Magic, and it refused to work on the drive in the laptop, and the desktop's internal copy of Trend ChipAway Virus sees it as a virus (even disabled). Is it because both drives are NTFS and I need to edit pmount.allow to make it work?

c) Does ubuntu have built-in NTFS read-write access? This isn't AS essential, but the storage drive in my tower (which acts as my fileserver for the house) is NTFS and I'd like to not have to pull everything onto DVD, format it FAT, and reload everything.

Sorry for the long post, but I would like the most efficient answer possible so I felt that providing themost information as possible would help.

Thanks.

---

### Post by jimbren on 2006-09-12
I'm going to answer out of order...

b) Be sure you defragment both drives within Windows before you try to resize the partitions.  Windows writes data whereever, and you probably can't install because there is not enough contiguous space.  

a) if you can post the error message you get on bootup, that would be very helpful.  You can also do a forum search on the error, or a google search, and probably find your answer.  Without the error though, specualtion would be a waste of time.
 
c) Ubuntu doesn't ship with read\write NTFS access, but you can add this.  It is not fool-proof, and it can cause problems, but you can do it with reletive ease.

---

### Post by jimbren on 2006-09-12
sorry for the horrible spelling up above.  It has ben a long time since I was that sloppy.

---

