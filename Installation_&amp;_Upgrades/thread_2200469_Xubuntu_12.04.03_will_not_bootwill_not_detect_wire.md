---
title: "Xubuntu 12.04.03 will not boot/will not detect wireless connections"
date: 2014-01-19
forum: Installation &amp; Upgrades
---

### Post by mister_t2 on 2014-01-19
Hello!  The upshot: I have installed but cannot boot Xubuntu, and I also cannot detect wireless internet connections from within any live Linux session I have tried on this computer.  Details:

I am attempting to set up a dual-boot scenario with Windows 8.1 (preinstalled) and Xubuntu 12.04.03 (64-bit), on a Toshiba laptop with an AMD Quad-core processor and UEFI.  After a few false starts and many tutorial articles I completed Xubuntu's installation process by running it in live mode with no error messages or problems. 

I then tried to add Xubuntu to the boot menu with EasyBCD 2.2, but when I try to load Xubuntu instead of Windows it says that "the application or operating system could not be loaded because a required file is missing or contains errors."  It says the problem file is \NST\AutoNeoGrub0.mbr and the status is 0xc000007b.  Windows still loads and runs fine.

I tried to fix this by running Boot-Repair from a live DVD, but it said that I needed to connect to the internet before continuing the process, or my computer will be rendered unbootable -- and unfortunately I cannot find any wireless connections from inside the live Boot-Repair session (I have the same connectivity issue from the live session of Xubuntu).

I have seen several articles and forum posts that describe similar/related issues, but I just can't get over the hump here.  Any help or advice would be greatly appreciated!

---

### Post by mister_t2 on 2014-01-20
Fixed the boot issue by 'converting Ubuntu into legacy mode' as described on [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).  Boot-Repair returns an error message when I do this, and in order to switch between Windows and Xubuntu I have to go into the UEFI settings when I boot the computer, but it's a totally workable solution.  Still figuring out the internet connectivity side but I'll mark this thread solved and post another connectivity-related question later if necessary.

---

