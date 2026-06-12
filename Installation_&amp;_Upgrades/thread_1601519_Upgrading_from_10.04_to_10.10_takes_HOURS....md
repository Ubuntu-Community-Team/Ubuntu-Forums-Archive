---
title: "Upgrading from 10.04 to 10.10 takes HOURS..."
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by zzarko on 2010-10-20
My 10.04 system has downloaded all packages needed for upgrade almost two hours ago (~2GB of files), and is PAINFULLY SLOWLY installing them on HD. Two hours ago, the message said "About 9 hours remaining", now it's "About 7 hours remaining". This is ridiculous. I already commented on launchpad bugs the difference in dpkg performance between 9.10 and 10.04 (dpkg, in my case, is 4 times slower in 10.04 than it was on 9.10, see [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/537241](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/537241)).

Any sugesstions (or should I just leave the damn thing till tomorrow...)? Did anyone expierenced anything similar? If not, then there is something seriously wrong with my system...

My HW: ASUS P5B Deluxe, 2GB RAM, ATI 4870, 4xSATA HD (system disk is 1.5TB WD15EARS-00Z5B1; Ubuntu partition is ext4, has 23GB free, so I guess it's enough).

P.S. I remembered the 4Kb partition alignment penalty, but fdisk says that this disk has 512b physical sectors, so I guess it's not that.

EDIT: Today, I also upgraded my other two machines (one older desktop, and one newer laptop), without issues. I'm confused...

---

### Post by TBABill on 2010-10-20
My upgrade on my laptop (Intel Core i3 if it matters) took about 2 hours, maybe a bit more, to complete. It's painfully slow to upgrade compared to a fresh install, but that's to be expected. 9 hours seems like a long estimate to me though. But stopping it would bork the system and require formatting, reinstalling, etc., plus possibly losing anything you didn't already backup (hoping you backed up before starting the upgrade!!).

---

### Post by Mr_VeRiTy on 2010-10-20
All of my previous experiences with upgrading didn't go so well, I highly recommend doing a fresh install for better results and faster speed.

---

### Post by psusi on 2010-10-20
> **zzarko said:**
> 
P.S. I remembered the 4Kb partition alignment penalty, but fdisk says that this disk has 512b physical sectors, so I guess it's not that.


That's because the drive lies.  It does use 4kb sectors, so make sure the partition is aligned.

---

### Post by zzarko on 2010-10-20
> **psusi said:**
> That's because the drive lies.  It does use 4kb sectors, so make sure the partition is aligned.

House: Everybody lies! :)

It's not aligned on 4k boundaries. I checked what fdisk said at the time of formatting, but I didn't checked the net to see if this was really true. It appears that this model reports 512b size, although it's 4k.

Well, I guess I'll need to find a 1TB drive to transfer all data, format my HD, and transfer it back. And I'm going to measure the performance before and after, to see if that was the problem. If not, then ARGH!

P.S. There was some question about grub, I wasn't by the computer to see it (who would?), and it was waiting... I answered, and now it's just 2 hours to go... :) or :( ?

---

### Post by Dale61 on 2010-10-21
I don't know what your worried about.  Back when I upgraded from 6.06LTS to the next LTS (8.10?), it took 100 hours and 20 minutes for the update, then another couple of hours to set up/replace old files with new.

---

