---
title: "What File System should I use for my HD?"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by mozilla2004 on 2010-01-10
I have a new computer with a 1 TB HDD.  That's more disk space than I really need.  So I want to partition the drive in a way that let's me install 3 different operating systems (ubuntu, winxp, os x) plus 1 big drive for storing movie files, mp3s and work files such that they can be accessed from any of the different OS I boot up from.

What file system should I use for the four different partitions to achieve this?  I'm going to be using Ubuntu 9.10 90% of the time.

If what I'm about to do is a bad thing, let me know of a better solution.

Thank you!

---

### Post by zvacet on 2010-01-11
Default Ubuntu filesystem is now ext4,Windows NTFS and OS X id hfs+ I believe.I think every of named OS can read& write on NTFS ( I don´t know about OS X so check that).

---

### Post by pedro_orange on 2010-01-11
There's nothing stopping you having different file system types on different partitions. 
So if you wanted ext3/4 on the Ubuntu partition and NTFS on the Windows one - then that's fine. 

If you're planning on having a data partition then you can either choose something common between the operating systems, or install the necessary driver so that the given Operating System can see that file system. (i.e - there is a driver that will allow Windows to see ext3) 

You can use something like GParted to sort out all your partitions before you install anything if you like. Remember, Ubuntu will want a swap partition. (Dunno about OSX)

---

### Post by Cabs21 on 2010-01-11
Just keep in mind that HDD can only have 4 primary partitions so if you want a recovery partition that is boot able for winXP you will only be able to make data storage partitions after making 4 primary boot able partitions.  If you don't care about that then go for it.  If it was me I and I was using Ubuntu 90% of the time I would use OS X for any mac exclusive related software (iTunes) and Wine for anything you want to run on a windows platform.  This way you dont need to over crowd your hard drive with 4 to 5 partitions and can avoid dealing with the troubles of Windows.  Again thats what I would do if I was in your shoes.  I personally dont like Macs or their OS go with what you like best.

Windows = NTFS

Ubuntu = ext3 or 4

Mac = hfs+

---

### Post by J V on 2010-01-11
in short, make an extended for linux so you can seperate /home as well...

---

