---
title: "File system for movie/music server"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by andrewsawyer on 2005-08-30
Hi all,

I want to make a movie server to either watch movies directly through a projector or via 802.11g to a laptop (running Ubuntu of course).

I am going to set it up with Ubuntu Server installation with MythTV, however I have no clue when it comes to the file systems.

I have a whole load of 350mb, 45min runtime avi files and a load more 700-800mb movie length avi/mpg files, along with about 50gb worth of mp3's - none of this breaches copyright of course!

I've currently got 2x300gb drives that are pretty much full and are formatted as NTFS (running Windows), and one spare unformatted 300gb.  I'm figuring on installing Ubuntu on the blank drive, and copying the contents of one NTFS drive over to it before formatting that drive and copying the second over to that, before formatting the second also.  This will leave me with again two pretty much full 300gb disks, however they will all be formatted for Linux, and I will have finally removed any trace on Windows from my house.

Can someone please tell me though, what would be my best option for file systems on these drives?  Should I just be using one file system for everything, or should the mp3's be in a separate partition under a different file system as they are smaller files?

Should I have any particular file type on the same physical drive as the OS or does this not really matter?  At a maximum, the computer will be playing something directly onto a projector while no more that two laptops stream off it.

I would obviously like something pretty stable, as it's kinda hard to backup all this stuff and I don't really want it disappearing one night!

Any help in this matter would be most appreciated.

Many thanks in advance,

Andy

---

### Post by sto6ma9ch on 2005-08-30
You may want to look into using XFS or JFS as the filesystem for the 
"media-only" drive partitions. These two filesystems handle larger files well. Between the two, it really depends who you ask as to which wil be better in your case. Here are some links of interest:

XFS: [http://oss.sgi.com/projects/xfs/](http://oss.sgi.com/projects/xfs/)
JFS: [http://ru.ecomstation.ru/showarticle.php?id=129](http://ru.ecomstation.ru/showarticle.php?id=129)

From what I've heard, the ext3 filesystem also has an option to support large files more efficiently. Here' some more info:

ext3 w/LFS: [http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html)

This info should help you make an informed decision. I'm not sure how/if Ubuntu supports these different types, but you could always give it a whirl.

---

### Post by tom-ubuntu on 2005-08-30
I used XFS for my MythTV Box, but ended up with corrupt files on the system. Since then, I switched 100percent to ReiserFS without any problems so far. My votes goes to ReiserFS.

---

### Post by sto6ma9ch on 2005-08-30
Hey Andrew,

Have you checked this out?
[The Home of Ubuntu MythTV](http://www.abarbaccia.com/)

sweet.

---

