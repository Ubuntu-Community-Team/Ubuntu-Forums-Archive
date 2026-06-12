---
title: "dual boot install with XP media"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by slowmotion on 2006-11-15
Hi all

Just got a new computer, with XP media on it.
Want to install Edgy in addition to XP,
so I end up with a dual boot system.
I have one 200GB harddisc.

Problem is the installer stops at the partition.
I get a message it cant partition the disc.

Had a working dualboot on my old computer,
but I don't know what to do here.?

Help please? 


cheers, Jan

---

### Post by earobinson on 2006-11-15
A lot of people seem to be having problems partitioning with edgy, My guess try to partition manually (eg launch gparted before the installer) If that don't word download the gparted livecd ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) use that to partition then install edgy.

---

### Post by bulldog on 2006-11-15
You can download the Gparted live cd and see if you can do the job with this one.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

It's only aprox. 25MB download,burn the ISO and boot from the cd.
The rest is pretty self explaining.

---

### Post by slowmotion on 2006-11-15
Thanks for the link. I've tried with Gparted from the ubuntu-live cd, but that didn't work.


cheers, Jan

---

### Post by earobinson on 2006-11-15
> **earobinson said:**
> A lot of people seem to be having problems partitioning with edgy, My guess try to partition manually (eg launch gparted before the installer) If that don't word download the gparted livecd ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) use that to partition then install edgy.
The gparted live cd is more uptodate than ubuntu as I understand it. download and try that livecd.

---

### Post by slowmotion on 2006-11-15
ok, downloaded the GParted LiveCD, tried it, program starts allright, but when it tries to partition, nothing happens.

Could the harddisc be locked somehow?



cheers

---

### Post by earobinson on 2006-11-15
nothing happens? do you get an error? Run it from the terminal and cut and paste the output.

---

### Post by slowmotion on 2006-11-15
Ok, got it to work.
Had to run chkdsk /f in windows twice and reboot twice,
and then everything worked. Don't ask me why, I don't know. :confused: 


Thanks for the help, everyone!


cheers, Jan

---

### Post by dheerajsp on 2006-11-18
ok. i had posted bout this before. i have this ext3 formatted drive that ivve currently installed Ubuntu into. not i want to just format this drive and install Ubuntu x86-64bit version into it. how can i install it without starting gparted during installer? 

my ext3 and swap drive are hda6 and hda7. i cant choose 'erase entire hard disk' option. if i choose 'largest amount of free space', it creates new partitions! i dont want this also.

and as u've guessed, installer hangs up during the gparted loading.!

---

