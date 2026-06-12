---
title: "Dual Boot on seperate drives"
date: 2018-09-16
forum: Installation &amp; Upgrades
---

### Post by schembrigiuseppe on 2018-09-16
I've been experiencing problems  booting my PC after ubuntu updates (probably when kernel is involved), most of time bootrepair could solve the issue. Last time I solved it through a fresh installation of ubuntu 18.04 on  sda5. I wonder if I could do something to improve my PC in order to prevent problems in future.
I've got some question about the bios settings too: should I enable Legacy mode? Should I disable fast boot?

This is the result of running ```
sudo parted -l
```
> Modello: ATA ST1000DM003-1ER1 (scsi)
Disco /dev/sda: 1000GB
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: gpt
Flag del disco: 

Numero  Inizio  Fine    Dimensione  File system     Nome                          Flag
 1      1049kB  106MB   105MB       fat32           EFI system partition          avvio, esp
 2      106MB   240MB   134MB                       Microsoft reserved partition  msftres
 3      240MB   64,4GB  64,2GB      ntfs            Basic data partition          msftdata
 4      64,4GB  73,0GB  8590MB      linux-swap(v1)
 5      73,0GB  202GB   129GB       ext4
 6      202GB   1000GB  798GB       ntfs                                          msftdata


Modello: ATA ST1000DM003-1ER1 (scsi)
Disco /dev/sdb: 1000GB
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: gpt
Flag del disco: 

Numero  Inizio  Fine    Dimensione  File system     Nome  Flag
 1      210MB   212MB   2097kB                            bios_grub
 2      212MB   140GB   140GB       ext4
 3      140GB   148GB   8094MB      linux-swap(v1)
 4      148GB   1000GB  852GB       ntfs                  msftdata


In sdb2 ubuntu 14.04 was installed through an image from an old machine. If I remember well it was a bios installation with an MBR in the old PC.
In sda3 Windows
In sda5 Ubuntu 18.04.1

Thanks for any suggestion

---

### Post by TheFu on 2018-09-16
Windows required UEFI booting with GPT partitions.  If you are booting Windows with UEFI, then Ubuntu should be booted that way too.
It is recommended that you disable Windows fast-boot with a dual-boot system.  Someone else will need to post links about that and other recommendations for Windows in a dual-boot setup.

The easy way to make text output readable in the forums is to use "code tags" - Adv Reply (#). It is preferred. You can edit any posts you've made to fix it.

---

### Post by yancek on 2018-09-16
You should run boot repair with the Create BootInfo Summary option and post the link given as it will have a lot of more useful information than you have posted.  You have an EFI partition so you should have both windows and Ubuntu install EFI.  You show a bios_grub partition on sdb which means an install in Legacy/MBR mode.  Not sure what's up with that as you say you have 18.04 as well as 14.04 installed on sda.  You need to post the output of boot repair.  Too many questions, too little information.

---

### Post by Mark Phelps on 2018-09-16
Just so you know -- Fast Boot is not the same as Fast Startup.  The first is a UEFI boot option; the second is a Windows Hibernation setting.  While they often achieve similar results, they are entirely different settings.

Win10 has enabled a new hibernation process known as Fast Startup -- which is different from Fast Boot.  This is supposed to dramatically speed up the booting process, but in some PCs, it actually slows it down or causes it to hang.
 
Disabling Fast Startup might fix any booting problems and is also then allows access to the Windows filesystem from Linux.
 
There are two ways to disable FastStartup in Win10: (1) through the Control Panel, and (2) through an elevated command prompt.
 
Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup
 
Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
 
In both cases, reboot Windows.
 
NOW, FastStartup is disabled.

---

### Post by schembrigiuseppe on 2018-09-17
Just to be clear I can boot with no problem at the moment. But I had many problems in the last few years, after ubuntu updates, and I wonder if it could be caused by a PC misconfiguration.

Here is the bootrepair info:
[http://paste.ubuntu.com/p/kktDZZqKKZ/](http://paste.ubuntu.com/p/kktDZZqKKZ/)

thanks

---

### Post by oldfred on 2018-09-17
It looks like you need lots of housecleaning. but make sure you have good backups, in case you houseclean something you really want.

Specifically you have many Boot-Repairs in ESP, sda1. Best to remove all but most current.

You have lots of old kernels. So it looks like you upgraded without housecleaning before upgrade.
And now those kernels may not be in dpkg for ease of removing.
Not only are kernels in /boot, but you may have files in other places.

Start with these:
       sudo apt-get update
sudo apt-get upgrade
apt-get autoremove
sudo apt-get autoclean
sudo apt-get dist-upgrade 
    
       Determine your current kernel, 18.04 only keeps 2 by default now:
uname -a 

then check all these places for old kernels.
      
 ls /var/cache/apt/archives/linux-image*
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
ls -al /vmlinuz* /initrd.img*

You then probably have many old log files and other things to houseclean.
      
 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

 Caution deborphan will delete anything you manually installed. See comment:

---

### Post by schembrigiuseppe on 2018-09-18
Thanks I may mark the post as solved.
Looking at my Grub menu I thought that it might not be normal to stack a kernel on top of the other.
I'll try to follow your suggestions, I kind of had the feeling that a tidy up was needed but it's not easy for me to clean up (my flat too), always scared to do something wrong.
I do not understand how boot repair logs are still there after I did a fresh installation of Ubuntu 18.04 on sda from an usb key.
I guess The boot partitions are not formatted as the one with / as mount point.

Thanks again to all of you people I had a very fast support on this forum.

---

### Post by oldfred on 2018-09-18
If you did a new clean install, you would not have the old kernels in /. 
Or did not not check the format box? Or choose to save your info?

Best to have good backup particularly of /home and anything custom you may have changed.
Then clean install & restore your data & configurations. If you added a lot of apps good to export list before install from old system and reimport list to add back all those apps.

---

