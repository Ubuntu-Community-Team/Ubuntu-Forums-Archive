---
title: "Gparted does not show Windows 7 for dual-boot"
date: 2012-08-05
forum: Installation &amp; Upgrades
---

### Post by KsKnightmare on 2012-08-05
Hey all,I just bought an Asus N56v the other day and did a fresh install of windows and am now trying to install Ubuntu. When I put the ubuntu disk in, everything works until I have to choose where to install it. Gparted shows that all 700GB are unallocated, but os-prober shows that Windows 7 is installed. In windows I even split the drive into two 350GB partitions. How do I fix this?

---

### Post by oldfred on 2012-08-05
Do not create partitions with Windows. I may convert to dynamic partitions.

Most new Windows computer use all four primary partitions. Windows uses 2, one the hidden 100MB boot/repair and the main install. Then the vendor adds an image of drive as purchased instead of install disks as a recovery partition and a utility or tools partition.

From liveCD post this:
sudo fdisk -lu
Or from gparted post a screenshot. You can attach to your message with the paperclip icon in the edit panel above you message.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

