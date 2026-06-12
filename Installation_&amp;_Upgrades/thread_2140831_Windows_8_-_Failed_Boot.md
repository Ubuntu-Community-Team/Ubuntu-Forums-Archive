---
title: "Windows 8 - Failed Boot"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by jakey455 on 2013-04-30
First to explain. I dual booted Ubuntu 13 with Windows 8. I can access Ubuntu with no problems but if I wish to access my windows 8, I receive and error.

File:/Boot/BCD
Error: 0xc000000d

My boot files are wacky and I have no clue how to fix them. I tried the recommended fix on Boot-Repair and it hasn't done anything.

Also, here is this link. 
[http://paste.ubuntu.com/5620934/](http://paste.ubuntu.com/5620934/)

Thanks a million,
Jake

---

### Post by jakey455 on 2013-04-30
Shameless self bump

---

### Post by oldfred on 2013-05-01
Boot-repair cannot fix internal Windows issues. You need a Windows repairCD or flash drive.
It looks like your boot files are in  sda1, but boot flag or active partition in Windows is on sda2. Grub does not use boot flag 

The info in Boot-Repair is saying you still have Windows hibernated. It does not dual boot well with that.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

    
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
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by jakey455 on 2013-05-01
I actually solved it myself. I ended up using a Windows 8 boot up disk to fix the boot files.
I then wasn't able to load Ubuntu so I used EasyBCD to add a new entry which now allows me to access Ubuntu.

Thanks though.

---

