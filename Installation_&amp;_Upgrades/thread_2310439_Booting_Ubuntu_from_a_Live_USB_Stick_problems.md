---
title: "Booting Ubuntu from a Live USB Stick problems"
date: 2016-01-19
forum: Installation &amp; Upgrades
---

### Post by abstract2 on 2016-01-19
Trying to Install Linux on a Live USB Drive and having no luck whatsoever, not sure if Linux Is up to date with Drivers as it is a newer Laptop or not but first here are the specifics

CPU 6th Gen i7 3.5Ghz 
RAM 16GB DDR3
Video NVIDIA GTX 960
Windows 10

Versions Tried
Ubuntu 14.04 x64 & x86
Mint 17.3 (Cinnamon) x64 & x86

Software Tried 
Rufus
PendriveLinux
LiLi USB Creator

So I have tried going at this from Booting it from the USB to Emulating it through Virtual Box neither method works, In the Bios I have the following Options

Intel Speedstep
Virtualization
VT for direct I/O
Integrated NIC
USB Emulation
USB Powershare

and under the Boot Tab I have the following
File Browser add Boot Option
Secure Boot
Load Legacy Boot Option Rom

I have tried Disabling all of them and trying to boot in Legacy Mode with "File Browser add Boot Option" pointed at boot/grub/efi.img as well as autostart.ini 

with both Mint & Ubuntu the USB flashes for a brief moment then the computer continues to load Windows

When using Virtual Box Option with LiLi USB Creator, the OS begins to load then the following Errors continue endlessly


96.#######] ata1.00: status: { DRDY ERR }
96.#######] ata1.00: error: { IDNF }
96.#######] ata1.00: configured for UDMA/33
96.#######] sd 0:0:0:0: [sda] FAILED Result: hostbyte=DID_Ok driverbyte=DRIVE


Anyone have any Idea of how I can go about getting around this and getting a Live USB stick working so I can use linux for a few things? Better yet if someone can point me to a Tutorial that takes Windows 10 and Newer Hardware into consideration that would be great as well.

Thanks

---

### Post by mörgæs on 2016-01-19
15.10 is worth trying. Here is some experience for a (more or less) similar processor:
[http://ubuntuforums.org/showthread.php?t=2307234](http://ubuntuforums.org/showthread.php?t=2307234)

---

### Post by yancek on 2016-01-19
You have windows 10 installed so it is probably using UEFI.  I would suggest reading the Ubuntu documentation below before beginning.  If you have windows UEFI, you must boot and install Ubuntu UEFI.  Disable anything relating to fastboot and hibernation first.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2016-01-19
> **mörgæs said:**
> 15.10 is worth trying. Here is some experience for a (more or less) similar processor:
[http://ubuntuforums.org/showthread.php?t=2307234](http://ubuntuforums.org/showthread.php?t=2307234)

It's probably that, but might be Skylake rather than Haswell (although I think the Skylake 6700 i7 is 3.6). If Skylake, that has a few differences, which you probably know more about that I. :)

---

### Post by Tod Merley on 2016-01-19
Not all flash drives allow booting.  You might try another drive.

---

### Post by Tod Merley on 2016-01-19
Also you might have better luck to install Ubuntu to the drive.  I like to use gparted to shrink the existing partition from the back leaving the front of the drive untouched.  You will often see several megabytes which look unused at the front of the drive - which - actually contain optimization data and other firmware handles.  The drive will work without them most of the time but may slow considerably.

If you do this be sure that the flash drive is selected to be where the boot loader lands.  You do not want the MBR of the computer drive to tell you to boot to the flash drive after all.

---

