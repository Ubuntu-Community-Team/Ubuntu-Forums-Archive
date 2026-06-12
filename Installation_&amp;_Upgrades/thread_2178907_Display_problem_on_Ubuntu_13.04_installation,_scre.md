---
title: "Display problem on Ubuntu 13.04 installation, screen goes"
date: 2013-10-05
forum: Installation &amp; Upgrades
---

### Post by Skerdi on 2013-10-05
Hello everyone !

Thanks for taking the time. I bought a new laptop a few weeks back and have been so far unable to install my favorite OS.

Here are the steps followed so far
1) Picked the laptop :
Asus J450F, quad core i7 4700 HQ Haswell, Nvidia GT745M, Windows 8 pre-installed on the internal HDD drive with a separate empty partition (vendor config). I aim to install Ubuntu on the empty partition without mowing the entire hard drive, given that no CD was supplied to reinstall Win 8.
2) Downloaded the Ubuntu 13.04 x86_64 .iso and burnt it into a DVD-R (too big for my CDs).
3) Put the LiveCD into the DVD drive and restart.
4) Enabled boot from DVD in the BIOS
5) Selected option 1 "Try Ubuntu without installing" (also tried with option 2, same thing).
6a) Pressed enter, the screen went black and nothing happened for hours.
6b) Pressed "e", the following instructions appeared :

set gfxpayload=keep
linux        /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
linux         /casper/initrd.lz

7) Replaced "splash" with "nomodeset" or "casper quiet splash" with "nomodeset" and pressed F10 to resume : the screen also went black.


The way I understand it is that I have to disable my Nvidia GT graphics card and use the intel integrated graphics instead for the install to work.
The threads I found were about custom built desktop computers where as a fix the GC was physically disconnected for the OS installation. I'm not too keen on doing that for my laptop.
The F2 grub command line works (it is displayed properly), although I am very unfamiliar with it.


Any advice would be much appreciated.

Best,

---

### Post by oldfred on 2013-10-06
The few that have posted with the very new Haswell based systems have found 13.10 to work better even though it is still beta (soon to be released). The new 13.10 has newer kernel & Intel video drivers that work with the Haswell based systems. I also think the newest nVidia drive needs the newest kernels also.

I am not sure what version you downloaded. With UEFI you have to have the 64 bit AMD version, not the 32 bit i386 version.

Lots of links to installing with UEFI with screenshots in link in my signature.
Be sure to create Windows repair flash and backups including efi partition.

While Toshiba, an example of Haswell.
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by Skerdi on 2013-10-10
13.10 solved the issue. Thanks !

---

