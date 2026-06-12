---
title: "repair boot error - can't boot windows"
date: 2017-07-14
forum: Installation &amp; Upgrades
---

### Post by zemer-avital on 2017-07-14
Hi

i'm trying to install windows 10 after ubuntu is isntalled. the windows installed, but than i could not run ubuntu. i run boot repair from a rescue disk, and it got the attached info, with an error message in the end. i can now run ubuntu, but not windows.

This is the output of boot repair is here:

[https://paste.ubuntu.com/25088191/](https://paste.ubuntu.com/25088191/)

---

### Post by yancek on 2017-07-14
Your boot repair output shows the Ubuntu Grub bootloader installed in the MBR of the drive with the proper boot files on the Ubuntu partition.  The grub.cfg menu file shows an entry for windows on the  correct partition and the windows partition is marked active.  What happens when you select windows from the boot menu?  Also, for some reason, you have two Grub installs, one on sda1 which I guess is a boot partition and another on the Ubuntu system partition (sda2).

---

### Post by oldfred on 2017-07-14
You generally do not want to install grub to a partition.
Grub only boots working Windows and Boot-Repair will not fix most Windows issues, you need Windows repair console or if Windows installer has repair console you can use it.

Windows 10 has  fast start-up which really is just hibernation. Linux NTFS driver will not mount hibernated Windows nor Windows that needs chkdsk. And then grub cannot boot Windows.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If Windows repair console cannot fix issue, you may have to temporarily reinstall the Windows boot loader to MBR, directly boot Windows and make fixes and changes in settings. Then restore grub to MBR with either Boot-Repair or manually.
       
        How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Note that Windows updates will often turn on fast start up and/or restore Windows boot loader to MBR. So always have a Windows repair flash drive and Ubuntu live installer handy when doing updates. Windows may also do updates in background and you may not know it updated.

Windows 10 dual boots easier in UEFI mode as then you can directly boot from UEFI boot menu when Windows does its updates and prevents grub from booting it.
 Or if BIOS use one drive for Windows and have Windows boot loader in MBR and another drive with Ubuntu and grub in that drive's MBR.

---

