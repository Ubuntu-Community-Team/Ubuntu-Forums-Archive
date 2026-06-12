---
title: "Can't create partition larger than 50 GiB"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by Curtisc on 2007-09-14
I'm installing Ubuntu (Feisty) onto a brand new computer (Asus P5B, Core 2 Duo E6420) and I'd like to create a simple partition table with 15 gigs for root, 2 gigs for swap, and the rest of the 500 gig hard drive for home.  I can create the swap and the root partitions with no problem, but when I try to create the home partition it only lets me create a small one (between 48000 and 52000 Mb).  What's going on?

---

### Post by Pumalite on 2007-09-14
Why don't you install: Guided>Use Entire Disk?. Or if you prefer use Gparted (the stand alone, burn to CD, boot from program): [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by Curtisc on 2007-09-14
Okay, using gparted (not the standalone, just the one on the live cd) seems to have worked (it's installing now).  I actually did try guided, and when it gave me the summary of what it was going to do it looked suspicious:
- create swap on partition #1
- create ext3 on partition #5
That didn't make sense to me - 5 partitions?  And what's going on with 2 through 4?

Even though it worked for me to create partitions separately, this seems like a bug.

---

### Post by Pumalite on 2007-09-14
It has to do with primary and extended partitions. Don't worry about it.

---

### Post by Curtisc on 2007-09-14
> **Pumalite said:**
> It has to do with primary and extended partitions. Don't worry about it.
Would you mind explaining why it behaves this way (just for my own curiosity)?  It seems weird to me that the installer can't create 3 primary partitions with one bigger than 50 gigs, but gparted outside of the installer obviously can.

---

### Post by Pumalite on 2007-09-14
The explanation escapes me, but I see it in my installations all the time. If merlinus was around, he could give you the details.

---

### Post by psusi on 2007-09-14
The guided install creates a primary partition for the root, and makes the rest of the drive an extended partition, then places your swap in the extended partition.  Partition 1 is your root, partition 2 is the extended partition ( not shown ), 3 and 4 are not used, and partition 5 is the first partition within the extended partition.

---

