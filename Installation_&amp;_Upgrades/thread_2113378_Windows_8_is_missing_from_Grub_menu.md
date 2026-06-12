---
title: "Windows 8 is missing from Grub menu"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by forochelian on 2013-02-07
After installing Ubuntu 12.10, I can't boot Windows 8. I read [**this thread**]("http://askubuntu.com/questions/136390/windows-7-windows-8-entries-missing-after-reinstalling-grub") and lots of others, I tried lots of things [ Boot-Repair, etc ], but I still couldn't make it.

Here is my boot info script output: [http://paste.ubuntu.com/1620269/](http://paste.ubuntu.com/1620269/)

My **fdisk -l** output: [http://pastebin.com/gQGsXtGk](http://pastebin.com/gQGsXtGk)

How can I fix this ?

---

### Post by oldfred on 2013-02-07
Welcome to the forums.

You cannot as configured. Windows has to boot from a primary partition, your install is in sda6 and has a corrupt PBR - partition boot sector. 

Did you have another Windows install in sda1 where you put swap. Second installs of Windows put all boot files into the first install. That way it is in a primary partition. 

You may be able to delete swap and make that partition the Windows boot. It needs to be NTFS formatted with the boot flag that is now on sda6. Grub does not use boot flag, but Windows has to have it on the primary partition you boot from. Then from a Windows 8 repairCD you may be able to repair the boot. But I am not sure that a Windows repairCD will run chkdsk on your Windows in the logical partition which you have to run to repair the PBR.

Since your Windows 8 is not UEFI, I am not sure what repairCD you need. Some of the Windows forums may know.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
To better understand how Windows works. Vista but even 8 is still the same if MBR not UEFI.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by forochelian on 2013-02-08
I tried everything, but I still couldn't make it.
I tried lots of ways, like these; [link 1]("http://superuser.com/questions/451277/missing-boot-files-in-windows-8"), [link 2]("http://qliktips.blogspot.com/2012/11/fix-windows-8-boot-issue.html"), there is no solution !

When I used diskpart to look at partitions, there is no partition shown.

What can I do ?

> **oldfred said:**
> Welcome to the forums.

You cannot as configured. Windows has to boot from a primary partition, your install is in sda6 and has a corrupt PBR - partition boot sector. 

Did you have another Windows install in sda1 where you put swap. Second installs of Windows put all boot files into the first install. That way it is in a primary partition. 

You may be able to delete swap and make that partition the Windows boot. It needs to be NTFS formatted with the boot flag that is now on sda6. Grub does not use boot flag, but Windows has to have it on the primary partition you boot from. Then from a Windows 8 repairCD you may be able to repair the boot. But I am not sure that a Windows repairCD will run chkdsk on your Windows in the logical partition which you have to run to repair the PBR.

Since your Windows 8 is not UEFI, I am not sure what repairCD you need. Some of the Windows forums may know.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
To better understand how Windows works. Vista but even 8 is still the same if MBR not UEFI.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by oldfred on 2013-02-08
The main issue you have is Windows is not in a primary partition. Windows normally only repairs, installs to, or boots from the primary NTFS partition with the boot flag. And Windows does not recognize boot flags on logical partitions.

If you are booting from a new sda1 primary NTFS then it may let you repair your install in the logical, but much better to have Windows in a primary partition. 

Be sure to backup any important data before doing anything else.

Edit you may be able to use this to convert to primary, then it may be repairable. You will have to make current sda1, 5 & 6 as sda1, 2 & 3 and then the rest as logicals. You have to follow rules on partition table, but it should guide you on what you can or cannot do.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table and save to another device.
sudo sfdisk -d /dev/sda > parts_sda.txt

---

