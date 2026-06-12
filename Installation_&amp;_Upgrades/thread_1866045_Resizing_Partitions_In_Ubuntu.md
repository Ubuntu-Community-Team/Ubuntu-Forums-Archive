---
title: "Resizing Partitions In Ubuntu"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by littlekatfish2003 on 2011-10-20
Hey guys,

Okay here is what I have done. I have downloaded the newest version of Ubuntu for my HP desktop. Instead of burning the ISO to a CD, I ran an install by mounting the ISO straight from my windows desktop however, when I set Ubuntu up, I must have done something wrong; I wanted Ubuntu to use the entire hard drive, instead it only used a portion of it, and now I have a dual boot system. My question would be, is there a way to resize the Ubuntu partition so that it is using the entire hard drive on my desktop, instead of just half of it?

Thanks:popcorn:

---

### Post by u-slayer on 2011-10-20
Yes. Boot for from your ubuntu CD.

Run Gparted. (system->admin->gparted)

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by littlekatfish2003 on 2011-10-21
OK thanks, I'll give this a shot. It shouldn't be that bad. I have had some experience with Ubuntu before. I believe in what it stands for. I'll let you know how it goes.
 
Thanks:)

---

### Post by varunendra on 2011-10-25
> **littlekatfish2003 said:**
> I have downloaded the newest version of Ubuntu for my HP desktop. Instead of burning the ISO to a CD, I ran an install by mounting the ISO straight from my windows desktop
How did you do that? I doubt it is a WUBI installation if you installed it 'directly through windows'. If so, you will have a 30GB limit on disk space. To confirm, see if your windows partition has a folder named "ubuntu". For more info, you may wish to read this page: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Mark Phelps on 2011-10-25
> **littlekatfish2003 said:**
> My question would be, is there a way to resize the Ubuntu partition so that it is using the entire hard drive on my desktop, instead of just half of it?

Sounds like you did a Wubi installation, and if so, while it is POSSIBLE to transform that to use the entire drive, it is a LOT of work.  It would be better, in that case, to erase the drive and start over with a clean installation -- using the entire drive this time.

---

