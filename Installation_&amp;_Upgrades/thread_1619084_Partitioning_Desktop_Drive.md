---
title: "Partitioning Desktop Drive"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by grifway on 2010-11-11
Newbie to Ubuntu/Linux.
Have a fairly new desktop(HP) with one TB drive.  It has Windows 7 Home Edition.  The current hard drive has 3 primary partitions, 1 for boot/system, 1 for operating system(900GB) and 1 for the recovery disc.
So I thought I could install ubuntu on this disk in a partition.  
 
Step 1. I used the shrink partition tool in windows and shrunk the OS 900gb partition to 700gb's.
Step2.  I now have an 200GB portion of drive as unallocated.
 
So from here I thought I could partion this 200GB as an extended partition and within the extended create virtural partitions for the /, tmp, home, data directories.
 
But so far when I insert the ubuntu CD, and go to install, it does not see any of these new ext4 partitions.
 
What am I missing.  Do I need to create a primary partion on this 200GB unallocated partition and work from there?
I don't want to install ubuntu as a program within windows.
 
Thank you.  Not sure if I have all the terminology correct.

---

### Post by dino99 on 2010-11-11
Little help:

[http://ubuntuforums.org/showpost.php?p=10098299&postcount=2](http://ubuntuforums.org/showpost.php?p=10098299&postcount=2)

---

### Post by sikander3786 on 2010-11-11
Hi and Welcome to the forums :popcorn:

Please boot an Ubuntu LiveCD and from Applications > Accessories > Terminal, post the output of

```
sudo fdisk -l
```

> it does not see any of these new ext4 partitions.


How were the partitions created? You didn't mention anywhere.

> Do I need to create a primary partion on this 200GB unallocated partition and work from there?

Ubuntu doesn't need a primary partition to boot from. You can install it to Extended/Logical drives. So that is not the real problem here.

> I don't want to install ubuntu as a program within windows.

Me too won't recommend that. Actually most of the people here wouldn't recommend that because that is just intended to test Ubuntu. It is problematic, slower, breaks at upgrades and more and more.

Try to properly dual-boot Ubuntu/Windows. You'll soon get there I assure :-)

---

### Post by grifway on 2010-11-11
Thank everyone for the replies. I will look into your suggestions.
 
I was also thinking I would just buy a small sata internal drive and install that, then put ubuntu on the second drive. Would that be more sensible than screwing up my windows install. I never got the windows 7 CD, so if I totally nuke my desktop somehow I would have to buy one.

---

### Post by Quackers on 2010-11-12
A Windows 7 repair disc can be downloaded free of charge. Google will help there. Using a second hard drive can bring problems of its own. I would go with what you have at first.

---

