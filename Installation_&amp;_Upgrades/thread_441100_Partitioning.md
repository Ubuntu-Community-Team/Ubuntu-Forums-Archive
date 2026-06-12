---
title: "Partitioning"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by liberalist on 2007-05-12
I have two partitions, one for Mac OS X and one for other files and applications. I wish to split up my last partition, so that one could be used for those files and another for Xubuntu 7.04. 

Since Xubuntu 7.04 refuses to load on my system, I use the Alternate Install CD to install Xubuntu 7.04. My question is which options I need to choose in the textual installer? I wish to split up the 2nd partition in two; one with 90 GB and another with about 20 GB. Thank you very much in advance.

---

### Post by alchimera on 2007-05-12
> ...which options I need to choose in the textual installer? I wish to split up the 2nd partition in two...

I suggest that you set your partitions up before installing - use a live cd (eg GParted) - then it's one less thing to go wrong during the install!

---

### Post by liberalist on 2007-05-12
> **alchimera said:**
> I suggest that you set your partitions up before installing - use a live cd (eg GParted) - then it's one less thing to go wrong during the install!

I prefer to use Apple's Disk Utility, but I don't think that matters. How much space should my swap partition be? I remember from previous Xubuntu installations that it was 880 MB, is this enough for a system with 1024 MB RAM? 

My plan of action now: create two partitions, one 20 GB HFS+ and one 880 MB HFS+. In the partitioner (of the textual installer), I can reformat them to respectively ext3 and swap. 

Thank you very much in advance for your advice.

---

### Post by bulldog on 2007-05-12
Can't speak about the Apple Disk Utility,so it might work :) 
Your question about the swap file,there's a rule of thumb which says 'twice the amount of installed memory' but I have 1GB installed and a swap file 1GB and Feisty and Dapper run fine with it.

---

### Post by liberalist on 2007-05-12
Maybe I should use the partitioner that comes with Xubuntu 6.06.1, that might be safer.

---

### Post by bulldog on 2007-05-12
The safest :) but certainly the easiest way,is to use the gparted live cd.
A graphical environment is yours,and it make the partitions much more visible.
Just try it,only a 55MB download. 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by liberalist on 2007-05-12
Thanks for the tip, bulldog.

---

### Post by liberalist on 2007-05-12
I could only launch the GUI of GParted with the force VESA option. Since GParted cannot read HFT+ volumes/partitions, I could not resize them. Are there any other ways to split up my 2nd partition?

---

### Post by alchimera on 2007-05-12
In the olden days, they used to say that swap = 1.5 x ram, but this was because they had so little ram that disc space was needed as an overflow, like extra ram, but slow.

If you have a gig or so of ram, it isnt very likely that your swap partition will get used very much - i have 1.25GB of ram and am currently using just 32MB of swapspace... so maybe give it half a gig to be totally safe. 

Sorry, it didnt twig that it's a Mac you have, duh! I would use the in-house tools, i'm sure that they are good but i cannot advise as i have no experience with such wonderful tech... once you have them in place you know where you're going when you start your install. Take it slow, run it through up to the point where stuff happens as many times as you like!

Just one more thing - i used the alternative install about a year ago (several times!) and i recall that some of the information in one part of the partitioner was only visible by scrolling down... possibly it was to finish the set up. Dont know if it has changed any, but thought it worth a mention.

All the best!

---

### Post by liberalist on 2007-05-13
Thanks for your reply. However, Apple's Disk Utility apparently cannot resize existing partitions. If I reformat my existing partition with GParted to ext3, is it then possible to split this partition up in one of 20 GB, one of 90 GB and one swap partition of 1.5 GB? Thank you very much in advance.

---

### Post by bulldog on 2007-05-13
I should think so,however,there are some things you should keep in mind though.

You can have only four primary partitions,if you want to have more as four partitions,you'll have to make an extended partitions.
To make an extended partition,you'll have to give in one primary,so you can have three primary's and one extended.
In the extended partition you can create logical partitions,as much as you want.
But keep in mind,although ubuntu doesn't care to be on a logical partition,windows does.
Windows should be on the first primary,don't know about Apple though.

Par Example,
hdd 100 GB
20GB windows first primary
20GB OSX second primary
10GB ubuntu / root partition third primary
50GB extended partition [you can't put any data to this one]
1GB swap first logical
20GB /home second logical
19GB /data third logical
10GB /data fourth logical

Hope you get what I mean,if not just ask.

---

### Post by alchimera on 2007-05-13
> **liberalist said:**
> Thanks for your reply. However, Apple's Disk Utility apparently cannot resize existing partitions. If I reformat my existing partition with GParted to ext3, is it then possible to split this partition up in one of 20 GB, one of 90 GB and one swap partition of 1.5 GB? Thank you very much in advance.

Q: are you familiar with the terms 'primary', 'extended', and 'logical' as applied to partitions? A breif explaination:
(i) a drive can have a maximum of 4 primary partitions
(ii) 1 of these can be an extended partition
(iii) an extended partition can be split into as many logical partitions as you like.

...so if the partition you are talking about is an extended partition, no problem - create and format partitions within it.

Reformatting to ext3 will not turn a primary partition into a extended partition, you have to do that yourself - without booting up gparted, i cant say for sure exactly how but with gparted nothing happens until you click 'apply', so you can play with it untill you are happy with how it looks.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) may be of interest.

Good luck!

---

### Post by liberalist on 2007-05-13
Thanks for the information. I am not familiar with the terms 'primary', 'extended' and 'logical'. Both disks are formatted HFS+ extended (Journaled), so I guess they both are extended (and journaled).

---

