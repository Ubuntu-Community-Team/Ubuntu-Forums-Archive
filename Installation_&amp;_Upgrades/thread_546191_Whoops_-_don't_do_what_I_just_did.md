---
title: "Whoops - don't do what I just did"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by bvz on 2007-09-08
I just accidentally blew away my roomate's windows computer trying to re-install ubuntu.

Damn. 

It was 99% backed up luckily.

Here is what I did:

I decided to re-install ubuntu (which I am trying to get her to use instead of windows which is giving her nothing but grief).  When it asked what partitions to use, I decided to do it manually.  This is because it kept trying to subdivide the existing windows partition smaller and smaller.

I found the ext3 partition using the Genome Partition Manager and deleted it.

When I continued, it gave me the list of things it was going to do, and I could see that it was only going to use the free space (sd5) and the swap (sd6).  But then... yikes... it gave me an error while it was formatting and boom - no more partitions at all and when grub loads I just get an error 5.


sigh.  That is what happens when you know just enough to get you into trouble...

Problem is:  I can't find her XP restore disks (there was a restore partition on her drive which is now also all gone).  And she is off camping for the weekend.


So... it's all ubuntu for her now :)



Here is the lesson I want to impart to you all:

a) do not mess with any sort of re-install or partitioning unless you really know what you are doing
b) always always always back up before you do anything

---

### Post by maybeway36 on 2007-09-08
You could try booting a DOS floppy/CD and typing ```
fdisk /mbr
```, this will get rid of Ubuntu but let you boot windows.

---

### Post by zipperback on 2007-09-08
> **bvz said:**
> 

Here is the lesson I want to impart to you all:

a) do not mess with any sort of re-install or partitioning unless you really know what you are doing
b) always always always back up before you do anything


And you left out a couple of really important ones.

c) RTFM before doing anything.

d)Thou shalt not play with other peoples computers without their express permission and a 100% full backup.

- jack
- zipperback

---

### Post by bvz on 2007-09-08
maybeway36: really?  Shoot.  I should have waited a bit.


I've gone ahead and re-partitioned the whole thing, and am re-installing windows (boo!) and ubunut (yay!)

Good to know for future reference.

Thanks

b

p.s.

Installing windows without the OEM disks is a real pain.  A plain XP install from a purchased disk leaves me with no wireless network,  screwed up video drivers,  no trackpad scrolling, nothing.  Ubuntu is much much easier.  My but how things have changed!

---

### Post by bvz on 2007-09-08
As far as re-installing is concerned...  how would one go about doing that?  The installed kept trying to re-partition the XP partition, it wouldn't re-use the existing ext3 one.

---

