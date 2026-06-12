---
title: "How much space for Ubuntu partition?"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by blackberries on 2011-05-27
hi,

I'm a total noob, and was wondering how much space should I partition part of my HDD for Ubuntu? I never used Linux in my life before and need an answer. got a 64-bit Ubuntu ready on CDRW to install.

I got a 200gigs of my old IDE Seagate HDD, Parition 1: 30gigs for Windows 7 and already like 25 filled up, Parition 2: rest is for backup. So, I was thinking of backup up all the files on Parition 2 to another HDD, and then delete it>create Parition 2 for Linux and Parition 3 for the rest, but how much space for 2?


my system:

AMD Athlon II X2 255 Regor 3.1GHz Socket AM3 65W
Foxconn A76ML-K
ECS NR9800GTE-512QX-F GeForce 9800 GT 512MB 256-bit DDR3
A-DATA 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)
CORSAIR CMPSU-400CX 400W
200G Seagate (Master)
500GB Wester Digitital SATA

---

### Post by Joe of loath on 2011-05-27
Personally I'd go for around 20 gigs for /, and as much space as you can spare for /home.

---

### Post by blackberries on 2011-05-27
is / and /home supposed to be on 2 different partitions? what is /?

---

### Post by Old_Grey_Wolf on 2011-05-27
> **blackberries said:**
> 
I got a 200gigs of my old IDE Seagate HDD, Parition 1: 30gigs for Windows 7 and already like 25 filled up, Parition 2: rest is for backup. So, I was thinking of backup up all the files on Parition 2 to another HDD, and then delete it>create Parition 2 for Linux and Parition 3 for the rest, but how much space for 2?


If you are going to use the 500GB Western Digital SATA for the backups; then, I would divide the 200GB Seagate in two spaces 50% for Windows and 50% for Linux. If you want an additional partition for a shared data partition, I would determine what that partition size should be then give Windows 50% and Linux 50% of what is left over. Since you are doing backup, you can safely change the partition sizes later if you determine you need more for one of then or another.

Edit: the reason I used the term spaces is because both Windows and Linux can use multiple partitions.

---

### Post by Joe of loath on 2011-05-27
Sorry, should have explained.

/ is the system root, where all the system files live. It generally doesn't take up more than 15gb (On my servers, / uses less than 1gb). /home is where the userdata lives. You can have them as separate partitions if you wish, although it's not necessary.

---

### Post by blackberries on 2011-05-27
unless there is going to be a difference in performance, i would rather have them on the same partition. as long as both are ran on linux, i'm good.

---

### Post by blackberries on 2011-05-27
> **Old_Gray_Wolf said:**
> If you are going to use the 500GB Western Digital SATA for the backups; then, I would divide the 200GB Seagate in two spaces 50% for Windows and 50% for Linux. If you want an additional partition for a shared data partition, I would determine what that partition size should be then give Windows 50% and Linux 50% of what is left over. Since you are doing backup, you can safely change the partition sizes later if you determine you need more for one of then or another.

Edit: the reason I used the term spaces is because both Windows and Linux can use multiple partitions.

I don't see the point of this because I use 200 gb HDD as a backup as well, and want to partition as less as needed for OSs.

---

### Post by Joe of loath on 2011-05-27
> **blackberries said:**
> unless there is going to be a difference in performance, i would rather have them on the same partition. as long as both are ran on linux, i'm good.

There's no performance hit, the only difference is it makes reinstalls and upgrades easier.

---

### Post by lordadi on 2011-05-27
Careful here: you should, ideally, backup to something that is NOT your primary day-to-day OS drive. Saves a lot of hair when the drive gets fried - happened to me ;)

---

### Post by Old_Grey_Wolf on 2011-05-27
> **blackberries said:**
> I don't see the point of this because I use 200 gb HDD as a backup as well, and want to partition as less as needed for OSs.

I thought that > So, I was thinking of backup up all the files on Parition 2 to another HDD, and then delete it>create Parition 2 for Linux and Parition 3 for the rest, but how much space for 2? meant that you were going to use the Western Digital for backups, then delete the backups from the Seagate, and install Linux on the second partition. I thought that you may be planning to use the third partition for shared data. I guess I misunderstood.

---

### Post by Old_Grey_Wolf on 2011-05-27
> **lordadi said:**
> Careful here: you should, ideally, backup to something that is NOT your primary day-to-day OS drive. Saves a lot of hair when the drive gets fried - happened to me ;)

Especially when the primary 200GB Seagate is an IDE drive that is obviously older than the 500GB Western Digital SATA drive.

---

### Post by lordadi on 2011-05-27
> **old_gray_wolf said:**
> especially when the primary 200gb seagate is an ide drive that is obviously older than the 500gb western digital sata drive.

+1

---

### Post by oldfred on 2011-05-27
There is a very minor advantage to smaller / (root) partitions and separate /home or data partition. We have seen from the boot script were on a 1 or 2TB drive the install files may be anywhere on the drive. Then the drive heads have to search entire drive for system files. If all system files are near each other then less searching. System files are accessed more than any data files so having data somewhat scattered is not an issue.

---

