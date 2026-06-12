---
title: "hddtemp partially broken in Feisty?"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by ykanello on 2007-06-08
Hello,
I have been reading a lot of forums, in ubuntu and debian sites about the problems with hddtemp on the new kernels.
For some reason most of the posts (the interesting ones at least) in ubuntu forums are locked.
So what is my problem?
I have four scsi disks, and four sata. The temperature doesn't work for all drives while it used to work before the upgrade to feisty.
The details:
> uname -a
Linux hera2 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux[/

The funny thing:
>  hddtemp /dev/sd[a-h]
/dev/sda: WDC WD1600JS-22MHB0                     &#65533;: 43°C
/dev/sdb: WDC WD1600JS-22MHB0                     &#65533;: 39°C
/dev/sdc: ST3320620AS                             &#65533;: drive is sleeping
/dev/sdd: ST3320620AS                             &#65533;: drive is sleeping
/dev/sde: SEAGATE ST173404LW: 69°C
/dev/sdf: MAXTOR ATLAS10K4_73SCA: 50°C
/dev/sdg: MAXTOR ATLAS10K4_73SCA: 59°C
/dev/sdh: MAXTOR ATLAS10K4_73SCA: 49°C



> dpkg -l |grep hddte
ii  hddtemp                                0.3-beta15-33                          Utility to monitor the temperature of your hard drive


If I do the smartctl tests on the sata drives says that there is no smart support for those drives, but for the scsi works fine :)
Also I am *really* sure that the disks are not sleeping :)

Has anyone seen this thing before?
only started when I upgraded to feisty.

---

### Post by mircione on 2007-07-28
Hi there.

I installed hddtemp in my computer, same linux version like you, and I don't now how can I start the program.:lolflag: I don't find any icon and I don't know the command line.
Best regards.

Mike

---

### Post by ykanello on 2007-07-30
First of all I want to apologize that since I found an answer to my problem I didn't post it.
My answer was laying in the man pages of hddtemp where the -w option wakes the drives up :)
so everything works again.

As for the question.
The command (the binary exists in /usr/sbin/hddtemp) is pretty simple. As root:
/usr/sbin/hddtemp -w /dev/sd? for sata disks & scsi disks
/usr/sbin/hddtemp - w /dev/hd? for ide disks.

There are some applets that show the disk temperatures on the X, but I cannot be sure which.
I used it as a deamon, and collect the temperatures with cacti and plot them. 

I hoped i helped.

---

