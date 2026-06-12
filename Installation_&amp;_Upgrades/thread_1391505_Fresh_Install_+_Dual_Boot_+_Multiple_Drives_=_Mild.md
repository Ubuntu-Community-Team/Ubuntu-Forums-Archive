---
title: "Fresh Install + Dual Boot + Multiple Drives = Mild Panic"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by random_excess23 on 2010-01-26
[SIZE=1]Hello

       I have been using Linux for a little while now, my friend gifted me a machine about a year and a half ago and it quickly became my favorite. It even sneaked onto my laptop in the form of a live CD when the hard drive died. I retained my Windows computer to use Adobe Creative Suite, to Sync with my phone and for playing LAN games with my housemate.

       I am about to upgrade the hard drive in the Linux box and thought I may as well go for a dual boot system. I don't use Windows that often so I thought it would be nice to pass on the other computer to someone else who needs it and free up some of my desk space. The current drive is about 40GB, I have a 320GB and 120GB to replace it with but am unsure of how to organize a dual boot fresh install across these two drives (possibly three if I can find the space to retain the 40GB.) All three drives are IDE and I have a 230GB external which I suppose I could use for backups or sharing files.

My main concerns are:
[/SIZE]
[LIST]
[*][SIZE=1]Which drive to install the two operating systems to, the larger, smaller or keep both separate?[/SIZE]
[*][SIZE=1]How to set up shared file access between both systems.[/SIZE]
[*][SIZE=1]What size to dedicate to the different partitions and what file systems to use for them.[/SIZE]
[*][SIZE=1]Will how I arrange things now impact on upgrading Ubuntu in the future?[/SIZE]
[/LIST]
[SIZE=1]
   I'm sure there are several ways of dealing with this situation, each with their own advantages and disadvantages but being relatively new to this I'd appreciate some experienced advice.

       I tried searching for a similar thread but all I could find were people trying to do things that were even more fiddly so sorry if this is a bit trivial.
[/SIZE]

---

### Post by earthpigg on 2010-01-26
> > **random_excess23 said:**
> [SIZE=1]
My main concerns are:
[/SIZE]

[*][SIZE=1]Which drive to install the two operating systems to, the larger, smaller or keep both separate?[/SIZE]
assuming both are reliable, install the OS on whichever hard drive is ***faster***.

[QUOTE][*][SIZE=1]How to set up shared file access between both systems.[/SIZE]

create a large NTFS or FAT32 partition somewhere. both will be able to read/write to it by default.

> [*][SIZE=1]What size to dedicate to the different partitions and what file systems to use for them.[/SIZE]

what i would do...

_if the 120gb is faster:_
15gb for /, ext4.
40gb for /home, ext4
2gb for swap
48gb for Windows
320gb hard drive, NTFS, shared/multimedia.

_if the 320gb is faster:_
15gb for /, ext4
??gb for /home, ext4... not counting multimedia/music/movies/etc in your current home, look at how big it is to get an idea of your usage habits.
2gb for swap
??gb for Windows. however big you anticipate needing. 
rest an NTFS partition, shared/multimedia.
120gb hard drive, NTFS, more shared/multimedia.

either way, i'd go for installing both operating systems on the same hard drive. partition everything first, install windows second, install ubuntu last.

> [*][SIZE=1]Will how I arrange things now impact on upgrading Ubuntu in the future?[/SIZE]

making a separate /home should take care of that. if you think you will ever find yourself wanting to install several different linux distros at once, then look into a separate /boot partition.

---

### Post by random_excess23 on 2010-04-04
Thanks very much earthpigg, I set this up a little while ago and all is working very well.

---

