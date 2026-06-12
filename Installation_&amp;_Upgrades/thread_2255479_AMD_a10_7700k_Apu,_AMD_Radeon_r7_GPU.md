---
title: "AMD a10 7700k Apu, AMD Radeon r7 GPU"
date: 2014-12-05
forum: Installation &amp; Upgrades
---

### Post by alex298 on 2014-12-05
Im looking for a little help with install ubuntu 14.04.1. Im using an iBUYpower gigabyte motherboard with ATI AMD a10 7700k Apu and AMD Radeon r7 GPU currently running windows 8.1 (i hate it) When i boot the the live CD i get the black display with the normal options (Try ubuntu, Install ubuntu, install OME and check disk) When i select install ubuntu the purple Ubuntu splash screen will come up with the 5 dots under the name flash and loading as it should. But when it get past that original splash screen when you SHOULD see the options to install and being the process of installation all i see is a black screen and in the middle of that screen a distorted corrupt image. I can here sound when i push the left and right keys but the display is just corrupt. Also a side note if I boot up the Linux mint disk image on my desktop, the action bar and start menu all display nicely. The emblems and selectable icons all appear, but when i go to open a window such as Software center the image of that menu pops up and is corrupt and will not display Also the back ground display is corrupt as well? Any ideas?

---

### Post by fantab on 2014-12-05
Use 'nomodeset' option during boot, as described [**here**]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997"). This will load Ubuntu in 'failsafe' graphics mode. Always go for 'try ubuntu' option. After the live desktop loads see how things fare, for instance check your networking, etc. Install Ubuntu from desktop... upon restart use the 'nomodeset' option again to boot to a desktop. From desktop open 'System Settings' and click on 'Additional Drivers' that should show you the needed graphic drivers, install the driver and restart to boot without using the 'failsafe' mode.

---

### Post by alex298 on 2014-12-05
I read about this option problem is when i hit F6 it doesn't pull up the "boot Options" is the anyway to add the nomodeset option to the arguments on live cd boot? thank you for a reply

---

### Post by ubfan1 on 2014-12-05
The F6 option is only available on non-UEFI boots, so you have to edit the grub commands directly.  Instructions are at the bottom of the screen, but you just type "e" to edit, then on the linux line, add the word nomodeset (and optionally remove the splash quiet words). Type ctrl X or F10 to boot.

---

### Post by alex298 on 2014-12-05
Great I'm working now but will give it a shot when i get home thanks for your help

---

### Post by alex298 on 2014-12-05
One last thing can you give me an example of how my "edit" line should look prior to me booting the disk, and secondly would this same command work with linux mint?

i am extremely new to the linux world so i would greatly appreciate all the help i can get t make sure i do this properly

---

### Post by ubfan1 on 2014-12-05
The latest recommendations I see look like:
linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- nomodeset
but I think the position used to be with the "quiet splash" (and the -- is a recent addition?).  Sorry I can't try this out and see, so try both.
Certainly the old permanent solution of adding the nomodeset to the /etc/default/grub file on the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
line just after the splash might need adjustment too!
Yes the same thing should work for Mint.

---

### Post by oldfred on 2014-12-05
Not sure if this also applies to AMD or not, but some other settings in UEFI/BIOS like iommu are needed:

 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

---

### Post by alex298 on 2014-12-05
OK nomodeset worked! No let's just hope I can figure out how to update and make everything run they way it needs to. I play diablo 3 religiously is there a good post on here on how to make it run with wine or POL

---

### Post by alex298 on 2014-12-05
It didn't work. It allowed me to install and run Ubuntu on initial start up but once it got going and installed drivers I would reboot just sat on purple Ubuntu splash screen

---

### Post by oldfred on 2014-12-05
I do not know AMD as I have nVidia.

But it seems some AMD work well, other do not work well or can only run the open source driver, or a legacy driver.

       open (Gallium3D) and closed-source (Catalyst) driver

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by fantab on 2014-12-06
> **alex298 said:**
> It didn't work. It allowed me to install and run Ubuntu on initial start up but once it got going and installed drivers I would reboot just sat on purple Ubuntu splash screen
Which driver did you install and how?

---

