---
title: "Ubuntu Server + XP Pro"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by LoganHarbour on 2007-05-29
Ok, my test PC has a 700mhz PIII with 128MB of ram. Currently I am running XP pro on it, considering it was an old office PC. I want to keep XP Pro, but install ubuntu server also.

Is there any way I can partition my drive while installing ubuntu server or is that not possible?

I see many guides on dual booting with ubuntu, but none w/ the server.

---

### Post by Ken_Lewis81 on 2007-05-30
I've only resized NTFS partitions using GParted from the Desktop CD.  I don't think that the Server disk will install the GNOME Desktop environment with GPartED, but it should have PartEd which will allow you to shrink your NTFS partition.  Take care to defragment the disk beforehand (boot XP into Safe Mode to minimize the other stuff XP is doing) and make sure you can make enough space for Ubuntu.  You might want to backup all important files.

Take care.
Ken.

---

### Post by LoganHarbour on 2007-05-30
Ok, I'm a bit new to Ubuntu so I would like to be able to do it in the GUI to be safe. Could I run the desktop CD, run GPartED and resize my win partition (live CD), and then run the server and create a new partition, or could I completley create a new partition using GPartED in ubuntu live, so all I woul d have to do is choose the drive when I install ubuntu server.

---

### Post by louieb on 2007-05-30
The server CD installs just like the alternate Ubuntu install CD.
You can use GParted off the live CD if you  can get it to run but I believe it requires 192MB ram. 
Get the    [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") to make your partitions  heres a how to [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm"). And like **Ken_Lewis81 **said defrag first. Heres a tool I like   [A better windows defragmenter.]("http://kessels.com/JkDefrag/index.html")
Then you can use the server CD. when you get to the partitioning section of the install use the manual partitioning option and point the installer to your new partitions. 
For a walk through of an alternate CD install this site is great    [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/").

---

