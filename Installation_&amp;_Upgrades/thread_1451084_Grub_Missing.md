---
title: "Grub Missing"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by akssps011 on 2010-04-10
Hi

I have been in  a problem now for a very long time now. 

A few months ago, I had a dual boot system(WinXP and Ubuntu). But something happened and I was not able to boot into my Ubuntu partition. It gave GRUB missing error.

I tried reformatting the dedicated 40 GB ubuntu partition to NTFS and again try to reinstall ubuntu. 
But now, when I install ubuntu through boot time install, it shows that my whole hard disk is empty( but I have windows XP on whole hdd at the moment) and do not give any other option but to use whole hdd.
Alternatively when I try to install it inside windows, then after rebooting it shows, no root file system defined error and neither gives any option to do so also ( this method worked earlier o my PC).

At the moment, It still shows ubuntu and windowsXP at OS choice menu at boot time but when booting in ubuntu, it shows GRUB missing. (I don't have any ubuntu installation on my hard disk at the moment).
What should I do ?
I have tried
 [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) 

but sudo grub says that command not found while using live CD.

Please Help.

---

### Post by oldfred on 2010-04-10
Do you have wubi installed on NTFS partiiton or a separate install in its own partitions?

To see what you have - from a live CD:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by akssps011 on 2010-04-12
Right now I just have windows XP and nothing else installed.

Contents of the RESULTS.txt is as follows:

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 5670. But according to the info from fdisk, 
                       sda3 starts at sector 40965750.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x030d030c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    21,093,344    21,093,282   7 HPFS/NTFS
/dev/sda2          21,093,345   156,280,319   135,186,975   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5          21,093,471    40,965,749    19,872,279   7 HPFS/NTFS
/dev/sda6          76,340,943    95,393,969    19,053,027   7 HPFS/NTFS
/dev/sda7          95,394,033   125,226,674    29,832,642   7 HPFS/NTFS
/dev/sda8         125,226,738   156,280,319    31,053,582   7 HPFS/NTFS
/dev/sda3          40,965,750    76,340,879    35,375,130   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6E39591574B2AE8A                       ntfs                                     
/dev/sda3        C468DC6668DC58AE                       ntfs                                     
/dev/sda5        67EDB4565D9D16C8                       ntfs                                     
/dev/sda6        5EBC127CBC124EC1                       ntfs                                     
/dev/sda7        C8541F39541F29A8                       ntfs                                     
/dev/sda8        0E878ACF2CCFB85F                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 



```

please guide.

---

### Post by 1999panos on 2010-04-12
You mustn't uninstall Ubuntu by just deleting its partition because GRUB is **still installed** and it **STILL keeps** Ubuntu boot information. GRUB gets installed into **MBR** & you haven't access to MBR via Explorer! In order to fix that, you have to replace **GRUB** loader with **Windows** loader [if you want **ONLY** Windows]. 
But if you want dual-boot Ubuntu - Windows, you just reinstall Ubuntu [SIZE=5][COLOR=Red]**+**[/COLOR][/SIZE] GRUB ! :)
But if you want [COLOR=Red]**ONLY**[/COLOR] Windows XP, I'm sorry, but I can't remember how you do that. I think you download a program for Windows called "MbrFix.exe" and you do something! I can't remember any further! You should search on Google about it. Sorry again! :(
But, according to your information, you haven't deleted Ubuntu partition. So... I don't know... I'm sorry :(

---

### Post by oldfred on 2010-04-12
There is no Ubuntu install, sometimes uninstalling wubi will leave an entry in boot.ini.

You do have a partition problem. sda3 is a primary partition but is inside the extended partition sda2, so it sees two extended partitions which is not possible.

I am not real knowledgeable on partition problems. Any editing of the partition table can cause data loss, so if you have any important data be sure to back it up.

I have see recommendations for testdisk, it is on most repair CDs and can be downloaded from the repository with Ubuntu.
repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I have seen this:
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

Using sfdisk to fix partition table problems 
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

---

### Post by akssps011 on 2010-04-17
thanks. 
Adjusted the Extended partition by using winXP cd and then deleting that partition and later used it as a partition for ubuntu install

---

