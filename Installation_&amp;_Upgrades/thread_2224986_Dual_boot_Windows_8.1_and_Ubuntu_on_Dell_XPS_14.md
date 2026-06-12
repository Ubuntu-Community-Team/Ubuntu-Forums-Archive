---
title: "Dual boot Windows 8.1 and Ubuntu on Dell XPS 14"
date: 2014-05-19
forum: Installation &amp; Upgrades
---

### Post by Richard_McKenna on 2014-05-19
Hi all,

I have a Dell XPS 14 that came with Windows 8 pre-installed and I've subsequently updated to 8.1. I'd like to be able to dual boot with Ubuntu. I've successfully done this on my self build desktop but I'm unsure how to proceed with the laptop due to OEM and recovery partitions.

It has a 500GB SSD installed with the following partitions:

[TABLE="width: 100%"]
[TR]
[TD]**Volume**[/TD]
[TD]**Layout**[/TD]
[TD]**Type**[/TD]
[TD]**File System**[/TD]
[TD]**Status**[/TD]
[TD]**Capacity**[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]Simple[/TD]
[TD]Basic[/TD]
[TD][/TD]
[TD]Healthy (EFI System Partition)[/TD]
[TD]500 MB[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]Simple[/TD]
[TD]Basic[/TD]
[TD][/TD]
[TD]Healthy (OEM Partition)[/TD]
[TD]40 MB[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]Simple[/TD]
[TD]Basic[/TD]
[TD][/TD]
[TD]Healthy (Recovery Partition)[/TD]
[TD]500 MB[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]Simple[/TD]
[TD]Basic[/TD]
[TD][/TD]
[TD]Healthy (Recovery Partition)[/TD]
[TD]350 MB[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]Simple[/TD]
[TD]Basic[/TD]
[TD][/TD]
[TD]Healthy (Recovery Partition)[/TD]
[TD]11.68 GB[/TD]
[/TR]
[TR]
[TD]OS (C:)[/TD]
[TD]Simple[/TD]
[TD]Basic[/TD]
[TD]NTFS[/TD]
[TD]Healthy (Boot, Page File, Crash Dump, Primary Partition)[/TD]
[TD]463.78 GB[/TD]
[/TR]
[/TABLE]

I would like to be able to return to this exact setup in the future if I wish, re-install Windows, remove Ubuntu etc. What would be the best way of getting Ubuntu installed?

Should I split the 463.78 GB partition and leave the rest untouched?

Is there a way of imaging the entire disc, including the partitions for an easy restore?

Any advice would be greatly appreciated.

Richard McKenna

---

### Post by oldfred on 2014-05-19
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Not sure if all partitions can be specified or you have to choose each. But include efi partition as well as main install. Note the Windows requires the reserved partition but it has no data initially. It is a scratch area for DRM, serial numbers and other data that it does not store directly in Windows.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Dell models are similar so this should also apply:

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)


 Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)

This gives better info on partitions as then you have the exact sector info and type.

 sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

gdisk is not in distribution, but is in repository, to add it.
sudo apt-get install gdisk

Use Windows to shrink Windows and reboot so it can run chkdsk and make repairs.
Then make sure fast boot is off and usually better to have secure boot off.

---

### Post by Richard_McKenna on 2014-05-20
Thanks oldfred,

That's a great help.

Richard

---

