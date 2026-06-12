---
title: "Installing 6.10 with XP"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by Sicilianmandolin on 2007-02-16
I printed a whole 24 page document with instructions on installing Dapper Drake, and low and behold, 6.10 is far different than I expected (WONDERFULLY so). I've reserved 40 GB of my 160 GB harddrive (the rest is being used by Windows) for Ubuntu 6.10 and, having clicked the Install icon and followed through to step 5, I'm prompted to choose how I would like to partition the disk. So, I'm thrown a curve ball because I wasn't expecting to see the option, "Use the largest continuous free space" and am wondering if I might want to choose it. The instructions I have are for manually editing the partition table, but I'm willing to dedicate the rest of my HDD space to this beautiful operating system. What will this new option do, exactly? What should I do?

Thanks!

(P.S. I already have 2 partitions on my disc, one for XP and one for recovery)

---

### Post by bjornolai on 2007-02-16
I take it you haven't made partitions for your linux system yet :) I prefer seting up the partitions before i run the install program (makes me feel I'm more in control). You probably have a live cd. Before you hit the install button go to system > administration > gparted. There you can easily edit your partitions manually. Sounds like you need to make an extended partition and put three logical partitions inside that one. ext3 for root and home and swap for (suprise) swap.

---

### Post by Sicilianmandolin on 2007-02-16
.....................

---

### Post by Sicilianmandolin on 2007-02-16
Ok, I went ahead and did some partitioning. I created an Extended partition with roughly 35 GB capacity. How should I divide the remaining logical partitions?

---

### Post by Sicilianmandolin on 2007-02-16
How does this look? [http://img300.imageshack.us/img300/6063/screenshotac9.png]("http://img300.imageshack.us/img300/6063/screenshotac9.png")
Have I selected the proper filesystems? How about the sizes? Now, what do I assign these partitions as?

---

### Post by bjornolai on 2007-02-16
Remaning logical? The logical partitions go into the extended. Maybe I just misunderstood you. In the extended partition you made (35 gig) you should make one partition approx 2gig this should be formated as swap, then you should make one approx 8 gig formated as ext3, then another ext3 partition for what you have left.

When you get to installing chose manually to set up the partitions. You dont have to do any partitioning since you've done it so skip that step :) Your root marked as  /   is the 8 gig partition. Your home marked as   /home   is whatever you had left. And your swap is the swap. In the installation these are the only drives ubuntu should format! He will tell you before he formats anything, so just make sure of you read carefully.

I would advise you to make you extended partition bigger and add a fourth partition into it. Ubuntu does not write to ntfs partitions. So what is nice is having a fat32 partition for swaping files between windows and ubuntu :)  

Setting up the mount points during install can really help you save time later. That is tell the instalation program to mount sda2 as sda2 and sda1 as sda1 :)

Well I'm off to bed. Hope to see you on ubuntu soon :)

---

### Post by bjornolai on 2007-02-16
Just saw your last picture. 

The swap looks ok, maybe a little small but I think it'll be alright. 

The ext3 i guess is were you want to put your root (I would use ext3 for root to play it safe at least). It's big. If you set it at 8 gigs i can hardly see you will ever run out of space. 

I'm not sure about having fat32 as your home. I guess it would work fine, I have just never done it :) The advantage would be read write acess from both win and linux. I say give it a go :)

my suggestion
25 gig fat32  this is  home     /home
8 gig ext3  this is root       /
1 gig swap  this is  swap

---

### Post by Snowbat on 2007-02-16
The disadvantages would be: no recovery journal, no file ownership, and maximum file size of 4GB.

I'd recommend you stick with EXT3 for /home.  There are free Windows programs that allow easy access to EXT2/3 partitions from within Windows.  There is also [Captive NTFS]("http://en.wikipedia.org/wiki/Captive_NTFS") if you need NTFS write from Linux.

---

