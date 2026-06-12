---
title: "Windows 7 x64 - Install Ubuntu 14.04.3 LTS Install Dual Boot On 2nd Hard Drive"
date: 2015-09-25
forum: Installation &amp; Upgrades
---

### Post by 3lCp on 2015-09-25
Running Windows 7 x64 on my HP notebook with (2) 500 GB hard drives and 8 GB RAM:

OS C: 340 GB free of 450 GB NTFS

D: 179 GB free of 465 GB NTFS

RECOVERY E: 1.56 GB free of 14.4 GB 

HP_TOOLS G: 84.6 MB free of 99.0 MB 

Drive C: is mainly used for OS and some documents while D: contains music, videos, etc. 

I installed Ubuntu OS on USB flash drive and ran from boot menu to test out and now trying to sort through the best installation option(s) for Ubuntu.

Ideally, (I think) I'd like to dual-boot, setup and install Ubuntu to boot from D: drive. I want to make sure I get the drive/partition(s) correct and around the size I prefer (100 - 150 GB total allocated for Ubuntu?) and not risk losing my current data or somehow format the entire drive.

Here's what it looks like from the Ubuntu trial/test version:

ubuntu@ubuntu:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME   FSTYPE     SIZE MOUNTPOINT                     LABEL
sda             465.8G                                
&#9500;&#9472;sda1 ntfs       199M /media/ubuntu/SYSTEM           SYSTEM
&#9500;&#9472;sda2 ntfs       451G /media/ubuntu/OS               OS
&#9500;&#9472;sda3 ntfs      14.5G                                RECOVERY
&#9492;&#9472;sda4 vfat       103M /media/ubuntu/HP_TOOLS         HP_TOOLS
sdb             465.8G                                
&#9492;&#9472;sdb1 ntfs     465.8G /media/ubuntu/AED4ABC5D4AB8E61 
sdc              29.8G                                
&#9492;&#9472;sdc1 vfat      29.8G /cdrom                         UUI
sr0              1024M                                
loop0  ext2         2G /media/ubuntu/casper-rw        casper-rw
loop1  squashfs 962.1M /rofs      

After some reading and a Ubuntu trial from the USB drive, I'm at least getting familiar with the different drive and partition terminology but am not confident I will be able to go through installation with setting up correctly and/or how I'd like.

When I did a test run partially through the install options here's what I get:

Select standard option: "Install Ubuntu alongside Windows 7"

Select Drive: SCSI2 (0,0,0) (sdb) - 500.1 GB ATA TOSHIBA MK5076GS          192.6 GB

Allocate drive space by dragging the slider below:

Files (307.5 GB)
/dev/sdb1 (ntfs)
400.9 GB

Ubuntu
/dev/sdb2 (ext4)
99.3 GB

I don't get a "select drive" option for sda (c) at all, which is fine I suppose since my preference is to install on sdb (d) anyway.
While I can move the slider and set to various sizes, I am not confident (or maybe over-thinking this...) that this will give me what I want in terms of setup/partitions, etc.

When I select "Something else" option:

Device       Type   Mount Point  Format  Size            Used            System

/dev/sda
 /dev/sda1   ntfs                                   208 MB        30 MB         Windows 7 (loader)
 /dev/sda2   ntfs                                   484256 MB   118327 MB  Windows Recovery Environment (loader)
 /dev/sda3   ntfs                                   15532 MB     13800 MB    Windows Recovery Environment (loader)
 /dev/sda4   fat32                                 108 MB         33 MB
/dev/sdb
 /dev/sdb1   ntfs                                   500105 MB    307470 MB

Device for boot loader installation: (dropdown options)

/dev/sda     ATA TOSHIBA MK5076GS (500.1 GB)
/dev/sda1   Windows 7 (loader)
/dev/sda2   Windows Recovery Environment (loader)
/dev/sda3   Windows Recovery Environment (loader)
/dev/sda4
/dev/sdb     ATA TOSHIBA MK5076GS (500.1 GB)
/dev/sdb1

Too many options and not enough knowledge I suppose, so any suggestions on best way to proceed or require more info. It would be appreciated, thanks.

---

### Post by oldfred on 2015-09-25
I would use Windows to shrink the NTFS partition and make free space for Ubuntu. 
And reboot Windows immediately to run chkdsk on resized partition.
The Linux NTFS driver only "sees" NTFS partitions that are working or not hibernated nor needing chkdsk. And chkdsk is always required after a resize.

I prefer something Else if installing to a second drive. All default installs, put the grub boot loader on sda. But you really want to keep the Windows boot loader on sda (more as backup way to boot) and install grub2's boot loader to the drive that is sdb. And set BIOS to boot sdb by default. Grub will then let you boot Ubuntu or Windows.

Default install is / (root) & swap. If allocating more than 30 or 50 GB to Ubuntu, worthwhile to separate data from system and have either /home or data partition(s). For a new user /home is easier to set up as you do that during install.

I also prefer to create partitions with gparted which is like any partitioning tool, but a bit easier to use. You still have to use Something Else to choose(change button) which partition is / & which is /home. If swap created in advance then it auto finds it.

        MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

So you understand Something Else these show the screens, each is about the same, but review a couple.
       
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

           
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

