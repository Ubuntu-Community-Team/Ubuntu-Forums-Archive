---
title: "Ubuntu 16.04.4 LTS, Installation Frozen at Dots"
date: 2018-04-16
forum: Installation &amp; Upgrades
---

### Post by fissy2 on 2018-04-16
Hey there,
I am trying to install Ubuntu 16.04.4 LTS on my MSI GL62 Laptop, so I can run both Windows 10 and Unbuntu on it.
I downloaded the ISO from the official Ubuntu site and made a bootable USB flash according to the official steps, however when I hit "install Ubuntu" it will take me to the Purple Ubuntu screen with 5 dots, which will then light up as a loading pattern, only to freeze very quickly.

My PC specs are the following:
Laptop: MSI GL62 6QF
CPU: i7-6700HQ 2.6GHz
RAM: 8Gb
GPU: Nvidia GTX 960M
SSD: 250 GB 
HDD: 1 TB

I have looked online and tried uninstalling my Nividia drivers, but that didn't help. 
I have never installed Unbuntu before, so if anyone could help me here that would be greatly appreciated.

Cheers!

---

### Post by oldfred on 2018-04-16
If a new UEFI system, you do not want the purple boot screen on the installer.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

And if you have nVidia, you will need nomodeset to boot installer and for install until you add the nVidia driver from the Ubuntu repository.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

And some other models of MSI have needed additional boot parameters.

 MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878) 

Is your system using RAID and two drives?

---

### Post by fissy2 on 2018-04-17
Thanks so much! I turned off Fast Boot in my UEFI and added nomodeset and it install perfectly fine!

---

