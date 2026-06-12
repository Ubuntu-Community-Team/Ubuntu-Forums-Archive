---
title: "Can't install any version of Ubuntu"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by Taters343 on 2012-01-26
I'm trying to set up a dual boot of Ubuntu and Windows 7 on my laptop, but Ubuntu refuses to install. I tried it a few months ago and got some error at the point when it was partitioning and reformatting the drive, but I can't remember specifically what it said. I tried 11.10, 10.10, and 9.4 (A new disk I made, and some old disks I had used on other systems).

Today I tried to use the Wubi option to install 11.10, but when I restarted my laptop it got to this screen and then stopped.

[IMG]https://lh5.googleusercontent.com/-ccg0UgWf0lc/TyIoC003CtI/AAAAAAAAAGQ/ncloqHpOfAQ/w814-h609-k/IMG_20120126_230808.jpg[/IMG]

Is there anything I can do to fix this?

---

### Post by mastablasta on 2012-01-27
have a look here on wubi solution (might work)
[http://ubuntuforums.org/showthread.php?t=1770167](http://ubuntuforums.org/showthread.php?t=1770167)
 
you probably have too many primary partitions that is why propper dual boot is not working as well.
 
easiest way to do dual boot is to create empty unformated disk space using windows disk manager which ubuntu then partitions automaticly.

---

### Post by Taters343 on 2012-01-27
This is a screenshot of disk 0 in the Windows disk manager. This was taken after running Wubi (In which I chose to give Ubuntu 20 GB), which appears to have done nothing to it.

[IMG]http://i44.tinypic.com/egp9gm.png[/IMG]

I'll read through that other thread and see if I can get it working.

---

### Post by Taters343 on 2012-01-29
Reinstalled Windows, was able to partition the disk and install Ubuntu.

---

