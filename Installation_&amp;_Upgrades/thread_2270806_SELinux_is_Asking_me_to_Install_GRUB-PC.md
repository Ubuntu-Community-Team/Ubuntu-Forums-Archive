---
title: "SELinux is Asking me to Install GRUB-PC"
date: 2015-03-25
forum: Installation &amp; Upgrades
---

### Post by Allister_Graham on 2015-03-25
I installed SELinux from the terminal in Ubuntu 14.10, and everything seemed to be going wellm until it asked me to configure/install GRUB-pc.
I know what GRUB is, but I obviously already have it installed.
The SELinux installer has now presented me with a menu with the following information:-

[B]Package Configuration
[/B]
[CENTER][B]Configuring grub-pc
[/B][/CENTER]
GRUB install devices:
[ ] /dev/sda
[ ] /dev/sda1

I have GRUB (and Ubuntu) installed on /dev/sda, so do I select it?

---

### Post by oldfred on 2015-03-25
If terminal then you typically use tab, spacebar & enter to choose.

Normally you install grub2 only to the MBR of a drive or sda, sdb, etc. And grub2 does not fit into a partition boot sector like sda1, so it has to convert to block lists.

But if you have grub installed with your first install you may or may not want this newer grub to be in control of boot process. Whichever system you will use the most should be the one in the MBR and control boot of all systems. But whichever system you install last is usually the one you install to MBR.

If you do not want SELinux to control boot, install to partition more as a throw away. And then boot into Ubuntu and run sudo update-grub and it will find the new install and add it to the grub menu.

Some other options are to turn off os-prober and manually add your own boot entry to boot another system using the link to newest kernel. That avoids the issue of having to boot Ubuntu and run update-grub everytime SELinux gets a new kernel.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

If you have installed wrong grub, you can easily reinstall grub from your other install, just by booting into it and installing grub to MBR.
      
 sudo grub-install /dev/sda

But each install may have saved hard drive entry on where to reinstall grub on major update. Or other install may convert install to its version of grub.

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

