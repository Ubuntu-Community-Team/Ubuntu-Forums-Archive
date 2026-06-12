---
title: "New Installation problem"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by bsprowl on 2006-12-16
My system has a Asus A8N-E motherboard, 512 MB of ram, Radeon X700 video card, and Raid with two Seagate 80 GB hard drives and works fine wiht Windows XP professional. NO disk partition is even half full.

During the initial installation from the CD the system locks with the orange progress box, two lines of blue fuzzy dots and a green line showing.

I tried it again in safe graphics mode; same result.

Tried it again after adding DEBCONF_DEBUG=5 as suggest in the installation notes; same results.

Any suggestions?

Thanks, Bob

---

### Post by taurus on 2006-12-16
Try using the alternate CD...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by bsprowl on 2006-12-17
OK.  I'll download that.

I've also down loaded Dapper Drake and  will try that in a few minutes.

Are any files stored on my computer as part of the initial boot process?  I couldn't see any.

Thanks, Bob

---

### Post by nyinge on 2006-12-17
Are you saying that you're installing Ubuntu on a raided hard drives with XP already on it?  You might wanna take a look at [this page]("https://help.ubuntu.com/community/FakeRaidHowto") first, imho.

---

### Post by rlgc79 on 2006-12-20
I had the same problem.  To install Ubuntu on my system, I had to turn off DMA for my DVD-RAM. You only need to pass the parameter ide=nodma to the kernel upon boot. 

If I turn on DMA, my computer locks up or behaves strangely when it reads any CD/DVD.  This problem is reproducible in every Linux distribution, but on Windows XP everything is ok  ](*,) . (Maybe an incompatibility between the Linux kernel and my IDE controller? )

My Computer:
Asus A8N-E 
MATSHITADVD-RAM SW-9585, FwRev=B100

---

