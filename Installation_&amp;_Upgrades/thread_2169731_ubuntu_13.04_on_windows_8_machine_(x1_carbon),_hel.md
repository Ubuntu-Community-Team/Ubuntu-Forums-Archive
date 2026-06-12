---
title: "ubuntu 13.04 on windows 8 machine (x1 carbon), help needed with boot repair"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by Glen_Fordham on 2013-08-23
my windows 8 partition won't boot and boot-repair didn't seem to help, hopefully someone else here can shed some light on what I can do about this. I had disabled secure boot in the bios, as far as I'm aware that is all that's needed right? Thanks in advance!

[http://paste.ubuntu.com/6017395/](http://paste.ubuntu.com/6017395/)

---

### Post by oldfred on 2013-08-23
Does Ubuntu boot ok?

You are showing a Intel Rapid start partition, but I thought they only did that on Ultrabooks with a small SSD which you do not show. That can also cause issues on installing grub correctly.

Did you turn off fast boot or hibernation in Windows? That can be a major issue on rebooting.
Did you resize Windows from inside Windows and reboot so it can run its chkdsk and recognize its new size. Windows often then has issues on whether it should run repair or attempt to restore form a hibernation that is restoring an incorrect system since it has been resized. You then need to run Windows repairs to correct.

If you cannot get into repair console with Windows 8, you need a separate Windows 8 repair flash drive.
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Most users do not create the repair drive in advance, but if you have access to another Windows 8 you can.
You may be able to remove hiberfile use Linux and then use third party Windows tools like BCDedit, Easeus or Partition Wizard.


 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)


 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

### Post by Glen_Fordham on 2013-08-23
Sorry I should've given more information but I wasn't sure what was relevant. Yes Ubuntu works perfectly, Windows 8 gets the invalid EFI file path error. I still have the recovery partition available so I can recover windows 8 if necessary (which I've already done once in this situation!). Ah I didn't turn off fast boot so that could be a factor! just to be clear I should recover Windows 8, turn off hibernation and fast boot, setup the ubuntu partition from within windows and then try the ubuntu installation again?

edit: the computer is an ultrabook, my model has a 128Gb ssd yes, what can I do to avoid these intel rapid start issues you mention?

---

### Post by oldfred on 2013-08-23
Some info on Ultrabooks in the links in my signatures and users with Ultrabooks have posted what they have done. Some have just turned it off. And then installed Ubuntu to SSD as they are primarily Ubuntu users. Others install Ubuntu onto hard drive and after Ubuntu works have turned SRT back on. If you have an 128GB SSD, you should be able to install Ubuntu to it as well as the Intel SRT. I have seen others with SSD from 16GB to 32GB but they often only used part of the SSD.

Ultrabooks also have the dual video which often causes issues also. Most seem to boot in nVidia mode and need nomodeset as a boot parameter in grub menu's linux line. Use e on grub menu and replace quiet splash. Others have been able to change video to Intel and that often works. But some needed boot parameters for Intel video and other parameters also. 

You should be able to directly boot Windows from the UEFI menu. But grub menu's Windows entry will not work as there is a grub bug. The entries created by Boot-Repair will work, but seem to have issues chain loading when hibernated. Works ok if not hibernated.

---

### Post by Glen_Fordham on 2013-08-24
ah what do you know you're right, I just assumed that if grub didn't work then it was toast! thanks a lot for your help

---

