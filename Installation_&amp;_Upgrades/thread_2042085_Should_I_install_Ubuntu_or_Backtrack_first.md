---
title: "Should I install Ubuntu or Backtrack first?"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by Jt00 on 2012-08-13
I am planning on having a triple boot setup on my laptop with Windows 7 (soon 8), Ubuntu, and Backtrack. I have read up on setting up dual and triple boot systems, and it seems like some operating systems like to replace the existing GRUB with their own bootloader. Both Backtrack and Ubuntu use GRUB for multi-boot installations. Does it matter what order I install them in? Right now the computer only has Windows on it.

---

### Post by oldfred on 2012-08-14
Minor convenience to install the one you want to boot the most, last as its boot loader will be the last one in the MBR and then first on the grub menu.

But you will need to know how to reinstall boot loaders and repair if necessary. You should have a repairCD (Windows) or liveCD/USB for the current version of every system you have installed so you can easily make repairs.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If you can boot into an install, you can easily install its boot loader to the MBR (assumes sda, but can be any drive).
sudo grub-install /dev/sda

Grub2 also remembers where to reinstall if you have major updates. So you may need to run this.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub


#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions. If you do not want it to reinstall to the MBR because you are booting with another install unchoose everything.

---

### Post by Jt00 on 2012-08-14
Thanks! One last question. I thought the Ubuntu iso's had gotten over 700 MB as of Ubuntu 11 (one of the versions of that, anyway) and therefore could not be installed on a CD. However, my Ubuntu torrent has finished downloading and it says the file is 698 MB. Can I still make a Live CD, or is it only bootable USB drives now?

---

### Post by oldfred on 2012-08-14
I installed from a CD to test it, but use flash drives as it is faster. Actually with multiple hard drives now, I install from one hard drive to anther hard drive which is very fast.

This will boot an ISO from a hard drive with grub2 loopmount.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

I also have multiple ISO on one flash drive for repairs.
These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by Jt00 on 2012-08-14
The examples page you linked to says Backtrack 5 only works as a menuentry after modifying the iso, but it doesn't say what kind of modification needs to be made.
I think I will have to make a bootable USB for Backtrack first, then I can try booting Ubuntu from the hard drive, since the process needs at least one linux system on the computer anyway. Even if it could be booted from the hard drive with no modifications, you said I should install the distro I want to boot most, last, and that would be Ubuntu. As nice as Backtrack is, I plan to use my computer more for everyday uses like internet browsing and typing documents than pentesting.

Thanks for your help!

---

