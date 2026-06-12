---
title: "Partitioning Error"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by new to ubuntoo on 2013-03-18
Hey i'm trying to install ubuntu 12.04.2 desktop i386 on a toshiba NB250, which currently has no OS, from a USB drive. I can get up to the point where the installer is creating partitions when i get the error (paraphrasing) "failed to created swap in partition 5 (0,0,0) sdb"
wondering if anyone has had a similar issue and/or knows of a fix, it would be greatly appreciated. :D

---

### Post by r.stiltskin on 2013-03-18
That doesn't give much information to go on.

Here's an idea.  Instead of trying to install immediately, when you boot from the USB choose "try ubuntu".  After it boots up you can run gparted to try to set up your hard disk partitions.  If it doesn't work at least it should give more information about the problem.

---

### Post by new to ubuntoo on 2013-03-18
thanks

---

### Post by oldfred on 2013-03-18
gparted is a app on the live installer. But it is not installed by default in your install as you cannot really use it on the same partition(s) you are working from.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

---

### Post by new to ubuntoo on 2013-03-18
can you give me a quick rundown of the best setup of partitions please? i'm running the machine really only for the sake of getting to know linux, working on learning python and web applications.

---

### Post by new to ubuntoo on 2013-03-18
the installer may have been trying to partition the flash drive i was booting from. 
then when i open gparted i have 3 partitions. /dev/sdb1 is 148/150 GB and is ext4
then there is /dev/sdb2 for 1012 MB it's extended
and then inside /dev/sdb2 is sdb5, the linux-swap at 1012 MB

---

### Post by r.stiltskin on 2013-03-18
In that case, and assuming that Ubuntu will be the only OS on your hard disk, maybe your best (and easiest) approach will be to just try using the installer again and let it set up the entire disk however it wants.  But this time make sure that you select the right disk to be partitioned.  You should be able to tell by the size that the partitioner shows.

---

### Post by new to ubuntoo on 2013-03-18
> **r.stiltskin said:**
>  try using the installer again and let it set up the entire disk however it wants 

I've tried that a few times, but i'll make sure to select the 150 GB drive and not the 1.9 GB drive :P

---

### Post by r.stiltskin on 2013-03-18
> **new to ubuntoo said:**
> the installer may have been trying to partition the flash drive i was booting from. 
then when i open gparted i have 3 partitions. /dev/sdb1 is 148/150 GB and is ext4
then there is /dev/sdb2 for 1012 MB it's extended
and then inside /dev/sdb2 is sdb5, the linux-swap at 1012 MB

I didn't see your edited info when I wrote my last post.  The partitions that you listed there seem perfectly sensible (assuming you have only 1 gb ram), and it seems to have created a swap partition in sdb5 so it's not clear what the installer was complaining about.  You could try to install again keeping the current partitions as-is, with the root file system mounted at sdb1 and swap on sdb5.

If that doesn't work, use gparted to delete all the partitions & then recreate them in the same sizes as before: sdb1 as primary (ext4), sdb2 as extended, and sdb5 logical (swap) in sdb2.

---

### Post by new to ubuntoo on 2013-03-18
[FONT=arial]i'm stumped. after reading through that guide oldfred directed me to i thought those partitions made sense as well. anyways i'm going to try again tomorrow and can hopefully get it sorted.[/FONT][COLOR=#000000][/COLOR]

---

### Post by r.stiltskin on 2013-03-18
LOL.  Our timing is a little bit off.  Re-read my post #9 which I was editing while you posted #10.

---

### Post by new to ubuntoo on 2013-03-19
haha yeah I saw it this morning, and I was thinking along those lines. I'll let you know this afternoon when I'm done studying

---

### Post by new to ubuntoo on 2013-03-19
> **r.stiltskin said:**
> If that doesn't work, use gparted to delete all the partitions & then recreate them in the same sizes as before: sdb1 as primary (ext4), sdb2 as extended, and sdb5 logical (swap) in sdb2.

I may be jumping the gun a bit here but if I want to run virtual machines will they need a partition? I don't wan to use gparted to set it all up then not have some space for that

also a friend of mine just suggested an AC3 partition... wut.

---

