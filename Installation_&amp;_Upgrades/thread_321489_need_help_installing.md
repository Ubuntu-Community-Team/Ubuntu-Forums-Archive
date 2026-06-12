---
title: "need help installing"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by nish_lal on 2006-12-19
i m trying to install ubuntu 6.06(trying linux for the 1st time) on my pc which already has windows xp and lots of data.
i m using the live cd for installation and so far i like this os.. i m even able to access the internet with almost no configuring.:)
now when i try to install i am unabe to use the option to usee the free space on the disk.. it gives me an error mssg 




[IMG]http://img220.imageshack.us/img220/4904/screenshotvq1.png[/IMG]

altho  if i click ok it still goes to the next screen which looks like this..



.[IMG]http://img222.imageshack.us/img222/732/screenshot1ek5.png[/IMG]




i go bak to manual partitioning .. and my partition table looks like this.. (without any changes)..




[IMG]http://img204.imageshack.us/img204/9835/screenshot2wz6.png[/IMG]




i had transferred data over from one of the partitions to make room for linux .. but now i dont know how i go about doing that cuz i cant make more than one partition in that free space.. (error mssg--"It is not possible to create more than 4 primary partitions
If you want more partitions you should first create an extended partition. Such a partition can contain other partitions.")


but if it also does not allow me to make extended partiotion in the free space.. 

any suggestions??

---

### Post by gruffy-06 on 2006-12-19
Looks like you're in a sticky situation.

There is already an extended partition on your disk and two primary partitions. Therefore, the installer cannot create two partitions: a root and swap partition. That would add up to five.

I suggest you either: (a) - backup all Windows data and install Ubuntu over it (I'm already boycotting Microsoft), (b) - get an external hard disk and install Ubuntu on that or (c) - get an external hard disk, create a root partition on the main disk and a swap partition on the external disk.

The cheapest option would be (a), but you may be better off with (c).

---

### Post by louieb on 2006-12-19
The reason you can not install Ubuntu is the location of the free space and the fact that you already have an extended partition (hdb1).  
You need two partitions to install Ubuntu one for / and one for swap.
If the free space were just after hdb1 then it could be used to create two more logical partitions  (you have 1 hdb5).
You could create a primary partition out of the free space and copy hdb2 to it.
Then delete hdb2 and resize hdb1 to include the newly freed space.
Then create the two logical partitions. 
Then install Ubuntu.
I hope you have a backup or you don't care if the data gets destroyed.

Aw heck with it. go with gruffy-06 idea.

---

### Post by Sef on 2006-12-19
You could run into a problem too because XP is on /dev/hdb2.   Windows likes to be on the first partition.

> There is already an extended partition on your disk and two primary partitions. Therefore, the installer cannot create two partitions: a root and swap partition. That would add up to five.

Only 4 primary partitions are allowed, but that limit does not apply to logical (extended) partitions.   You can make as many of them as you want.

---

### Post by bahn on 2006-12-19
> **Sef said:**
> You could run into a problem too because XP is on /dev/hdb2.   Windows likes to be on the first partition.



Only 4 primary partitions are allowed, but that limit does not apply to logical (extended) partitions.   You can make as many of them as you want.

You can edit the boot.ini to refect the change so that it will boot of the second partition or others.

---

### Post by nish_lal on 2006-12-19
thanks guyzz fer the help .. 
i solved the problem by fairly simple means...
>>>>downloaded partition magic 
>>>> merged 2 storage partitions which i use wid windows 
>>>> now because the free space was between these two partitions so it also became a part of one 95 gb partition 
>>>> then i resized this partition for it to leave 20gigs free space at the end of my drive 
(between all of the above steps i m omiting the part when pm spit out weird error mssgs and once when my pc got stuck after verifying dmi pool data)

but anyways now i had only 2 partitions on my drive and 20 gigs of free space right where i wanted it :D :D >>> put in the live cd and the installation went without a hitch:KS  ( i let unbutu do the partitioning)

so thx everyone.. i now  have a very sweet little copy of ubuntu running on my pc without annoying windows too much!!
(i m gonna kill next few dayz understanding this terminal thing on linux.....)

one more thing .. can anyone suggest an equivalent of k-lite codec pack i have on windows for linux???

---

### Post by darrenm on 2006-12-19
> **nish_lal said:**
> one more thing .. can anyone suggest an equivalent of k-lite codec pack i have on windows for linux???

Don't know what K-Lite is but this should give you every codec you need:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

