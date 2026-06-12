---
title: "The OS installation book menu order is lost when the files and folders where moved"
date: 2021-12-06
forum: Installation &amp; Upgrades
---

### Post by kalaiarasiperiyasamy on 2021-12-06
The Ubuntu OS is installed by default directly as Folders, files on the drive itself.  Can ubuntu create a Root folder or UbuntuOS folder and install all files related to the OS into it.  I happen to move the files manually into a folder by the ubuntuos thus leading to situation where the Boot Menu option and the order of Boot, the Entry for Ubuntu boot option in the HP Boot manager order bios setup was also lost.  Evert time the user has to use the EMI file and navigate to the system information ubuntu folder and the to shimx64.*** file to boot the ubuntu OS, but the default boot order goes missing?   How to retrieve or readd the entry?  Does this require a repair package option or reinstall?

Can the Ubuntu OS be by default installed into a Root folder name UbuntuOS20.04 folder or Root?

---

### Post by tea for one on 2021-12-06
It is not clear what you want to do exactly?
Therefore can you supply some clarification?
> **kalaiarasiperiyasamy said:**
>  I happen to move the files manually into a folder by the ubuntuos 
Which files do you move?
Where to?
> **kalaiarasiperiyasamy said:**
> the user has to use the EMI file
What is an EMI file?

---

### Post by yancek on 2021-12-06
Ubuntu and other Linux systems are installed in the / (root) directory of any linux system, symbolized by "/".  What files are you moving, from what location to what location?  Do you mean EFI files used to boot?

---

### Post by grahammechanical on 2021-12-06
The Linux boot loader (called Grub ) looks for boot files in a certain partition (EFI partition). The Linux/Ubuntu installer knows this and puts the relevant boot files (EFI boot files) in that partition. If you have moved those files to a folder in another partition then the Grub boot loader cannot do what it is designed to do. The UEFI settings utility is expecting to see those kind of files in the EFI partition.

There is a program designed to correct boot problems and it fixes things by re-installing Linux/Ubuntu EFI boot files into the EFI boot partition. The user is then instructed to set the UEFI settings to boot from the EFI boot file in the EFI partition.

I imagine that the UEFI settings utility and the Grub boot loader have been designed to limit user interaction in order to simply and automate boot loading. But just in case there are boot problems the user is allowed a certain access in order to continue using the machine. If Grub was loading but not finding the Linux kernel then Grub would offer a command line where the user can direct Grub to the location of the Linux kernel. A lot of thought has gone into designing the operation of computers. 

Regards

---

### Post by yancek on 2021-12-07
You seem to lack an understanding of the basic layout of a Linux system.  The forward slash ( / ) is the symbol for the root of the entire system.  If you open a terminal and run this simple command, it will show the root or base of the Linux system:

```
 ls /
bin    dev   lib    libx32      mnt   root  snap      sys  var
boot   etc   lib32  lost+found  opt   run   srv       tmp
cdrom  home  lib64  media       proc  sbin  swapfile  usr
  
```

The entire system will be in these directories or in sub-directories of those shown.  If you have an EFI system, you will see the proper EFI files located in the /boot/efi/EFII partition which it seems you are referring to?  You need to clarify what exactly you did and what you intended to accomplish by doing so.

---

