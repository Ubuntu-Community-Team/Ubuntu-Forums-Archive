---
title: "Dual Boot Problem, Ubuntu 14.04 fine, but tries to boot Win 7, instead of 10"
date: 2016-07-24
forum: Installation &amp; Upgrades
---

### Post by newbiemike on 2016-07-24
Hi,

I installed Ubuntu 14.04 on a Toshiba Satellite L550D which came installed with Windows 7 and was upgraded to Windows 10.

The Ubuntu works fine, in fact, it is dazzling compared to the Windows 10. But the dual boot failed to recognize Windows 10, instead identified Windows 7 as the installed version of Windows and tries to boot Windows 7.  As such the Windows boot fails.

Much thanks for all help,

Newbie Mike

PS Not quite Newbie as this is my second Linux installation.

---

### Post by oldfred on 2016-07-24
Some versions of grub were not yet updated to use correct description. But still correctly chain load to Windows.

But Windows 8 or later has fast start up or always on hibernation.
From grub you can only boot a working Windows, or Windows that is not hibernated nor needing chkdsk.

If you left Windows 10 fast start up on, you may have to reinstall a Windows boot loader temporarily, fix Windows and then restore grub.
Best to have a Windows repair flash drive for Windows 10. Chkdsk can only be run from Windows and if corrupted you must have a way to run chkdsk.
From Windows repair console you can use fixMBR to restore Windows BIOS based MBR boot.

You can also use Boot-Repair, but if it does not see Windows it may not offer to install a Windows boot loader in advanced options. You can manually install syslinux if needed as that is what Boot-Repair installs.
After Windows is fixed, restore grub2's boot loader to MBR with either Boot-Repair or manually.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL] f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 

      
 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 
    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by newbiemike on 2016-07-26
Thanks, all working now, Ubuntu and Windows 10 dual boot.

Much appreciated.

---

