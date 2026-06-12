---
title: "Refuse to boot the CD / USB"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by Pierrick584 on 2012-02-28
Greetings, on my brand new computer, Ubuntu refuse to boot the live installation no matter the media (well, cd, or usb) happend on 11.10, and 12.04 daily build of today, ubuntu, and kubuntu. it just freeze during boot with no bug/error (i did check the verbose mode) 

Sometime the cd doesnt even want to actualy reach the boot menu, problem also happend on backtrack witch is based on ubuntu, last time i tried fedora it did work... but then i have problems with nouveau preventing me to have x11 started...

My mother board is gygabite x68x-ud3h-b3, if anyone have an idea i would apreciate.. this computer drive me crazy, the only way i got to install linux on it yet, is to put his hard drive in another computer, then install on it, then put the hard drive back (and its extremely complex considering that the hard drives are stuck behind alot of cables and my two huge video cards_

---

### Post by polipantev on 2012-02-28
Guys i am really totally lost so please help really done evrything i saw logical but nothing made things work.First of all i do not know if the problem isn't in the Universall USB installer because i downloaded it then downloaded the version Ubuntu 11.10 and installed it on a USB stick which i formatted to FAT file system!!!Then i get the message when i boot from the same USB mentioned "no default or UI configuration directive found" and when i read about renaming files on the USBdir i opened those files and for example in isolinux/syslinux i found nothing guys...I am totally lost and really hate it when i feel like noob so please help!!!Thank you in advance!

BTW i am trying to run it on a Compaq Mini 110c-1110EQ


Microprocessor 	1.60 GHz Intel Atom processor N270
Microprocessor Cache 	512 MB Level 2 cache
Memory 	1024 MB (1 x 1024 MB)
Memory Max 	Up to 1 GB DDR2
Video Graphics 	Intel GMA950
Video Memory 	Up to 128 MB
Hard Drive 	160 GB (5400 rpm)
Display 	10.1” Diagonal SD LED Anti-glare Widescreen Display (1024 x 576)
Network Card 	Integrated 10/100 Ethernet LAN

---

### Post by oldfred on 2012-02-28
Have you tried nomodeset?

[http://askubuntu.com/questions/84385/getting-drivers-to-work-for-intel-gma-950](http://askubuntu.com/questions/84385/getting-drivers-to-work-for-intel-gma-950)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

