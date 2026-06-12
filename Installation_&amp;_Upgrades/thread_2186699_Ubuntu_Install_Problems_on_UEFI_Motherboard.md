---
title: "Ubuntu Install Problems on UEFI Motherboard"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by xxibiilxx on 2013-11-08
I need someone who is trained in the arts of Ubuntu.

I am trying to install Ubuntu on a secondary HDD I picked up, and I am having difficult times. 
I have the AsRock Z77 Extreme4 motherboard, and I believe that may be the problem.
HOWEVER, it may also be my video card (GTX 770) or a combination of the two. 

I have been searching the interwebs for hours trying to locate a fix for this. 

Apparently it is very difficult to install Ubuntu (or any Linux distro  for that matter) onto an HDD that is connected to a UEFI motherboard. I  have no idea how to get around this and am very confused. Any insight  into the matter would be greatly appreciated!

Also I will reiterate a couple details:
-Trying to install Ubuntu 12.10.
-I have an AsRock Z77 Extreme4 MOBO, which happens to be a UEFI MOBO.
-My video card is an EVGA Geforce GTX 770.
-When I attempt to install using WUBI, I encounter one of two errors when switching between the different install methods:
1. I get a black screen with a purple line on the left side and a command line type of screen but no commands execute.
2. I get a completely black screen, and a command line interface. Dozens  of commands execute, but it hangs on a command that says "switched to  clocksource tsc" then continues. It finally stops execution at the  following command: "ata8: hard resetting link".

Before you suggest it, hard drive failure is not a problem, because I have tried it with multiple disks.


Here is some of the research I have done, take a look if you think it will help.
[http://ubuntuforums.org/showthread.php?t=2020496](http://ubuntuforums.org/showthread.php?t=2020496)
[http://dedwarmo.com/cant-install-ubu...z77-extreme-4/]("http://dedwarmo.com/cant-install-ubuntu-12-04-on-asrock-z77-extreme-4/")
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://ubuntuforums.org/showthread.php?t=2137093](http://ubuntuforums.org/showthread.php?t=2137093)

---

### Post by oldfred on 2013-11-08
If you have two hard drives and want Ubuntu on second, you do not want wubi.

How is system on first motherboard booting? UEFI or BIOS/CSM/Legacy? You will want to to install Ubuntu in the same boot mode to be able to easily dual boot. You can have each different, but UEFI & BIOS are not compatible and once you start booting in one mode you cannot switch. So grub menu will not give a valid boot if other install is not in same boot mode.

With nVidia you will need nomodeset. If in BIOS mode &  purple screen you have to hit a key at accessiblity icons and f6 add nomodeset. If UEFI boot you get grub menu and have to use e to edit, scroll to linux line and replace quiet splash with nomodeset. You also need that after install and until you install the proprietary nVidia driver.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

This shows both BIOS (purple) and UEFI (black with grub menu) screens.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Post this:
sudo parted -l

---

### Post by xxibiilxx on 2013-11-08
Thanks! How can I check whether my Windows OS is booting in UEFI or Legacy though?

---

### Post by xxibiilxx on 2013-11-08
I found that my Windows OS is booting in Legacy mode, so in my MOBO settings I changed my disk drive to boot into ACHI mode (That's my MOBO's way of saying BIOS.)

I do this, and I get the accessibility menu, and I hit f6 to change nomodeset, and then I try to boot but it gives me a black screen. It has a command line interface, though no commands run at all. 

I'm still stuck! :(

---

### Post by oldfred on 2013-11-08
Someone posted this, which may or may not be related. Generally nomodeset works with nVidia. :
>  So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!



Some other threads that may have more info?
 UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)

---

