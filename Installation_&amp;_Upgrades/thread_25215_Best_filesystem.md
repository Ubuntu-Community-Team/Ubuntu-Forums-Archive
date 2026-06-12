---
title: "Best filesystem?"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by Promethe on 2005-04-09
I'm going to install Ubuntu second time - this time with full version, very careful (without messing with ...argh... KDE) and make OS very fast. 
I've got one 40 gigs HDD which I can use for it. I want to store MP3 and movies in my home directory, install VMware there, etc. I don't need exchange with WinXP becouse I'm usually doing file exchange beetwen my PCs by uploading/downloading on my server or I use drivers for windows (very rare). 
So - how I should partition my disk-drive and what filesystems I should use?

My conf used for Linux:
Athlon XP 2800+
40 GB Maxtor 7200RPM
nVIDIA GeForce 5900XT
1 GB RAM
2x DVD-+RW DL recorder
Sound Blaster Audigy 2 ZS
SyncMaster 913n
(if you are intrested of course :))

---

### Post by humanity_to_others on 2005-04-09
reiserfs faster, but ext3 more stable.

---

### Post by sas on 2005-04-09
[QUOTE=Promethe]I'm going to install Ubuntu second time - this time with full version, very careful (without messing with ...argh... KDE) and make OS very fast. 
I've got one 40 gigs HDD which I can use for it. I want to store MP3 and movies in my home directory, install VMware there, etc. I don't need exchange with WinXP becouse I'm usually doing file exchange beetwen my PCs by uploading/downloading on my server or I use drivers for windows (very rare). 
So - how I should partition my disk-drive and what filesystems I should use?

My conf used for Linux:
Athlon XP 2800+
40 GB Maxtor 7200RPM
nVIDIA GeForce 5900XT
1 GB RAM
2x DVD-+RW DL recorder
Sound Blaster Audigy 2 ZS
SyncMaster 913n
(if you are intrested of course :))[/QUOTE]
 It depends on what files you are using, some file systems are optimised for lots of little files, some for bigger files. 

There's [thorough benchmarks and comparisons](http://linuxgazette.net/102/piszcz.html)  which concludes:
>  For those of you still reading, congrats! The conclusion is obvious by the "Total Time For All Benchmarks Test." The best journaling file system to choose based upon these results would be: JFS, ReiserFS or XFS depending on your needs and what types of files you are dealing with. I was quite surprised how slow ext3 was overall, as many distributions use this file system as their default file system. Overall, one should choose the best file system based upon the properties of the files they are dealing with for the best performance possible!

Personally I always use reiserfs.

---

### Post by Promethe on 2005-04-09
I heard that reiserfs isn't very stable fs, but XFS is quite fast and very safe. True or not?

---

### Post by sas on 2005-04-09
[QUOTE=Promethe]I heard that reiserfs isn't very stable fs, but XFS is quite fast and very safe. True or not?[/QUOTE]
 Reiser fs is plenty stable these days, Suse for example use it as the default fs in their distro, the version that comes with ubuntu is plenty stable.

XFS had stability problems in the past too.

---

### Post by NilsHG on 2008-06-21
I found this thread and by bumping it I hope to get some more comments.

I am about to set up a new machine with a fast 10k rpm HDD (WD Raptor) and wonder what the best filesystem would be. "best" as in fast, but not at the cost of stability. The computer will be a normal Desktop used for office, web, chat and some gaming and to store music and video collection. should i stick to ext3 or are there alternatives too consider

---

### Post by articpenguin on 2008-06-21
stick with ext3, Its tried and tested. ALso EXT4 should be ready in 6 months or so. The other filesystems are a little more fast than ext3 but not much of a difference. If you want more speed use JFS.

---

### Post by kerry_s on 2008-06-21
jfs, it rocks, good enough for servers, better performance for the desktop/laptop.

---

