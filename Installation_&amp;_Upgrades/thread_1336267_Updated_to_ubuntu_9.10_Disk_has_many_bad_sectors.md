---
title: "Updated to ubuntu 9.10 Disk has many bad sectors"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by waleedakleh on 2009-11-24
yesterday i updated ubuntu 9.04 to 9.10, after it finished i rebooted my pc,
after every login a message started to pop up by "gdu-notification-daemon" saying > a hard disks may be failing one or more hard disk report health problem. click the icon to get more information
so i clicked ok then clicked on the new hard disk icon on my panel with a "!" inside a yellow triangle, doing so "palimpsest disk utility" application comes up saying > Disk has many bad sectors!!!
i bought this hard disk 9 months ago, and never had any problems with it, till this moment.

so i wanted to ask could this "palimpsest disk utility" be wrong???
how can i be sure??
did anybody else had this problem??

note: i dont know if this matters but i have ubuntu on ext4, and i have windows xp and backtrack 4 on the same HD each on a partition
i read an other post and didnt get a full answer

IS IT A BUG??? 

thank in advanced :)

---

### Post by dddw on 2009-11-24
I have the exact same issue!

---

### Post by howefield on 2009-11-24
Take a second opinion using an utility from your hard disk vendors website.

---

### Post by phillw on 2009-11-24
You can run fsck on the partition, firstly you need to unmount it. So, take a note of ```
fdisk -l
``` to find the name of the partition 

Then, it's follow this [http://ubuntuforums.org/showpost.php?p=833916&postcount=8](http://ubuntuforums.org/showpost.php?p=833916&postcount=8)

Should get you sorted.

Regards,

Phill.

---

### Post by ptn107 on 2009-11-24
It's a bug.  I remember this from the karmic beta, but I thought it was fixed[1].  Guess not??

[1] [https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

---

### Post by r_barndt on 2009-11-24
I had the same issue when I upgraded to Karmic.  It might be a bug, or it might be real, so check the details window to determine which errors are flagged and if the values seem in range.  An extremely large value or a negative value would indicate the utility is not correctly interpreting the S.M.A.R.T. values from your brand of drive.
 
Based on information gathered from other threads on this topic, my opinion was that the Palimsest utility is overly sensitive to the metric of the "Reallocated sector count" and was incorrectly flagging my drive as too many bad sectors.  Mine was at 68 on a 10-month old drive, but one that has been on 24/7.  The threshhold was 140 so I was thinking that the message should not come up until that time.  So I decided to take a wait-and-watch approach.  
 
One week later the reallocated sector count jumped up to 280.  Now I am convinced that this utility just saved my data.  I installed a replacement drive but I am wondering if Western Digital is going to honor a warranty claim because of only the one metric that their proprietary utility does not flag as a failure.  I suppose I can use it as a scratch drive or use rsync to mirror my live filesystem until it does fail, but I don't trust the drive to hold my valuable data.

---

### Post by waleedakleh on 2009-11-24
is seagate seatools for windows a trusted Hard Disk tester for bad sectors???

---

### Post by presence1960 on 2009-11-24
> **waleedakleh said:**
> is seagate seatools for windows a trusted Hard Disk tester for bad sectors???

As long as you have a Seagate hard disk that will be great. Download the bootable CD version iso, burn it to a CD and boot from it. Note: if you have AHCI enabled for your disks change them back to IDE in BIOS for the test, the Seatools will not detect AHCI enabled hard disks.

I had the same issue with a new 500 GB Seagate disk in Karmic. I ran Seatools bootable CD and Everest from windows and the disk was fine in both instances.

I wound up disabling that function (Palimpsest) which reports the disk failing message by going System > Preferences > Startup Applications and unticking Disk Notifications. This will prevent it from running at startup. If you ever need to run Palimpsest go System > Administration > Disk Utility, then you will get that message again.

P.S. run the Long Test from Seatools, if errors are found they will be corrected if possible.

---

### Post by waleedakleh on 2009-11-24
i have a seagate
i executed the "long generic" test using the windows version and it passed it.
i even tried the windows "error-checking" tool and it passed it.
it must be a bug
unless the seatools bootable version is more reliable!!!

---

### Post by phillw on 2009-11-24
Hi, I've just looked & there is a bug report for it over here ---> [https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

Get a launchpad login, pop on that it also affects you & you can track the bug progress.

Phill.

---

### Post by unclesamslair on 2010-01-07
I had the same problem the moment I installed Ubuntu 9.10. I was using a partition of Xubuntu 9.10 and it never detected any malfunction. I don't know what any of this means so I'll just post it in hopes that someone will be able to tell form just the error values that this is just a bug in Ubuntu and that my hard drive is fine since I'm broke as hell and can't afford a new one.
```

5 Reallocated Sector Count 
Warning Normalized: 97 Worst: 97 Threshold: 24 Value: 4915290

197 Current Pending Sector Count
Warning Normalized: 91 Worst: 91 Threshold: 0 Value: 10
```
Also, I have a Fujitsu Hard Drive for the Dell INspiron 1501 that's been running for 1.2 years if that's of any help.

---

### Post by emarkay on 2010-01-24
Same issue here:
[http://georgia.ubuntuforums.org/showthread.php?t=1336267&page=2](http://georgia.ubuntuforums.org/showthread.php?t=1336267&page=2)

---

