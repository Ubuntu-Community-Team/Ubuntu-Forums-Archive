---
title: "Can't create more than 4 partitions."
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by Pink401k on 2010-11-22
Hey guys, I'm trying to install Zorin OS to my computer, but I can't create a partition on my HD to get it to work.  This is my first attempt at having multiple OSs on my computer, and my first delve into anything Linux, so I'm sorry in advance.  My problem is that my computer (running Windows 7) already has 4 partitions, so creating another for Zorin won't work.  I'm attaching a screenshot so you guys can see the partitions I have at the moment.  Any help would be greatly appreciated.  I really hope to figure this out tonight so I can start to explore the OS asap!

Have a good night/day.

Pink

---

### Post by wilee-nilee on 2010-11-22
Well 4 primaries is the limit. But you could get rid of a partition, make sure you know what your doing here as you probably have the boot on another besides the main usual C in Windows. You then put a extended partition in there and you can put as many ext type in the extended. If you want to see where all the boot files are post the bootscript in my signature, or run it for yourself. If you post it put the text in code tags, by clicking on the # the paste the text in between the code tags. sda1 is the booting partition on your system.

The one your trying to install is Linux based so it should boot from a extended, if it was me I would be concerned about the version of grub just for ease of use.

---

### Post by srs5694 on 2010-11-24
Your /dev/sda3 partition almost certainly contains the equivalent of the OS installation DVDs that HP was too cheap to include with the computer. There should be an application on your system that will create the DVDs that HP should have shipped with the computer, at your cost and at your effort. Try running that program, and while you're doing so, write to HP and Microsoft to complain about how incredibly cheap they are; they'll keep pulling this stunt so long as people don't complain.

Once you've got a recovery DVD set (or better yet, two; burned DVDs aren't as reliable as manufactured DVDs), you should be able to safely delete /dev/sda3.

---

