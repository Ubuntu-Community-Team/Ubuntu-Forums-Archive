---
title: "Prep for Dual Boot Upgrade"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by J-Logger on 2011-01-23
Hello, folks,

I have a laptop currently set up dual boot, Windows XP and Ubuntu 7.x.  Recently, I managed to hose the wireless setup on the Ubuntu side (massive user error), and have decided to bite the bullet and upgrade my Ubuntu version to the latest and greatest.  My hard drive has 3 partitions, I believe, including windows, ubuntu, and a separate boot manager area. This was all set up about 3.5 years ago, and candidly I am not real sure how I did it (I got a lot of help off the forums). 

Rather than blindly start then hit the forums for weeks to fix my errors, I thought I would ask for help before messing something up.  I am not highly experienced using ubuntu or the boot management process.  My overall plan is to download the 10.10 version, press a CD, then boot to ubuntu and do the install.  My major concern is how to update the boot process to recognize the new ubuntu system.

I have looked at several posts and see that there have been a number of issues reported.  It is not clear to me, though, how to avoid them!  If someone has a pointer to a good checklist for doing this kind of install, I would love to see it!

Thanks in advance,

Jim C.

---

### Post by gordintoronto on 2011-01-23
When you say, "boot to Ubuntu," I assume you mean, "Boot from the CD." If you install into the same partition as Ubuntu is currently using, the boot process will not be an issue.

There are two big issues though:
 - if you don't know what you are doing, you might hose the laptop completely, and wind up with only Ubuntu, and all your data gone,
 - if you avoid that, you may lose all the data and settings you have in Ubuntu.

Make sure you have two copies of backup of your data and settings, for both Windows and Ubuntu, before you do anything else.

---

### Post by J-Logger on 2011-01-24
Thanks, Gordon,

I did a bad install several years ago and hosed everything.  I am a lot more careful now, which is why I asked for help.  I have, in fact, backed up all the data... twice as you suggested.

Yes, I did mean to boot from the live CD... I have booted to the 10.10 CD and it comes up fine.  I do want to validate my previous notes about what is in what partition...  Hoping to use my 10.10 live CD to do that.  Is there a good utility in 10.10 to do that?

My concern in asking the question is that I saw many entries where the boot partition gets clobbered with an install.  Even if it lets the XP part alone but clobbers the boot partition, I am in deep yogurt as my knowledge level of how to set up a dual boot boot partition is minimal.

Thanks. 

Jim

---

### Post by gordintoronto on 2011-01-24
If you open Accessories/Terminal and enter the command:
sudo fdisk -l
it will list all your partitions, including their size and how they are formatted. Generally, ntfs partitions are Windows, and ext3 or ext4 is Linux. Perhaps you could copy/paste the output here?

---

### Post by Bucky Ball on 2011-01-24
Firstly, I'd go for the long term support release, 10.04 LTS (support til April 2013 - [http://www.ubuntugeek.com/the-ubuntu-release-cycle.html](http://www.ubuntugeek.com/the-ubuntu-release-cycle.html)). 

Secondly, are you looking to *replace* 7.04 or go for a triple boot?

Thirdly, it might be an idea when you have burned an ISO CD of your chosen Ubuntu release, to:

Boot into 'Try Ubuntu' from the disk,
Open Gparted,
Unmount the Ubuntu partitions if they are not already with right clicking on the partition,
Right click on the partitions again and delete them leaving free space. 

This might make things a little less confusing. Don't worry, you will see your Windows partition(s) right there in Gparted (NTFS or FAT file system, obvious - all Linux partitions with be EXT) so just leave 'em alone.

Now go ahead and install! When you get to partitioning use manual partitioning and create these:

/ = OS, 20Gb is heaps.
/home = big as you like.
/swap = 2Gb, *or* same size as your RAM if you intend hibernation.

... in that order, /swap at the end of the HDD. 

Done.

* The install will identify your Windows install and add it to grub2. You don't need to do anything. 10.04 ROCKS!

---

### Post by J-Logger on 2011-01-25
Thanks to both of you for your advice.  Gordon, I will paste the partition info here...

Great tip on 10.04, Bucky.  I will repress a 10.04 live CD and use that as a starting point.  

I am swamped today and tonight.  Next opportunity for me to work on this is Wednesday evening East Coast U.S. time.  I will report back to you when I make progress.

Regards,

Jim C.

---

### Post by J-Logger on 2011-01-26
Gord, Bucky, a quick update.

I ran both sudo and gparted... twice.  I got basically this info:

Partition    FileSys    Size    Used    unused    Flags
/dev/sda1    ext3       99M    34.9M    65M       Boot
unalloc      unalloc    1.98M
/dev/sda2    ntfs       54.04G  31.35G  22.69G
/dev/sda3    ext3       53.91G  3.17G   50.73G
/dev/sda4    extended   2.34G    --      --
    /dev/sda5 linuxswap 2.34G    --      --

It looks like /dev/sda5 is a subset of sda4, although they are the same size.

I ran GParted twice, once from a GPartedLive CD and the second time from the gui in ubuntu 10.04.  When I ran it under ubuntu, the /dev/sda4 and /sda5 disks were locked: they were reported as being used by "some process".  I am wondering if the ubuntu live CD is using the linux-swap file since it is there.

Given all the above, my plan is to basically do what you said, Bucky, but with a little twist.  I will boot the gparted live CD, delete/dev/sda3 and /dev/sda4 (and sda5), then boot ubuntu live, click install, and build the partitions as you describe.

My only hesitation is the locked file(s)... do you guys see any issue with my plan?

Thanks, guys... would love to hang a solved sign on this thread tomorrow.

Jim

---

### Post by Bucky Ball on 2011-01-26
Sounds good and good luck. Just avoid that NTFS partition. It will be obvious when you get to the partitioner so easy peasy.

---

### Post by gordintoronto on 2011-01-27
When you are running Ubuntu, Gparted can't mess around with a partition that Ubuntu is using. Thus, the swap file was locked. When you install from CD, it won't be locked.

---

### Post by Bucky Ball on 2011-01-27
And by the way, yea, /swap appears to be an extended partition all its own. 

Something to remember: a physical drive can only contain four partitions. Therefore, if you need more, and you might, you need to create an extended partition. This is just a container inside which you can put many logical partitions but the extended appears to the system as a single partition. Therefore, three primary partitions and one extended partition with, for instance, five logical partitions inside will be fine, still treated as four partitions. 

Point to ponder ...

So, Ubuntu will exist without an issue on a logical partition inside an extended partition. Windows will not (first primary partition, first hard drive, thanks!). With this info in hand, good luck!

Pays to scribble out exactly what you are going to set up with pen and paper before booting the machine and starting so you have a clear plan and idea of what's to be done. Post that plan back here before you start if you like . ;)

---

### Post by J-Logger on 2011-01-28
I am pleased to report success...  Ran into a couple of glitches...

First, it took me a little while to figure out the physical versus logical partition scheme...  your explanation was excellent, Bucky, but I read it after I was done...  :-)

I had already pressed a 10.10 CD, so I tried that, and it ran great.  I did the setup exactly as you outlined, Bucky, and had no issues.  I am not up and running.

I have some questions on the UI, but that is for another forum, another thread, another time.  Thanks to both of you for your help.  I would have inflicted serious wounds on this old laptop without your advice.

Best Regards,

Jim

---

### Post by Bucky Ball on 2011-01-28
Great to hear. Enjoy the new OS and the learning curve and, of course, post a new thread with any thing else.

> I am not up and running.

You're not up and running?

---

