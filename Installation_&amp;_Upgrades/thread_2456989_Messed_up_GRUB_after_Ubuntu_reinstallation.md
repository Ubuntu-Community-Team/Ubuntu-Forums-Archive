---
title: "Messed up GRUB after Ubuntu reinstallation"
date: 2021-01-23
forum: Installation &amp; Upgrades
---

### Post by secretgarden2 on 2021-01-23
Hello guys!
Here is my problem, any help would be much appreciated!
I had Ubuntu 20.04 and Windows 10 dual boot. Then one day I was updating Ubuntu to 20.10 version but during the process a power outage happened which messed up the system.
Soo from GRUB menu I was still able to boot either Windows or Ubuntu. But Ubuntu drops to recovery prompt shell. I tried to fix the system... to no avail.
I've installed a fresh Ubuntu 20.10 from a live USB. Here is my disks setup: a separate physical disk for Ubuntu, a separate physical disk for Windows and a disk for media files which I use on both systems.
I don't know where is my GRUB2 was  installed during the previous Ubuntu installation. 
Now when I want to get into GRUB menu and select an OS to boot, there is a trouble. If I select any of my drives as first priority boot, I got a GRUB message:
```
grub error: disk 'lvid/{%MANY_CHARACTERS%}' not found.       Entering rescue mode..
```
Then if I disable secure boot  in BIOS Settings, there appears an option in BIOS to boot Ubuntu.
I've tried using boot-repair from live USB, no success...
I need to repair my GRUB so that I can boot either Ubuntu or Windows from it. Looking for help.
Sorry for a dummy question, just trying things I googled doesn't work :(
Thanks in advance!

---

### Post by oldfred on 2021-01-23
With multiple drives do not run any auto fix from Boot-Repair.
Only use its advanced mode. And be sure to boot live installer in same boot mode UEFI or BIOS as all of your installs.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by secretgarden2 on 2021-01-23
> **oldfred said:**
> With multiple drives do not run any auto fix from Boot-Repair.
Only use its advanced mode. And be sure to boot live installer in same boot mode UEFI or BIOS as all of your installs.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Here is my summary report:
[https://paste.ubuntu.com/p/TzzdkpvD7c/](https://paste.ubuntu.com/p/TzzdkpvD7c/)

---

### Post by yancek on 2021-01-23
Your boot repair output shows  (beginning at line 27) only Ubuntu EFI files.  Your windows is not installed UEFI.  You can't mix UEFI with Legacy as an EFI install of Ubuntu Grub will not boot a windows in Legacy mode.  The reverse is also true.  You have Grub installed in the MBR of the windows drive which I expect you did when you used boot repair. That was a mistake as your windows code in the MBR of that drive has now been overwritten.  You can use your windows 10 installation media or your Recovery disk with the repair option to install windows boot code to the MBR of the windows drive (/dev/nvme1n1) and you will then be able to select either the Ubuntu drive or the windows drive from the BIOS on boot.   If you want to boot both from Grub, you need to install Ubuntu in Legacy mode.  The Ubuntu documentation on dual booting Ubuntu with windows 10 is at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by secretgarden2 on 2021-01-23
I see, so another mistake I made is installing Ubuntu in UEFI mode while having Windows installed in Legacy mode. I will try out your solution, @yancek! Thanks everyone, I might come back here

---

### Post by oldfred on 2021-01-23
You can dual boot, since each is installed on separate drives. 
But only from UEFI boot menu, not from grub.
UEFI & BIOS are not compatible, and once you start to boot, you cannot change. Or grub can only boot other installs in same boot mode.

Boot-Repair can also install a Windows type boot loader (syslinux) to the Windows drive, using its advanced mode to select Windows & select the MBR of the Windows drive.
But you should have a Windows repair/recovery flash drive to make Windows repairs.

I think the error was installing Windows in the now 40 year old BIOS/MBR configuration with new hardware.
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012 and release of Windows 8.
Users can install in BIOS/MBR mode, but that was primarily kept for those large companies with many systems using BIOS/MBR Windows 7 and wanted same configuration on all systems and/or older hardware only with BIOS.

You cannot easily convert a BIOS/MBR Windows to UEFI/gpt, it will require a full reinstall.
How you boot install media UEFI or BIOS is how it installs.

You can convert Ubuntu install to BIOS boot, if desired. 
You need a 1MB unformatted partition with bios_grub flag on Ubuntu drive using gparted.
Then totally reinstall grub changing from UEFI version of grub to BIOS version of grub. Boot-Repair can do that.

---

### Post by secretgarden2 on 2021-01-25
Thanks a lot! I managed to install Ubuntu in legacy mode and boot either it or Windows from GRUB. Closing the thread

---

