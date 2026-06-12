---
title: "Unable to Boot Win8 after installing Ubuntu 14.0.4 on a Dell Latitute E5450"
date: 2016-04-17
forum: Installation &amp; Upgrades
---

### Post by Fabio_Estevam on 2016-04-17
Hi,

My Dell Latitute E5450 came with Win8 installed and I want to make it dual boot with Ubuntu 14.04.

After installing Ubuntu 14.04 I can no longer boot to Windows.

Here is the log generated from boot-repair:
[http://paste.ubuntu.com/15903087/](http://paste.ubuntu.com/15903087/)

Any suggestions, please?

Thanks

---

### Post by oldfred on 2016-04-17
Can you directly boot Windows from UEFI or one time boot key like f12?

You need to make sure fast start up or Windows always on hibernation is off.
       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by Fabio_Estevam on 2016-04-18
Unfortunately I can no longer boot into Windows, even if I try it via F12.

---

### Post by oldfred on 2016-04-18
Grub only boots working Windows. 
So either f12 and then f8 to get into the internal repair console or you need the Windows repair disk or Windows installer in repair console to fix Windows.

Boot-Repair can only fix very minor Windows issues, best to always have repair flash drive for current version of every system installed. Ubuntu live installer and adding Boot-Repair is good for Ubuntu.

 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[URL="http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB"]http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB
[/URL]
 Manually create repair flash, shows files & locations
[http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools](http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools)

[URL="http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB"]
[/URL]

---

