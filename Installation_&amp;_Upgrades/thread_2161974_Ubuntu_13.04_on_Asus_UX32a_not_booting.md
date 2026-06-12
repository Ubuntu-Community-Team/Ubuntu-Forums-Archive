---
title: "Ubuntu 13.04 on Asus UX32a not booting"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by lorinduq on 2013-07-12
Hi there,

I bought an Asus UX32a today and want to run Ubuntu 13.04 alongside Windows 7. 
Right now I have  Windows 7 pre-installed and I managed to install Ubuntu 13.04 alongside of it from a USB-stick. I did no particular partitioning, just let the installer decide what to do by default.
Up to this point everything went fine but now I can't boot Ubuntu. It keeps on booting into Windows...
What to do? I tried browsing this forum but can't wrap my head around it all...

my bios is 214   version 2.15.1226
boot option #1 Windows Boot manager
no boot option #2 right now


thx!

---

### Post by oldfred on 2013-07-13
Most Windows 7 systems are installed in BIOS mode, even if system was UEFI capable. Ubuntu may install in either mode depending on how you boot installer.

Best to see details.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

