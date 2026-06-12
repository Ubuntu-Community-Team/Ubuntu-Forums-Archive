---
title: "[64-bit win7] Wubi &quot;no root file system is defined&quot;"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by wayaxD on 2011-06-11
Hi,

I've been using Ubuntu 11.04 from my USB-stick for about 2 weeks now and I really enjoy the OS. So I ran Wubi in windows a couple of times resulting with the same problem after rebooting and showing a error "no root file system is defined" during the finishing stage of the installation.

I did the bootinfoscript and it shows that mounting failed.

                 ```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/mapper/isw_jdbeehhfb_Volume0.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 61046 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_jdbeehhfb_Volume01: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_jdbeehhfb_Volume02: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_jdbeehhfb_Volume03: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             44    15,679,439    15,679,396   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    30,386,175    30,384,128  27 Hidden NTFS (Recovery Environment)
/dev/sdb2    *     30,386,176    30,590,975       204,800   7 NTFS / exFAT / HPFS
/dev/sdb3          30,590,976   250,079,231   219,488,256   7 NTFS / exFAT / HPFS

/dev/sdb3 ends after the last sector of /dev/sdb

Drive: isw_jdbeehhfb_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_jdbeehhfb_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_jdbeehhfb_Volume01              2,048    30,386,175    30,384,128  27 Hidden NTFS (Recovery Environment)
/dev/mapper/isw_jdbeehhfb_Volume02   *     30,386,176    30,590,975       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_jdbeehhfb_Volume03         30,590,976   250,079,231   219,488,256   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_jdbeehhfb_Volume0p1 782801C228017FFC                       ntfs       Recovery
/dev/mapper/isw_jdbeehhfb_Volume0p2 C092FE3A92FE348E                       ntfs       System Reserved
/dev/mapper/isw_jdbeehhfb_Volume0p3 380EFF2F0EFEE4B2                       ntfs       
/dev/sda1        160D-2C19                              vfat       PENDRIVE
/dev/sdb                                                isw_raid_member 
/dev/sdc                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_jdbeehhfb_Volume0
isw_jdbeehhfb_Volume0p1
isw_jdbeehhfb_Volume0p2
isw_jdbeehhfb_Volume0p3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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

========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1


Unknown BootLoader on sdb2


Unknown BootLoader on sdb3


Unknown BootLoader on isw_jdbeehhfb_Volume01


Unknown BootLoader on isw_jdbeehhfb_Volume02


Unknown BootLoader on isw_jdbeehhfb_Volume03



=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume01: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume01: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume02: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume02: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume03: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume03: No such file or directory
```Thank you

---

### Post by linuxinstalledfromhdd on 2011-06-11
Why don't you install Ubuntu from your USB Live stick of Ubuntu?

The installation icon should be right on your desktop or during bootup from the USB drive.

Backup all you stuff first in Windows. 

That should work just fine.  Just install it side-by-side with Windows.

Here is a nice guide once you get that installed:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by wayaxD on 2011-06-12
Hello linuxinstalledfromhdd,

Thanks for the reply. I have have tried that method as well. However when I try to install ubuntu from the USB the option to install it side-by-side with windows is not given. There are only 2 options, replace windows 7 and something else.

I have 48 GB of free space on my SSD and prefer not to resize and partition because I only have 128 GB in total.

Virtualbox is another option I've considered but it runs quite slow for some reason and is not my favorite alternative.

---

### Post by Rubi1200 on 2011-06-12
Hi,
please boot into Windows and go to the Disk Management utility and take a screenshot of how Windows sees your drive/partitions.

Post the screenshot in a new post and attach it using the paper clip icon on the menu.

Thanks.

---

### Post by wayaxD on 2011-06-12
Thanks Rubi1200.

---

### Post by Rubi1200 on 2011-06-12
As I understand the boot script results you have a RAID array; is that correct?

Can you confirm whether it is a software or hardware RAID please.

In general, Wubi installs are not supported on RAID. They are theoretically possible, but not in all situations.

I suspect you may be in one of those situations.

---

### Post by wayaxD on 2011-06-12
I'm not sure if this answers your question but my SSD consists of 2 times 64 GB.

---

### Post by Rubi1200 on 2011-06-12
As I said you appear to have a RAID array. Now, I am certainly not that familiar with RAID, but I do know it can be problematic sometimes to get it to play nicely with Ubuntu.

I am also concerned by the mounting failed errors that the script reported the first time.

To double check whether or not this is a problem with the version of the script download and run it again but this time on the downloads page choose other versions and use the 055 script.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Post the results as you did the first time please.

Thanks.

---

### Post by wayaxD on 2011-06-12
Thanks again for you reply 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/mapper/isw_jdbeehhfb_Volume0

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

isw_jdbeehhfb_Volume01: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

isw_jdbeehhfb_Volume02: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_jdbeehhfb_Volume03: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             44    15,679,439    15,679,396   c W95 FAT32 (LBA)


Drive: isw_jdbeehhfb_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_jdbeehhfb_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_jdbeehhfb_Volume01              2,048    30,386,175    30,384,128  27 Hidden HPFS/NTFS
/dev/mapper/isw_jdbeehhfb_Volume02   *     30,386,176    30,590,975       204,800   7 HPFS/NTFS
/dev/mapper/isw_jdbeehhfb_Volume03         30,590,976   250,079,231   219,488,256   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_jdbeehhfb_Volume0p1 782801C228017FFC                       ntfs       Recovery                      
/dev/mapper/isw_jdbeehhfb_Volume0p2 C092FE3A92FE348E                       ntfs       System Reserved               
/dev/mapper/isw_jdbeehhfb_Volume0p3 380EFF2F0EFEE4B2                       ntfs                                     
/dev/mapper/isw_jdbeehhfb_Volume0: PTTYPE="dos" 
/dev/sda1        160D-2C19                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                isw_raid_member                               
/dev/sdc                                                isw_raid_member                               
error: /dev/mapper/isw_jdbeehhfb_Volume01: No such file or directory
error: /dev/mapper/isw_jdbeehhfb_Volume02: No such file or directory
error: /dev/mapper/isw_jdbeehhfb_Volume03: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_jdbeehhfb_Volume0
isw_jdbeehhfb_Volume0p1
isw_jdbeehhfb_Volume0p2
isw_jdbeehhfb_Volume0p3

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================


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

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 2c 00 00 00  |........?...,...|
00000020  a4 3f ef 00 29 77 00 00  00 00 00 00 02 00 00 00  |.?..)w..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 19 2c 0d 16 4e  4f 20 4e 41 4d 45 20 20  |..).,..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d f8 50 50 50 50 cd  13 eb 62 8b 55 aa 8b 75  |.M.PPPP...b.U..u|
000000a0  a8 c1 ee 04 01 f2 83 fa  4f 76 31 81 fa b2 07 73  |........Ov1....s|
000000b0  2b f6 45 b4 7f 75 25 38  4d b8 74 20 66 3d 21 47  |+.E..u%8M.t f=!G|
000000c0  50 54 75 10 80 7d b8 ed  75 0a 66 ff 75 ec 66 ff  |PTu..}..u.f.u.f.|
000000d0  75 e8 eb 0f 51 51 66 ff  75 bc eb 07 51 51 66 ff  |u...QQf.u...QQf.|
000000e0  36 1c 7c b4 08 e8 e9 00  72 13 20 e4 75 0f c1 ea  |6.|.....r. .u...|
000000f0  08 42 89 16 1a 7c 83 e1  3f 89 0e 18 7c fb bb aa  |.B...|..?...|...|
00000100  55 b4 41 e8 cb 00 72 10  81 fb 55 aa 75 0a f6 c1  |U.A...r...U.u...|
00000110  01 74 05 c6 06 46 7d 00  66 b8 76 ee 00 00 66 ba  |.t...F}.f.v...f.|
00000120  00 00 00 00 bb 00 7e e8  0e 00 66 81 3e 1c 7e cf  |......~...f.>.~.|
00000130  ae 1e 73 75 74 e9 f8 00  66 03 06 60 7b 66 13 16  |..sut...f..`{f..|
00000140  64 7b b9 10 00 eb 2b 66  52 66 50 06 53 6a 01 6a  |d{....+fRfP.Sj.j|
00000150  10 89 e6 66 60 b4 42 e8  77 00 66 61 8d 64 10 72  |...f`.B.w.fa.d.r|
00000160  01 c3 66 60 31 c0 e8 68  00 66 61 e2 da c6 06 46  |..f`1..h.fa....F|
00000170  7d 2b 66 60 66 0f b7 36  18 7c 66 0f b7 3e 1a 7c  |}+f`f..6.|f..>.||
00000180  66 f7 f6 31 c9 87 ca 66  f7 f7 66 3d ff 03 00 00  |f..1...f..f=....|
00000190  77 17 c0 e4 06 41 08 e1  88 c5 88 d6 b8 01 02 e8  |w....A..........|
000001a0  2f 00 66 61 72 01 c3 e2  c9 31 f6 8e d6 bc 68 7b  |/.far....1....h{|
000001b0  8e de 66 8f 06 78 00 be  da 7d ac 20 c0 74 09 b4  |..f..x...}. .t..|
000001c0  0e bb 07 00 cd 10 eb f2  31 c0 cd 16 cd 19 f4 eb  |........1.......|
000001d0  fd 8a 16 74 7b 06 cd 13  07 c3 42 6f 6f 74 20 65  |...t{.....Boot e|
000001e0  72 72 6f 72 0d 0a 00 00  00 00 00 00 00 00 00 00  |rror............|
000001f0  00 00 00 00 00 00 00 00  fe 02 b2 3e 18 37 55 aa  |...........>.7U.|
00000200

Unknown BootLoader  on isw_jdbeehhfb_Volume01


Unknown BootLoader  on isw_jdbeehhfb_Volume02


Unknown BootLoader  on isw_jdbeehhfb_Volume03



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/isw_jdbeehhfb_Volume01: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume01: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume02: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume02: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume03: No such file or directory
hexdump: /dev/mapper/isw_jdbeehhfb_Volume03: No such file or directory
```

---

### Post by Rubi1200 on 2011-06-13
Well, clearly something happened because now the script results show at least some files on sda1.

I am going to send a message to ronparent, who knows more about RAID, asking him to take a look and offer some perspectives.

Hang in there please!

---

### Post by wayaxD on 2011-06-13
ok:D

---

### Post by arukaddp on 2011-06-14
If I might intervene,

I am by no means a specialist, BUT I had the same problem on my laptop. After a little research I found out that there was a problem with the partitions.

At some point in time I did some resizing or something and the beginning and end of the partitions got overwritten.

To solve the problem I used TestDisk, you can find it here: 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You will have to look over the manual found here: 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

just so that you don't brake anything! 

If you have RAID I have no idea if this fix is still for you,  but you can run TestDisk just in order to make a diagnosis to see if this is the problem!

Good Luck!

---

### Post by wayaxD on 2011-06-15
hey thanks for the reply! I'll check it out :p

---

### Post by DrWhoFan2011 on 2011-06-16
I'm not using 64Bit Windows 7; but, I'm experiencing the same error under Windows XP Home (SP3).

My ultimate goal is to get into an Ubuntu 10.xx installation on the same hard drive in another partition. Now that I have a boot.ini is can I manually add a line referring to the second partition? Is there a file name I need to include?

---

### Post by DarkSpartan on 2011-06-19
I'm having the same issue as the OP, although in my case there is only a single installed HD on SATA with a DVD-RW drive. A LiveCD copy of Maverick Meerkat wouldn't see that drive, but did see the externals I have connected via USB. Installing via Wubi the first time to an external drive resulted in the same issue. 

Ack!

---

### Post by DrWhoFan2011 on 2011-06-19
> **DrWhoFan2011 said:**
> I'm not using 64Bit Windows 7; but, I'm experiencing the same error under Windows XP Home (SP3).

My ultimate goal is to get into an Ubuntu 10.xx installation on the same hard drive in another partition. Now that I have a boot.ini is can I manually add a line referring to the second partition? Is there a file name I need to include?

To make a long story short, I overwrote the MBR (and therefore the bootloader) when I installed Windows XP. Are the boot files for the Ubuntu installation still in the partition that XP can't recognize. What are the file names I need to include in the Win XP bootloader to use the linux boot routine in the extended partition?

---

### Post by arukaddp on 2011-06-19
From what I know Windows usually deletes the mbr and then writes it, I think you might have to install grub from the Live CD.

---

### Post by DrWhoFan2011 on 2011-06-22
I've downloaded the testdisk utility that was recommended earlier. I've attached an image file which is a trimmed windows screenshot. The result of my boot.ini after using wubi follows:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr = "Ubuntu"

How would I "phrase" a manual entry into this file to gain access to the partitions revealed by testdisk?

---

