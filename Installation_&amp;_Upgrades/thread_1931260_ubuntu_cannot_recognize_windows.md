---
title: "ubuntu cannot recognize windows"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by beyondlimit on 2012-02-25
I was installing ubuntu boot from usb ,half way it says:the computer currently has no detected operationg system...  my windows version is win7,can any body help me?

---

### Post by darkod on 2012-02-25
Half way?

At the start of the install process it should show if another OS is detected or not. It can't "change its mind" half way trough.

So did the installation finish? Can you boot ubuntu now?

---

### Post by beyondlimit on 2012-02-25
Time is not the point,maybe i have not stated precisely.The point is it said.
Or can you tell me how does ubuntu read the information of other OS so that maybe i could figure out how to fix that?

---

### Post by beyondlimit on 2012-02-25
When it told me that,i stopped the installation

---

### Post by darkod on 2012-02-25
Ubuntu detects the boot files. If for any reason the files are deleted or not present, it doesn't detect it.
There can be other reason, if the disk is Dynamic in windows, and not Basic, if it was used in raid earlier, etc.

So, does windows boot now? Did you stop the installation before it started partitioning your disk?

You can run the boot info script from the link in my signature, and post the results as explained there. You can do that from ubuntu live mode. That will show more details.

Alternatively, if windows can boot, open Disk Management and check if the hdd is Dynamic or Basic.
Also tell us if you used it in raid earlier.

---

### Post by ThomasAndersn on 2012-02-25
well you need to repair ur windows 7, as:
Boot from Windows 7 DVD & when it say install now click on repair windows.
In the next box it search for windows after search complete don't select any OS & click next.
Now select the command prompt and run the following:
Fixmbr  
Fixboot 
& than restart ur computer.

I hope this will work for u.

---

### Post by beyondlimit on 2012-02-25
Yea, when i buy my hp deskop i didn't know i can got a win7 dvd.Since two years has passed i can no longer get a one.I used easyBCD to fix this ,but now i even can not start win7,it said no valid entry in boot.What a tragic

---

### Post by darkod on 2012-02-25
Run the boot info script as suggested in my previous post. We can't help you blind, we have no idea what you have on your computer.

---

### Post by beyondlimit on 2012-02-25
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 0.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/BCD

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 1697256 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       616,447       614,400   7 NTFS / exFAT / HPFS
/dev/sda2             616,448    77,304,779    76,688,332   7 NTFS / exFAT / HPFS
/dev/sda3          77,302,795   589,496,311   512,193,517   f W95 Extended (LBA)
/dev/sda5          77,304,843   118,447,244    41,142,402   7 NTFS / exFAT / HPFS
/dev/sda6         118,447,308   224,508,374   106,061,067   7 NTFS / exFAT / HPFS
/dev/sda7         224,508,438   438,494,174   213,985,737   7 NTFS / exFAT / HPFS
/dev/sda8         438,505,472   589,496,311   150,990,840   7 NTFS / exFAT / HPFS
/dev/sda4         589,505,175   625,137,344    35,632,170   7 NTFS / exFAT / HPFS

/dev/sda2 overlaps with /dev/sda3

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4041 MB, 4041211904 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,892,991     7,892,929   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        EA5ADFF45ADFBB8F                       ntfs       SYSTEM
/dev/sda2        01CB5F0F522E8640                       ntfs       donnot touch!!
/dev/sda4        9874ABE474ABC37C                       ntfs       K
/dev/sda5        01CCF3630A1211D0                       ntfs       &#23089;&#20048;
/dev/sda6        01CCF38AF450BC70                       ntfs       &#23454;&#29992;&#24037;&#20855;
/dev/sda7        01CCF38AA154AFE0                       ntfs       j
/dev/sda8        2FB8047CB15E3264                       ntfs       &#24037;&#20316;
/dev/sdb1        0008-611E                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(7)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(7)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)
 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  27 60 fa 60 10 62 1f 66  5f 66 29 73 f9 73 db 76  |'`.`.b.f_f)s.s.v|
00000010  01 77 6c 7b fe ff fe ff  fe ff fe ff fe ff fe ff  |.wl{............|
00000020  fe ff fe ff fe ff fe ff  fe ff fe ff fe ff fe ff  |................|
*
000000d0  fe ff fe ff 56 80 72 80  65 81 a0 8a 92 91 16 4e  |....V.r.e......N|
000000e0  e2 52 72 6b 17 6d 05 7a  39 7b 30 7d 6f f9 b0 8c  |.Rrk.m.z9{0}o...|
000000f0  ec 53 2f 56 51 58 b5 5b  0f 5c 11 5c e2 5d 40 62  |.S/VQX.[.\.\.]@b|
00000100  83 63 14 64 2d 66 b3 68  bc 6c 88 6d af 6e 1f 70  |.c.d-f.h.l.m.n.p|
00000110  a4 70 d2 71 26 75 8f 75  8e 75 19 76 11 7b e0 7b  |.p.q&u.u.u.v.{.{|
00000120  2b 7c 20 7d 39 7d 2c 85  6d 85 07 86 34 8a 0d 90  |+| }9},.m...4...|
00000130  61 90 b5 90 b7 92 f6 97  37 9a d7 4f 6c 5c 5f 67  |a.......7..Ol\_g|
00000140  91 6d 9f 7c 8c 7e 16 8b  16 8d 1f 90 6b 5b fd 5d  |.m.|.~......k[.]|
00000150  0d 64 c0 84 5c 90 e1 98  87 73 8b 5b 9a 60 7e 67  |.d..\....s.[.`~g|
00000160  de 6d 1f 8a a6 8a 01 90  0c 98 37 52 70 f9 51 70  |.m........7Rp.Qp|
00000170  8e 78 96 93 70 88 d7 91  ee 4f d7 53 fd 55 da 56  |.x..p....O.S.U.V|
00000180  82 57 fd 58 c2 5a 88 5b  ab 5c c0 5c 25 5e 01 61  |.W.X.Z.[.\.\%^.a|
00000190  fe ff fe ff fe ff fe ff  fe ff fe ff fe ff fe ff  |................|
*
000001b0  fe ff fe ff fe ff fe ff  fe ff fe ff fe ff 00 fe  |................|
000001c0  ff ff 07 fe ff ff 00 08  00 00 82 c8 73 02 00 fe  |............s...|
000001d0  ff ff 05 fe ff ff 82 d0  73 02 4a 5d 52 06 00 00  |........s.J]R...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by beyondlimit on 2012-02-25
Above is what i got by did what you suggested

---

### Post by darkod on 2012-02-25
Your boot files are a mess.

Boot your ubuntu cd in live mode and also have a usb stick at hand to move some files on it instead of deleting them, just in case you need them later.

Open the partition /dev/sda1 and move to the usb stick the files:
- boot.ini
- ntldr
- ntdetect.com

Then open /dev/sda2 and move to the stick:
- bootmgr
- boot/BCD
- wubildr
- wubildr.mbr

Restart and see if that loads win7 from the hdd.

You have no ubuntu install, you do have some traces of wubi install (ubuntu inside windows) but not the main install also.

If the above makes win7 booting then you can think about the next steps you want to take.

---

### Post by Mark Phelps on 2012-02-25
Even if you do get Win7 booting, you can NOT install Ubuntu -- because it looks like you already have the maximum of three Primary and one Extended partition on your drive.  The installer won't let you create any more partitions.

---

