---
title: "Sharing a /home partition"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by Pumpkin Eater on 2007-03-21
After a disaster where WinXP's partition editor decided unilaterally to renumber all my partitions resulting in Ubuntu trying to use the Win partition as Swap, I'm about to do a reinstall of XP.  While I'm about it, I'd like to install 32 bit Edgy to compare with the existing 64bit version I already have.  If possible, I'd like all 3 OS's to share the same data partition.  

Is it feasible to define a FAT32 partition as /home in both the Ubuntu installations and map it to "My Documents" (uggh!) in windows?  

My main concern is whether the settings stored by the 2 flavours of Ubuntu in my /home directory will clash.  Any thoughts or experiences of this?

---

### Post by chewearn on 2007-03-21
Afaik, it is not a good idea to share /home partition between two linux installs.  Many applications store their configuration files there and you might get conflicting settings.

---

### Post by Pumpkin Eater on 2007-03-21
That's what I thought.  

I have a supplementary question:

Is there any problem with 2 linux installations sharing the same swap partition?  I don't see why there should be, and I presume they would both find it automatically without being pointed at it.

---

### Post by chewearn on 2007-03-21
Sharing swap partition should work, no problem.  I used to have one shared swap partition for 3 different linux install on my system (two ubuntu + 1 opensuse).

---

### Post by Homeschool Hacker on 2007-03-22
I happen to have the same question as Pumpkin Eater:
"Is it feasible to define a FAT32 partition as /home in both the Ubuntu installations and map it to "My Documents" (uggh!) in windows?"

---

### Post by lloyd_b on 2007-03-22
> **Homeschool Hacker said:**
> I happen to have the same question as Pumpkin Eater:
"Is it feasible to define a FAT32 partition as /home in both the Ubuntu installations and map it to "My Documents" (uggh!) in windows?"
I suspect not (though I haven't tested it).  For one thing, I don't believe that FAT32 will allow filenames that start with a period, of which there are tons in the typical home directory (.bashrc, .mozilla, etc).  

Secondly, FAT32 will not allow the creation of symlinks, which could potentially cause problems.

Lloyd B.

---

### Post by Homeschool Hacker on 2007-03-22
Thanks, Lloyd.  I'm assuming you couldn't share the partition were it in another format?

---

### Post by chewearn on 2007-03-22
One way you might consider is mount one directory below /home and My Documents; e.g.

/home/fat32share
My Documents\fat32share

---

