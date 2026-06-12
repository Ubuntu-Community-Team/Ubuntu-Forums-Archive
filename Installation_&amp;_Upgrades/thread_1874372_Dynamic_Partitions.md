---
title: "Dynamic Partitions"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by marck.karam on 2011-11-02
Now that you have a Repair CD, you need to confirm that the final   partition is not actually INSIDE an extended partition -- which would   explain why there is no actual free space seen by the installer.



> **Mark Phelps said:**
>  do NOT allow the partitioner to create  another partition.  This will convert your partitions into Dynamic Disks  -- effectively preventing the installation of Ubuntu and causing you  further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and  burn a Win7 Repair CD. This will come in handy later, should you need to  repair your Win7 boot loader from the dual boot setup.


.

how  i dont allow  the partitioner to create another partition.?


> you need to confirm that the final  partition is not actually  INSIDE an extended partition -- which would  explain why there is no  actual free space seen by the installer. how  too ?

> To do that, boot from the Ubuntu desktop CD, choose Try Ubuntu when the  screen comes up. When you get to a desktop, use Dash to search for Disk  Utility and click that.  When that opens, look at the partition  arrangement on your PC

i follow your steps but when the desktop comes up i press on dash and i wrote .Disk  Utility  on the text box but it dosen't  show me anything


this is some pic
 
1-this is form my computer
show us that i have 320 GB hard disk 4 partions
1-100 giga for windows os
2-30 giga for ubuntu
3-8 giga (SWAP)
4-165 giga to the other data


[IMG]http://i147.photobucket.com/albums/r316/mcool5/DSC02469.jpg[/IMG]


2-this pic from my disk mangement utility
[IMG]http://i147.photobucket.com/albums/r316/mcool5/DSC02472.jpg[/IMG]

 
3-this is what ubuntu installer show  me
[IMG]http://i147.photobucket.com/albums/r316/mcool5/DSC02468.jpg[/IMG]


> **oldfred said:**
> It is always best to have backups. There are no  guarantees that a hard drive will not fail, software may not do what you  expect or a user makes an error and erases something.  I consider  myself pretty knowledgeable and have had all those occur to me.

Post screen shot from Gparted and a copy of this from the terminal.

sudo fdisk -lu

The vendor recovery DVDs are just an image of your drive as purchased.  If you have housecleaned a lot of cruft normally included, run many  updates with many reboots, and added software you may want a full back  up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)



4-and this is the command sudo fdisk -l output
[IMG]http://i147.photobucket.com/albums/r316/mcool5/DSC02482.jpg[/IMG]


so what i have to do  ?

am waiting for replay

any hint will appreciated
Thx in advance and sorry agin for topic owner to use the topic to get help for my problem

---

### Post by oldfred on 2011-11-02
Please do not hijack another thread. Moved to your own thread.

Your dynamic partition issue is so different I created a new thread for you.

The SFS means you used the Windows partition tool to create partitions and it converted to dynamic. Even some Windows repair tools do not work on dynamic partitions. And most Linux tools do not even see the SFS partitions correctly.

Window offical policy is to totally backup drive, erase drive, recreate basic partitions, reinstall and restore your data. Whatever you do you do need good backups.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

