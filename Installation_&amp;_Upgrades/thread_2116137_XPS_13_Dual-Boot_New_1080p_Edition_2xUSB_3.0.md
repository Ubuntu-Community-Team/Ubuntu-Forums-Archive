---
title: "XPS 13 Dual-Boot New 1080p Edition 2xUSB 3.0"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by xian98 on 2013-02-14
I just got the newest version of the XPS 13 yesterday. Has anyone managed to get an Ubuntu/Windows 8 dual boot figured out?

**I tried all of the step-by-step instructions listed here:** [http://ubuntuforums.org/showpost.php?p=12486498&postcount=10]("http://ubuntuforums.org/showpost.php?p=12486498&postcount=10")

I've noticed that some people have had issues on the previous versions using the RHS USB 3.0 slot and had to use the USB 2.0 slot. However, both slots of this newest version are USB 3.0!!

I've even tried using an external DVD drive with a live CD.

Using the above instructions verbatim, at best the system reboots and ignores the USB/DVD. At worst, it seems to hang and do nothing. It actually has me a little concerned that it would actually recognize a rescue USB for Windows 8!!

Where it usually hangs is when I follow the instructions:

[LIST]
In Windows 8 find the power off icon (i.e. hit the bottom-left corner and select settings) press it and select reboot while holding the shift key down
[/LIST]

[LIST]
Select "Use a device" (again translated from IT)
[/LIST]

[LIST]
Select "USB Storage Device" <--- Hangs, often leaving a faded screen with the options
[/LIST]

I have even tried making a USB option in the Bios. The problem with that, upon the next reboot, it seems to not see the USB stick that's still in the slot!!



I bought this machine purely with the intention of dual-booting. It's a beautifully awesome machine.

---

### Post by oldfred on 2013-02-15
Have you turned off secure boot and turned off fast boot?

Have you booted directly from UEFI menu not from the Windows menu which may take you back to the UEFI menu but leaves Windows as default?

Have you backed up efi partition and your Windows install?

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by xian98 on 2013-02-15
Inexplicably, after many many many reboots.  With the USB stick in the RHS, it finally worked.

---

