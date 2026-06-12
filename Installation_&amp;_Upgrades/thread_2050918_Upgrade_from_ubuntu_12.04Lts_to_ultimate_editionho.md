---
title: "Upgrade from ubuntu 12.04Lts to ultimate edition/how to remove it"
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by oloyeadeniran on 2012-08-31
Guys i need huge help here and am confused on how to get it solved
Yesterday i downloaded the latest 12.04 Lts from Ubuntu site,and it was installed by wubi
it was great getting hold of  an ubuntu at last,bt it was shortlived as i saw a bit different windows ,i was unable to play music,videos and other stuff,this made me angry nd wanted to remove it and install with ultimate edition that an online buddy said has wine preinstalled ...cool with me but how do i do this without crashing mi harddisc,without losing 110Gb worth of files on mi win7 in C:/ plz i just need a God sent fellow to baik me out

---

### Post by oldfred on 2012-08-31
Welcome to the forums. Changed your type to standard.

How many partitions do you now have? Post this:
```

sudo fdisk -lu
```

Do you have anything in wubi you want to save? If so backup /home from wubi or use this  to copy wubi to a full install.

Use Windows tools to shrink the Windows partition, but do not create any partitions with Windows.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Make vendor recovery, full backup & a Windows repairCD or USB:

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
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

### Post by darkod on 2012-09-01
You can remove wubi in Control Panel - Programs like any other program. It will do nothing to your hdd since wubi is virtual working inside windows.

I'm not sure you need to install another edition just to watch videos and play music. In most cases the first time you try to play some multi media, it will tell you what it needs to install and ask you for permission to do it.

Also, wubi is not designed to be used as long term install, just a quick try. So I don't see much point trying to configure many details if you are going to use it only a short time. And using it long term is not recommended.

---

### Post by oloyeadeniran on 2012-09-10
Uninstallation of ubuntu 12.04 LTS was a piece of cake,and after i descised to Go after the real thing (Ultimate 3.4 based on 12.04 LTS)precise, before all my Eternet & wireless Lan were working on ubuntu 12.04 using wubi to install it, but 
[b]The main problem i have with ultimate edition 3.4 is the internet connectivity i am unable to make a connection to any LAN OR WLAN, it being an headache for the me,,my ulimate has Ndiswrapper preinstalled with it but without a driver.how to do i go about the installation or how to fix  the problem at hand  am tired of the situation please help me out!! thanks

---

