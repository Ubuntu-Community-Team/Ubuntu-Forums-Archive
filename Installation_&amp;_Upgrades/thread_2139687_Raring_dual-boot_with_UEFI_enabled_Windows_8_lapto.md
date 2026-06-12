---
title: "Raring dual-boot with UEFI enabled Windows 8 laptop?"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by bjmatakaetis on 2013-04-27
Hello.

I wanted to dual boot my Samsung laptop with Ubuntu. Is it possible? If so, how?

-BJ Matakaetis

---

### Post by oldfred on 2013-04-27
Is this Windows 8 pre-installed so it has secure boot? And is it an UltraBook which has even more things to reconfigure?

       You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 


 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

### Post by bjmatakaetis on 2013-04-27
Yes, Windows 8 was pre-installed. No, it's not an UltraBook, but it does have touchscreen.

I thought Ubuntu was capable of resizing the partition itself?

-BJ Matakaetis

---

### Post by oldfred on 2013-04-27
While Ubuntu can resize partitions, some have reported issues using Linux tools. Also with Windows 8 always hibernated, that can cause issues.
So we normally say to use Windows tools for Windows & Linux tools for Linux. 

Windows does have to run chkdsk after any resize, so best to resize from Windows and then reboot so it can make its repairs to its new size.

---

