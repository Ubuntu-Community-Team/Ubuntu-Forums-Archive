---
title: "Ubuntu created a flase partition?"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by Opeth115 on 2007-03-06
Ok well i tried installing herd 5 on my hard drive and iw as gunna give it half of my hard driv.  but during the installation the installer failed so i boot back up into windows and i look at my c drive settings and it still set up the partition with half of my hard drive....  how can i get the rest of my hard drive back to be used with windows?

---

### Post by tommcd on 2007-03-06
You should be able to go into windows disk management utility and delele the partition that was created. 
Did you know that herd 5 is the beta version of ubuntu fiesty, which is due out in april? If you want something more stable and predictable, then install edgy. You can then upgrade to fiesty when it goes  to stable. You could just put edgy on the partition that was created.
EDIT: See this also:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_TWO_DELETE_THE_LINUX_PARTITION_](http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_TWO_DELETE_THE_LINUX_PARTITION_)

---

### Post by Opeth115 on 2007-03-06
how do i open the windows disk management utility and yea i know that herd 5 is the beta but my mobo (Intel DP965LT) is not supported in edgy.  But now i know that it will work in feisty so im gunna just have to wait untill they release it i guess...

---

### Post by Opeth115 on 2007-03-06
ok well igot disk management open but how do i resize the drive so that it uses my whole hard drive??

---

### Post by Opeth115 on 2007-03-06
it says i have a 196 gb ntfs and a 176 gb unallocated how can i extend my winows partition into the allocated space?

---

### Post by tommcd on 2007-03-06
You have 3 options.
1) You can use windows disk management utility to format a new partition in the unallocated space. You can then use it as a data partition (similar to a seperate /home partition in linux). That way if you ever have to reinstall windows your data is safe.
2) You can use gparted live CD to resize the partition to fill up the whole drive.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Or you could use a program like partition magic to do the same thing.
3) Just leave the partition the way it is and install fiesty on it when it goes stable.
If it were me, I would go for #1 if you were going to stay with windows, or #3 if you want to install ubuntu fiesty. With a disk that big you could make partitions for a few distros to try out.

---

