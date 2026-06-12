---
title: "Proper uninstallation/ Partitioning"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Rbrewer19 on 2010-01-18
I have some spare room on my drive and was thinking of putting Ubuntu on it. I've done this before and it didn't really like my computer and I had to remove it...in doing so I had to go back and fix my MBR etc to get Windows to work correctly again. My question is what is the proper way to uninstall ubuntu from a second partition without messing up my MBR?

---

### Post by audiomick on 2010-01-18
I am not aware of any way around having to go back and fix the mbr when Ubuntu is gone.

What you can do is boot into the liveCD, that is the one you would install from, using the "try without changing" option. This will allow you to see if the computer will like it without having to fix anything afterwards if it doesn't.

---

### Post by Rbrewer19 on 2010-01-18
I didn't think about that. I've just been running Ubuntu virtualized and it gets a little choppy at times. I'll give it a shot!

---

### Post by phillw on 2010-01-18
If you ever need to rebuild either your Win MBR, or Grub - then head over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

A 10 GB partition is all you need for Ubuntu - Depending on which version of Win you are using, there are two approaches to shrinking Win and making a partition for Ubuntu.
For Vista or Win7 use --> [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

For 98 / XP, use Gparted, which is on the LiveCD. - Use it in LiveCD mode (i.e. 'try Ubuntu without touching my computer)

Either way, shrink Win by 10GB, have the 10GB area as 'unused'.

Tell the LiveCD to install & tell it to use the unused area.

To remove.. Go into LiveCD - delete the Ubuntu Partition.
Recover your MBR, as per link at top of post.
If on 98 / XP, use Gparted to 'Grow' your Win partition
If on Vista / Win7 - use the system in the howtogeek thread to 'grow' your Win area.

When installing Ubutnu for swap you want about 1GB of swap - If you have 2GB of ram, then make it 2gb of swap.

Regards,

Phill.

---

