---
title: "Can't upgrade because disk is full..."
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by goemonburo on 2010-01-15
Hi, I am trying to upgrade to 9.10 but it fails because the disk is full.  I am running a Dell Mini with 16GB SSD...so there isn't a lot of free space to begin with.  Added to that, I have some hefty applications (rosegarden, audacity, skype, etc) which I kind of need.

Am I better off just sticking to 9.04?  Are there any good ways to clean up the system and get rid of stuff that might be sticking around?  I did apt-get clean and it didn't clean enough.

Thanks for any and all help!

---

### Post by raymondh on 2010-01-15
[http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

Always worth a try ... 'specially the tutorial by Dave (DRS305).

16GB can handle Ubuntu .... but, you do have existing apps already that may make it "tight" ... space-wise.  If you can trim that down to say, 8GB, then I think you can upgrade with no problems.

Raymond

---

### Post by lykwydchykyn on 2010-01-15
can you post the output of "df -h"?

Also, did the upgrade utility tell you how much free space you needed?

---

### Post by goemonburo on 2010-01-15
Well, it appears df -h explains much of the mystery:  I have only 5.7 gig on my root partition, then about 6 500 megabyte partitions that are almost empty...in total they take up probably 3 Gig.

Then 8 Gig is for my /home.  

Here's the output:

me@mydellmini9:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.7G  5.1G  298M  95% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  112K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  148K  497M   1% /dev
tmpfs                 497M   88K  497M   1% /dev/shm
lrm                   497M  2.2M  495M   1% /lib/modules/2.6.28-17-generic/volatile
/dev/sda2             8.5G  5.3G  2.9G  65% /home
/dev/mmcblk0p1         15G   15G  655M  96% /media/disk-16


I didn't do the partitioning...this was prepartitioned and I bought it with Ubuntu on it from Dell.  Can I just back up my home directory and wipe everything with a fresh install?

I am a novice with Ubuntu but have been using Linux for a long time.  I just don't want to see things like my integrated webcam or sound break...that kind of thing.  

Many thanks for suggestions...

:-)

---

### Post by Sef on 2010-01-15
> I didn't do the partitioning...this was prepartitioned and I bought it with Ubuntu on it from Dell. Can I just back up my home directory and wipe everything with a fresh install?

I am a novice with Ubuntu but have been using Linux for a long time. I just don't want to see things like my integrated webcam or sound break...that kind of thing. 

If you do not want to risk breakage, then stick with 9.04, Jaunty Jackalope.

---

### Post by lykwydchykyn on 2010-01-15
Ok, first those 500Mb file systems are not actual disk partitions, they're just virtual filesystems in RAM.  you can ignore them.

You really have only the two partitions on the disk.

Second, I agree with Sef.  If you don't want to risk breakage, don't upgrade.  At the very least, make a bootable usb drive with 9.10 on it and see if all those things work from a live environment first.


Finally, if you do feel brave enough for an upgrade, I'd say a reinstall is your best bet.  But don't wipe the disk, you can just install to sda1 and leave your home partition intact.  

One more thing, you might want to contact Dell customer service to see what they advise about this maneuver.  They may have known issues with 9.10 or have advice on how to avoid problems.

---

### Post by goemonburo on 2010-01-16
Okay, for now I will just hold off.  I am pretty used to breakage but on the other hand, things work pretty well right now.  My biggest hope was that snd-rtctimer might be fixed for 9.10, so that Rosegarden and other audio/music-recording apps would work better.  But I can still do most of that on my other system.  

Thanks for the suggestions and help!

---

