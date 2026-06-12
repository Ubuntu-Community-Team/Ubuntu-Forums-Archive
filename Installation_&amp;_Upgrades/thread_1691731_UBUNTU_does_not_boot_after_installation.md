---
title: "UBUNTU does not boot after installation"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by tedzot on 2011-02-20
Hello Im new here and new to Ubuntu. First off let me say Im VERY impressed with Ubuntu...ran it for a little bit on a laptop for work but had to revert to windows for work purposes. I have an issue that i was hoping I could get some advice on. I have anotder desktop IBM intellistaion mpro 6850. Im using it to stream videos from the internet on my widescreen TV. I didn't want to install windows on it due to all the issues with drivers etc you get plus firewalss you have to install and spyware blockers...so i was really wanting to install UBUNTU as its very fast and clean . Anyway...I went through the whole installation process 3 times ...and each time when it says its complete and the system needs to restart it crashed on restart...one time I got a whole bunch of listed dumped code on a black screen and an error msg...or the other time I got a message that the comp. cant find a windows file for boot up...or one time I just got a blinking cursor on a black screen. I got frustrated and installed windows xp again so there is no longer an UBUNTU install on the machine but I would really like to have it on this machine...:confused:

anyway...if any of you good folks have any ideas just what is going on I would appreciate it...

I have ubuntu 10.04 iso burned 1x to cd...(slow burn so there would be no burning errors)


Thanks in advance

---

### Post by kansasnoob on 2011-02-20
> one time I got a whole bunch of listed dumped code on a black screen and an error msg

That is likely this:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install)

> the other time I got a message that the comp. cant find a windows file for boot up

That sounds like maybe grub failed to install properly. It just happens occasionally, but can be fixed using the Live CD.

> one time I just got a blinking cursor on a black screen

That sounds like an issue with your graphics chip, but we need to know the exact gpu info so please post the output of the following command using the Live CD:

```
lspci | grep VGA
```

For the most part you're going to have to take the time to troubleshoot things post-install by running the Live CD and gathering info for us. Since you have Windows installed now you might want to consider a dual-boot. With XP and 10.04/Lucid it's pretty easy:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

NOTE: that procedure does not work with Ubuntu 10.10/Maverick! Also never move the beginning (left end) of the XP partition!

---

### Post by tedzot on 2011-02-20
ok Thank you for your prompt and detailed response...my intention then is to do a dual boot and trouble shoot form there...

"end_request: I/O error, dev sr0, sector 437628"

that error message was the one I saw...yes...after it scrolled out a bunch of code...hm maybe all i had to do at that point was press enter...ah well...ok I'll get back to you

also my graphics card is an older ATI 9200 SE AGP   128 meg ram on board


but I will try the suggestions you outlined as i really would like to dump xp all together...

---

### Post by tedzot on 2011-02-20
I tried to install it as a dual boot...it refused to install a boot record...would not even let me choose where to install one...so I chose to install one manually (the only choice I had) and at boot up I get a message that says windows can't boot missing <windows root>\system32\hal.dll

reinstall the file...

anyideas?

---

### Post by Quackers on 2011-02-20
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2011-02-20
> **Quackers said:**
> Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

+1!

If you just keep giving up without troubleshooting the problem you'll never get anywhere.

---

### Post by tedzot on 2011-02-20
```
                                                                    
                                                                     
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.5 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders, total 40011300 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    38,252,543    38,250,496  83 Linux
/dev/sda2          38,254,590    40,009,727     1,755,138   5 Extended
/dev/sda5          38,254,592    40,009,727     1,755,136  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 18.4 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders, total 35843670 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    35,841,014    35,840,952   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        861f805f-3c20-4053-a001-483eb6a12a40   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2f5db9c1-8e6e-4f09-912e-827d78ec5691   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0C907C46907C3872                       ntfs       E_SCSI_320                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2f5db9c1-8e6e-4f09-912e-827d78ec5691 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   9.0GB: boot/initrd.img-2.6.35-22-generic
    .5GB: boot/vmlinuz-2.6.35-22-generic
   9.0GB: initrd.img
    .5GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff

```


ok there is my info

thanks in advance

---

### Post by deconstrained on 2011-02-20
May not be the cause of your current problems, but it's rather important: If you have more than one hard drive, which it looks like you do, I think you should be using UUID's to identify block devices in /etc/fstab, and not kernel names (i.e. sda2, sdb1) because udev sometimes assigns them differently during different boot-ups.

---

### Post by tedzot on 2011-02-20
well thanks but I have absolutely no idea what you are saying...you see I have no experience with Linux and know nothing about the terms and code phrases you are talking about! 

so if you could explain it in a way a TOTAL linux noob like myself could understand then I would appreciate it...
Thanks for your patience and time

---

### Post by Hakunka-Matata on 2011-02-20
@tedzot, your results.txt shows that Grub (the bootloader) was not installed.  Hang on I'll find a thread that tells you exactly how to fix that

---

### Post by Hakunka-Matata on 2011-02-20
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Have a look there, you want to reinstall GRUB, or install it actually because it hasn't been installed yet.  kansasbob and Quackers are great help, they'll be back sometime.  Bedtime for me.  Good Luck

---

### Post by tedzot on 2011-02-21
ok thanks for your kind help. I tried the link posted above and used the first method i.e: **SIMPLEST - Copy GRUB 2 Files from the LiveCD**

I opened a terminal and cut and pasted the commands and below is what i got :


```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.5 GB, 20485785600 bytes
 255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000903d9
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2382    19125248   83  Linux
/dev/sda2            2382        2491      877569    5  Extended
/dev/sda5            2382        2491      877568   82  Linux swap / Solaris
 
Disk /dev/sdb: 18.4 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x900b5b43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2231    17920476    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda1
 /usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup:  warn: Embedding is not possible.  GRUB can only be installed in this  setup by using blocklists.  However, blocklists are UNRELIABLE and their  use is discouraged..
 /usr/sbin/grub-setup: error: if you really want blocklists, use --force. 
```I thought it didn't sound good but I tried rebooting anyway and it just gave me the same missing file windows error I noted above. 
am I doing something wrong? Should I have tried to install grub on the sdb1 drive where windows xp is installed?

Again thanks in advance for your patience....

---

### Post by deconstrained on 2011-02-21
> **tedzot said:**
> well thanks but I have absolutely no idea what you are saying...you see I have no experience with Linux and know nothing about the terms and code phrases you are talking about! 

so if you could explain it in a way a TOTAL linux noob like myself could understand then I would appreciate it...
Thanks for your patience and time
All Unix-like systems use the file /etc/fstab to dictate where each block device (i.e. hard drive partition) should be mounted. When a device is "mounted", the operating system (kernel and programs that run in the userspace) can then access the files inside the file system contained within that device.

Entries in fstab begin with the device itself in the first column, which can be specified either by the device path (i.e. /dev/sda1) or by the UUID ([universal unique identifier](http://en.wikipedia.org/wiki/Universally_unique_identifier)) using the format "UUID=8charact-4char-4cha-4cha-12characters". The second column is the mount point (place in the main filesystem where the device's own filesystem is to be mounted).

Here's what you can do to find the UUID of a block device:
```
$ ls -l /dev/disk/by-uuid/
```
or this:
```
$ sudo blkid
```
That should tell you which hard drive partitions have been assigned which UUID.

The problem I brought up was with regard to device paths. Those names are assigned by a core Linux utility called udev at boot time, which the kernel uses to create symbolic links and interfaces for all devices, so that the kernel and programs in the userspace can control and manipulate them. What can happen, sometimes, is that udev assigns a different name to the same device, if another device takes the original name first. Example: you have two hard drives, sda and sdb, but those names (kernel names) don't always refer to the same drives; you could have 4 partitions on sda and 2 partitions on sdb, and boot to a live disk, and look in dev and see sda1, sda2, sdb1,sdb2,sdb3,sdb4 (an indication the kernel names got switched around).

The UUID is unique to a block device (or group of block devices, in a multiple-device array a.k.a. software RAID) and, for all intents and purposes, never changes, so it's more reliable to use in identifying which hard drive and partition is which.

---

### Post by Quackers on 2011-02-21
It seems that for some reason Ubuntu is not installing completely.
According to the boot script you currently have Ubuntu 10.10 partly installed to the first partition of your 20GB hard drive.
On your 18GB second hard drive you have a Windows XP type partition with some Windows XP boot files in it, but no operating system installed there.
What I would recommend is to re-install XP (if you want it) and get that system booting first.
Once that's done, I would recommend booting from the Ubuntu live cd and at the first purple screen (the one with the little man icon at the bottom) press any key. Then choose your language and on the next screen, choose the option to check the cd for errors.
If it finds any errors the cd is no good. 
You should then check that the iso file you downloaded is good, by checking the md5sum as detailed below.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by tedzot on 2011-02-21
xp was fine before I tried to install Ubuntu...dunno about the cd...all I can tell you is that I have 2 cds with 10.10 on it from different sources and burned slow...tried installing from them both and both bonked my system.I will check em both out when I get home later (at work now) as you state to do above. What I am going to try to do is yank the 18 gig hard drive and just install Ubuntu on the 20 gig drive ...then put the other drive in afterwards. Dont want a dual boot anyway...and I feel it might simplify natters anyway...I'll keep you posted.



edit...ok did a checksum on the iso...it matches...so I guess that is ruled out...

oh and BTW @ deconstrained...thank you for taking the time to explain things...it is much appreciated

---

