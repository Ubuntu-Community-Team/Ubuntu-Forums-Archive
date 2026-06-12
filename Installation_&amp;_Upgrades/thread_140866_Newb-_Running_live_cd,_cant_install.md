---
title: "Newb- Running live cd, cant install"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by PsychoGIno on 2006-03-07
IM having trouble partitioning.  I have a 400gb hard drive with 250 used with XP.  I wanted to make a partition for ubuntu that was 60gb but I cant resize the original.  I pretty much have no idea what to do.

---

### Post by Sutekh on 2006-03-07
The LiveCD can't be used for installing (I think thats the plan for the future but that's just a whisper I heard)

You *can* use the LiveCD to resize the WinXP partition if you like, or you can get the Install CD, it has a partitioning set in the install that can resize the WinXP partition.

This is a great guide (with screenshots) for using the Install CD (and its included partitioner) for installing Ubuntu alongside Windows (on an NTFS disc)

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

There is also GPartED (GNOME Partition Editor), which can be installed during a LiveCD session.  You can use GParted to resize the WinXP partition.  It functions very similar to Norton Partition Magic (if you have used that before)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

There is probably some good stuff lying around the forums for using Gparted and a LiveCD

---

### Post by aysiu on 2006-03-07
[QUOTE=Sutekh]
There is also GPartED (GNOME Partition Editor), which can be installed during a LiveCD session.  You can use GParted to resize the WinXP partition.  It functions very similar to Norton Partition Magic (if you have used that before)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)[/QUOTE] While the live CD's running, go to Applications > Accessories > Terminal and type these commands: ```
sudo apt-get update
sudo apt-get install ntfsprogs gparted
sudo gparted
```

The most reliable partitioning program I know is [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142), though.

---

