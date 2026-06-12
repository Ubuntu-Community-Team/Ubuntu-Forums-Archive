---
title: "Reinstall 10.04 LTS over existing 10.04 system"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by lkraemer on 2010-09-30
I am starting to have lots of unusual problems show up on my Ubuntu 10.04
install, missing Icons for the Volume Slider, Email Icon, and a Error
mounting Static on startup (because I plugged in my Smartdisk FDUSB-TM2
Mitsumi Model #: D353FUE) and it is trying to mount as SDC instead of
as a USB Floppy Drive.....and it DOES NOT work as a USB Floppy Drive
on 10.04.

REF:
[http://ubuntuforums.org/showthread.php?t=1577481](http://ubuntuforums.org/showthread.php?t=1577481)

I have my system set up as follows:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba58e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2            2551       59717   459193927+  83  Linux
/dev/sda4           59718       60801     8707230   82  Linux swap / Solaris

```

My question is:
If I boot from the LiveCD again, and Install again from the LiveCD, will
all my installed software still be functional, or will I have to re-install, and repeat everything I have done to build my system to date
since my system is on / and is a separate partition?

Thanks.

lk

---

### Post by Goolie on 2010-09-30
Wait for verification from someone more in the know, but I'm pretty sure if you have / and your home folder on seperate partitions, then you should be fine to re-install over the / partition.  Most programs you add-on usually end up on the home folder, albeit hidden,

a quick glance of my home folder shows .emerald .frostwire .Heroes of Newerth .mozilla .mplayer .nautilus, etc., etc.

So it is my educated guess that re-installing Ubuntu on your / partition should allow you to save most settings and applications within Ubuntu 10.04 even when you re-install 10.04 itself, though I'm not entirely sure if there are any steps to setting things up further.

---

### Post by albertwt on 2010-09-30
what is LTS version ? Light Terminal Server ?

---

### Post by lkraemer on 2010-09-30
LTS = LONG TERM SUPPORT.....ie 8.04, 10.04,.....
Full support for Three Years.....


I just booted from the LiveCD and everything, including my USB Floppy Drive works fine.
I don't understand how my system got messed up.....It's been running fine since early
May when I installed 10.04.


lk

---

### Post by oldfred on 2010-09-30
Your user settings are in /home, is that the sda2 partition? If you have made some settings they will be preserved but may have the same issues, if you have set something strange?

Your programs will not be reinstalled but the program settings and saved data should be in /home.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

If you have made any special system settings the are in /etc and will be overwritten when you reinstall to /. If you know what you changed you can back up those settings or back up all of /etc just in case.

---

### Post by lkraemer on 2010-09-30
oldfred,
OK, Thanks for the info.  I can assure you I haven't changed any settings
since I did the initial install, but some weird things have been happening.

I've backed up my bookmarks, looked at what I have installed, and I am
just about ready to wipe / and do a fresh install.  Then I can install
the remaining software as needed.

lk

---

### Post by albertwt on 2010-10-21
> **lkraemer said:**
> LTS = LONG TERM SUPPORT.....ie 8.04, 10.04,.....
Full support for Three Years.....


I just booted from the LiveCD and everything, including my USB Floppy Drive works fine.
I don't understand how my system got messed up.....It's been running fine since early
May when I installed 10.04.


lk


Thanks man for the explanation.

---

