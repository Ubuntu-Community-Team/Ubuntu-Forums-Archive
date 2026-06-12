---
title: "Dual-boot windows 8 and ubuntu 13.04"
date: 2013-06-28
forum: Installation &amp; Upgrades
---

### Post by Heinzelmannchen on 2013-06-28
I have a Lenovo G580 with windows 8 + Ubuntu 13.04 installed. I've been  trying to get Dual-boot to work for the past few hours with no success.  I've been following this [guide]("http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/2/").  After setting up the partitions similar to the ones in the guide i  downloaded easyBCD on windows 8. I then added Ubuntu 13.04 to the grub  menu. When i restart my laptop i get the menu with lenovo recovery,  windows 8, and Ubuntu(not Ubuntu 13.04 like i labeled) when clicking Ubuntu it says windows failed to load, insert media for recovery. I can't  do anything to access Ubuntu at this point. I don't know what it is i'm  doing wrong but could use some help. Below are some pictures of the  process. I'll post any needed info that i may have forgotten. When  choosing OS it's in uefi mode.
[URL="http://gyazo.com/8d365d10a645465f2243a173a494dcde"]

partitions[/URL]
[OS's]("http://gyazo.com/5320e220462bc810c58cf81390dfb84c")

---

### Post by Heinzelmannchen on 2013-06-28
I can the os manually by going to bios and switching ubuntu or windows. They both appear in each others bootloaders but fail to load. So my main problem is getting them to both work in one anothers boot loaders. Preferably windows.

---

### Post by oldfred on 2013-06-28
I cannot tell much from Windows screenshots as Windows does not see Linux partitions. It just thinks they all are unformatted.
Did you install Ubuntu in BIOS mode or UEFI mode? How you boot install media is how it installs. 
Are you able to boot Windows with secure boot off?
Did you turn off fast boot in Windows and UEFI?

You can install Boot-Repair to your Ubuntu install media (but again each time you reboot), or download a full RepairCD or flash drive with it included.
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

### Post by Heinzelmannchen on 2013-06-29
I installed in UEFI mode. I'm not sure about the secure boot and fast boot(i'm guessing launching windows automatically? If so no i get a bootloader to decide which os for both ubuntu and windows) I know when i installed ubuntu it said secure boot is not enabled. I'll try the info out in those links tommorow i need a break from this for now. ):P

---

