---
title: "[SOLVED] How should I partition?"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by PickPocket8686 on 2007-10-22
I don’t really have a problem, so much as I’m just looking for some suggestions.
I’m in the process of moving from Windows to Ubuntu…  But I’m not sure how I should partition my hard drives.  Keep in mind I’m dumping Windows while I’m doing this so I’m only going to be running Ubuntu.

I have a 150GB 10,000RPM SATA Raptor, and a 300GB 7,200RPM IDE Barracuda 7200.8, I also have 2GB of Ram.
Now from the reading I’ve been doing I know I want to make a “/” a “/home” and a swap of 4096MB.
My questions to you guys is, how big should the “/” and the “/home” partitions be?  Should I make any other partitions?  And how should I do this across the two hard drives?
Also, because of the speed I would prefer to use the Raptor as much as possible.

Any advice you guys can give me would be great.
Thanks,
Austin

---

### Post by anotherdisciple on 2007-10-22
Sounds like you have the same question that I posted.. I had a few additional questions though. Let me know if someone replies to you... I'll let you know if I get an answer too.

---

### Post by aaaantoine on 2007-10-22
My suggestion: Put / and swap on the Raptor, and put /home on the Barracuda.  The reasoning is, put your applications on the fast drive because they will affect overall system performance, and store your documents on the big drive for the best utilization of space.  Also, in the event you run out of RAM (some day ;)), the swap file will operate more quickly on the Raptor.

---

### Post by forestpixie on 2007-10-22
Are you running 64bit - because otherwise I don't believe you'd be using 6Gb of ram and swap. 

I'd be inclined to use the SATA for / , /home and swap

use 10 - 20 Gb for /
if you're only using 32bit I'd do 1Gb max for swap
remainder for /home

I'd also use [gparted]("http://gparted.sourceforge.net/download.php") to do the formatting before installing, download and burn as an iso then boot with it. If you also format the other drive at the same time install should pick it up for you - it'll give it a name 

_another disciple_ - answered you as well :)

---

### Post by PickPocket8686 on 2007-10-22
I’ll be using the 64 bit edition.

I have a little over 150GB of music, videos, and documents.
So what I’m thinking is, I run the operating system, the swap, and all of my programs on the raptor, and keep my music/videos/documents on the seagate.
My question to you guys is how would I go about doing that?
And what all is kept in the “/home” partition?

Thanks,
Austin

---

### Post by forestpixie on 2007-10-22
think of /home as 'my documents' and you'll not go far wrong - it also keeps your config files for applications you install - much the same as the user folder in windows does.

I have 2 hdd's - I've got /, /home and swap on one with a bunch of music and the like on it and have more music etc on the other drive

It really is easiest I think to do all the partitioning outside of the install though. Personally I think that if you only have / and swap on the fast drive it'll be a waste.

Might be worth having a look at the forums regarding the amount of swap you're intending to use - I don't know enough to comment properly, but of course if you later find that you want to shrink it and add it to home that's not a problem

Hope that helps some :)

---

### Post by PickPocket8686 on 2007-10-22
Thanks for all of the help guys I've decided to go with this.

Western Digital Raptor 150GB 10,000RPM
/
Swap

Seagate Barracuda 7200.8 300GB 7,200RPM
/home

And I'll use gParted before hand to partition the drives.

---

