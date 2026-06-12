---
title: "No root file system is defined, Wubi and USB installation"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by shazmailz on 2011-11-17
Hello all,

I guess this problem is becoming quite common but with no straight-forward solution. I have windows 7 installed and want to install Ubuntu. Apparently, both Wubi and a USB based installation installation fails to read the existing partitions. In Wubi I have no option to set the mount points or partitions. It installs the basic files (while in windows), reboots, and straight away gives the error "No root file system defined" 
[http://i54.tinypic.com/6glk7q.jpg](http://i54.tinypic.com/6glk7q.jpg)
If I try to do a clean install from a bootable USB drive, and want to specify/make the needed partitions, the installation process fails to acknowledge the existence of existing partitions and windows OS.
I have searched through the forums and didn't get a clear answer. The only thing i did understand is to run a configuration script and post the output here, and hope that some 'Pro' will kill his time and give an answer only applicable to my problem. Here is the output. Do help please..

/OUTPUT/////////////////////////////////////////////////

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   307,202,047   306,995,200   7 NTFS / exFAT / HPFS
/dev/sda3         307,202,048   976,771,071   669,569,024   f W95 Extended (LBA)
/dev/sda5         307,204,096   614,404,095   307,200,000   7 NTFS / exFAT / HPFS
/dev/sda6         614,406,144   976,771,071   362,364,928   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2021 MB, 2021654528 bytes
2 heads, 63 sectors/track, 31337 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,948,543     3,948,512   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        70B8FF4BB8FF0DFA                       ntfs       System Reserved
/dev/sda2        1890045E9004452A                       ntfs       
/dev/sda5        669CC6579CC62203                       ntfs       New Volume
/dev/sda6        FCF0CEAAF0CE6B0A                       ntfs       New Volume
/dev/sdb1        50D3-6B73                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc
```

---

### Post by bcbc on 2011-11-17
This is the problem:
> GUID Partition Table detected, but does not seem to be used.

The ubuntu installer - or actually the tools it uses like parted - kick out an error when there is a mix of MBR and GPT partition tables. This most often happens when using a disk that was previously on a MAC.

You can research the issue and remove the gpt data using this: [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by shazmailz on 2011-11-17
Thank you "bcbc" for your reply. I did skim over the link you gave in your response of clearing the GUID thing, but I cannot afford to lose my current windows system. Is it possible to remedy the problem without compromising my existing Windows 7 OS and other partitions with the tool you want me to use ??

---

### Post by Mark Phelps on 2011-11-17
If you are really serious about doing dual-boot, then read the following:

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by bcbc on 2011-11-17
> **shazmailz said:**
> Thank you "bcbc" for your reply. I did skim over the link you gave in your response of clearing the GUID thing, but I cannot afford to lose my current windows system. Is it possible to remedy the problem without compromising my existing Windows 7 OS and other partitions with the tool you want me to use ??
If you can't afford to lose your Win7 install, then make sure you have full backups, restore dvds, repair cd etc. because it's possible to have random hardware failures (not just when playing with partitions).

Please review in detail the fixparts website, and if you have any questions not covered, there is an email address to follow up with the author.

---

### Post by Rubi1200 on 2011-11-18
As bcbc pointed out, you must make backups in any event.

As with any tool that manipulates partitions, you need to be very careful. 

However, we have seen fixparts used on numerous occasions and it has worked very well to resolve issues like this.

---

### Post by saidii89 on 2012-05-15
a lot of users faced such problem and the solution to it is pretty simple
 
make sure that the partition file system [you wish to install linux, ubunto or backrack on it] is ext4, ext3 or ext2 [not fat32 or ntfs]
 
then mount "/" on it, how? easy: 
1- on the installation process press [change] on the partition you wish to use
 
2- make sure [do not use this partition] scroll is not chosen, scroll to ext4, ext3 or ext2
 
3- and on "mount" field write "/"
 
4- when clicking ok then next a message will appear saying something like [swap area was not defined, do you wish to continue or choose a swap area? because bla bla bla..], click "ok" and continue or click "go back" and choose another partition and click change, on the file system scroll choose [swap] and click ok and next
 
this will solve both "no root file system is defined" and the "swap area" message, if you still get the swap area message then on step 4 mount "/swap" to the partition
 
**AND THIS SOLVES IT!**
 
every time anyone need solutions don't hesitate to search for help
 
ask me if you need something and I can help I will do it, I don't log to forums a lot, I found this thread while searching on google and I copied this answer to all the threads with the same problem, so If you need contact here it goes ->
 
[http://www.twitter.com/saidii89](http://www.twitter.com/saidii89)
[http://www.facebook.com/saidii89](http://www.facebook.com/saidii89)
[http://www.formsrping.me/saidii89](http://www.formsrping.me/saidii89)
[http://www.saidi-theory.blogspot.com]("http://www.saidi-theory.blogspot.com/")
 
brought to you by Sa'eed Awad
[Saidi Theory Solutions] by Sa'eed Awad

---

