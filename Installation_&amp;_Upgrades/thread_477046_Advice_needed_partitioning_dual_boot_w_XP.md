---
title: "Advice needed: partitioning dual boot w/ XP"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by whistle on 2007-06-17
I'm going to have a Dellbuntu in about two days or so, and I'm going to be dual booting XP (I don't trust Vista) and Feisty.  I thought about some possible ways to repartition the 80 GB drive I'm going to be getting... want some advice from people who either have experience dual booting or just know what's going on.

I don't know if I'm going to use Ubuntu or XP as my main OS - I hope to use Ubuntu, but XP's actually treated me pretty well over the years, and I don't know how much battery life I'm going to get in Ubuntu.  I've seen some reports of 20 minutes, and some reports of 5 hours.

I'm more trying to decide on the *number* of partitions rather than the size of them, but advice on size would also be much appreciated.

Oh, and I don't know a lot about Linux filesystems, so if I've got some stuff wrong in the partition names or if one of the partitions seems radically under/over-sized, let me know :)

Dell utilities - 32 MB
Dell restore - 2GB
Backup (partimage) - 10 GB

Swap - 3 GB
Linux boot - 10 GB (???)
XP - 20 GB

This leaves about 35 GB for my /home partition (I'm not missing any essential partitions here, am I?)... I want to be able to access my documents in both XP and Ubuntu, without having multiple copies of both.  I *think* there's a setting in Windows to point the "My Documents" folder to somewhere other than its normal place, so I want to have this /home partition be both my Linux /home and my XP "My Documents".  So, this should be formatted FAT32, right?

The questions in this post come down to these:
- Should I bother keeping the Dell partitions? (I'm leaning towards chucking the restore and keeping the utilities, just because it's only 32 MB)
- Is the Linux boot partition everything in / except for home? If so, is 10 GB a good size for it, under normal use?
- What format for the home partition?
- Anyone else who's using approximately the same setup (dual boot w/ home partition) that can share their partition scheme?

Thanks for taking the time to read this (and hopefully respond) :D - I know my thoughts aren't organized.

edit: yes, I've used the search function, and found a few people asking for partitioning help, but none that really told me anything I didn't know already.

---

### Post by whistle on 2007-06-18
Bump! anyone?

I've found answers to most of the questions... anyone want to take a look at this setup?

10 GB - partimage backups (ext3)
32 MB - utilities (whatever)
20 GB - XP (NTFS)
35 GB - /home (NTFS)*
12 GB - /
3 GB - swap

I guess the big question is if the /home partition should  be NTFS... what kind of battery life would I get if I had ntfs-3g running constantly?

---

### Post by crxvfr on 2007-06-18
I have a delbuntu with xp and fiesty.

I split my 160 gig drive into two primaries then split the later to create the swap. 

I loaded windows first and used acronis to do the partition work. ...installed ubuntu.

I then installed virtualbox in both OS's and re-installed winxp into ubuntu and ubuntu into xp.

Why?

Why not? (I'm trying to learn how these things work and what works best. Having mouse problems with Ubuntu OS but I think its caused by virtualbox)

---

### Post by harpazo on 2007-06-19
I'm a fairly new user to Linux (less than 1 year) and have learned quite a bit since using Ubuntu.  I'm running the following:

HP zv6000 (AMD)
100 GB HDD
1.5 Gig RAM

Originally came with XP home.  After a couple of different configurations, I've settled on dual booting XP pro and Ubuntu 7.04 Feisty.  My HDD is split 50/50 with a 2 GB swap. 
 
The nice thing is that you can use software like Partition Magic to resize your Partitions later if you find the need ( originally 70/30 with more for XP.)

Hope this helps.

---

