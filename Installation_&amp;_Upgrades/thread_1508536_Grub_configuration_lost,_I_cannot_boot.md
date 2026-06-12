---
title: "Grub configuration lost, I cannot boot"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by Peppuzzo on 2010-06-13
I have accidentally started the recovery OS of my netbook, and messed-up grub.
I can start the Netbook from a live CD, but I do not manage to restore grub to anything useful. Below the outcome of the Boot Info Script I have found in the forum::confused:

```

                               Boot Info Script 0.55    dated February 15th,  2010                    

============================= Boot Info  Summary: ==============================

 => Grub 0.97 is  installed in the MBR of /dev/sda and looks on the same drive 
    in  partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 =>  Syslinux is installed in the MBR of /dev/sdb

sda1:  _________________________________________________________________________

     File system:       ntfs
    Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  Windows 7
    Boot files/dirs:   /bootmgr  /Boot/BCD /Windows/System32/winload.exe

sda2:  _________________________________________________________________________

     File system:       Extended Partition
    Boot sector type:  -
     Boot sector info:  

sda5:  _________________________________________________________________________

     File system:       ext2
    Boot sector type:  -
    Boot sector  info:  
    Operating System:  
    Boot files/dirs:   

sda6:   _________________________________________________________________________

     File system:       swap
    Boot sector type:  -
    Boot sector  info:  

sda7:  _________________________________________________________________________

     File system:       ext2
    Boot sector type:  -
    Boot sector  info:  
    Operating System:  
    Boot files/dirs:   

sda8:   _________________________________________________________________________

     File system:       ntfs
    Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
    Boot files/dirs:   

sda3:  _________________________________________________________________________

     File system:       vfat
    Boot sector type:  Vista: Fat 32
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4:   _________________________________________________________________________

     File system:       
    Boot sector type:  Unknown
    Boot  sector info:  
    Mounting failed:
mount: unknown filesystem type  ''

sdb1:  _________________________________________________________________________

     File system:       vfat
    Boot sector type:  Fat32
    Boot  sector info:  According to the info in the boot sector, sdb1 starts 
                        at sector 0. But according to the info from fdisk, 
                        sdb1 starts at sector 62.
    Operating System:  
    Boot  files/dirs:   

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk  /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track,  30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 =  512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition   Boot         Start           End          Size  Id System

/dev/sda1     *          2,048   118,737,245   118,735,198   7 HPFS/NTFS
/dev/sda2          118,738,942   467,379,044   348,640,103   5 Extended
/dev/sda5          209,728,638   257,650,469    47,921,832  83 Linux
/dev/sda6          257,650,533   261,843,434     4,192,902  82 Linux swap / Solaris
/dev/sda7          261,843,498   365,848,244   104,004,747  83 Linux
/dev/sda8          365,848,308   467,379,044   101,530,737   7 HPFS/NTFS
/dev/sda3          467,386,368   488,357,887    20,971,520  1b Hidden W95 FAT32
/dev/sda4          488,357,888   488,392,064        34,177  1b Hidden W95 FAT32


Drive:  sdb ___________________  _____________________________________________________

Disk  /dev/sdb: 2032 MB, 2032664576 bytes
63 heads, 62 sectors/track, 1016  cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512  bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition   Boot         Start           End          Size  Id System

/dev/sdb1     *             62     3,968,495     3,968,434   c W95 FAT32 (LBA)


blkid  -c /dev/null:  ____________________________________________________________

Device            UUID                                   TYPE        LABEL                         

/dev/loop0                                               squashfs                                 
/dev/sda1         76708D71708D393F                        ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3         86F4-D40A                              vfat        „z¨ª˜š©˜ˆ™˜                   
/dev/sda5         52a1f00c-3489-4f89-8645-15ed11fd4071   ext2        linuxos                       
/dev/sda6         baa83723-8698-4cbc-a7f6-fc69e6cabfb1   swap        linux-swap                    
/dev/sda7         887f9334-80d8-4ad8-a5f1-b5ec12d954a9   ext2       linux  data                    
/dev/sda8         795F2895216CD401                       ntfs       windows  data                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1         29F5-F9D6                               vfat                                     
/dev/sdb: PTTYPE="dos" 

============================  "mount | grep ^/dev  output: ===========================

Device            Mount_Point              Type       Options

aufs              /                        aufs       (rw)
/dev/sdb1         /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0        /rofs                    squashfs   (ro,noatime)


===================  sda5: Location of files loaded by Grub: ===================


 108.8GB: boot/grub/stage2
=========================== Unknown  MBRs/Boot Sectors/etc =======================

Unknown BootLoader   on sda4

00000000  55 aa 03 e9 7a 00 93 00  00 00 00 00 00 00 00  00  |U...z...........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00  00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00   ff ff 00 00 00 9b cf 00  |................|
00000030  ff ff 00 00 00  93 cf 00  ff ff 00 00 00 9a 0f 00  |................|
00000040  ff ff  00 00 00 92 0f 00  27 00 20 00 00 00 00 00  |........'. .....|
00000050   ff ff 00 00 00 00 00 00  10 00 44 65 76 69 63 65  |..........Device|
00000060   56 4d 20 52 6f 6d 20 4c  6f 61 64 65 72 00 00 00  |VM Rom Loader...|
00000070   01 31 31 2f 32 32 2f 32  30 30 37 00 00 00 00 00  |.11/22/2007.....|
00000080   0e 58 2e a3 42 02 68 00  00 1f 68 00 00 07 57 2e  |.X..B.h...h...W.|
00000090   8d 3e 00 06 2e 80 7d 20  03 75 17 9c 60 b8 03 00  |.>....} .u..`...|
000000a0   cd 10 61 9d 2e 8d 3e 8c  03 e8 fd 02 b4 00 50 cd  |..a...>.......P.|
000000b0   16 58 5f b8 03 00 c1 e0  09 89 c3 0e 07 26 66 8b   |.X_..........&f.|
000000c0  47 0c 66 85 c0 74 05 2e  66 a3 56 00  fa 66 31 c0  |G.f..t..f.V..f1.|
000000d0  8c c8 66 c1 e0 04 2e 66   01 06 4a 00 fb 2e 66 a3  |..f....f..J...f.|
000000e0  3a 00 b0 9a 2e  a2 3d 00  66 50 e8 25 03 66 58 66  |:.....=.fP.%.fXf|
000000f0  50 66  51 1e c8 0c 00 00  0e 1f 66 31 c0 3e a1 06  |PfQ.......f1.>..|
00000100   00 66 c1 e0 09 66 2d 03  00 00 00 66 50 2e 66 a1  |.f...f-....fP.f.|
00000110   56 00 66 50 66 31 c0 66  31 c9 b9 00 06 8c c8 66  |V.fPf1.f1......f|
00000120   c1 e0 04 66 01 c8 66 50  e8 cb 01 c9 1f 66 59 66  |...f..fP.....fYf|
00000130   58 fa 2e 0f 01 16 48 00  0f 20 c0 0c 01 0f 22 c0  |X.....H.. ....".|
00000140   2e 66 8b 36 56 00 66 67  66 67 8b 06 66 3d eb 3e  |.f.6V.fgfg..f=.>|
00000150   45 54 74 14 0f 20 c0 24  fe 0f 22 c0 57 2e 8d 3e  |ETt.. .$..".W..>|
00000160   5a 03 e8 44 02 5f cd 18  0f 20 c0 24 fe 0f 22 c0  |Z..D._... .$..".|
00000170   06 53 8c cb 8e c3 bb 00  06 e8 e0 00 5b 07 c8 0c  |.S..........[...|
00000180   00 00 66 b8 00 02 00 00  66 50 2e 66 a1 56 00 66  |..f.....fP.f.V.f|
00000190   50 66 31 c0 66 31 c9 b9  00 06 8c c8 66 c1 e0 04  |Pf1.f1......f...|
000001a0   66 01 c8 66 50 e8 4e 01  c9 2e 66 8b 36 56 00 66  |f..fP.N...f.6V.f|
000001b0   89 e0 66 50 16 66 29 db  bb 48 00 66 29 c9 8c c9  |..fP.f)..H.f)...|
000001c0   66 c1 e1 04 66 01 d9 66  51 66 29 c0 66 29 c9 b8  |f...f..fQf).f)..|
000001d0   08 00 66 50 b8 14 02 8c  c9 66 c1 e1 04 66 01 c1  |..fP.....f...f..|
000001e0   66 51 66 29 c0 89 e0 66  29 c9 8c d1 66 c1 e1 04  |fQf)...f)...f...|
000001f0   66 01 c1 fa 2e 0f 01 16  48 00 0f 20 c0 0c 01 0f  |f.......H.. ....|
00000200

```

anyone could help?

---

### Post by wilee-nilee on 2010-06-13
I see you have the bcd boot in windows, but you have been using grub to boot is this correct?

---

### Post by Peppuzzo on 2010-06-13
Yes, this is correct

---

### Post by wilee-nilee on 2010-06-13
> **Peppuzzo said:**
> Yes, this is correct

I'm not familiar enough with grub-legacy but people are on line daytime US that are.

---

### Post by Peppuzzo on 2010-06-13
Yes, this is correct indeed. Shall I run the script?

---

### Post by wilee-nilee on 2010-06-13
> **Peppuzzo said:**
> Yes, this is correct indeed. Shall I run the script?

What script? the one in my sig is the one you posted, if you do any tweaking and it doesn't get working, run the boot script again. I would wait for some help though. You might give a description of exactly whats going on when you boot, I assume that you just get a blinking cursor. Also how far into the recovery did it get and what did you do. This shouldn't have broken grub, but it seems it has so more info will help those that know some fixes.

---

### Post by Peppuzzo on 2010-06-13
> **wilee-nilee said:**
> What script? the one in my sig is the one you posted, if you do any tweaking and it doesn't get working, run the boot script again. I would wait for some help though. You might give a description of exactly whats going on when you boot, I assume that you just get a blinking cursor. Also how far into the recovery did it get and what did you do. This shouldn't have broken grub, but it seems it has so more info will help those that know some fixes.

Thanks for your quick reply. Ok, I re-run the script and post the code below

when I boot I get the grub prompt and do not get much further than that.
I have tried some of the tricks in the forums [(http://www.sorgonet.com/linux/grubrestore/)]("http://www.sorgonet.com/linux/grubrestore/"), by installing grub and try to mount some devices, but I do not get the grub menu when I reboot, only the grub prompt.

What has broken grub in the first place, I suspect, is the Vista recovery mode of the Netbook, which I started by mistake; the tool went into recovery mode, and asked me if I wanted to go further, I clicked on no, but damage was done nevertheless.

               ```
 
               Boot Info Script 0.55    dated February 15th,  2010                    

============================= Boot Info  Summary: ==============================

 => Grub 0.97 is  installed in the MBR of /dev/sda and looks on the same drive 
    in  partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 =>  Syslinux is installed in the MBR of /dev/sdb

sda1:  _________________________________________________________________________

     File system:       ntfs
    Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  Windows 7
    Boot files/dirs:   /bootmgr  /Boot/BCD /Windows/System32/winload.exe

sda2:  _________________________________________________________________________

     File system:       Extended Partition
    Boot sector type:  -
     Boot sector info:  

sda5:  _________________________________________________________________________

     File system:       ext2
    Boot sector type:  -
    Boot sector  info:  
    Operating System:  
    Boot files/dirs:   

sda6:   _________________________________________________________________________

     File system:       swap
    Boot sector type:  -
    Boot sector  info:  

sda7:  _________________________________________________________________________

     File system:       ext2
    Boot sector type:  -
    Boot sector  info:  
    Operating System:  
    Boot files/dirs:   

sda8:   _________________________________________________________________________

     File system:       ntfs
    Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
    Boot files/dirs:   

sda3:  _________________________________________________________________________

     File system:       vfat
    Boot sector type:  Vista: Fat 32
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4:   _________________________________________________________________________

     File system:       
    Boot sector type:  Unknown
    Boot  sector info:  
    Mounting failed:
mount: unknown filesystem type  ''

sdb1:  _________________________________________________________________________

     File system:       vfat
    Boot sector type:  Fat32
    Boot  sector info:  According to the info in the boot sector, sdb1 starts 
                        at sector 0. But according to the info from fdisk, 
                        sdb1 starts at sector 62.
    Operating System:  
    Boot  files/dirs:   

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk  /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track,  30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 =  512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition   Boot         Start           End          Size  Id System

/dev/sda1     *          2,048   118,737,245   118,735,198   7 HPFS/NTFS
/dev/sda2          118,738,942   467,379,044   348,640,103   5 Extended
/dev/sda5          209,728,638   257,650,469    47,921,832  83 Linux
/dev/sda6          257,650,533   261,843,434     4,192,902  82 Linux swap / Solaris
/dev/sda7          261,843,498   365,848,244   104,004,747  83 Linux
/dev/sda8          365,848,308   467,379,044   101,530,737   7 HPFS/NTFS
/dev/sda3          467,386,368   488,357,887    20,971,520  1b Hidden W95 FAT32
/dev/sda4          488,357,888   488,392,064        34,177  1b Hidden W95 FAT32


Drive:  sdb ___________________  _____________________________________________________

Disk  /dev/sdb: 2032 MB, 2032664576 bytes
63 heads, 62 sectors/track, 1016  cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512  bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition   Boot         Start           End          Size  Id System

/dev/sdb1     *             62     3,968,495     3,968,434   c W95 FAT32 (LBA)


blkid  -c /dev/null:  ____________________________________________________________

Device            UUID                                   TYPE        LABEL                         

/dev/loop0                                               squashfs                                 
/dev/sda1         76708D71708D393F                        ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3         86F4-D40A                              vfat        „z¨ª˜š©˜ˆ™˜                   
/dev/sda5         52a1f00c-3489-4f89-8645-15ed11fd4071   ext2        linuxos                       
/dev/sda6         baa83723-8698-4cbc-a7f6-fc69e6cabfb1   swap        linux-swap                    
/dev/sda7         887f9334-80d8-4ad8-a5f1-b5ec12d954a9   ext2       linux  data                    
/dev/sda8         795F2895216CD401                       ntfs       windows  data                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1         29F5-F9D6                               vfat                                     
/dev/sdb: PTTYPE="dos" 

============================  "mount | grep ^/dev  output: ===========================

Device            Mount_Point              Type       Options

aufs              /                        aufs       (rw)
/dev/sdb1         /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0        /rofs                    squashfs   (ro,noatime)


===================  sda5: Location of files loaded by Grub: ===================


 108.8GB: boot/grub/stage2
=========================== Unknown  MBRs/Boot Sectors/etc =======================

Unknown BootLoader   on sda4

00000000  55 aa 03 e9 7a 00 93 00  00 00 00 00 00 00 00  00  |U...z...........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00  00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00   ff ff 00 00 00 9b cf 00  |................|
00000030  ff ff 00 00 00  93 cf 00  ff ff 00 00 00 9a 0f 00  |................|
00000040  ff ff  00 00 00 92 0f 00  27 00 20 00 00 00 00 00  |........'. .....|
00000050   ff ff 00 00 00 00 00 00  10 00 44 65 76 69 63 65  |..........Device|
00000060   56 4d 20 52 6f 6d 20 4c  6f 61 64 65 72 00 00 00  |VM Rom Loader...|
00000070   01 31 31 2f 32 32 2f 32  30 30 37 00 00 00 00 00  |.11/22/2007.....|
00000080   0e 58 2e a3 42 02 68 00  00 1f 68 00 00 07 57 2e  |.X..B.h...h...W.|
00000090   8d 3e 00 06 2e 80 7d 20  03 75 17 9c 60 b8 03 00  |.>....} .u..`...|
000000a0   cd 10 61 9d 2e 8d 3e 8c  03 e8 fd 02 b4 00 50 cd  |..a...>.......P.|
000000b0   16 58 5f b8 03 00 c1 e0  09 89 c3 0e 07 26 66 8b   |.X_..........&f.|
000000c0  47 0c 66 85 c0 74 05 2e  66 a3 56 00  fa 66 31 c0  |G.f..t..f.V..f1.|
000000d0  8c c8 66 c1 e0 04 2e 66   01 06 4a 00 fb 2e 66 a3  |..f....f..J...f.|
000000e0  3a 00 b0 9a 2e  a2 3d 00  66 50 e8 25 03 66 58 66  |:.....=.fP.%.fXf|
000000f0  50 66  51 1e c8 0c 00 00  0e 1f 66 31 c0 3e a1 06  |PfQ.......f1.>..|
00000100   00 66 c1 e0 09 66 2d 03  00 00 00 66 50 2e 66 a1  |.f...f-....fP.f.|
00000110   56 00 66 50 66 31 c0 66  31 c9 b9 00 06 8c c8 66  |V.fPf1.f1......f|
00000120   c1 e0 04 66 01 c8 66 50  e8 cb 01 c9 1f 66 59 66  |...f..fP.....fYf|
00000130   58 fa 2e 0f 01 16 48 00  0f 20 c0 0c 01 0f 22 c0  |X.....H.. ....".|
00000140   2e 66 8b 36 56 00 66 67  66 67 8b 06 66 3d eb 3e  |.f.6V.fgfg..f=.>|
00000150   45 54 74 14 0f 20 c0 24  fe 0f 22 c0 57 2e 8d 3e  |ETt.. .$..".W..>|
00000160   5a 03 e8 44 02 5f cd 18  0f 20 c0 24 fe 0f 22 c0  |Z..D._... .$..".|
00000170   06 53 8c cb 8e c3 bb 00  06 e8 e0 00 5b 07 c8 0c  |.S..........[...|
00000180   00 00 66 b8 00 02 00 00  66 50 2e 66 a1 56 00 66  |..f.....fP.f.V.f|
00000190   50 66 31 c0 66 31 c9 b9  00 06 8c c8 66 c1 e0 04  |Pf1.f1......f...|
000001a0   66 01 c8 66 50 e8 4e 01  c9 2e 66 8b 36 56 00 66  |f..fP.N...f.6V.f|
000001b0   89 e0 66 50 16 66 29 db  bb 48 00 66 29 c9 8c c9  |..fP.f)..H.f)...|
000001c0   66 c1 e1 04 66 01 d9 66  51 66 29 c0 66 29 c9 b8  |f...f..fQf).f)..|
000001d0   08 00 66 50 b8 14 02 8c  c9 66 c1 e1 04 66 01 c1  |..fP.....f...f..|
000001e0   66 51 66 29 c0 89 e0 66  29 c9 8c d1 66 c1 e1 04  |fQf)...f)...f...|
000001f0   66 01 c1 fa 2e 0f 01 16  48 00 0f 20 c0 0c 01 0f  |f.......H.. ....|
00000200

```

---

### Post by wilee-nilee on 2010-06-13
I had not noticed before but sda5 appears to be the Linux OS, and there are no grub files listed there or anywhere so I think this will definitely take somebody who knows what to do.

---

### Post by Peppuzzo on 2010-06-13
Indeed. Thanks anyhow so far. I will wait form some help from someone expert on the matter..

---

### Post by darkod on 2010-06-13
Unfortunately losing grub1 on the MBR is not the only damage. Here:

sda5:  _________________________________________________________________________

     File system:       ext2
    Boot sector type:  -
    Boot sector  info:  
    Operating System:  
    Boot files/dirs:

Not only that there are no ubuntu boot files on sda5 which seems to be your root partition, but it's not even recognized as Ubuntu OS.

If you have important data there, you can try restoring it with Testdisk or Photorec. If you don't, maybe reinstalling in your existing partitions is the best and fastest way.
Note that when you want to install linux in existing partitions, you need to use the manual partitioning and tell it what partition to use for what. It doesn't do it automatically and if you use the side-by-side guided option it will just create another parallel installation.

If you open sda5 in live mode can you see the files inside, is the folder structure still there? The /boot folder with the kernel files inside? The /boot/grub folder?

---

### Post by Peppuzzo on 2010-06-13
> **darkod said:**
> Unfortunately losing grub1 on the MBR is not the only damage. Here:

sda5:  _________________________________________________________________________

     File system:       ext2
    Boot sector type:  -
    Boot sector  info:  
    Operating System:  
    Boot files/dirs:

Not only that there are no ubuntu boot files on sda5 which seems to be your root partition, but it's not even recognized as Ubuntu OS.

If you have important data there, you can try restoring it with Testdisk or Photorec. If you don't, maybe reinstalling in your existing partitions is the best and fastest way.
Note that when you want to install linux in existing partitions, you need to use the manual partitioning and tell it what partition to use for what. It doesn't do it automatically and if you use the side-by-side guided option it will just create another parallel installation.

If you open sda5 in live mode can you see the files inside, is the folder structure still there? The /boot folder with the kernel files inside? The /boot/grub folder?

I have no important data there, so I will go for a re-installation in sda5, I am afraid. Thanks for the warning as well. I see a structure with /boot and /boot/grub directory, but the boot directory looks pretty empty to me

---

### Post by Peppuzzo on 2010-06-13
I am trying to reinstall ubuntu on the sda5 partition, but I get the error that root is not present there. 

It says: 

```
No root file system is defined

Please correct this from the partitioning menu.

```
How to do tha?

---

### Post by darkod on 2010-06-13
In Manual Partitioning, you need to select the partition from the list, then click the Change button on bottom. It will allow to select filesystem ext4, tick the format box, and set mount point as /.

That is how you specify what partition to be used for what manually. The swap partition should be detected and used automatically but you can double check by selecting it and the Change button again, and specify to be used as swap area. There is no format and mount point for swap.

---

### Post by Peppuzzo on 2010-06-13
Thanks Darko. It is happily installing now.:)

---

### Post by Peppuzzo on 2010-06-13
Solved. Thanks very much.

---

