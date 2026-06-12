---
title: "Dual boot with Windows 7, corsair accelerator"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by Velcio on 2012-11-15
I want to install Ubuntu as a dual boot on my computer, I have a SSD and a HDD which is accelerated with a Corsair Accelerator 30 GB. Because there isn't much space left on my SSD I want to install ubuntu on my hdd. When I'm booting the installation, it finds my 2 TB hdd but it's saying there isn't a thing on it while there's already 300 GB's used. Can I just use GParted to make a new partition or will this erase my hdd? If I can't make a new partition, how can I install ubuntu without erasing my HDD?

---

### Post by Mark Phelps on 2012-11-15
Word of warning: do NOT use any Linux tools to resize your Win7 install.  Doing so risks corrupting Win7 and rendering it unbootable as a result.

In addition, BEFORE you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD.  At least with this, you will have a way to fix Win7 filesystem corruptions should something happen during the Ubuntu installation.

And finally, do you know if your PC uses UEFI? IF so, that could explain why the installer doesn't see the current disk usage.

---

### Post by Velcio on 2012-11-15
My motherboard using EFI (that's what it is saying in the description). I won't resize my Win7 boot disk, Win7 is installed on my ssd and i want to install ubuntu on my hdd. Right now i'm making a backup of my hdd and then i'm going to take the risk of using GParted in linux to make a new partition in ubuntu. Do you have any things i have to keep in mind when i'm doing the resize/installation?

---

### Post by oldfred on 2012-11-15
If your configuration is Intel SRT, then it may have RAID. Not quite sure how that is done. 

The standard desktop installer does not have the RAID drivers and gparted nor the installer works with RAID. And since they did away with the alternative installer in 12.10, you can only install the server version of 12.10 with RAID.

Some have turned the RAID off, so then the installer works or just installed Ubuntu to the small SSD as a boot drive.

 Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by losfalcor on 2012-11-15
I got a dualboot of windows7 and ubunutu on my laptop.  I used g parted on a live cd to shrink my Ubuntu partion then installed windows 7 on that partion.  The grub menu wasnt there and windows loaded with no option to pick ubuntu on load up, so i used the ubuntu install disk as live cd to install boot repair.    I like the dual boot cause i can play my video games and use photoshop when i want.  And ubuntu puts the windows partion as a file system on the desktop so you can transfer files back and forth from Ubuntu to windows or play files saved in your windows.  its cool.  good luck

---

### Post by Velcio on 2012-11-16
So if I want to install it with my raid I need to use the server version? If is disable raid, install ubuntu and re-enable it, will it still work? if i disable raid will then find my usage? because it's olfred said, i'm using uefi as bios

---

### Post by oldfred on 2012-11-16
I have not seen anyone with UEFI and Intel SRT install. So you can be first. Good backups and a repairCD or USB are then always a good idea, but you should have those anyway.

I would not think boot method would make a difference so those that turned RAID off and back on should be a good example.

May be best to post Boot-Info report just to confirm where everything is at and document system.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
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
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by Velcio on 2012-11-16
i didn't really used intel SRT directly, i used corsair Dataplex and i may be the first to dualboot with this setup but i'm definitly not the first with UEFI and Intel SRT. I had problems with the installation of win7 and searched on the internet :P
thnx for the links, backup almost finished then i'm going to start the installation of ubuntu :P

---

