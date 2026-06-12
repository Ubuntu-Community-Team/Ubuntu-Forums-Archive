---
title: "Unable to install GRUB alongside Windows 8.1"
date: 2018-10-25
forum: Installation &amp; Upgrades
---

### Post by tetraspore on 2018-10-25
Hello!


I'm trying to install Ubuntu Budgie 18.04.1


Everything goes well with the installer except for the part where it must install GRUB. I get the following error:


    Unable to install GRUB in /dev/sda
    Executing `grub-install /dev/sda` failed.
    This is a fatal error.


I've read that this may have something to do with Fastboot, Secureboot, and UEFI Bios settings, however I have both Fastboot and Secureboot disabled, and my motherboard supports both UEFI and Legacy options. I've tried installing both from a Live USB (Try Budgie before installing) and the installer (Install Budgie), both yielding the same result. I've tried using the "Install alongside Windows" option as well as trying to set it up my partitions manually with "Something else" to no avail. I'm trying to install from a USB stick to my SSD as I don't have a disc drive, and it appears to be trying to install to the proper drive and not trying to install to the flash drive (I read that was an issue for some people). Could someone help me pinpoint exactly what's wrong here? Willing to run whatever diagnostics necessary. 


Thanks!

---

### Post by yancek on 2018-10-26
I would suggest that you read the Ubuntu documentation on dual booting UEFI with windows at the link below.  Also, which version of windows are you using?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If the information at the link above does not help to resolve your issue, go to the site at the link below for boot repair, download and run it according to the instructions on the page.  Make sure you do NOT try to make repairs but select the option to Create BootInfo Summary.  When it finishes, it will give you a link to post here and someone should be able to suggest a possible solution.  When you download boot repair, use the 2nd option with the ppa.  You can do this from the Ubuntu install DVD/usb.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

