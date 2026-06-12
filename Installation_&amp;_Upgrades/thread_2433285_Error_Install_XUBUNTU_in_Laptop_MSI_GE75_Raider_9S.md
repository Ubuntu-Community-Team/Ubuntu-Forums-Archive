---
title: "Error Install XUBUNTU in Laptop MSI GE75 Raider 9SG - HDs not recognized by installer"
date: 2019-12-16
forum: Installation &amp; Upgrades
---

### Post by dr7tbien on 2019-12-16
[SIZE=3][FONT=arial narrow][COLOR=#333333]Hi.

I'm looking for help cause I've been trying to install UBUNTU (Xubuntu, Lubuntu, Ubuntu ...[SIZE=3]) [/SIZE][/COLOR][/FONT]next to a windows[FONT=arial narrow][COLOR=#333333][SIZE=3] on a[/SIZE]n **MSI GE75 Raider 9SG laptop** for days. 

I am trying to install from a bootable USB. The problem is that the USB installer does **not recognize** the internal hard drives of the notebook. It only recognizes the installer's own USB device (16Gbs) and calls it **[FONT=courier new]/dev/sda1[/FONT]**.[/COLOR]

It is possible to see it in the following image. This is the final result of the installation, where it only allows the option to see the USB device. It does not give options to see other devices or install UBUNTU in a place other than[/FONT][/SIZE][COLOR=#333333][FONT=Ubuntu][FONT=courier new]**[SIZE=3]/dev/sda[/SIZE]**

[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][URL="https://i.ibb.co/7jK9yJz/instalacion-0-1280x720.jpg"]
[/URL][/FONT][/COLOR][IMG]https://i.ibb.co/7jK9yJz/instalacion-0-1280x720.jpg[/IMG][COLOR=#333333][FONT=Ubuntu]

[SIZE=3][FONT=arial narrow]The basic specifications of the laptop manufacturer are:[/FONT][/SIZE][/FONT][/COLOR][SIZE=3][FONT=arial narrow]
[COLOR=#333333]
Brand: MSI
Model: GE75 Raider 9SG
CPU: Up to 9th Gen. Intel® Core &#8482; i9 Processor
CHIPSET: Intel® HM370
MEMORY TYPE: DDR4-2666 - 64Gbs[/COLOR]
[COLOR=#333333]
Many tutorials coincide on the following points:[/COLOR]
[COLOR=#333333]- Remove safe mode at system startup
- Suppress quick start
- Suppress hibernate mode[/COLOR]
[COLOR=#333333]
All this I have already done and the result is always the same: It only recognizes the installation USB itself. [/COLOR][COLOR=#333333]I attach different screenshots of the BIOS, current partitioning that I have and the final window where only the device is seen on /dev/sda[/COLOR]
[/FONT][/SIZE][COLOR=#333333][FONT=Ubuntu][URL="https://i.ibb.co/58xZ1nr/BIOS-0-1280x720.jpg"]

[/URL][/FONT][/COLOR][IMG]https://i.ibb.co/58xZ1nr/BIOS-0-1280x720.jpg[/IMG]




[IMG]https://i.ibb.co/0JVsmqB/BIOS-2-1280x720.jpg[/IMG]



[IMG]https://i.ibb.co/Zf05ZZQ/BIOS-3-1280x720.jpg[/IMG]





[IMG]https://i.ibb.co/dcjJJ8F/BIOS-5-1280x720.jpg[/IMG]


[IMG]https://i.ibb.co/mqHZjTq/particionado-0-1280x720.jpg[/IMG]



[IMG]https://i.ibb.co/FKY36fh/botones-0-1280x720.jpg[/IMG]



[SIZE=3][FONT=arial narrow][COLOR=#333333]Thanks in advance, Emilio[/COLOR][/FONT][/SIZE]

---

### Post by oldfred on 2019-12-16
I do not know RAID and it looks like you have RAID 0.
Generally RAID 0 is not recommended. It was used for those who have no data on system, but use it for games or compiling software from a server as striped HDDs were faster than one HDD. Now NVMe drives are faster.
A few break RAID, but that destroys all current data. You have to have good backup to restore to one drive, it that is an option for you.

Desktop installer does not have RAID drivers.
You can try the server installer and when it gets to installing software, you can install desktop & software you want, not necessarily all the optional server software.
       [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

I do not think any of these were RAID 0.
       MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues) & 
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)
MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)

---

