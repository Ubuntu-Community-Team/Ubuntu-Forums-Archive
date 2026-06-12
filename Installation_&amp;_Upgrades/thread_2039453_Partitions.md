---
title: "Partitions"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by DipsWithBuckets on 2012-08-08
Hi,

I was looking to format my laptop but didn't have any hardware to do it the traditional way so I came across Wubi. I figured I'd give Ubuntu a go and so far I'm LOVING the OS. Anyways, I installed it through Wubi, but now I have my old W7 OS still sitting on my HD. I went to format it so I could free up some space and actually make the complete switch but it's saying I can't unmount it because it's active.

Here's the exact message I receive;
"One or more partitions are busy on /dev/sda"

Here's a screenshot of my drives;
[http://i.imgur.com/qlC25.png](http://i.imgur.com/qlC25.png)

I'm under the assumption that the root.disk is the Wubi installation of Ubuntu, is this correct? All in all I just want everything except this fresh install on the hard drive.

---

### Post by oldfred on 2012-08-08
Welcome to the forums.

root.disk is just a file inside the Windows NTFS partition or sda1. So if you try to delete sda1 your also are deleting your Ubuntu install. Somewhat like sitting on the limb that you are sawing off. :)

You need to create new partition(s) and migrate wubi to a partition, or do a clean install to a new partition and copy data over. Then you can delete Windows. But I might make a full backup of Windows, as some do come back and have one application they cannot live without and have to keep Windows. It has taken me about 5 years to wean myself from XP.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

