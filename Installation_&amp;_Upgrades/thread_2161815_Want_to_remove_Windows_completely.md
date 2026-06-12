---
title: "Want to remove Windows completely"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by tsajan on 2013-07-12
Dear all,
I have a windows computer alongside Ubuntu 13.04. I like to remove the windows OS and get a free disk in that drive! Also I am suffering from frequent crashes in ubuntu 13.04, i am thinking of switching to ubuntu 12.04. How do I manage the installation? Please reply ASAP!
thank you

---

### Post by VMC on 2013-07-12
Are you wanting any thing off of either Windows or Ubuntu 13.04?

If not then get the Ubuntu Precise 12.04 ISO and boot it up. There's an option from the Install to use the entire desk which will erase the disk and install Ubuntu on it.
 If that's not exactly what you want to do, then you will need to use the "Something Else" option. That however takes a little more advance knowledge.

---

### Post by leosubhadeep on 2013-07-12
**If you can remember on which partition your bootloader is**, you can use *gparted partition editor* and *boot repair* to delete and re-create partitions. First, install gparted and boot repair in Ubuntu. Then unmount ntfs partitions and create/allocate ext4 partitions you want. Finally, run boot repair with default options.

> 
sudo apt-get install gparted
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install boot-repair


If you can elaborate a bit about system crashes you are facing with Ubuntu 13.04, people here might be helpful as this new version has some improvements,too, worth using.

---

### Post by oldfred on 2013-07-12
I would make a Windows image backup and a Windows repairCD. We regularly get users who find one application or game that they cannot live without that only runs in Windows. It took me about 5 years before I could totally wean myself from Windows.

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

