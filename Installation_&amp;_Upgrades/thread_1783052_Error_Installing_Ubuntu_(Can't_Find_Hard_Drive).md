---
title: "Error Installing Ubuntu (Can't Find Hard Drive)"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by pokelovs on 2011-06-15
Hello, I'm new to the forums, mostly because of this problem though...
I've tried installing Ubuntu from the installation disk, flash drive, and using windows installer. The drive and disk said I didn't have enough memory open to install (I have 160GB open)upon looking around in the demo, i noticed that it couldn't find my hard drive as it wasn't on the drive explorer. So i searched for answers and found a few possible ones but i wanted to find someone with my exact problem--Couldn't find any. So then I came upon the  [Windows Installer]("http://www.ubuntu.com/download/ubuntu/windows-installer") and Tried it out. All went well until i had to reboot, it said it couldn't find the installation.iso (which is indeed on my computer) and that i should run "Chkdsk /r" and i did. Nothing changed. I still believe that Ubuntu can't see my hard drive when windows can, why is this? Is there a way to fix it?
EDIT: How could I forget to mention I'm on Windows 7?

---

### Post by Rubi1200 on 2011-06-15
Hi and welcome to the forums :-)

We need you to do 2 things please:

1. take a screenshot of the Disk Management utility in Windows so we can see how Windows sees your drives and then post it here

2. post the results of the boot info script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by pokelovs on 2011-06-15
[IMG]http://filesmelt.com/dl/DiskManagement.png[/IMG]
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22
    Boot sector info:   Syslinux looks at sector 7768312 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the H:\syslinux 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 4160 MB, 4160503808 bytes
32 heads, 63 sectors/track, 4030 cylinders, total 8125984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     8,124,479     8,124,417   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        208E-F824                              vfat       MYLINUXLIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

no block devices found 

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```Hope that helps! Also: the first time I booted ubuntu to do this, it came up with an error that stated it couldn't find the disk it was running off of... I restarted and second time was the charm!
EDIT: Before I used it the second time, I plugged in my flash drive that also had ubuntu on it. So when i opened ubuntu, after posting this i decided it was useless, so I tried wiping it from ubuntu. It started then error'd out and now i'm unable to do most things. Also: when i open Disk utility, it just crashes

---

### Post by Rubi1200 on 2011-06-15
The screenshot you posted is okay because it tells me you don't have dynamic disks (which can be a big problem for Linux).

However, the script results are for the flash drive and not your Windows drive, so I am unable to comment on why you are having issues.

I suggest that you boot with the Ubuntu flash drive and take a screenshot of the drives from GParted and post it here.

But, also run this command in the terminal and post the results:

```
sudo fdisk -lu
```

Thanks.

---

### Post by pokelovs on 2011-06-15
Im sorry, but i've decided that installing ubuntu wasn't worth all of this trouble :(

You've been really kind and helpful, and i appreciate it, but i give up. I didn't expect installation to be this time consuming.

I may be back, i may not. but thank you for your help.

---

### Post by Rubi1200 on 2011-06-16
It's your decision obviously, but I have some ideas that you may want to consider trying:

1. try an earlier version of Ubuntu such as 10.10 or 10.04

2. try a lighter version such as Xubuntu or Lubuntu

3. consider purchasing an external drive and installing Ubuntu there

4. download and burn to CD other distros to play around with until you find one you like and works with your setup:
[http://distrowatch.com/](http://distrowatch.com/)

In any event, I wish you luck and hope you will continue to try and explore the world of Linux.

---

