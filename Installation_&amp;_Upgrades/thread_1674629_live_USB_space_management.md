---
title: "live USB space management"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by yndesai on 2011-01-24
Friends  . . 

I have created ubuntu 10.04 live USB from the Live CD. I have got 8GB USB Stick.  It worked gr8. To keep the live USB up-to-date and install additional softwares; I kept 2GB under "Stored in reserved extra space".

I did all the security upgrade and installed needed additional software. This amounted to about 502 MB download. (I do not have data on what would be its size when installed as I currently have backed up cache\ of apt folder)

Now I am getting error that there is hardly any disk space available. I  removed a big ticket items like deleted the cache for apt. I removed "ubuntu-docs" using synaptic package manager  this as per the info must have freed 270 MB. But alas ! I do not see this freed space in the live usb.

Can any one point out how the disk space is managed under live USB mode. . .

My disk usage analyzer gives following output

total 6.0GB 
cdrom 2.2 GB - 36.1%
rofs 1.7 GB - 29.2%
usr 1.6 GB - 26.6%
var 236.7 MB 3.9%
lib 117.0 MB 1.9%
and so on . . .

Can any one explain what happens when I install / remove packages from live usb where the disk space have gone . Also is there a way to flush some temp data from live user session . . 

Thanks and advance.

yndesai

---

### Post by xgt001 on 2011-01-24
I think u must uninstall some unused software so as to free space... remember that the pendrive uses FAT32 still as its a liveboot. Not quite sure but i faced similar issue .... try removing the apps or rerun the usb-creator application and allocate twice-thrice the space u need. that is to say if u plan to use the pendrive for 2 gb allocate 4 gb while creating startup disk.... try this...and pls do reply if u experience similar issues

---

### Post by yndesai on 2011-01-24
Thank you , I am going to try the same as it came first to my mind. But as you can see removing some apps did not freed any space so I wondered what is happening. 

Will surly post my experience with added space installation. I am also trying my hand on remastersys to see if I can remaster current usb session and then add the space while re-installing. As while remastering there is a scope to flush temp files.

---

### Post by C.S.Cameron on 2011-01-24
Doing updates and upgrades to a Live USB persistent install quickly fills the casper-rw file. When this file is full the drive will no longer boot.
The kernel is part of a squashfile and can't be upgraded.

If you want a pendrive with all the latest updates do a full install to the pendrive.

Following step by step for Full install of 10.10 to USB device, adjust partition size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by yndesai on 2011-01-27
[C.S.Cameron]("http://ubuntuforums.org/member.php?u=317145")

Thanks for your help.  Since I use Laptop I will need to take care while installing on usb disk. 

I understand that due to multiple write cycles the usb drive has issues.
[http://en.wikipedia.org/wiki/Live_USB#Full_install](http://en.wikipedia.org/wiki/Live_USB#Full_install)

But finally I could not understand why I was not able to create space in liveUSB ie  casper-rw file
even after removing heavy packages. . . !

---

### Post by C.S.Cameron on 2011-01-27
> **yndesai said:**
> [C.S.Cameron]("http://ubuntuforums.org/member.php?u=317145")

Thanks for your help.  Since I use Laptop I will need to take care while installing on usb disk. 

I understand that due to multiple write cycles the usb drive has issues.
[http://en.wikipedia.org/wiki/Live_USB#Full_install](http://en.wikipedia.org/wiki/Live_USB#Full_install)

But finally I could not understand why I was not able to create space in liveUSB ie  casper-rw file
even after removing heavy packages. . . !

With data leveling a flash drive is good for 10000 writes, at 5MB/s a 8GB drive will last years of full time use.

---

### Post by yndesai on 2011-01-28
[]("http://ubuntuforums.org/member.php?u=317145")Awaiting reply on ;

> **yndesai said:**
> 
But finally I could not understand why I was not able to create space in liveUSB ie  casper-rw file
even after removing heavy packages. . . !

---

### Post by C.S.Cameron on 2011-01-28
To access casper-rw:

[http://ubuntuforums.org/showpost.php?p=7055983&postcount=2](http://ubuntuforums.org/showpost.php?p=7055983&postcount=2)

---

### Post by yndesai on 2011-02-06
> **C.S.Cameron said:**
> To access casper-rw:

[http://ubuntuforums.org/showpost.php?p=7055983&postcount=2](http://ubuntuforums.org/showpost.php?p=7055983&postcount=2)

Well I could use
```

sudo mount -o loop /cdrom/casper-rw /media/casper/

```to mount the casper-rw

but the surprise is the size of the casper-rw file is 1.5GB but 
once mounted the folder it shows total of only 916MB.

---

### Post by yndesai on 2011-04-06
> **C.S.Cameron said:**
> With data leveling a flash drive is good for 10000 writes, at 5MB/s a 8GB drive will last years of full time use.
Taking your advise I have now I have made a full install on the usb . .

---

### Post by C.S.Cameron on 2011-04-06
If your drive bricks please let us know
In am convinced a drive with a full install will last years and that if it does fail the data on it will remain readable.

---

### Post by yndesai on 2011-12-07
I have created the live USB using UNETBOOTIN and it is creating the bootable usb which is also allowing the installation of new software and file storage.

This seems to be good solution .

---

