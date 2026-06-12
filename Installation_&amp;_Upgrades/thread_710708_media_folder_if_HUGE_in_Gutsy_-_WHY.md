---
title: "/media folder if HUGE in Gutsy - WHY?"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by jal4568 on 2008-02-28
I hope this is the right place for this issue.....My ‘/media’ folder is HUGE in Gutsy. In fact, according to the “Disk Usage Analyzer”, it’s bigger than my entire HD drive! I attached a screenshot of its results. 'Media' is showing up as 50+ GB but my internal HD is only 40GB! :shock: This is causing my install to register my “disk is full” which makes no sense given the applications, home directory, etc are almost exactly the same as when I had Feisty*. 

The /media folder is so huge because for some reason my computer is including the disk space inside my external HD and the Windows partitions. It’s not a one-to-one correlation but why would the folder linking to my external HD take up all of the space on my internal HD? 

I may not understand this correctly but I thought ‘/media’ was just to provide a means of linking my computer filesystem to the external HD filesystem. If that’s the case why would the ‘/media’ folder be so huge? Am I missing something?  :confused:

During my recent update to Gutsy Gibbon, I had the usual glitches involving accessing my external HD and USB stick. They have been resolved. But this just started in the last couple of days and I haven't been able to find the issue anywhere else in the forums. What is it with Gutsy and external drives? 

I performed an fdisk check and didn't notice any problems with how the drives are being mounted. Here are the results:
> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        3828    30716280    7  HPFS/NTFS
/dev/sda3            3829        4720     7164990   83  Linux
/dev/sda4            4721        4848     1028160   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8be2f02b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375        7012     5124735   82  Linux swap / Solaris
/dev/sdb3            7013       38913   256244782+  83  Linux


Does anyone have any ideas? 

*Biggest changes are from Feisty AWN to Gutsy version and from Beryl to Compiz. Near as I can tell, the new file size isn’t related to these updates.

---

### Post by ridetheteapot on 2008-02-28
that space is not being taken up your local hard drive.
its just that when you mount something (ssh share, dvd, samba, external hardrive, or anything) to the local file system it will appear that its part of the fs by most programs. try using df (command line) and see if it shows you the mounts seperatly like you'd rather it have.
so don't worry its just apperance, not actually copying file to your local drive or anythiing.

---

### Post by Pumalite on 2008-02-28
You didn't do an 'update'; you 'upgraded to Gutsy and according to your own statements, you had issues with your external drive and USB stick. Could you tell us in more detail what happened?
(I have my other 3 drives mounted in /media, so it's size is 2 Terabytes)

---

### Post by jal4568 on 2008-02-28
**ridetheteapot:** This is the result for the df command:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3              7052496   6658864     35384 100% /
varrun                  322056        88    321968   1% /var/run
varlock                 322056         0    322056   0% /var/lock
udev                    322056       112    321944   1% /dev
devshm                  322056         0    322056   0% /dev/shm
lrm                     322056     33788    288268  11% /lib/modules/2.6.20-16-generic/volatile
/dev/sda2             30716276  15019872  15696404  49% /media/host0
/dev/sdb1             51199120  11623028  39576092  23% /media/sdb1
/dev/sdb3            252224280  12492136 226919908   6% /media/sdb3
/dev/sda1                32018      6934     25084  22% /media/sda1
/dev/sda2             30716276  15019872  15696404  49% /media/sda2
/dev/sda3              7052496   6658864     35384 100% /media/sda3
/dev/sdc1               507104    356968    150136  71% /media/sdc1

The only weird thing I can see is that sda3 is listed 2x. Is that normal? 

**Pumalite:** Oops, I meant upgraded. :oops: I did have some problems and there were mainly related to mounting various drives. 

1) "Undefined Mode Number"?: I got this error message during the boot process. I used _[COLOR="Blue"][these instructions]("http://www.linuxquestions.org/questions/linux-newbie-8/undefined-mode-number-error-320298/")[/COLOR]_ to correct the issue. 

2) Did Not Mount My External HD: It didn't mount automatically the first boot-up but when I went into "Storage Device Manager" and clicked "Mount", it corrected the problem. The drive auto-mounts now also no problems. 

3) Did Not Recognize My Flash Drive: This took the longest to fix. I tried probably a half-dozen things suggested in the forums. But what ended up working was editing the 'fstab' file similar to what's suggested in _[COLOR="Blue"][this post]("http://ubuntuforums.org/showpost.php?p=4162523&postcount=62")[/COLOR]_. 

The '/media' folder issue just appeared in the last 2+ days (about the time I changed 'fstab'). Before that I know my disk wasn't registering as full b/c I was able to update and download files to my home directory. Could changing 'fstab' for my flash drive have messed up '/media/ somehow? I only changed the line pertaining to the flash drive.

---

