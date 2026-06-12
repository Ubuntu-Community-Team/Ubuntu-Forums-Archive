---
title: "Need help with advanced partitioning during installation"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by xarinlemox on 2013-06-30
Hello guys

I want a detailed walk-through of how I should go about installing Linux on my system.  None of the basic guides I found on internet cover this , hence I am posting here.

I have an Athlon II X2 260 3.2 GHZ, 4 GB DDR 3 Gskill, 500 GB hard drive and Asus Radeon HD 7750 1 GB DDR5 card with suitable PSU. 

I have Windows 7 Ultimate SP1 64-bit installed on my C drive (146 GB).

My hard drive partitions are as follows C drive 146GB , D drive 146 GB and E drive 172GB. I want to partition D drive into sizes  70 GB,70 GB and 6 GB during installation for use of UBUNTU 12.04 Desktop Edition LTS Linux. I want to setup the first 70GB partition for Linux installation , next 70GB for Data and the next 6GB for Swap file.

But I don't know how to go about doing this. The last time I installed UBUNTU choosing 'Install alongside Windows 7' option and default settings for partition I was unable to boot to Windows 7. I have vaguely heard something about UBUNTU not being able to detect MBR if windows C drive partition is above 100GB. Is this the cause for my windows being unable to boot ?

I want to learn Linux and I am an absolute beginner. Can you kindly guide me to install Linux on my Drive or give me an link to appropriate trustworthy documentation resource.

Thank you for your time.

Xarin.

---

### Post by cmcanulty on 2013-06-30
70gb for ubuntu system is way too much. even if you install multipe desktops like ubuntu, xubuntu, etc and tons of apps 25GB would be more than enough.

---

### Post by oldfred on 2013-06-30
You may have used all 4 primary partitions? In MBR(msdos) partitioning you can only have 4 primary partitions, but one can be converted to an extended partition which then is just a container for an unlimited number of logical partitions. Also if you created partitions with Windows it may have converted from basic to dynamic which does not work with Linux and not even with all Windows repair tools.

You may just need to delete d: so you have an available primary partition to be the extended partition. Be sure to back up everything before hand and make a Windows repairCD or flash drive.

Post this from terminal in liveDVD or flash. 
sudo parted -l

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by xarinlemox on 2013-07-01
Thank you for the replies. I will try the steps given above (I actually want to avoid trial and error method because it is too expensive in terms of time and effort and heavy usage of my HDD and after reading through the installation guide given above I think this would be a trial and error method and not the exact customized guide). Firstly I will backup my Windows. Then I will go about attempting to install UBUNTU. BTW I don't know how to restore my Windows 7 OS  and the MBR using these back up discs but I guess I will find that information on Windows website.

I want to be able to play Games on UBUNTU. Games like Far Cry 3, Dota 2, Counter-Strike, The Elder Scrolls V: Skyrim. The last time I installed UBUNTU it said something like I'd have to buy a driver for my Graphic Card and I found that the official website of my Graphic Card manufacturer doesn't make drivers for LINUX. So I don't really see much choice but to use UBUNTU for anything other that browsing the web and playing movies (which don't run with subtitles by default).

---

### Post by Mark Phelps on 2013-07-01
For backing up Win7, I recommend that you download and install the FREE version of Macrium Reflect in Win7.  Image off the Win7 install to an external drive.  Look in Disk Management in Win7 and see if there is a small system partition.  If this PC came preinstalled with Win7, there is one.  In that case, image off both the small system partition and your Win7 OS partition.  Then, use the MR option to create and burn a Linux Boot CD.  You will need that in the future to do Win7 restores from the MR backup.

As to Windows games in Linux -- that's generally a bad idea.  Combination of different drivers (between Windows and Linux) and poor support for DirectX makes Windows gaming in Linux a disappointing experience.

---

