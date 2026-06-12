---
title: "How do I remove xp from dual boot."
date: 2006-05-06
forum: Installation &amp; Upgrades
---

### Post by Paul Barnett on 2006-05-06
I am using both ubuntu and xp. I want to remove xp and open up the hard drive to use with ubuntu. How do I do that?

---

### Post by rado_london on 2006-05-06
Well I dont know how to merge the xp partition to already in use ext3. But to delete it and create new ext3 use gparted:
```
sudo apt-get install gparted
```
There delete the xp partition and create new ext3 one. The next reboot you will end up with new ext3 partition.
NOTE: I never tried it so I dont carrry any responsibility for data loss etc.

GOOD LUCK

---

### Post by Sef on 2006-05-06
> I am using both ubuntu and xp. I want to remove xp and open up the hard drive to use with ubuntu. How do I do that?

First **back up** your data before you do anything.

Only way would be how would be to reinstall the Ubuntu.   Simply delete the partions and repartition to your desired size.

If you wanted to merge the partitions, then I don't know what open source partitioner can merge partitions without reinstalling the os.  If you do use a proprietary partitioner, do NOT use Partition Magic.  It and Linux tend not to get along with each other.


> Well I dont know how to merge the xp partition to already in use ext3. But to delete it and create new ext3 use gparted:
Code:

sudo apt-get install gparted

There delete the xp partition and create new ext3 one. The next reboot you will end up with new ext3 partition.
NOTE: I never tried it so I dont carrry any responsibility for data loss etc.

You can't partition on drives that are mounted.

---

### Post by rado_london on 2006-05-07
I swear there is an option in gparted to unmount the drive and then manipulate it. Am I right?

---

### Post by Sutekh on 2006-05-07
If Ubuntu and XP are on the same hard drive, GParted will not let you work on it.  You can't unmount the drive that Ubuntu is on...

Unless you use something like the [GParted LiveCD](http://gparted.sourceforge.net/livecd.php) (its only 30MB)

As for merging, just remove the Windows partition, don't create a new one.  GParted can grow the current Ubuntu ext3 partition to fill the whole hard disc.  

You could, of course, always use a second partition if you would like to, you don't have to make just one large one.

---

