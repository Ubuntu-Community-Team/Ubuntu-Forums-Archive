---
title: "No bootloader"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by bullinchinashop on 2006-10-17
I just reinstalled Ubuntu 6.06 for the third time and it still refuses to install or offer any kind of bootloader. Grub was not installedautomatically (It didn't even try) and it doesn't give me an opportunity to install it myself. The Ubuntu system itself installs fine. but when I reboot when it tells me to I go straight to Windows (XP). I'm using 1 drive seperated into 3 primary partitions. 1 NTFS for Windows 1 (I've tried ext3 reiser fs and xfs) for linux and another smaller partition for linux swap.
Slackware 11 installed fine with this set up (LILO included - installed to MBR of Windows partition). I even sat in front of the computer the last 2 times and stared at the monitor waiting for it to say anything about a bootloader.

---

### Post by Herman on 2006-10-18
Hello bullinchinashop,
> I just reinstalled Ubuntu 6.06 for the third time and it still refuses to install or offer any kind of bootloader. Grub was not installedautomatically (It didn't even try) and it doesn't give me an opportunity to install it myself. The Ubuntu system itself installs fine. but when I reboot when it tells me to I go straight to Windows (XP). I'm using 1 drive seperated into 3 primary partitions. 1 NTFS for Windows 1 (I've tried ext3 reiser fs and xfs) for linux and another smaller partition for linux swap. That is very strange. Have you taken the extra time to verify the integrity of your CD? Perhaps there is some physical damage on the CD disk, or maybe an error in the downloading or burning of the .iso file to CD. 
In any case, I recommend [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"), which is free, and only a 541 kb download. If you burn that to a CD, it will boot Ubuntu or any other operating system for you, including Windows. It can even boot any Linux system or other operating systems (except Windows), without any bootloader installed at all. Then once you have it booted, you may be able to see what's wrong and repair it more easliy that any other way.

I have installed Grub successfully in ext2fs, ext3 and reiserfs filesystems, but I'm not sure if Grub likes xfs or not. Maybe it's okay, I haven't tried it, if you are not sure, you should check. I think I remember reading that Grub doesn't go in a jfs or xfs filesystem. I think people who want one of those filesytems for '/' (root) use a seperate ext2fs for /boot.
> Slackware 11 installed fine with this set up (LILO included - installed to MBR of Windows partition). I even sat in front of the computer the last 2 times and stared at the monitor waiting for it to say anything about a bootloader. There is a popular misconception that the MBR is in the Windows partition.

 The MBR is not part of the Windows partition.  

There is a boot sector at the beginning of each partition. One for each operating system.
There is one MBR in the first sector of each hard disk, it is entirely seperate from any filesystem. It does not belong to any operating system at all.
If you did install a Linux bootloader to a Windows partition I imagine it would most likely ruin your Windows install. However, *Ubuntu does not install Grub to the Windows partition at all*. Grub's 'IPL' (Initial Program Loader), will be installed to the hard disk's Master Boot Record (MBR).
It may seem like a trivial point to you, I know it's not the main point of your post, but I want to make that clear for the benefit of others who might happen to read this post, I wouldn't want them to be misled.

Regards, Herman  :D

---

### Post by danbuffington on 2006-10-20
Mine is doing the same thing. I did check the disk for errors, and there was nothing reported as missing. 

I have a 120gb primary drive, with a 40gb drive slave with XP. After I install Ubuntu 6.06, it boots directly to Windows. I find it strange because the Windows install is on the slave drive.

Any other solutions?

---

### Post by confused57 on 2006-10-20
> **danbuffington said:**
> Mine is doing the same thing. I did check the disk for errors, and there was nothing reported as missing. 

I have a 120gb primary drive, with a 40gb drive slave with XP. After I install Ubuntu 6.06, it boots directly to Windows. I find it strange because the Windows install is on the slave drive.

Any other solutions?
I'm assuming both drives are connected to the same IDE controller, Ubuntu as master and Windows as slave.  Is your bios set to boot the master drive as the first hard drive in the boot order?

---

### Post by Herman on 2006-10-20
>  Any other solutions?Yes, check your cmos and see if there is any MBR protection or anti (bootsector) virus active in there that could be blocking Grub from writing it's IPL code to the MBR.
Links on BIOS and CMOS, 
[CENTER][BIOS (Basic Input / Output System)]("http://webpages.charter.net/netw_1/bios.htm")[/CENTER]
    
   [CENTER][The Definitive BIOS Optimisation Guide]("http://www.adriansrojakpot.com/Speed_Demonz/BIOS_Guide/BIOS_Guide_Index.htm")

[LEFT]I hope that will be helpful to you, if it's not that then we'll need to do more troubleshooting, butyou should at least be able to boot it with a Super Grub Disk, (for now), because that can still boot Linux without any Grub at all, if you at least have a kernel and an initrd.img
Regards, Herman :D

[/LEFT]
[/CENTER]

---

### Post by danbuffington on 2006-10-21
> **confused57 said:**
> I'm assuming both drives are connected to the same IDE controller, Ubuntu as master and Windows as slave.  Is your bios set to boot the master drive as the first hard drive in the boot order?

My bios is set to boot from the hard drive, but it doesn't allow me to select which one. I'm booting off of the same IDE. I have installed several different distros with no trouble. I keep coming back and trying Ubuntu, but honestly, don't have the user friendly experience that's supposed to exist.

This is important to me, because I want to use linux on all of my company desktops. I wonder if there could be something wrong with the iso I downloaded. None of the mirrors should be different than the others though. I don't know....

---

### Post by confused57 on 2006-10-21
You could try the Super Grub Disk "howto" on Herman's website:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Here's an iso download & burn "howto" for Ubuntu:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

If you went through the installation process without any error messages, the iso is "probably" not the problem.

The Super Grub Disk is only about a 500 kb download, but you may be able to boot Ubuntu with it...if you can, we'll go from there to come up with a solution.

You might also want to boot with the Desktop live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

it would probably be helpful to post the output of the above command.
I won't be able to help you anymore tonight, but there are plenty of experienced people who can, most notably Herman.

---

### Post by adrian15 on 2006-10-23
> **bullinchinashop said:**
> I just reinstalled Ubuntu 6.06 for the third time and it still refuses to install or offer any kind of bootloader. Grub was not installedautomatically (It didn't even try) and it doesn't give me an opportunity to install it myself. The Ubuntu system itself installs fine. but when I reboot when it tells me to I go straight to Windows (XP). I'm using 1 drive seperated into 3 primary partitions. 1 NTFS for Windows 1 (I've tried ext3 reiser fs and xfs) for linux and another smaller partition for linux swap.
Slackware 11 installed fine with this set up (LILO included - installed to MBR of Windows partition). I even sat in front of the computer the last 2 times and stared at the monitor waiting for it to say anything about a bootloader.

Using Super Grub Disk Boot Linux option inside Linux menu does it boot your Ubuntu ?

adrian15

---

### Post by gn2 on 2006-10-23
> **danbuffington said:**
> Mine is doing the same thing. I did check the disk for errors, and there was nothing reported as missing. 

I have a 120gb primary drive, with a 40gb drive slave with XP. After I install Ubuntu 6.06, it boots directly to Windows. I find it strange because the Windows install is on the slave drive.

Any other solutions?

Here's a suggestion for you: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

