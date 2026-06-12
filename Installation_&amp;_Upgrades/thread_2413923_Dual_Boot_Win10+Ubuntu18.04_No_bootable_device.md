---
title: "Dual Boot Win10+Ubuntu18.04 No bootable device"
date: 2019-03-04
forum: Installation &amp; Upgrades
---

### Post by avsarria on 2019-03-04
I have been trying to setup dual boot on my Asus NX500J. I'm using Rufus v3.4 to create a bootable drive with GPT and UEFI as target system. I install Windows 10 and use Windows Disk Management to shrink the partition for Ubuntu 18.04. Once Windows 10 is installed, I use Rufus again to create a bootable drive for Ubuntu 18.04 but with MBR partition scheme and BIOS or UEFI as target system (those settings are automatically selected by Rufus. Then I boot into my Ubuntu usb and install Ubuntu. I select the option "Something else" to create a swap partition of 16GB to match my RAM size and the rest for /. After installation is complete, I try to reboot my laptop and it just boots into BIOS. In the Boot section, there is no device available to boot from. It seems as if my hard drive is gone. If I insert a USB drive I can boot from it and reinstall Windows or Ubuntu, but I want to fix whatever the problem is. I can't seem to find a solution. Does anyone have any ideas? Thank you!

---

### Post by yancek on 2019-03-04
Boot the Ubuntu usb and open a terminal and type in the following command, post the output.  That's a lower case Letter L in the command.  THis will show drives/partitions and filesystem types on your system.

```
sudo parted -l
```

Did you read the Ubuntu documentation at the link below on dual booting windows 10/Ubuntu?  If not, do so.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-03-04
UEFI and BIOS are not compatible.
UEFI just has the old BIOS/Legacy/CSM mode for some users who want all systems the same (typically large companies with many old systems).
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
You can dual boot when not in same boot mode, but only from UEFI, not from grub menu as once you start boot in one mode you cannot switch.
Best to always have all systems in same boot mode, both UEFI is recommended, if UEFI hardware.

Ubuntu now does not need a swap partition. It uses a swap file. But if a swap partition is found it will use it.

---

