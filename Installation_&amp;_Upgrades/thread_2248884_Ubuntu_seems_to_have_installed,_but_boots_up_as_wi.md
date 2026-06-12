---
title: "Ubuntu seems to have installed, but boots up as windows"
date: 2014-10-17
forum: Installation &amp; Upgrades
---

### Post by Sonuahua on 2014-10-17
Trying to replace XP Home, 2G virtual mem, 3333mhz processor... trying to install Ubuntu 32 bit as sole OS. Using USB boot on my old emachine. I boot using F10 as it requests, it seems to be asking the right questions and I am giving the right answers (I assume).... It gives me a progress bar and appears to be installing, I get a notification that it is completer and that I need to reboot... So I reboot... and Windows loads as usual... is my system too old to carry it?? Or am I doing something wrong??

---

### Post by Sonuahua on 2014-10-17
reading Simricks Posting and replys perhaps I should try a different version of linux, maybe a similar issue

---

### Post by grahammechanical on 2014-10-17
Did you choose the Erase disk and install Ubuntu option? Or Install alongside? Or Something else. I cannot really say what you did wrong because you do not say what your answers you gave. Cannot comment on the hardware because the information is not sufficient. We do not know if the CPU is Intel or AMD. What graphic adapter does the machine have? How much of its own memory does the graphic adapter have? How many partitions?

---

### Post by yancek on 2014-10-17
Might this be a wubi install?  If you just want Ubuntu, the best option is the Erase Disk option.

---

### Post by Sonuahua on 2014-10-17
> **grahammechanical said:**
> Did you choose the Erase disk and install Ubuntu option? Or Install alongside? Or Something else. I cannot really say what you did wrong because you do not say what your answers you gave. Cannot comment on the hardware because the information is not sufficient. We do not know if the CPU is Intel or AMD. What graphic adapter does the machine have? How much of its own memory does the graphic adapter have? How many partitions?

 Yes I chose the erase disk option, it currently has 3 partitions, it was supposed to delete 2 of them on the install

Copy paste System Req...

OS Name    Microsoft Windows XP Home Edition
Version    5.1.2600 Service Pack 3 Build 2600
OS Manufacturer    Microsoft Corporation
System Manufacturer    GATEWAY
System Model    T3508
System Type    X86-based PC
Processor    x86 Family 15 Model 6 Stepping 4 GenuineIntel ~3333 Mhz
BIOS Version/Date    Intel Corp. GC11010M.15A.0009.2006.0420.1045, 4/20/2006
SMBIOS Version    2.4
Windows Directory    C:\WINDOWS
System Directory    C:\WINDOWS\system32
Boot Device    \Device\HarddiskVolume3
Hardware Abstraction Layer    Version = "5.1.2600.5512 (xpsp.080413-2111)"
Total Physical Memory    768.00 MB
Available Physical Memory    112.43 MB
Total Virtual Memory    2.00 GB
Available Virtual Memory    1.96 GB
Page File Space    1.02 GB
Page File    C:\pagefile.sys

Cannot find any info on my graphics card... maybe that is my issue....

---

### Post by Sonuahua on 2014-10-17
> **yancek said:**
> Might this be a wubi install?  If you just want Ubuntu, the best option is the Erase Disk option.

Yes Wubi on the bootable USB

indeed, I was surprised to see windows boot-up after it was supposed to be erased

---

### Post by Sonuahua on 2014-10-17
I may have found the issue, system report says there is only 524mb ram, that maybe too small

Perhaps a smaller flavor, Lubuntu or Puppy?

---

### Post by yancek on 2014-10-17
Wubi is not supported any longer although it is still available.  It might work??  Lubuntu, Puppy and AntiX are options that will run with that RAM.  Also check the link below for other options.

[http://distrowatch.com/search.php?category=Old+Computers](http://distrowatch.com/search.php?category=Old+Computers)

---

### Post by Vladlenin5000 on 2014-10-18
> **Sonuahua said:**
> I may have found the issue, system report says there is only 524mb ram, that maybe too small

Small indeed according to current standards but not the issue.

---

### Post by Sonuahua on 2014-10-18
> **yancek said:**
> Wubi is not supported any longer although it is still available.  It might work??  Lubuntu, Puppy and AntiX are options that will run with that RAM.  Also check the link below for other options.

[http://distrowatch.com/search.php?category=Old+Computers](http://distrowatch.com/search.php?category=Old+Computers)

Thanks I will check into those :KS

also found this article... seems very helpful... [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by Sonuahua on 2014-10-18
> **grahammechanical said:**
> Did you choose the Erase disk and install Ubuntu option? Or Install alongside? Or Something else. _**I cannot really say what you did wrong because you do not say what your answers you gave.**_ Cannot comment on the hardware because the information is not sufficient. We do not know if the CPU is Intel or AMD. What graphic adapter does the machine have? How much of its own memory does the graphic adapter have? How many partitions?


Ok, I will record as I go one more time...

Restart > 
F10 to boot menu > 
install Ubuntu>

English >continue..
*connect to network. [entered password] >connect >continue

connected... 
*[yes]download updates while installing
*[yes]install this third party software
>continue....

options..
*[no] install alongside windows
*[yes] replace windows
**[no] encrypt
**[no] use LVM
*[no] something else

Replacing xp menu... (This is where I loose confidence)
Select Drive - optons
*[yes]SCS13 (0,0,0) (sda) -  80.0 GB ATA HDS728080PLA380
*[no] SCS15 (0,0,0) (sdb) - 160.0 GB ATA WDC WD1600BB-OOR
                        ...(wubi symbol) ..Ubuntu../dev/sda (ext4)..80.0 GB
                        ...2 partitions will be deleted use _APTool_ for more control... >Install Now...

choose time zone... >continue
English >continue

Name..password..login options >continue....

Install screen... copying files.... slide show :p....

preparing varios programs(i386)... configuring....unpacking..removing..again,again,ect. .... running post installation... downloading packages....
... more running, preparing, configuring,unpacking, and installing....

"Installation is complete. You need to restart the computer in order to use the new installation" >restart Now...

....and.....It loads Windows XP..... again.... nothing is changed... nothing is different....

---

### Post by Sonuahua on 2014-10-18
Now... looking in "My Computer" >C: I have an Ubuntu folder which contains folders:disks,install,winboot; a wubi icon labeled "Ubuntu"; and a wubi icon labeled "uninstall- wubi" .... 
I do not know if this is from the installing, or my previous attempts(fails) at creating a dvd to install Ubuntu-32bit.... probably from my attempts at creating the dvd...

My bootable USB was made by my nephew, who has several years experience with Ubuntu

---

### Post by Sonuahua on 2014-10-18
deleted

---

