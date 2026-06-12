---
title: "Ubuntu installation on a portable USB hard drive &amp; Grub2 boot manager"
date: 2015-03-26
forum: Installation &amp; Upgrades
---

### Post by neb8 on 2015-03-26
Hello,

I'm trying to create a Ubuntu 14.04 usb drive installation that can be used from multiple PCs.

The problem I'm having is the Ubuntu external USB drive installation is only capable of booting from the original installation PC.
___

(history of the installation)

Ubuntu version 13.02 was originally installed to an external usb drive from Windows using wubi. Once booted Ubuntu version 13.02 was eventually upgraded to version 14.04. 

The PC's internal hard drive has Windows XP installed on drive C. The wubi installer added a file named wubildr.mbr to the root of drive C which is referenced to from the boot.ini.

I've tried copying Windows boot.ini and the wubildr.mbr from the installation PC drive C: to a second identical PC, hardware and bios without any success. The Ubuntu USB drive boots to a Grub2 terminal when connected to any other PC than the original install PC.
____

The Ubuntu installation seems to have modified the internal C: drive's mbr and somehow has become a requirement to boot Ubuntu.

I'm still reading about the different types of Linux boot loaders available and wondering if it would be better to re-install grub2 or switch to another boot manager?

Ideally I would like to be able to boot to any PC capable  of running the Ubuntu 64 bit installation.

---

### Post by dino99 on 2015-03-26
wubi was an experiment and is no more used/maintained since a while.

better to make a real install from scratch    [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
to remove wubi, follow [http://askubuntu.com/questions/144237/how-do-i-uninstall-ubuntu-wubi](http://askubuntu.com/questions/144237/how-do-i-uninstall-ubuntu-wubi)

---

### Post by yancek on 2015-03-26
> 
I'm trying to create a Ubuntu 14.04 usb drive installation that can be used from multiple PCs.

That can certainly be done.  You can either use software such as unetbootin or pendrivelinux (and others) to install to a flash/usb drive.  This would be a Live CD with which you can also ceate persistence to enable you to modify it and save changes.  Another option is to just do an actual complete install to the usb drive of Ubuntu.  If you don't install proprietary drives, this should not be a problem although your graphics may not be up to par if you have certain graphics cards.

As indicated above, wubi is not longer supported but that type of installation requires a windows system in which to install Ubuntu as a program with Ubuntu.  Using wubi puts an entry in the boot.ini file so windows bootloader can access the Ubuntu system.

---

### Post by hakuna_matata on 2015-03-26
> **neb8feo said:**
> 
I've tried copying Windows boot.ini and the wubildr.mbr from the installation PC drive C: to a second identical PC, hardware and bios without any success. 

There is a third file wubildr which contains a lot of necessary GRUB modules.
> **neb8feo said:**
> 
Ideally I would like to be able to boot to any PC capable  of running the Ubuntu 64 bit installation.

wubildr uses GRUB modules for 32 bit BIOS mode. i.e. You cannot use it in UEFI mode but a 32 bit GRUB loader can boot into 64 bit installations, too. 

It is also possible to boot a Wubi installed Ubuntu with GRUB without Windows but ...

... if you have an external drive for Ubuntu it is easier to install Ubuntu without Wubi on your external drive. If you need a Windows boot entry in BIOS mode for Ubuntu you can use programs like EASYBCD: [https://neosmart.net/wiki/easybcd/dual-boot/linux/ubuntu/](https://neosmart.net/wiki/easybcd/dual-boot/linux/ubuntu/) -> Chapter "Adding Ubuntu to the Windows Bootloader" STEP 2,3,4, for all other steps  I recommend a newer Ubuntu how-to because how-to for 10.04 is outdated.

---

### Post by neb8 on 2015-03-26
I appreciate the links and information. 

It would have been much easier to have installed from a DVD or usb stick. I don't have any spare DVD's and both my 32 GB USB sticks went south. Which is the only reason for the wubi install.

 I have performed Linux installs in the past from a USB flash and DVD drive. 

 However, after spending hours installing and configuration of other programming for this particular installation, I would prefer to try and modify or replace the existing boot strapping and boot manager.

Any modifications to drive C's mbr should be repairable from Windows recovery console using fixboot and fixmbr and apparently wubi Windows installation can be easily removed.

  I'm mainly looking for suggestions, ideas and technical details about replacing the  boot manager for the current installation and usb drive.

The wubi boot loader apparently installs onto the windows drive. If wubi can be cleanly removed and another boot loader/manager added to the usb Ubuntu drive would solve the problem. I can see why wubi was discontinued as it potentially cripples an Ubuntu installation if the Windows drive or partition is damaged or removed.

---

### Post by grahammechanical on 2015-03-26
I think that you misunderstand the nature of a wubi.exe installation of Ubuntu. It runs inside Windows as if it is a Windows application. You have set aside the external USB disk as the location of Ubuntu but it is actually very much a part of the XP installation on the original PC. There must be some files in the Windows installation of the original PC that are referenced by the Ubuntu boot loader (Grub). These files tell Grub where to find Ubuntu. These files need to be on the second PC.

The reason you are getting the Grub terminal is because Grub cannot find some of the information it needs. And it cannot find the information because it is not been copied from the original XP to the second PC.

This is a forum for users of Ubuntu. As I understand it one of the reasons for not giving support for wubi installations is the fact that there are very few forum mebers with experience of wubi. I doubt very much if the kind of support that you require is available here. This is why the recommendation to make a true portable installation of Ubuntu onto the external USB drive with its boot loader in the MBR of the drive is the best advice.

Regards.

---

### Post by neb8 on 2015-03-26
> **grahammechanical said:**
> I think that you misunderstand the nature of a wubi.exe installation of Ubuntu. It runs inside Windows as if it is a Windows application. You have set aside the external USB disk as the location of Ubuntu but it is actually very much a part of the XP installation on the original PC. There must be some files in the Windows installation of the original PC that are referenced by the Ubuntu boot loader (Grub). These files tell Grub where to find Ubuntu. These files need to be on the second PC.

The reason you are getting the Grub terminal is because Grub cannot find some of the information it needs. And it cannot find the information because it is not been copied from the original XP to the second PC.

This is a forum for users of Ubuntu. As I understand it one of the reasons for not giving support for wubi installations is the fact that there are very few forum mebers with experience of wubi. I doubt very much if the kind of support that you require is available here. This is why the recommendation to make a true portable installation of Ubuntu onto the external USB drive with its boot loader in the MBR of the drive is the best advice.

Regards.

I would think being unable to boot Ubuntu is a Ubuntu issue. I've been working with PCs for more than 30 years before there was a GUI and DOS and helped to create support for PC's and their operating systems. I don't really see this as particularly a wubi issue, which can be easily removed. It's more of a boot strapping problem I'm trying to resolve and obtain some suggestions, information about installing a boot manager to a Ubuntu drive.

---

### Post by oldfred on 2015-03-26
I use grub for everything, but that may be part of knowing enough about grub to be dangerous and like having only a hammer everything looks like a nail.

You can directly boot wubi from grub. You have to mount NTFS partition and loopmount the root.disk file.

I do not know nor suggest continuing to use wubi. Better to use live installer with extra space for saved data, or an external drive.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

No idea if any of this still works:
HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

.meiefra was one of the developers of the bootinfoscript, still used in Boot-Repair and may have just been proving an issue. He knows the inner workings of Linux/Ubuntu very well, but has not been active in forum lately.

---

### Post by neb8 on 2015-03-26
Ok, thanks. I recently installed supergrub and will try to work out a solution. I consider bootstrapping and boot loaders more as a bios and hard drive issue. Involving application  software and guis sometimes prohibits both understanding and resolve of certain types of issues and problems with lower level functions, especially if the software is unable address certain issues and problems.

---

### Post by hakuna_matata on 2015-03-26
Maybe helpful: The default boot sequence of Wubi boot loader is:

wubildr.mbr -> wubildr -> /ubuntu/disks/root.disk -> /boot/grub/grub.cfg within (/ubuntu/disks/root.disk)

if  /ubuntu/disks/root.disk doesn't exist -> /ubuntu/install/boot/grub/grub.cfg
if /ubuntu/install/boot/grub/grub.cfg doesn't exist -> /grub.cfg

If wubildr (without suffix .mbr) doesn't exist, it doesn't work. Are you sure that you copied a file **wubildr**? You didn't mentioned it.

---

### Post by oldfred on 2015-03-26
If you have grub2 installed.

 wubi direct boot on first drive second partition or sda2 or hd0,2

```
menuentry "Wubi" {
insmod ntfs
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
 set root=(loop0)
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
initrd /initrd.img
}

```
I have installed grub to NTFS, FAT32 & Linux formatted partitions, so it works just about anywhere.

---

