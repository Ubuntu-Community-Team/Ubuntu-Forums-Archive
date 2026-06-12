---
title: "Ubuntu installation for a Windows 8 pre-install"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by erikthedrink on 2013-04-08
I need to know the step by step details on how to install either 12.04 or 12.10 on a system with Windows 8 pre installed. I have already disabled the secure boot. I tried using wubi yet to no avail. Should I create a live DVD with all files. Last time, I only placed the install file on the DVD.:confused: I have followed the directions and did the longer secure download on 12.10 and burned it onto a disk. Even after changing the boot order to start with the cd/dvd drive, it still won't load. I can't find where to disable the SRT in BIOS or UEFI. I have an HP Pavilion gt6

---

### Post by erikthedrink on 2013-04-09
Tried to switch to legacy, only to find out I have been using DVDRs to make a startup disk. The system says they are not bootable. Due to the file being larger than 700 MB, I could not use a CDR. What I am doing wrong?

---

### Post by erikthedrink on 2013-04-09
Not even a USB drive is recognized with the secure 12.10 iso file. It read 'Missing operating system', while it recognized the USB flash drive was connected. What gives?

---

### Post by oldfred on 2013-04-09
Please do not ask same question in two threads. I posted this in your other thread. Most find flash drive works better, but not all flash drives seem to work.
       Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

    

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

      
 Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by erikthedrink on 2013-04-09
64 bit -- Been using it the whole time. Boot using a dvd, didn't work. Yes, I changed the boot sequence to do internal cd/dvd rom drive first and then USB drive and then OS boot. Neither on the DVD nor the USB drive, does it recognize the file as an operating system. I just got this system built and shipped to me, straight from China, yesterday. Maybe Windows figured a new way to disclude Ubuntu?

---

### Post by erikthedrink on 2013-04-09
BTW, I love the Ubuntu system. Windows 8 is even worse in functionality than Windows 7. I can increase the delay to boot the OS. Right now, it's at 10 seconds. The file, which I have on both the DVD and the USB flash drive is linux-secure-12.10-64bit. Is there something I am missing?

---

### Post by erikthedrink on 2013-04-09
I know where Secure Boot is and disabled it. I do not know where Quick or Fast Boot is located. Yet I can increase the delay to boot the system.

---

### Post by erikthedrink on 2013-04-09
Increased the boot delay to 20 seconds, where it maxes out. Copied the .iso to hard drive, and then burned the image to a fresh DVD. I thought this would do it. Nope. I heard and felt the system cycling the cd/dvd drive and reading the dvd for about five seconds. It still doesn't boot. Is there a way to install the system while Windows 8 is open?

---

### Post by erikthedrink on 2013-04-09
Turned out, I needed to use the how to install a USB boot drive guide, then download the disc image from ubuntu, then load both onto my USB drive. Once it was downloaded, I needed to re use my usb install to 'try ubunutu' and use the tips on how to install the 'boot repair.' Works great now.:P

---

