---
title: "Issues trying to install 12.04 lts/ 12.10 on a Laptop"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by Deadpool79 on 2013-03-15
I've been trying to get ubuntu 12.04lts and or 12.10 on my girlfriends Laptop (HP G6 AMD A6, 4 gigs of ram, 320GB HDD, Win7) to no avail. I've tried booting from flashdrive (hung unresponsive) and from disk.  I've attached an image of the error I keep getting.  I've google searched this issue inserting multiple individual lines of this error and have gotten no results.  Any insight is greatly appreciated. Thank you.[IMG]http://i1303.photobucket.com/albums/ag160/Edgar_Irizarry/IMG_20130315_143731_zps7d6e6d39.jpg[/IMG]

---

### Post by oldfred on 2013-03-15
Have you used all 4 primary partitions?

Have you shrunk Windows using Windows Disk tools and rebooted several times so Windows can update itself with its new size.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Have you backed up Windows and made a Windows repairCD?
      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[URL="http://forums.techarena.in/guides-tutorials/1114725.htm"]http://forums.techarena.in/guides-tutorials/1114725.htm
[/URL]
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[URL="http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html"]http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html

[/URL]
 Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

[URL="http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html"]
[/URL]

[URL="http://forums.techarena.in/guides-tutorials/1114725.htm"]
[/URL]

---

