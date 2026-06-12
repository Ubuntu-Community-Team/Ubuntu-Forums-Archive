---
title: "Ubuntu third party software and secure boot."
date: 2017-06-28
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2017-06-28
Why is with Ubuntu 17.04 install asking for a password to disable secure boot, when I select to install third party software.  I thought for some time now that Ubuntu was compatible with uefi/secure boot. my old laptop had uefi and legacy, and so does my new laptop.  But after 4 years of using legacy I want to use uefi/secure boot.

Henry.

---

### Post by oldfred on 2017-06-29
Proprietary drivers for video or WiFi are binary blobs, not supported directly by Ubuntu.
So Canonical cannot sign those drivers.

If you want UEFI Secure Boot, you can use all open source drivers.

Not sure how Windows does it, or if they have permissions from vendors.
There are some improvements in grub that may solve some of the issues.

---

### Post by Hewjr100 on 2017-06-29
Ok thanks. I guess I will thry to install it with third party software un-checked.

Henry.

---

### Post by Hewjr100 on 2017-06-29
Update. I was unable to dual boot Windows 10 and Ubuntu 17.04.  So I switched back to Legacy/Bios and erased everything and installed Ubuntu 17.04.  Other than Gufw, is there anything esle I can install to protect Legacy/Bios system.

Henry.

---

### Post by oldfred on 2017-06-29
You may mis-understand UEFI Secure Boot.
That is currently just Microsoft marketing. And eventually we may want it.

If you have an operating system that is in the news all the time about security issues, what better than to market this new "UEFI Secure Boot" system. But that has nothing to do with most Windows virus' which are in operating system, not in boot process.

Most well known boot virus was actually from Sony trying to prevent all computers from running Sony music.

 Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security 

UEFI with gpt has a lot of other advantages.
      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Hewjr100 on 2017-06-29
I understand what you are saying, but actually my motivation is quite simple.  It is just a matter off wanting to use what is available to me, in this case uefi/secure boot.  My old laptop had it but it was easy to use with linux.  Now that I have a more modern/updated system I feel that I should be able to use it to its fullest capabilities.

Henry.

---

### Post by oldfred on 2017-06-29
Then you can contact nVidia and suggest they work better with the open source community.
They actually are better than they used to be and are cooperating on improving the open source driver.

---

### Post by Hewjr100 on 2017-06-29
Actually you make a valid point, case at hand, When I got this laptop and installed Ubuntu 17.04 I opted to use propriety nvidia driver and upon reboot got the black screen of death.  So yes I am going to start with an email to nvidia and go from there.

Henry.

---

### Post by Hewjr100 on 2017-07-03
Oldfred, if your out there I was wondering if I could install Ubuntu with third party software unchecked, and then activate it after installation is done.  Hopefully this will avoid Ubuntu from asking to disable secure boot.

Henry

---

### Post by oldfred on 2017-07-03
I do not think you can work around the limits. The binary blobs have to be incorporated into the kernel. And the Secure boot kernel is different as it is signed.

---

### Post by Hewjr100 on 2017-07-03
Ok, so I can install without third partysoftware, and do not activate after install.

Henry.

---

### Post by Hewjr100 on 2017-07-03
Well I installed Ubuntu without third party software, but when I rebooted it went to windows.  Next I rebooted and hit F9 to select boot order and I found two entries one for windows and one for Ubuntu.  I was not going to keep hitting F9 to boot either or,so I reinstalled Ubuntu and erased everything.  Works fine.  Will not use non free or multiverse repos.  Don't need them anyway.

Henry.

---

### Post by Hewjr100 on 2017-07-03
OK, I just decided to wipe the disk and install Ubuntu, without third party software/drivers.System still set tu Uefi/Secure boot.  Install and reboot went fine.  Was able to install Gparted, Lm-Sensors, Bleachbit, and Google Chrome and Unity tweak Tool and rebooted without issue.  Aslo checked do not use Nvidia drivers or Intel drivers.  Did select using X.org X server. rebooted and all is well.

Henry.

---

