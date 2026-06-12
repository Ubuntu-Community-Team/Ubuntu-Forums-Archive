---
title: "How to install Ubuntu in another Drive than Windows ?"
date: 2016-03-08
forum: Installation &amp; Upgrades
---

### Post by Samjazz on 2016-03-08
Hello Everyone,

I'm Samjazz, Gamer and a new Ubuntu user (i mean i will be one :roll:) and i'd like to have some support to begin the experience of ubuntu instead of Windows.

My friend told me to choose Mint but it looks like windows and i want something new with the biggest support population

First of all my config :
[I]CPU : I7 4790k
RAM : 16 Go
GPU : Geforce 780
SSD 840 pro : for windows 
HDD 1 : 1TO Data
HDD 2 : 500 GO with **[COLOR=#ff0000]256Go for Ubuntu[/COLOR]**[/I]

I tried yesterday to make an installation via USB BOOT (i used Universal-USB-Installer-1.9.6.3) and when i runed the installation everything was good except when i wanted an installation with dual boot option, it didn't let me to choose the disk.

I want to install ubuntu in another disk (256Go) and I'm wondering how to do it ? which systeme files shoul i choose (ext4, ntfs, fat32 ... )? the swap is it mendatory ? :confused::confused:

Can someone give me the right step to make it easy for me :)

Thank you all

---

### Post by slickymaster on 2016-03-08
Hi Samjazz, welcome to the forums.

I'm moving your thread to the **Installation & Upgrades**&#8203; sub-forum, which is the proper venue for it.

---

### Post by grahammechanical on 2016-03-08
There is a Ubuntu family of distributions that are all supported on this forum. So, we have choice and we can download and try a live session to see what suits us.

When we start the installation process we get these options.

1) Install Ubuntu Alongside them [that is other operating systems]
2) Erase disk and Install Ubuntu
3) Encrypt the new Ubuntu installation for security
4) Use LVM with the new Ubuntu installation
5) Something else - create & resize partitions yourself or choose multiple partitions for Ubuntu.

Which option did you choose? Do you want to dual boot with Windows? What version of Windows? Does the motherboard have a BIOS or a UEFI boot system?

If you chose Install Ubuntu alongside windows you should see dialogs like these.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)


Take note of image #5 Begin the installation. Do you see the panel at the top of the window? The one labelled Select Drive? That has a small down pointing arrow. click on that and you should be able to change the drive that Ubuntu is going to be installed on.

We get a similar option when we choose the Something Else option. But the dialog and the process is a little more complicated. With the Install Alongside & the Erase disk & install Ubuntu options we do not have to worry about which partitions to install Ubuntu in and what format (it is usually EXT4 by the way) or mount  points. That is all taken care of.

A swap partition will automatically be created by the installer unless we are using the Something Else option. With 16 GB of RAM you may never make use of swap unless you intend to hibernate Ubuntu. Then you will need a little more than the amount of RAM.

If you intend to install using the Something Else option then lets us know as you may need advice particular to that way of installing.

Regards.

---

### Post by Samjazz on 2016-03-08
Thank you for the reply,

When i arrive to the step of the image #5 i wasn't able to change the drive. It just show me the SSD where the windows is installed and i don't want to install it in the same drive.

At this point i selected Something Else and here are the probleme ... what should i do here ?

PS : i guess it's preferable to have dual boot to be able to choose between windows and ubuntu but if there is a bette way ... please tell me :)

---

### Post by Geoffrey_Arndt on 2016-03-09
The ubuntu disk (sda or sdb - - you need to find the right label) should be formatted to ext4 (a linux filesystem).   ALso, be sure Windows fast startup/hibernation is "disabled" . . . turned off.   Do both these things, and the installer should see both drives.

---

### Post by mastablasta on 2016-03-10
To get the alongside option there should be unformatted disk space available. and if you have MBR, then you have to make sure you do not have 4 primary partitions on the disk. if you do, you need to change one into secondary (extended).

> **Samjazz said:**
> 

I want to install ubuntu in another disk (256Go) and I'm wondering how to do it ? 

choose something else. set partitions / and /swap into the free disk space and continue with install. make sure you put the grub in the right place (can still be fixed later).
> 
which systeme files shoul i choose (ext4, ntfs, fat32 ... )?  

definitely not NTFS or FAT32! since it's your first time, use the default file system ext4.
> 
the swap is it mendatory ? :confused::confused:


not in your case (plenty of RAM). however having a little bit swap is always good and since you have plenty of disk space it should be a problem. set it to 4 GB. Swap is kind of like pagefile in windows. it is used when the ram runs out or when you hibernate the PC. you can then set "swapiness" - ie. when swap is accessed. since you have plenty of ram you can set it to access it when RAM is 80 % or 90% full for example.

---

