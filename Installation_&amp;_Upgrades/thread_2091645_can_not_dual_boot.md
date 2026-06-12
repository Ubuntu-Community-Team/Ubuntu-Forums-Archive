---
title: "can not dual boot?"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by Elitenoname on 2012-12-05
I am trying to install ubuntu 12.04 on my laptop, Lenovo G780, when i boot the cd and go to select my partition it does not have my windows partition listed. Is there something with lenovo that lock the hard drive or anything in the bios that i need to change? I never had this problem when dual booting on my asus laptop

---

### Post by oldfred on 2012-12-05
These have all cause similar issues:
Is this Windows 8? 
Does it have Intel SRT? 
RAID which may be part of Intel SRT?
Windows with dynamic partitions?

Post this from liveCD terminal:

        sudo parted /dev/sda unit s print

---

### Post by Elitenoname on 2012-12-05
I and running windows 7 home premium x 64
I am not using raid or SRT
and the partitions are not dynamic


[IMG]http://i279.photobucket.com/albums/kk150/elitewaffles/Screenshotfrom2012-12-06015059.png[/IMG]

---

### Post by trogdor1138 on 2012-12-05
Nothing appears amiss there. However, that disk is using a MBR partition table. You need to be aware that:

- MBR disks are limited to 4 physical partitions
- Your disk already has 4 partitions
- Something's gotta give; you'll have to drop a partition

Alternatively, you could set up some logical partitions, but that's in-depth, potentially messy, and probably not the best option.

GPT disks don't have the above limitations, but Windows generally can't boot off of GPT volumes. 64-bit versions of Vista, 7, and 8 can, but only when set up and installed on an EFI system, not BIOS.

---

### Post by oldfred on 2012-12-06
While some of these links are for HP the same logic applies. All Windows 7 systems seem to use all 4 primary partitions. And the configurations are all the same. A hidden 100MB boot/repair,  main Windows system, vendor image of drive, and a "utilities" partition. 

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
**Be sure to create recovery DVD(s) first. And a Windows repair CD.**
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

           

Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by Elitenoname on 2012-12-07
what would you guys recommend doing in terms of the best way of doing it?

---

### Post by oldfred on 2012-12-07
If you have made a full set of DVDs, there is not much use for restore partition. In fact you should not need the restore DVDs unless you later want to sell system and it needs to be Windows.

Better to make a full image backup of Windows.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
You can also copy the HP tools partition easily as it is small. Make a backup and/or copy into the Windows main partition. Some have said the HP tools still work if recopied back into a logical partition.

After shrinking Windows with Windows and rebooting several times to let it repair itself with new size, then you can create partitions or install and create partitions as part of install.

       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

