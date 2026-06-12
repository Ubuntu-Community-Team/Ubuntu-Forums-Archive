---
title: "Ubuntu install locks up/More info"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by magpie03 on 2014-08-13
Please read this post very carefully. People are answering my previous post asking questions that are answered in my orginal post. Please no more links to dual boot problems as I cannot even get to the main desktop. Great thanks to oldfred and others I have them all bookmarked and well read. I think this may be a "shim" problem but I am totally lost. 

Downloaded Ubuntu 14.04.1 and MD5sum is ok. Using Unetbootin I created a bootable USB drive. I changed "quiet splash" to "nomodeset". Booted up and choose try Ubuntu. It locked up during loading. Please see screen picture. I read that Unetbootin has problems with UEFI, so I made another USB with Start Up Disk creator. That also locked up during loading. Please see screen picture again. I then made a DVD and booted from that and it also locked up during install. Please see screen picture again. I made a bootable USB with Boot Repair in case I needed it, and that also locked up during install. Please note that I waited at least 5 minutes every time to see if it would contiue but it would not and the keyboard was locked up.

Toshiba Satellite C855d-S5201  <-- Bios is current. No update available.
Windows 8 preinstalled then upgraded to Windows 8.1
Secure boot disabled  <--Note: I tried enabled also 
Boot mode UEFI Boot
AMD Dual-Core E1-1200 Accelerated Processor
AMD Radeon™ HD 7310 Intergrated Graphics
4GB DDR3 1600MHz memory
640 GB HDD   <--Note. Set aside 100GB for Ubuntu
I have three sets of hard drive backups made in case of problems.

Ubuntu will boot with UEFI disabled but all info I have read says that the modern distro will boot and should be installed in UEFI mode. Is it possible that this laptop cannot run Ubuntu in UEFI mode? Should I try another distro or drop down to Ubuntu 13? Any advice on how to procede will be greatly appreciated.

Many thanks all,
magpie

---

### Post by fantab on 2014-08-14
> Ubuntu will boot with UEFI disabled but all info I have read says that  the modern distro will boot and should be installed in UEFI mode. Is it  possible that this laptop cannot run Ubuntu in UEFI mode? Should I try  another distro or drop down to Ubuntu 13? Any advice on how to procede  will be greatly appreciated.


It is quite possible that your laptop's OEM UEFI firmware has issues and its not uncommon. There are several buggy UEFI firmware out there.

You can actually boot Ubuntu in 'Legacy/CSM mode... but since you have Win8 in UEFI, you will have to manage this from UEFI menu by disabling UEFI when you need Ubuntu and enabling UEFI when you need Windows.

You should also try distros and see how they fare... try Fedora and/or OpenSuse etc. As for Ubuntu versions try 12.04 and 12.04.5 and they can be found [here]("http://releases.ubuntu.com/"). Also try the latest development version 14.10, its daily build can be downloaded from [here]("http://cdimage.ubuntu.com/daily-live/current/").

---

### Post by magpie03 on 2014-08-14
Thank you fantab. I'll try the other distros as you suggest.

---

