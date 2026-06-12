---
title: "Hardware problems with installing?"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by Dinjaga on 2007-11-26
Guys, I have a computer, and, its one that I made myself.  Its got an Intel Pentium 3 processor, an ATI Radeon graphics card, a Western Digital hard drive, and an old HP CD-RW drive.  Its had Linux on it(6.10) and windows XP, and both ran fine.  But now, its wiped.  And I'm trying to install Ubuntu 7.10.  I got some disks from Ubuntu, popped them in, and started installing.  I did everything, it was fine, until I got to the partitioner.  I selected largest continuous space, and clicked next.  But as soon as I type in my first name on the next screen, it freezes.  Always.  Sometimes it freezes before that.  Sometimes, it'll just go to my monitors "Your monitor is working" thingy, as if the computer wasn't even on. The disks are fine...any clue what my problem is?

Thanks!
~Dinj*

---

### Post by dabl on 2007-11-26
I'd make a GParted Live CD, boot that, and do the partitioning with it, before booting the *buntu installation CD.  Download the ISO here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

It should not be necessary to have the "boot" flag set, unless you want to install Win XP again (if you do, install XP first and Linux second).

ATI cards are not famous for their Linux drivers ... you might want to try to configure it as a VESA display first, then download Envy and let that install a driver:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

:)

---

