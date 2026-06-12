---
title: "From 320 GB HD to 180 GB SSD (dual boot)"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by jimbop99 on 2012-11-25
I currently have a 320 GB HD with ubuntu and windows 7. I purchased a 180 BD SSD and want to use it as my boot drive. The 320 GB has windows (100GB), ubuntu (50 GB) and data (the rest). I want to put the windows and ubuntu partitions on the SSD then make the old HD the data drive. I've used clonezilla to clone entire drives before but this seems a little more complicated. Any suggestions/tips would be appreciated. Thanks.

---

### Post by oldfred on 2012-11-26
I do not know the Windows way, but some suggest Windows tools for Windows & Linux tools for Linux. Windows is very particular about partitions, sizes and changes. So it will require repairs if it does restore to a new drive.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

I also prefer clean installs. So for Ubuntu I would suggest a clean install. If you copy it, you will have to reinstall grub2's boot loader and manually edit fstab with new UUIDs. If you attempt a full clone you will have duplicate UUIDs and have to manually edit UUIDs on one drive other the other. (May be same issue with Windows?)

If you keep /home or separate data from /home you can just install to the SSD. 

I use my SSD as just a boot drive for Ubuntu and include /home, but no data. I am also aggressive about moving data to my data partitions, so my / (root) is not large. I use about 9GB of my 25GB / partition.

---

### Post by jimbop99 on 2012-11-26
Thanks for the replay oldfred. I think I'm going to try this ([http://lifehacker.com/5837543/how-to-migrate-to-a-solid+state-drive-without-reinstalling-windows](http://lifehacker.com/5837543/how-to-migrate-to-a-solid+state-drive-without-reinstalling-windows)). I'm going to clone my Windows partition then do a fresh install of Ubuntu.

---

