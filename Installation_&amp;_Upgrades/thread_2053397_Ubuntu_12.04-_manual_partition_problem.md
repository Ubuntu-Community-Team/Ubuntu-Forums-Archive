---
title: "Ubuntu 12.04- manual partition problem"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by fregeslogic on 2012-09-05
Hi all. 

 Basically i tried to dual install ubuntu from live CD alongside a windows 7. This first install i got the option of auto partition for dual boot that is inbuilt with the ubuntu installer. However the automatic config for that partition left too little disk space for my Windows , so i used the little slider and put it half half.

All well and good . But it froze immediatly saying 'preparing partition' for one hour. I pressed back and got out of that and then restarted the computer.

Ever since, i don't have the auto config dual boot option. Now i'm ok with doing a manual parition and went onto the 'other options' button. But now, as soon as i go on my main hard disk partition (partition 3) I cannot 'add' partition to it. 

Is there a chance that some basic ubuntu stuff was installed? Its not showing up on the main partition (which is a solid bar 448gb).

Ok hope that made sense. Please help i love ubuntu and cannot live wihtout it.
thanks.

---

### Post by oldfred on 2012-09-05
Welcome to the forums.

Does Windows still boot ok. It is usually best to shrink Windows with the Windows MMC tools and reboot a couple of times so it can run chkdsk and update itself to its new size. Often housecleaning, defragging and a full backup is recommended also. And having a separate repairCD is worthwhile.

Did the installer create a new partition so now it cannot see space to install into?

Post this from terminal in liveCD.

sudo fdisk -lu

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

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by fregeslogic on 2012-09-10
Hi thanks for your very detailed reply. In the end it was a faulty disc.  Unfortunately some elements of 12.04 had been installed so although i tried a dual boot intall I ended up wiping everything using ubuntu 10 and then upgrading to 12. 

Well that's not an issue for me since i love ubuntu so losing windows 7 is no loss. However one unfortunate thing is losing adobe pro 9. I used it in my research to put bookmarks on pdfs. I've tried to find an unbuntu program but had no luck. now browsing for solution. Thanks for the help anyway.

---

### Post by Tankerdog2002 on 2013-01-10
I realize I'm a bit late for this thread; however, If you've been using Adobe-Pro you can use an open source alternative called "PDF Studio". Been using it for years. Does what Adobe Pro does for a fraction of the cost.

---

