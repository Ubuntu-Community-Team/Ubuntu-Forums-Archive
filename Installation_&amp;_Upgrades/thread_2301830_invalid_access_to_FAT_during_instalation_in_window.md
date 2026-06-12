---
title: "invalid access to FAT during instalation in windows boot partition"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by glorfindus on 2015-11-05
Hallo,

When I try to install ubuntu 15.10 on my dual boot pc I get the following error (at the middle to end of installation):

Ubuntu Kernel [.......] FAT-fs (sda2): error, invalid access to FAT (entry ......)

Sda2 is the partition of my windows boot manager, the error also occurs  when I don't override this partition and choose another partition as  location for grub.
The message is constantly repeated and the ...... part changes.
The grub of my previous installment of ubuntu was removed when upgrading  to windows 10 and reinstalling grub didn't work, so I reinstalled  ubuntu.
I install using usb pendrive Linux and have already installed Linux  using the same image (usb unchanged), later I have also recreated the  image from the iso. 
My computer is a lenovo y50. 

Any help would be much appreciated.

---

### Post by yancek on 2015-11-05
Probably the best step to take is to get the boot repair software, download it and run the script form your Ubuntu installation medium.  Is windows 10 installed in MBR or UEFI?  Ubuntu and windows need to be both the same.  Select the option to Create BootInfo Summary with boot repair should give that and much other pertinent info.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by glorfindus on 2015-11-08
Boot-repair asked for disabling of secureboot. I didn't want to do that unless there are alternatives, so I reinstalled and upgraded windows first. After that installing Ubuntu worked fine. 

Thank you for your time.

---

