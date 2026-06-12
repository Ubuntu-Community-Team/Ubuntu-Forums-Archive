---
title: "Recovery Partition"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by devster31 on 2013-05-10
Hello, I'm trying to install Ubuntu 13.04 on an Asus U30Jc, which already has Windows 7.
The actual partition table is as follows (for some reason I'm not able to get a screenshot):

/dev/sda1 19.53 gb - fat32 - RECOVERY partition for windows 7, came preinstalled with the laptop, it's hidden and lba flagged
/dev/sda2 100 mb - ntfs - system reserved, boot flag, I suppose it's the loader for Windows 7
/dev/sda3 116.34 gb - ntfs - Windows 7 OS partition
/dev/sda4 329.79 gb - ntfs - extended logic partition (lba flag)
   /dev/sda5 329.79 gb - ntfs - actually the only logical partition, for shared data

what I want to do is replace the recovery partition with Ubuntu and create a swap partition on the logical one. the "something else" option of the installer currently doesn't let me resize the logical partition to create a swap space and I have no idea if I should replace the boot partition with something else or let the installer do his thing and just pointing at the hard drive in general. can someone guide me a little here?

thanks

---

### Post by oldfred on 2013-05-10
I would only delete recovery partition if you have made a set of DVDs from it. It would allow you to restore your system to as purchased. More if you might later want to sell system with a clean install.

How full are partitions?
You should be able to use Windows to shrink NTFS partitions. 

But then use gparted from live installer to modify partitions. I would at least put swap in the extended. 
If you use gparted from live installer, you can create partitions in advance.
Then use manual install to choose which partition is /.  For your root partition: From manual install click change, use as ext4, check box to format, mount / . If you already have created swap the install will auto find it.

Even if you have recovery set, it still is a good idea to have a full backup of Windows and a Windows recovery CD in case you have to repair Windows.
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

### Post by darkod on 2013-05-10
Try rezising the logical partition in windows Disk Management. Only the logical partition, not the extended one. But even if it shrinks the extended container, no problem. Make sure you resize it from the back, not the front, so that swap ends at the back of the disk.
Leave the newly created space as unallocated. Reboot windows few times, it often needs that after resizing partitions.

Then start the ubuntu installer, the Something Else option, and do this:
1. Click the sda1 partition, then the button Change below. In the windows that opens, select Use As ext4, mount point /, tick the format box.
2. Make a new swap partition from the unallocated space at the back.

For the bootloader destination select /dev/sda, without any number in it.

That should be it.

But before you start, did you make a set of restore DVDs? Deleting your restore partition will make it impossible for you to restore to factory state if you ever want to.

---

### Post by devster31 on 2013-05-11
Thanks for the tips, just one more question: do I need to resize the extended partition with Windows first or can I do it all from GParted from the Live CD?

---

### Post by darkod on 2013-05-11
I don't recall the exact resize options in Disk Management but if it allows you to shrink the logical partition only (without shrinking the extended container), I would do that. The thing is that swap will need to be created as logical into the same extended container, so you don't actually need the container resized, only the ntfs partition so that it leaves some space for swap. Does that make sense?

Even if windows shrinks the whole extended container, no problem. By creating the swap logical partition later, ubuntu will recalculate and enlarge the extended container automatically and it will contain both the ntfs partition and swap.

So either way it will work.

---

