---
title: "Problem Booting With SATA"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by epol81 on 2008-08-14
hi guy,

I got problem when install kubuntu 8.0.4.1 64bit (Busybox) bla bla bla, then i try used IDE Cd-rom so no more busybox but partion hard disk not detect (Seagate 500Gb S32MB SATA II)

Then on bios I enable ACHI, = Problem solve, can detect my SATA Hardisk and install nicely :)

The problem is, i must enable ACHI on Bios when want used Kubuntu and disable it if want lood WinXP, so hope u guys have any idea and best way how to boot winxp or kubuntu without change any bios seting, if i disable ACHI on bios, so my kubuntu get Busybox :confused: 

Hope u all can help me.

Below My spec :-
Intel Core 2 Duo E8400
Gigabyte Intel GA-Ep43-DS3L
Seagate 500Gb HDD 7200rpm 32MB SATA 
Gigabyte PCX GF 8500GT 256MB DDR3


hope it will help both :)

thanks guy and have a nice day.

---

### Post by cariboo on 2008-08-14
IF you install the sata drivers for your windows installation you probably won't have to change your bios all the time. Windows was released before there were sata drives, so there are no default windows drivers.

Jim

---

### Post by epol81 on 2008-08-14
> **cariboo907 said:**
> IF you install the sata drivers for your windows installation you probably won't have to change your bios all the time. Windows was released before there were sata drives, so there are no default windows drivers.

Jim


ya i noted that, but when use achi for boot windows, blue scren apper same as hardware conflict :( thanks for help dude, any order idea, all comment welcome, thanks again.

---

### Post by prshah on 2008-08-14
> **epol81 said:**
> 
Then on bios I enable ACHI, = Problem solve, 
The problem is, i must enable ACHI on Bios when want used Kubuntu and disable it if want lood WinXP, 

Note: You perform the following suggestion at your own risk; it has worked fine for me, your mileage may vary.

Boot normally into XP. First, make sure your XP is up-to-date (Especially that SATA drivers are installed.) Then, create a system restore checkpoint. (You can also create a hardware profile for good measure, if you know how.)

Then load XP in safe mode with command prompt (Keep tapping and releasing F8 after BIOS screen, but before splash screen of Windows XP). When it is loaded, give the command ```
start devmgmt.msc
```, and from Device Manager, remove _all_ HDD controller entries.

Reboot ```
shutdown -r -t 1
```

Change your BIOS settings back to AHCI, then boot into windows normally. On startup, Windows XP should look for and re-install the IDE controller drivers automatically. If it fails with a blue screen error on startup, boot into safe mode and run "Add new Hardware" from the Control Panel. Ignore the error about Safe Mode. If add new hardware refuses to run from safe mode, open device manager (as above) and right click the first icon and choose "Refresh".

If all fails, from the boot up menu, instead of safe mode, choose "Lask Known Good Configuration". If it still doesn't work, boot into safe mode and restore your hardware profile / system restore.

To access system restore in Safe Mode, click start-run and give the command ```
c:\windows\system32\restore\rstrui.exe
```

Once again, you do this at your own risk; you _might_ land up with an unbootable Windows.

---

