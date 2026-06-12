---
title: "Error when trying to dual boot windows 10 and ubuntu 18.04."
date: 2018-07-05
forum: Installation &amp; Upgrades
---

### Post by Oreo100 on 2018-07-05
I have been attempting to dual boot my dell xps 15 9570 with ubuntu 18.04. However, after trying to boot from a usb and selecting "Install Ubuntu" it gets stuck on the loading screen at the last dot. I have already updated my bios but this hasn't worked. Any help would be much appreciated.

---

### Post by yancek on 2018-07-05
Dual boot with what?  Do you have some windows version installed?  If so, which version?  Windows 10, have you turned off fastboot and hibernation and created unallocated space on the drive you want to install to using windows Disk Management, if you have windows?

---

### Post by Oreo100 on 2018-07-05
Dual Boot with windows 10, and I have done all of those things.

---

### Post by oldfred on 2018-07-05
Have you updated UEFI from Dell? And if NVMe SSD, the firmware for it?
Also are you using nomodeset, if nVidia card/chip?

       Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en)
 Dell 9570 No nvidia Driver working - only one kernel version seems to work?
[https://ubuntuforums.org/showthread.php?t=2392938](https://ubuntuforums.org/showthread.php?t=2392938) 
    
Issues are most common by vendor, so similar models have similar issues.
       Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[URL="https://ubuntuforums.org/showthread.php?t=2345444"]https://ubuntuforums.org/showthread.php?t=2345444

      [/URL] At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 
    [URL="https://ubuntuforums.org/showthread.php?t=2345444"]
[/URL]

---

### Post by yancek on 2018-07-05
Did you verify that the download was not corrupted, see link below?

[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu?_ga=2.137508787.2093109034.1530823014-1455427143.1529748621#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu?_ga=2.137508787.2093109034.1530823014-1455427143.1529748621#0)

Did you read the Ubuntu documentation on dual booting with windows 10, see the link below?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Oreo100 on 2018-07-05
It isn't allowing me to add in nomodeset as it goes straight to the ubuntu loading screen where it freezes.

---

### Post by oldfred on 2018-07-05
If booting with UEFI, you press escape key between UEFI screen and before grub menu. May have to press more than once.
Also if fast boot in UEFI is on, you may not have any time to press any keys, so make sure it is off.
Fast boot in UEFI, is different than fast start up (hibernation) in Windows.

---

