---
title: "Boot Manager 3 OSs showing up."
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by jan-90 on 2011-01-14
Hi,
linux newbie here, i did ubuntu 10.10 install in windows and something must have gone wrong since in the preboot menu the ubuntu was visible but could not boot [a windows boot manager message came up immediately on selective ubuntu]
i reinstalled it and now have 1 windows 7 and 2 ubuntu. 
when i select the ubuntu in the an other boot screen [GNTU or GNU come up [2 ubuntu options 2 windows] when i select the normal ubuntu on both the screen flickers and nothing shows up.

How can i remove both ubuntu installations and start all over again?
ideally without removing windows.

ps i have an hp tm2-2100 notebook which ran ubuntu x64 fine from a live pendrive
thanks

---

### Post by Rubi1200 on 2011-01-14
Hi and welcome to the forums :)

I am assuming by "in windows" you mean this is a Wubi install?

Can you boot Windows normally?

Use a LiveUSB to boot the computer and then download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

Also, what graphics card do you have installed?

Thanks.

---

### Post by dino99 on 2011-01-14
if you have installed ubuntu inside windows (wubi), then i cant follow you on that choice. For a real experience, nothing better than a real installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

about grub menu, in a terminal:

sudo dpkg-reconfigure grub-pc

---

### Post by jan-90 on 2011-01-14
Yep thats correct  Wubi install.
i can remove one of the ubuntu from windows add remove but the other one now points to a corrupted / deleted file.
/ubuntu .....mbr something.
i have a dual graphics an intel and amd
i will try that you told me
thanks alot

---

### Post by jan-90 on 2011-01-14
> **dino99 said:**
> if you have installed ubuntu inside windows (wubi), then i cant follow you on that choice. For a real experience, nothing better than a real installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

about grub menu, in a terminal:

sudo dpkg-reconfigure grub-pc


Hi thanks for you info i cant install it that way [ to my limited knowledge] since i already have 2 partitions which i need and want for windows.
I dont know if there is a walk around for having both OS on one hard drive with >4 partitions.
also since im a total newbie for the above command i need to boot from a live linux and input that command in the terminal? and whats next?

---

### Post by jan-90 on 2011-01-14
resutls attached
what to do next?

---

### Post by Rubi1200 on 2011-01-14
First show us the results of the script I mentioned so we can get a better overview of the current state of your system. Anything else is just poking around in the dark and is likely to mess things up.

EDIT: got it; thanks

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 241051648.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   241,051,647   240,844,800   7 HPFS/NTFS
/dev/sda4         241,051,648   976,771,071   735,719,424   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2013 MB, 2013265920 bytes
255 heads, 63 sectors/track, 244 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,919,859     3,919,797   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2004 MB, 2004877312 bytes
16 heads, 32 sectors/track, 7648 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,064     3,915,775     3,907,712   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D2AE7D37AE7D14E7                       ntfs       System Reserved               
/dev/sda2        5820901D20900462                       ntfs                                     
/dev/sda4        3717B1B7DFF54AA6                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1DF7-0A22                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        C005-F763                              vfat       HP_TOOLS                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/HP_TOOLS          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================


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

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  b5 cf 3b 00 ed 0e 00 00  00 00 00 00 02 00 00 00  |..;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 22 0a f7 1d 4e  4f 20 4e 41 4d 45 20 20  |..)"...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 02 1e 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by jan-90 on 2011-01-14
I think i know where i messed up, i did a recovery back to win 7 home premium since most drivers where missing when i did a clean win 7 install, the ubuntu was probably already there when i did the restore.
anyway i can remove it, im not sure it its taking up any space on the hard disk.

---

### Post by Rubi1200 on 2011-01-14
According to the boot script you do not have a Wubi install on the drive, only Windows.

Did you remove it already?

If there are any vestiges of it in Windows you can use the instructions in the Wubi Guide for manually uninstalling:
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by jan-90 on 2011-01-14
> **Rubi1200 said:**
> According to the boot script you do not have a Wubi install on the drive, only Windows.

Did you remove it already?

If there are any vestiges of it in Windows you can use the instructions in the Wubi Guide for manually uninstalling:
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

i hate 2 wubis one in the windows pro from which i restored the factory win home premium
in add remove the wubi in the win pro is not showing up
proceeding to remove it manually thanks
will report back

---

### Post by jan-90 on 2011-01-14
the folder where not there [an neither hidden] i remove it with easy bcd
is it possible that there are still the ubuntu file somewhere since i have 40gb id data in drive C with almost no programs installed

---

### Post by Rubi1200 on 2011-01-15
I am not sure, but you might want to look if there was a restore point created that could be taking up the space (though I doubt it):

Perhaps also try defragmenting and clearing out any temp folders.

---

### Post by jan-90 on 2011-01-15
im reformating and adding extended partitions to avoid wubi.
thanks for you help, forking up is part of learning

---

