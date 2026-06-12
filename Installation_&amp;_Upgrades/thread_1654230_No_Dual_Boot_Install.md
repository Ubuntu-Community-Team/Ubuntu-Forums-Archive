---
title: "No Dual Boot Install"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by abanta11 on 2010-12-28
SO, I currently have this exact same problem as another poster- no option to install alongside another OS.

I have Win7 Starter on this new netbook and need to install Ubuntu 10.10 netbook addition.

Disk Management shows 4 partitions, one is C:, one is D:, and two I've never seen before they're so small. Is it safe to delete these or do they have a purpose for the current Win OS?

I would gladly install the 10.10 to my D: drive which seems to be SDA2, the 131GB partition. What's the right sequence of partitioning and formatting to give Ubuntu the full install it needs manually?

And what needs to be taken care of for a Swap drive?


This is a lifesaver! (As you can probably tell)

---

### Post by karthick87 on 2010-12-28
Delete the D partition.And during installation choose freespace..

---

### Post by Quackers on 2010-12-28
Do you know why you have a EFI partition?

---

### Post by abanta11 on 2010-12-28
I don't even know what that stands for! It can't be deleted, though.

Are D: and the 10GB space deletable? 

Also, can Ubuntu and Windows save and index between the partitions? Stupid question, but My Documents will still be My Documents whether I'm using either OS?

---

### Post by Quackers on 2010-12-28
Hmm, you may, for some reason, have a GUID Partition Table, which will make things more involved.
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by abanta11 on 2010-12-28
Not what I was expecting, but here I go!

---

### Post by abanta11 on 2010-12-28
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,717,248   467,386,367   257,669,120   7 HPFS/NTFS
/dev/sda3         467,386,368   488,357,887    20,971,520  1b Hidden W95 FAT32
/dev/sda4         488,357,888   488,392,064        34,177  ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DA343B57343B35BB                       ntfs                                     
/dev/sda2        AAAEF70BAEF6CF37                       ntfs                                     
/dev/sda3        86F4-D40A                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         0A0C-0F46                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  55 aa 03 e9 7a 00 93 00  00 00 00 00 00 00 00 00  |U...z...........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  ff ff 00 00 00 9b cf 00  |................|
00000030  ff ff 00 00 00 93 cf 00  ff ff 00 00 00 9a 0f 00  |................|
00000040  ff ff 00 00 00 92 0f 00  27 00 20 00 00 00 00 00  |........'. .....|
00000050  ff ff 00 00 00 00 00 00  10 00 44 65 76 69 63 65  |..........Device|
00000060  56 4d 20 52 6f 6d 20 4c  6f 61 64 65 72 00 00 00  |VM Rom Loader...|
00000070  01 31 31 2f 32 32 2f 32  30 30 37 00 00 00 00 00  |.11/22/2007.....|
00000080  0e 58 2e a3 42 02 68 00  00 1f 68 00 00 07 57 2e  |.X..B.h...h...W.|
00000090  8d 3e 00 06 2e 80 7d 20  03 75 17 9c 60 b8 03 00  |.>....} .u..`...|
000000a0  cd 10 61 9d 2e 8d 3e 8c  03 e8 fd 02 b4 00 50 cd  |..a...>.......P.|
000000b0  16 58 5f b8 03 00 c1 e0  09 89 c3 0e 07 26 66 8b  |.X_..........&f.|
000000c0  47 0c 66 85 c0 74 05 2e  66 a3 56 00 fa 66 31 c0  |G.f..t..f.V..f1.|
000000d0  8c c8 66 c1 e0 04 2e 66  01 06 4a 00 fb 2e 66 a3  |..f....f..J...f.|
000000e0  3a 00 b0 9a 2e a2 3d 00  66 50 e8 25 03 66 58 66  |:.....=.fP.%.fXf|
000000f0  50 66 51 1e c8 0c 00 00  0e 1f 66 31 c0 3e a1 06  |PfQ.......f1.>..|
00000100  00 66 c1 e0 09 66 2d 03  00 00 00 66 50 2e 66 a1  |.f...f-....fP.f.|
00000110  56 00 66 50 66 31 c0 66  31 c9 b9 00 06 8c c8 66  |V.fPf1.f1......f|
00000120  c1 e0 04 66 01 c8 66 50  e8 cb 01 c9 1f 66 59 66  |...f..fP.....fYf|
00000130  58 fa 2e 0f 01 16 48 00  0f 20 c0 0c 01 0f 22 c0  |X.....H.. ....".|
00000140  2e 66 8b 36 56 00 66 67  66 67 8b 06 66 3d eb 3e  |.f.6V.fgfg..f=.>|
00000150  45 54 74 14 0f 20 c0 24  fe 0f 22 c0 57 2e 8d 3e  |ETt.. .$..".W..>|
00000160  5a 03 e8 44 02 5f cd 18  0f 20 c0 24 fe 0f 22 c0  |Z..D._... .$..".|
00000170  06 53 8c cb 8e c3 bb 00  06 e8 e0 00 5b 07 c8 0c  |.S..........[...|
00000180  00 00 66 b8 00 02 00 00  66 50 2e 66 a1 56 00 66  |..f.....fP.f.V.f|
00000190  50 66 31 c0 66 31 c9 b9  00 06 8c c8 66 c1 e0 04  |Pf1.f1......f...|
000001a0  66 01 c8 66 50 e8 4e 01  c9 2e 66 8b 36 56 00 66  |f..fP.N...f.6V.f|
000001b0  89 e0 66 50 16 66 29 db  bb 48 00 66 29 c9 8c c9  |..fP.f)..H.f)...|
000001c0  66 c1 e1 04 66 01 d9 66  51 66 29 c0 66 29 c9 b8  |f...f..fQf).f)..|
000001d0  08 00 66 50 b8 14 02 8c  c9 66 c1 e1 04 66 01 c1  |..fP.....f...f..|
000001e0  66 51 66 29 c0 89 e0 66  29 c9 8c d1 66 c1 e1 04  |fQf)...f)...f...|
000001f0  66 01 c1 fa 2e 0f 01 16  48 00 0f 20 c0 0c 01 0f  |f.......H.. ....|
00000200

Unknown BootLoader  on sdb

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 f1 00 22 3c 00 00  00 00 00 00 02 00 00 00  |...."<..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 46 0f 0c 0a 4e  4f 20 4e 41 4d 45 20 20  |..)F...NO NAME  |
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
00000100  7d 00 66 b8 6c 78 00 00  66 ba 00 00 00 00 bb 00  |}.f.lx..f.......|
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

### Post by abanta11 on 2010-12-28
Did that help, or am I pretty much back to where I was?

---

### Post by Quackers on 2010-12-28
Well, you don't appear to have a GUID Partition Table, but you do have an EFI partition, which doesn't want to mount. I've seen this before but can't remember why :-( You don't appear to have LVM so it's not that, but something installed EFI and may need it.
Your D: partition is 6% used. You could see what's in there and back it up and then delete that partition, if you want to. This would give you unallocated space for Ubuntu to install into.
Waiting for a second opinion would be a good idea too though :-)

---

### Post by bludgard on 2010-12-28
Sorry to interrupt.

You can mount the EFI from within Windows from command prompt:type->     mountvol /s command
and hit enter.

Your netbook has a partition that is used to restore the machine back to factory condition.If you delete this partition there is no going back.Even if you reimage your drive.


EDIT:Then again,some claim you can get factory conditions back if you image before you erase this partition.I didn't have any luck with it....

---

