---
title: "Windows partion broken but ubuntu still working. How do I got about reparing windows"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by farface18 on 2013-02-22
I have a Samsung rv520 laptop with ubuntu thats partitioned. Windows on 1 and ubuntu on the other. My main os is ubuntu but every now and then I may want to play a game or run a program ubuntu doesnt have. 

I tried logging in to windows today and it blued screened. will installing the recovery disc i got with my pc and running risk wiping ubuntu?

also looking at gparted my harddrive is a bit of a mess, I've attached a screen shot.

I haven't got a clue on how to use gparted correctly so any tips would be helpful.

---

### Post by tjsummers51l on 2013-02-22
Have you tried booting windows in safe mode. If you can get in, you can restore windows back to before the issue.

---

### Post by oldfred on 2013-02-22
Restore Disk often just makes system exactly as you purchased it. That erases everything including all your Window updates & changes.  A few will just refresh Windows, but you need to review.

Better to have a full backup of Windows (once it is working).
Do you have a Windows repairCD? If you have another Windows 7, or a friend with Windows 7 you can easily make a repairCd or Flash.

Gparted often has a tiny red or yellow icon next to a NTFS partition that has issues. I do not see one in you screen shot, so that is good.  Sometimes it just needs chkdsk other times it may need more repairs and those all have to be done by a Windows repairCD or Flash.

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

---

### Post by fdrake on 2013-02-22
+ 1 oldefred;

Also just wanted to point out 1 thing that blue screens aren't related mostly to partition problem only but also can be a wrong drive installed or a system application mulfunction:

[http://windows.microsoft.com/en-US/windows7/Resolving-stop-blue-screen-errors-in-Windows-7](http://windows.microsoft.com/en-US/windows7/Resolving-stop-blue-screen-errors-in-Windows-7)

---

