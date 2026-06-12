---
title: "Ubuntu Studio 12.10 with Windows 8"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by Nicole Sharp on 2013-02-24
I cannot install Ubuntu Studio 12.10 64-bit on Windows 8 Pro 64-bit with UEFI.  I cannot run the live DVD or install from disc, nor install from Wubi.EXE.  I have secure boot disabled and have tried installing it both with UEFI and from legacy boot with UEFI disabled.  I am currently on a GPT partition table with Windows 8 using three partitions (but it did not install on MBR either).  When trying to run the live DVD, I get a blank black screen.  I was not able to load nomodeset per [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) though not sure if that is the issue.  I would like to set up the computer for dual-boot with both Windows 8 and Ubuntu Studio on separate partitions (but Ubuntu Studio on NTFS Wubi is fine too).

---

### Post by oldfred on 2013-02-24
Welcome to the forums.

You cannot use wubi with gpt partitions, so with Windows 8 pre-installed with UEFI you have to have gpt partitioning.

I do not know if Studio includes the UEFI boot capability. It is only in some versions.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 

Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
You will need Boot-Repair to fix some issues.

Use Windows to shrink the Windows partition, but not to create any new partitions.

---

### Post by Nicole Sharp on 2013-02-24
I have a GPT partition table with the first three partitions being created by the Windows 8 installation (the C drive followed by two small partitions less than 300 MB) and then 100 GB of unallocated space reserved for the new Linux partition.  I am using an HP laptop with AMD graphics, manufactured in 2012 with Windows 7.  Secure boot is disabled.  On booting up, I hit ESC to go to boot options, select boot from disc (with UEFI enabled), whereupon the screen flashes that secure boot is disabled and it goes to the options for run live disc, install Ubuntu Studio, etc.  Either running live or installing though both proceed to the blank screen.  I had the same result with legacy boot and UEFI disabled though, as well as trying with MBR instead of GPT (I reset using a GPartEd live CD).
 
Might the issue be then with Ubuntu Studio 12.10?  I haven't tried the Ubuntu 12.10 disc yet.  I have a strong preference for Ubuntu Studio because even though you can install the Ubuntu Studio packages on Ubuntu, I like the XFCE+Nautilus work environment.  Ubuntu defaults with GNOME and if you then add XFCE to it and log in under the XFCE GUI, the Nautilus filemanager doesn't seem to play well with XFCE/Thunar.

---

### Post by Nicole Sharp on 2013-02-24
I just tried the Ubuntu Desktop 12.10 64-bit DVD and had the exact same issue. According to [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) the CD is definitely booting in EFI mode with the text menu to try or install Ubuntu instead of the graphic menu ("Identifying if the Computer Boots the CD in EFI Mode"). Legacy mode and secure boot are both turned off in the BIOS. There is an EFI partition created by Windows 8 as well as a small similar-sized "recovery" partition also for Windows 8 (I believe it is used to recover the EFI partition should it become unusable), in addition to the Windows OS partition and the unallocated space.
 
Pressing F6 at any point doesn't bring up any menus or change anything. The Ubuntu disk is good since I've used it before on an older system.

---

### Post by oldfred on 2013-02-25
With the text mode does e work to edit the grub menu like you do when you first boot after an install?

Then you should be able to add nomodeset to linux line.

---

### Post by Nicole Sharp on 2013-02-26
#Ubuntu webchat was able to help resolve the issue.  The problem was not with Windows 8 or UEFI but rather the graphics card.  Upon booting the disc, I hit "e" and entered "nomodeset" after the text "quiet splash".  After that, everything went normal.  After installing though, it would still load the blank screen when trying to boot Ubuntu Studio from BIOS boot options.  I selected boot from EFI then went through the menu system to find the GRUB EFI file to boot where I was again able to hit "e" and use "nomodeset".  After logging in, I switched the graphics driver from the open-source fglrx to the proprietary AMD driver which solved the problem.
 
However, I would still like to see Ubuntu listed in the Windows bootloader (alongside Windows 8 and Windows 7, both installed) instead of having to hit ESC on powering on and then selecting Ubuntu through the BIOS boot options.  Is there an easy way to do that?

---

### Post by oldfred on 2013-02-27
Windows will not show grub/ubuntu.

Grub's menu should give you a correct entry to load Windows if you run Boot-Repair.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I have not used and do not recommend EasyBCD. But supposedly it was just updated to work with UEFI.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Nicole Sharp on 2013-02-28
Yes I saw a blog where the author had Windows 8 and Ubuntu both listed together in the Windows 8 bootloader (with the fancy graphics).  I think they were using EasyBCD, but the instructions looked very complicated and I'd probably mess up my system trying.  Was hoping for something quick and easy.  Maybe the Ubuntu or GRUB teams will have a patch to install on Windows 8 to add it when 13.04 comes out.

---

