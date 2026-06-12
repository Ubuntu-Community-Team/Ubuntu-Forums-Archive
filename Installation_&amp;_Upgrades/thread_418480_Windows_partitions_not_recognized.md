---
title: "Windows partitions not recognized"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Manus on 2007-04-22
I just downloaded Feisty and booted from CD. Looks great.

However, when I want to install, it says I have 160 GB of unpartitioned space. That's not true! I use 2 Windows partitions that take up about 100 GB and I'd like to keep them (for the time being).

Any thoughts on how this issue can be resolved?

Thanks!

---

### Post by carpex on 2007-04-22
What is your computer? Is it a Dell by any chance? See those threads:

[http://ubuntuforums.org/showthread.php?t=415274](http://ubuntuforums.org/showthread.php?t=415274)
[http://ubuntuforums.org/showthread.php?t=416800](http://ubuntuforums.org/showthread.php?t=416800)

It seems to be caused by computers having overlapping partition tables. The solution, which I haven't tried seems to use partition table doctor:

[https://bugs.launchpad.net/ubuntu/+bug/108562](https://bugs.launchpad.net/ubuntu/+bug/108562)

HTH, 

GL

---

### Post by pepsi_max2k on 2007-04-22
Another guide for the same thing:

[http://ubuntuforums.org/showthread.php?t=413745&page=2](http://ubuntuforums.org/showthread.php?t=413745&page=2)

---

### Post by Manus on 2007-04-22
Actually, it's not a Dell PC. It's a custom made PC with an Asus motherboard and a Maxtor HD.

However, I tried using Partition Table Doctor, and it worked! I suspect a recent BIOS update to have screwed up my partition table. But now it works fine.

In fact I'm posting this from the freshly installed Ubuntu :) . Thank you very much for the fast and accurate response!

---

