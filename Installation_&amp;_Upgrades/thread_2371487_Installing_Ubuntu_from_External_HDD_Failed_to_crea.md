---
title: "Installing Ubuntu from External HDD Failed to create kernel channel 22"
date: 2017-09-15
forum: Installation &amp; Upgrades
---

### Post by cptscragglybeard on 2017-09-15
Tried the 16LTS and then the 17 both give same error. Followed instructions in the guide to make the external HDD bootable.
Using an Alienware 17 R4
GTX 1070.

From looking at other posts im pretty sure the issue lies with the graphics card. Cant simply unplug as others have :(. Tried nomodeset however this brings me to a black screen which lets me type but no responses when I hit enter. Unsure what to do next.

Thanks for your time in this matter.

---

### Post by ajgreeny on 2017-09-15
Are you trying to install **from** a hard disk or to install **to** a hard disk?  I'm confused as it sounds as if you have installed but can not get it to boot.

What instructions did you follow that have not succeeded, and tell us more about your hardware and system setup; RAM, CPU, BIOS or UEFI, etc etc?

---

### Post by oldfred on 2017-09-15
Need to know answers to  ajgreeny's questions.

Somewhat older model:
 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr) 

UEFI may be similar to Dell. 
Dell usually has RAID on and has to be reset to AHCI for drive(s). And it seems to be the only one that wants Legacy/CSM/BIOS mode on, even to install in UEFI mode. Most with that on, only install in BIOS mode.

How you boot install media UEFI or BIOS is then how it installs.
For more info on UEFI install see link in my signature below.

---

### Post by cptscragglybeard on 2017-09-15
I have the Ubuntu 17 iso on a 1TB external(USB3.0) HDD. I followed this instruction set [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop?_ga=2.160797685.993593352.1505443630-749660695.1505443630#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop?_ga=2.160797685.993593352.1505443630-749660695.1505443630#0). I also used the included tutorial on how to make a bootable USB/HDD using Rufus. I have a partitioned internal HDD (190 GB) which I would like to install Ubunto to.

16GB Ram
CPU I7-7820K
BIOS: 1.1.8
OS Windows 10
GPU GTX 1070

---

### Post by oldfred on 2017-09-15
Have you updated UEFI from Alienware to latest version.
Do you have SSD and if so updated firmware for SSD?

Have you turned off RAID?

Use Windows to shrink the Windows NTFS partition and make unallocated space for Ubuntu.
Best to use Something Else install option.

 MBR(for BIOS) or gpt(for UEFI) partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

        Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You will need nomodeset for nvidia.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 



 Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 


[URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by cptscragglybeard on 2017-09-15
ok so I replaced the quiet splash with nomodeset and that allowed me to run Ubuntu. Still ran into some errors with the install but i feel like i can troubleshoot those now. 
The initial time i tried nomodeset the guide i found told me to just add it at the end of the quiet splash line but that didn't work. With the initial issue resolved I will close this "ticket" Thank you.

---

### Post by oldfred on 2017-09-15
Glad you got it working. 
You can change to solved.

If further issues start a new thread with that issue in title.

Bit surprised that replacing quiet splash worked where adding it did not.
I normally suggest replace, most suggest adding it & I thought either worked.
I prefer not to have the quiet splash just to see what system is doing.

---

