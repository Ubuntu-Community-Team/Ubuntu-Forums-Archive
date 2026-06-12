---
title: "boot issues. dual boot. windows bootloader not showing"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by pddevesh on 2016-04-25
I had ubuntu 16.04. I wanted to dual boot my system with windows 10. After installing windows 10, i could not boot with ubuntu. So, i followed  forum and inserted ubuntu liveUSB and installed boot repair program. After completing the procedure successfully, when i rebooted my PC i got only ubuntu in my bootloader menu. There was no option for windows 10.
Any fixes?
URL:[https://paste2.org/5B8PALdf](https://paste2.org/5B8PALdf)

---

### Post by oldfred on 2016-04-25
You have BIOS installs on newer UEFI hardware.
You should boot Boot-Repair in BIOS mode.

Did you leave Windows 10 fast start up on? That is always on hibernation.
And grub only boots working Windows, or Windows that is not hibernated nor needing chkdsk. And it needs chkdsk after any resize.

Temporarily restore Windows boot loader with either your Windows repair flash drive or installer in repair console and run fixMBR. Turn off fast start up. Once Windows is working restore grub to MBR with Boot-Repair or manually.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System
[/URL]
 Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold) 

[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

