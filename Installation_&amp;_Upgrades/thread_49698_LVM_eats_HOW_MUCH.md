---
title: "LVM eats HOW MUCH?"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by macgyver2 on 2005-07-17
I'm looking to redo my notebook with Ubuntu (ran Gentoo on it since I got it 3 years ago) and I want to use LVM. I have no experience with LVM but I read through the howto and some threads on here.

My issue is this: I have a 20 gig hard drive. I've taken out 1 gig and allocated that among /, /boot, and swap partitions, so I have 19.0 gigs left. I'm using that entire 19.0 gigs for LVM. However, when I go to configure LVM (through the Ubuntu installer) and create the volume group, it then says I have only 17.68 gigs free to use for logical volume(s). Is that right? LVM is eating nearly 1.5 gigs? Seems like quite a bit...

Thanks in advance for any feedback.

---

### Post by AndrewStout on 2005-08-30
I'm having a similar problem: I'm trying to set up LVM through the 5.04 installer.  I made a volume group from two partitions: 249.5 GB + 90 GB = 339.5 GB.  But when I try to put a logical volume on the group, it tells me the size of the group is 316.5 GB.  Where did the other 23 GB go?!?  Is it normal for LVM to eat so much space?--it seems objectionable to me.

Experienced users, please advise.

--Andrew
[newbie here, first post.]

---

### Post by duminas on 2005-08-30
[QUOTE=AndrewStout]I'm having a similar problem: I'm trying to set up LVM through the 5.04 installer.  I made a volume group from two partitions: 249.5 GB + 90 GB = 339.5 GB.  But when I try to put a logical volume on the group, it tells me the size of the group is 316.5 GB.  Where did the other 23 GB go?!?  Is it normal for LVM to eat so much space?--it seems objectionable to me.

Experienced users, please advise.

--Andrew
[newbie here, first post.][/QUOTE]
 What both of you are experiencing is not a "problem" per se.
I can't really explain this too well in here, so go here and see if it helps:

[GFF Post of mine.](http://www.gamingforce.com/forums/showthread.php?p=1304794#post1304794)

[size=1]Replace Windows with Linux in that post, since it's the same thing you're experiencing. Basically, Ubuntu is speaking in true GB (1000:1), whereas LVM is speaking to you in GiB (1024:1). It's completely normal, and you're not losing any space.[/size]

---

### Post by AndrewStout on 2005-08-30
[QUOTE=duminas]Replace Windows with Linux in that post, since it's the same thing you're experiencing. Basically, Ubuntu is speaking in true GB (1000:1), whereas LVM is speaking to you in GiB (1024:1). It's completely normal, and you're not losing any space.[/size][/QUOTE]

Duh.  I should have thought of that...I guess I just assumed that the partitioner and LVM would use the same definition of "GB".

For the curious, the math is this:

339.5 x 1000 MB/GB x 1000 KB/MB x 1000 B/KB  / 1024 B/KiB / 1024 KiB/MiB / 1024 MiB/GiB = 316.

Thanks, Duminas.

--A.

---

