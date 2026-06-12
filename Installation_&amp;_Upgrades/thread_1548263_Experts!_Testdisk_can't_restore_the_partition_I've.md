---
title: "Experts! Testdisk can't restore the partition I've just deleted"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by opetrenko on 2010-08-08
I tried to install Ubuntu next to XP.
After restart - no XP and no  Ubuntu. Something wrong with loader I guess, I see command line prompt  (of the loader I guess). 

So I restarted from liveCD. 
But no  "Repair Install" option like in XP CD. 
So, I deleted partition to  install again on top of old, then learned a loader possibly could be  fixed.

So, the problem is: **testdisk cannot restore partition I  deleted**. I didn't write on disk anything. May be swap space after  couple reloads from liveCD corrupted it?

It complains "The  harddisk (...) seems to small!", it sees some other partitions and  doesn't see what Gparted and Disk Utility. 

Please, let me know  the best approach to get back XP running (having Ubuntu would be good  too). 

Here below are the screen captures for details.

[IMG]https://dl.dropbox.com/u/4703812/testdisk_screenshots/DiskUtility.png[/IMG]
**[COLOR=black]Deleted partition shown in Disk Utility[/COLOR]**


[IMG]https://dl.dropbox.com/u/4703812/testdisk_screenshots/GParted.png[/IMG]
**...in Gparted**


[SIZE=5]Testdisk[/SIZE]

[IMG]https://dl.dropbox.com/u/4703812/testdisk_screenshots/testdisk_HidSect.png[/IMG]
**warning about hidden sectors. Is it OK?**


[IMG]https://dl.dropbox.com/u/4703812/testdisk_screenshots/testdisk_SeemsSmall.png[/IMG]
[B]Quich Search results. Can't recover what's found. Why 4 partitions are found?
Notice, "The harddisk seems too small !" Could this be a problem?
HDD is not Maxtor anymore


[/B][IMG]https://dl.dropbox.com/u/4703812/testdisk_screenshots/testdisk_green.png[/IMG]
[B]The gap is there
but no deleted partition shown[/B]



[IMG]https://dl.dropbox.com/u/4703812/testdisk_screenshots/testdisk_partitions.png[/IMG]
essentially same thing... going for deeper search




Deep Search hasn't recover anything new. And shows same results as Quick Search (2nd testdisc image ) Hit "continue"...




[IMG]https://dl.dropbox.com/u/4703812/testdisk_screenshots/testdisk_deepscan2.png[/IMG]
[B]Now the partitions shown as deleted because of overlapping. The  partition to be recovered is still not in the list. 
I'm confused even more. [/B]


[SIZE=5]Anyway, [/SIZE]
my final goal is to get WinXP back and if possible, install Ubuntu.
It's nice that installer still sees the XP. Too bad the loader doesn't. 
So your ideas how to get it done are highly appreciated.

[IMG]https://dl.dropbox.com/u/4703812/testdisk_screenshots/UbuntuInstall.png[/IMG]

Unlike during installation of XP, ubuntu doesn't offer to utilize the deleted partition. Is it going to stay empty/unallocated? Forget the empty space, will I get XP running if I continue and install?
[SIZE=5]Thanks[/SIZE]

---

### Post by kelvin spratt on 2010-08-08
So I restarted from liveCD. 
But no  "Repair Install" option like in XP CD. 
You have answered your own question about Xp insert a XP install disk. not a recovery. or upgrade disk, and use the reinstall Mbr option then reinstall ubuntu correctly by specifying the partition you want to use its the last option on the prepare disk space page .

---

### Post by arasbm on 2010-08-08
If I understand correctly this is a fresh install and you dont have any data on the deleted partition. If you just installed ubuntu, why are you trying to restore the deleted partition? It would be easier to just reinstall, and this time pay attention to the partitioning and the grub (the boot loader) installation. 
Your original issue sounds like a grub problem which could be fixed very easily. What do you mean by "no xp and no ubuntu", what error message did you get?
And as far as the free space goes, unlike xp, you can do whatever you want with that space. You can configure your partitions during the installation or afterward. The power is in your hands, so be careful ;).

---

### Post by bereta on 2010-08-08
Hello All

I am having a similar problem except I did not delete the partitions with gparted or testdisk like above but I have destroyed the MBR. 

I was able to rebuild the MBR with an MBRwork that comes on UBCD (ultimate boot CD) The problem is that this utility will scan the HDD and add only NTFS or FAT partitions on the MBR.

Is there a way or an app in linux that will scan the HDD and look for ext and swap partitions and than write the MBR accordingly? There's got to be something.

Thanks

---

### Post by dino99 on 2010-08-08
prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by smith28 on 2010-08-08
I loaned a WD 1TB My Book to a friend and it came back w/o being able to access the files – over 350GB of music and 200GB of photos! The error stated that “the disk was not formatted do you want to format now?” I chose “No” and used TestDisk (on Win XP) to try to find the partition. It found the right one in a backup sector (the primary sector was bad) and rewrote it. Works great now, all files are accessible. Thanks! You might want to tell people where to download TestDisk.

________________________________________________________________
Want to get-on Google's first page and loads of traffic to your website? Hire a SEO Specialist from Ocean*Groups* [seo pecialist ](http://***********.org/)

---

### Post by opetrenko on 2010-08-08
[kelvin spratt, ]("http://ubuntuforums.org/member.php?u=264885")
Thank you. I understand repair install will fix my XP? 
Not sure what is "MBR option". Could you elaborate, so I'll know what to do when I'll get there. (It was a while since last time I installed XP)
If there is no way to recover partition I'll do just that.

---

### Post by opetrenko on 2010-08-08
[arasbm]("http://wwww.ubuntuforums.org/member.php?u=381938")

Yes, there is no data on the partition, only fresh installation of 10.04 Ubuntu. 

The error at loading I get:
> error: no such device: 54d02ccd-5606-4d7-a62e-62c0707ce2150
grub rescue>

I deleted the partition to reinstall over that space, as the installer was showing me that space it taken by ubuntu 10.04 LTS installation. Since I don't need two, I deleted it to install in that space. 

> Your original issue sounds like a grub problem which could be fixed very easily. 
That's why I attempt to restore the partition. May be loader could be easily fixed, and have both OS working. 
> It would be easier to just reinstall
I'll do that then. Kelvin Spratt suggest to repair install (?) XP first and then reinstall Ubuntu. Do you mean the same?

>  and this time pay attention to the partitioning and the grub (the boot loader) installation 
I don't see much I can do. On the last screenshot of installer you can see only one slide, that selects amount of disk I allocate to Ubuntu. Can't even tell it to use that deleted partition. 
I understand it's all done automatically. 
If there ways I can control partitioning and grub installation, please, let me know what to watch for and how to control it. 
Thank you!

---

### Post by opetrenko on 2010-09-07
[dino99]("http://ubuntuforums.org/member.php?u=129712"), 
Thank you!
followed your link . Made two partitions on the second HDD, but not inside an extended partition, but took a bit off the first ntfs partition. 
one partition is swap and another is for ubuntu. 
installed using "alternate". Grub 2 still doesn't see anything on the second HDD. Though sees floppy. 
I'll try to put ubuntu same way on the first HDD. But worry, grub won't see my second installation of winXP on second HDD. Anyway, FIXMBR in XP repair mode can get me back. 

Thanks to everyone who participated and helped me in this quite a tedious problem!

---

### Post by opetrenko on 2010-12-23
Thanks for help everybody!
I finally set alternate up on first HDD manually partitioning :D

off-topic:It runs much slower than XP on my P4 750MB RAM  :-s

---

