---
title: "64bit installation hangs  on quadcore machine"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by pcmxa on 2008-02-10
I see there are a number of other posts with a similar issue but I haven't been able to find any solutions yet so I thought I would throw this in and see what happens.

I am trying to install the 64bit version of Ubuntu.  This is my first time installing a linux operating system (I am hoping to migrate away from windows).  On the live cd the installation hangs after I select the first option.  The kernal loads, It says please wait, then the monitors lose signal and after a while the CD spins down.  When I try the alternate CD once it got to a point where it was having an error with a drive.  The other time it said it could not mount the CD/DVD drive.

I have tried installing from both my internal sata dvd drive and from my external usb dvd drive.  In all cases it either hangs or returns an unidentified error when looking at one of the drives.

My system:

Inetl core duo 2 q6600 quad. 2.4 gHz
8 gigs of ram
abit ip35 pro mb
xfx force 8600gt nvidia card with 256mb
3 x 500 gig Western Digital sata drives;

currently has vista home premium x64 on the c drive (which is why I am interested in migrating.

Thanks for any pointers

---

### Post by pcmxa on 2008-02-10
More Info:

I successfully installed from the live cd (didn't do anything different it just worked one time),  After the install, every attempt to boot to the OS hung at the same place the CD did, even when booting to recover from one of the cds. I removed the partitions the installation created to see if I could replicate the install but no luck.

The Alt CD fails to mount the cd/dvd drive when installed from the internal sata drive.  It hangs when run from the external USB drive after it tests all the cores and finds they pass synchronization.  It just says 4 CPUs loaded and then does nothing.

The Live CD hangs either immediately after loading the kernel, or with no splash set, it runs through a bunch of text too fast for me to see then goes to a blank screen which then loses signal and after a minute the dvd drive powers down.

Any suggestions?

Thanks

Patrick

---

### Post by BassKozz on 2008-02-16
Patrick,

I think the Abit IP35 Pro is the culprit, I am having the [exact same problems]("http://ubuntuforums.org/showthread.php?t=698912"), and I've found a [thread that discusses the issue]("http://ubuntuforums.org/showthread.php?t=637721"), but I have yet to have gotten it to work for my self yet.

---

