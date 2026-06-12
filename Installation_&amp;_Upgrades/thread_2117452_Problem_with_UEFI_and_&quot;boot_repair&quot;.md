---
title: "Problem with UEFI and &quot;boot repair&quot;"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by brenogalvao on 2013-02-18
Hi all.
I have a Samsung ultra book with windows 8 and the UEFI thing.
I am struggling to get linux working on it and gave ubuntu secure remix a try.

In the BIOS, I disabled "quick boot" and another security thing that wouldn't allow any CD to boot. 
But there wasn't a  "Intel Smart Response Technology (SRT)" option as described here: help.ubuntu.com/community/UEFI

Anyway, it installed okay, but after that I had to open the liveCD and choose "boot repair" two times to make it work (it would show GRUB but not load the system correctly). 
But as soon as I reboot it's not working again, and I have to do a "boot repair" every time I want to turn the computer on. It seems that the MBR is changing every time I open the system (either windows or ubuntu).

Is there a fix for this?

here are the links for Boot repair logs.

paste.ubuntu.com/1669161
paste.ubuntu.com/1672835

Thanks in advance for any help.
Cheers

---

### Post by oldfred on 2013-02-18
You have seen issues with some models of Samsung. But some have installed ok.

       Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

    
Are you booting from UEFI and selecting ubuntu, not letting Windows boot first as then it will still stay as default.

       Protection against Samsung UEFI bug merged into Linux kernel
[http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html](http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html)
Since these patches have not yet been integrated into the installation media for these distributions, users should always use the UEFI firmware's Compatibility Support Module (CSM), which emulates a BIOS mode, when booting on affected laptops. 
The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
    
       UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.

---

