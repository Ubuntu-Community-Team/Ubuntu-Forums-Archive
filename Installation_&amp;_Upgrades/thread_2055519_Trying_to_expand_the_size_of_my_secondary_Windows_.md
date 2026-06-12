---
title: "Trying to expand the size of my secondary Windows partition is confusing!"
date: 2012-09-09
forum: Installation &amp; Upgrades
---

### Post by hardisty on 2012-09-09
Hello!

I was wondering if anybody might be able to help me through something. See, some time ago I installed Windows on a partition, in order to use Photoshop and some other programs required by my university. Anyways, I've used way more space than I'd thought and now I need to enlarge it!

I've tried googling this but everything I've read seems to involve being wishing to reabsorb from the secondary partition. 

[IMG]http://i.imgur.com/WyN2D.png

I'm trying to take about 20 or so GBs from sda6 and give it to sda2. This is the point where I was about to make a "Help me Ubuntu Forums, you're my only hope" joke, but I'm going to assume it's been done to death.

Thank you!

---

### Post by Cheesemill on 2012-09-09
1 - Shrink sda6 so that there is 20GB of unallocated space to its right.
2 - Shrink sda1 so that the unallocated space is now outside of the extended partition.
3 - Resize sda2 to take up the unallocated free space.

As always gparted operations can take a very long time and can be fatal if interupted by a power cut.

Make sure that you have a backup before you begin.

---

### Post by oldfred on 2012-09-09
Make sure you have your Windows RepairCD or USB handy. It will require repairs after the resize/move. The NTFS partition boot sector has partition info in it on partition start and size (which matches partition table). If that is not correct in the PBR Windows will not boot.

Normally chkdsk should fix it but have good backups as sometime Windows just will not fix itself.

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

