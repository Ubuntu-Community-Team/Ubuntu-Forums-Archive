---
title: "grub rescue"
date: 2018-06-15
forum: Installation &amp; Upgrades
---

### Post by abenardis on 2018-06-15
hello i install 18.04 the grud2 failled install, i took boot-info if someone can help me

[http://paste.ubuntu.com/p/pGSzkVfQbF/](http://paste.ubuntu.com/p/pGSzkVfQbF/)


thanks

---

### Post by yancek on 2018-06-15
Your boot repair shows at the very top of the page that the Grub bootload code is installed in the MBR of the drive.  That is correct.  THe problem you can see just below that is that it is looking for the remaining boot files needed by grub on (mdsos7 or sda7) which does not exist.  The boot repair output does not show any Grub menu (grub.cfg file) which is needed to boot although it does show another Grub file.  Not sure how all this happened as I've never seen anything like this before.

Do you have an installation of windows 7 or some other windows (sda2)?
The Grub bootloader did not install properly and the suggested repair would install it's file on sda5 where your Ubuntu actually is.  If this is a new install, it might be easier to re-install and make sure you install Ubuntu to sda5 and Grub to the MBR (/dev/sda).

---

### Post by abenardis on 2018-06-16
I was have 16.04 with win10 (sda2), I update at 17 but it was very slow in my system and try to down back to 16 and from that time it start the problem I try to install 18 and the same problem,

---

### Post by abenardis on 2018-06-16
i try one more time with manual partition again th same
[http://paste.ubuntu.com/p/Vd6DcH2Z3Y/](http://paste.ubuntu.com/p/Vd6DcH2Z3Y/)

---

### Post by yancek on 2018-06-16
Reviewing your last boot repair output, you stilll have not properly installed the Grub bootloader.  Not sure what you are doing but you have a number of Linux partitions but none show the Grub boot files.  Best to just do an install of the system to one partition (sda5) and install Grub to the MBR.  YOur boot repair output once again shows Grub code in the MBR but it is pointing to the swap partition (sda7) for the other Grub files which will not be there.  Take a look at the link below which has detailed instructions including images on installing with windows in Legacy mode.  You can just do an online search for dual booting windows 10 and Ubuntu in Legacy mode if you need more instructions.  There are a lot of sites available.

[https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/](https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/)

---

### Post by oldfred on 2018-06-16
You are showing you booted Ubuntu installer/Boot-Repair in UEFI mode & have UEFI hardware.
But both Windows install & Ubuntu install are in BIOS boot mode with MBR partitioning. Usually better to use UEFI with newer UEFI hardware, but that would require backup,  total erase of drive and reinstall of systems & data. 
So always boot in BIOS boot mode.

Also in BIOS boot mode you must have boot flag on the NTFS boot partition with Windows boot files, your sda1. Did you delete a small 100MB Windows boot partition at beginning of drive?
Windows needs boot flag to know partition to boot from or repair. Grub does not need boot flag as it just looks for the Windows boot files and will boot Windows. But grub only boots working Windows and a Windows 10 update will turn fast start up back on. Then you have to directly boot Windows.

With UEFI you can directly boot Windows from UEFI boot menu. But with BIOS you have to temporarily reinstall a Windows BIOS boot loader to MBR, boot Windows, repair Windows and then use Boot-Repair to restore grub to MBR to boot both systems.
Be sure to keep both a Windows repair flash drive and the Ubuntu live installer which you can add Boot-Repair to reinstall grub or make other Linux repairs.

You can use gparted or your Windows repair disk or installer (make active in Windows) to add boot flag to sda2.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by abenardis on 2018-06-18
all ok i fixed, with a lot of try boot with win usd in prompt i fix mbr and bootsector and after that rescue gone and i install 18,04
thanks

---

