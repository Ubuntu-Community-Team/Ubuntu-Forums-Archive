---
title: "grub error if I boot my external hdd in other computer."
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by ilyesoft on 2011-12-04
So, I have an external hdd drive with two partitions, the first is ntfs for data, second is ext4 for ubuntu 11.10.
Grub2 is installed in the external hdd in mbr and ext4.

When I boot my laptop with usb (with external hdd), I get grub working, then ubuntu running..
When I do the same in my friends laptops it is also ok.

No, when I try to boot from my desktop pc, I get grub rescue mode !

I unistalled grub 2 and installed grub legacy, same problem -> works in my laptop but not on the desktop computer.

Can you help me please ?

---

### Post by darkod on 2011-12-04
Plug the ext HDD into the desktop but don't boot the desktop from its HDD. Boot with the ubuntu cd in live mode and run the boot info script from my signature. The explanation how to run it and post the results are in that link.

That should show the boot process on your desktop.

---

### Post by ilyesoft on 2011-12-04
Thank you your boot info script is cool ;)

Here is the result

> 
[SIZE=1]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /grldr /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 973005344 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x36b48cd3

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   167,766,794   167,766,732   7 NTFS / exFAT / HPFS
/dev/sda2         167,766,795   732,178,439   564,411,645   7 NTFS / exFAT / HPFS
/dev/sda4         732,178,440   976,768,064   244,589,625   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00087ecf

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   955,797,503   955,795,456   7 NTFS / exFAT / HPFS
/dev/sdb2         955,797,504   974,675,967    18,878,464  83 Linux
/dev/sdb3         974,675,968   976,773,119     2,097,152  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7C94C9E194C99DD0                       ntfs       
/dev/sda2        3B4F45954607AA6A                       ntfs       
/dev/sda4        264C96894C965381                       ntfs       Back Up
/dev/sdb1        EACC9755CC971AC1                       ntfs       Verbatim
/dev/sdb2        ffdef4f2-f819-44cd-baf8-612a53abd979   ext4       
/dev/sdb3        03f1f8cb-661c-4928-9bf0-9e53ad6ab00a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/sdb1        /media/Verbatim          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /NOEXECUTE=OPTIN /FASTDETECT 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professionnel" /FASTDETECT 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professionnel" /FASTDETECT 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professionnel" /FASTDETECT 
--------------------------------------------------------------------------------

========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
[/SIZE]


But I dont understand very much but I think the the grub2 is installed on the ntfs sdb1 ? So how I can boot in my laptop! anyway I uninstalled grub2 and installed grub legacy..

Can you help me please ?

---

### Post by ilyesoft on 2011-12-04
> sdb2: __________________________________________________  ________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'[SIZE=1]

[SIZE=2]also ubuntu file browser can not mount the partition;[/SIZE]
[/SIZE]> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[SIZE=1]
[SIZE=2]why is that and why my laptop can solve the problem? Is it the bios who had the driver for filesystem ext4 ???

Edit> the ubuntu in live cd is an old version that maybe does not read ext4
[/SIZE] [/SIZE]

---

### Post by darkod on 2011-12-04
Some BIOS are limited searching for boot files beyond 137GB and I wonder if this is your problem on the desktop. The first ntfs partition takes almost all of the disk so the ubuntu files are definitely beyond 137GB.

I wonder if creating a small /boot partition on the beginning of the disk would sort that out. But not sure if new install is needed for that.

Also, grub1 is limited working with ext4, it's better if you use grub2. But doesn't seem to be the main problem since you say on the laptop it runs with grub1 and ext4.

---

### Post by oldfred on 2011-12-04
Darko's suggest may work for your boot issue. But you have another issue also.

All NTFS partitions whether bootable or not have to have a NTFS signature in the partition boot sector (PBR). You need to remove grub2 from the PBR of sdb1 for windows to see the NTFS partition.

NTFS does save a backup of the NTFS PBR so you often can recover it if the backup is still valid. If not testdisk can recreate a standard NTFS PBR but it often is not bootable with Windows 7. Since it is a NTFS data partition you should then be able to use the rebuild if the recovery does nto work.


Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If you need to rebuild the NTFS PBR.

As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by ilyesoft on 2011-12-04
> **darkod said:**
> Some BIOS are limited searching for boot files beyond 137GB and I wonder if this is your problem on the desktop. The first ntfs partition takes almost all of the disk so the ubuntu files are definitely beyond 137GB.

I wonder if creating a small /boot partition on the beginning of the disk would sort that out. But not sure if new install is needed for that.

Also, grub1 is limited working with ext4, it's better if you use grub2. But doesn't seem to be the main problem since you say on the laptop it runs with grub1 and ext4.

That really makes sens, my desktop is too old...
I tryed almost everything even removing out the internal disk and floppy drive with no hope for 10 days ! but never thought for the 137g :)
I will try that, thank you very much for your help :)

---

### Post by efflandt on 2011-12-05
Even some relatively new desktops seem to have a problem booting large external drives, although, older ones are more likely to.  My Dell desktop is from 2010 XPS 8100) and it boots fine with 64-bit Ubuntu 10.10 partition starting almost 900 GB into its 1 TB internal drive.  And it boots fine from 160 GB USB drive.  But same Ubuntu just dumps into grub rescue trying to boot a 500 GB USB drive that boots fine on both Dell and Toshiba laptops from 2006. I have not tried released installs of 11.04 or 11.10 on USB, I am running 11.10 on internal SSD which boots everything else.

And even if I boot an "internal" drive to grub and go into regular grub prompt (not grub rescue), that can list files in / and /boot, but not files in /boot/grub of the 500 GB USB drive. That is why booting my desktop from a large USB drive dumps into grub rescue with a file not found error.  I have not tried making a smaller boot partition at the beginning of the drive because then I would need to "move" an NTFS partition which could take many hours.

Same with my old HP desktop from 2004.  It can boot Ubuntu (64-bit 10.04 on that one) beyond 137 GB on its 200 GB internal drive, and can boot 160 GB USB, but cannot boot the 500 GB USB drive.

None of the PC's have any trouble mounting any ntfs or Linux partitions the 500 GB drive from a running Linux system.

If there is some sort of 137 GB BIOS limit, why would it "only" affect booting "external" drives (USB 2.0) and not internal drives?  That has remained a mystery to me.

---

