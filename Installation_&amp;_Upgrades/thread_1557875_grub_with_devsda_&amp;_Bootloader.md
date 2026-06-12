---
title: "grub with /dev/sda/ &amp; Bootloader"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by freemankofi on 2010-08-21
Hi,
I am new to linux, specifically ubuntu. I am trying for have dual booting with my Windows XP. 

During installation of Ubuntu 10.04 LTS, everything was OKAY until installation of 'grub'. grub failed with FATAL ERROR... it kept looking for a /dev/sda disk... when installing GRUB. An option was given to select another disk which I did by choosing one from the drop down and press OK. However, IT just kept on trying  to access /dev/sda disk... again. In the end, I to have to skip it and my computer restarted. However, I can't even see ubuntu.

I have to say that, I reinstalled it. In the stage where it displayed my information, I clicked on 'advance' option which allowed me to select the location of the 'boot loder'. I did, however, it looks like 'grub' has been wired to use /dev/sda. When it came to installing grub it was still looking for this '/dev/sda disk'.

I have read so many postings on boot loader, but none seems to fix my problem. Because, ALL talked about getting a 'prompt' or something like. My case is I don't get the prompt and let alone change any path.

 
This is a bit of frustration, since I really need to get this working. Any help on this will be much appreciated. 

Freeman

---

### Post by Rubi1200 on 2010-08-21
If you have the Ubuntu CD you used for installation, then boot the computer with it choosing the option to try not install.

Then, click on the link at the bottom of my post and follow the instructions there.

Post the results back here and wrap the text with the # tag please.

Thanks.

---

### Post by freemankofi on 2010-08-21
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/mapper/sil_ahbiaecebgej

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sil_ahbiaecebgej1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sil_ahbiaecebgej2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sil_ahbiaecebgej5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1                 256 1,941,488,383 1,941,488,128  83 Linux
/dev/sda2       1,941,488,638 1,953,542,143    12,053,506   5 Extended
Invalid MBR Signature found
/dev/sda5     ? 1,941,488,638 1,941,488,637                   Unknown
/dev/sda6     ? 1,941,488,638 1,941,488,637                   Unknown

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda2

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   292,307,181   292,307,119   7 HPFS/NTFS
/dev/sdc2         292,308,990   625,141,759   332,832,770   5 Extended
/dev/sdc5         292,308,992   613,089,279   320,780,288  83 Linux
/dev/sdc6         613,091,328   625,141,759    12,050,432  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1998 MB, 1998585856 bytes
129 heads, 32 sectors/track, 945 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32     3,903,487     3,903,456   6 FAT16


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1999 MB, 1999568384 bytes
32 heads, 63 sectors/track, 1937 cylinders, total 3905407 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63     3,904,991     3,904,929   6 FAT16


Drive: sil_ahbiaecebgej ___________________ _____________________________________________________

Disk /dev/mapper/sil_ahbiaecebgej: 1000.2 GB, 1000213577728 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953542144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/sil_ahbiaecebgej1                256 1,941,488,383 1,941,488,128  83 Linux
/dev/mapper/sil_ahbiaecebgej2      1,941,488,638 1,953,542,143    12,053,506   5 Extended
/dev/mapper/sil_ahbiaecebgej5      1,941,488,640 1,953,542,143    12,053,504  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/sil_ahbiaecebgej1 4bf2d025-af5b-43d7-aea1-13f9545856e5   ext4                                     
/dev/mapper/sil_ahbiaecebgej5 41892152-3f1d-412e-873b-a2a6800f4a26   swap                                     
/dev/mapper/sil_ahbiaecebgej: PTTYPE="dos" 
/dev/sda                                                silicon_medley_raid_member                               
/dev/sdb                                                silicon_medley_raid_member                               
/dev/sdc1        AC5814FE5814C8CA                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        a0fd67be-fe4c-4fc3-a945-f8e23ddd555c   ext4                                     
/dev/sdc6        4febea37-837e-4837-8149-0b12cc8f44e0   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        2046-B84A                              vfat       FREEMANMOBI                   
/dev/sdd: PTTYPE="dos" 
/dev/sde1        161F-5BAA                              vfat       KINGSTON                      
/dev/sde: PTTYPE="dos" 
error: /dev/mapper/sil_ahbiaecebgej2: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
sil_ahbiaecebgej
sil_ahbiaecebgej1
sil_ahbiaecebgej5

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc5        /media/a0fd67be-fe4c-4fc3-a945-f8e23ddd555c ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=a0fd67be-fe4c-4fc3-a945-f8e23ddd555c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=4febea37-837e-4837-8149-0b12cc8f44e0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

========================= sil_ahbiaecebgej1/etc/fstab: =========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/sil_ahbiaecebgej1 /               ext4    errors=remount-ro 0       1
/dev/mapper/sil_ahbiaecebgej5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

============= sil_ahbiaecebgej1: Location of files loaded by Grub: =============


 354.4GB: boot/grub/core.img
  12.0GB: boot/initrd.img-2.6.32-24-generic
 354.4GB: boot/vmlinuz-2.6.32-24-generic
  12.0GB: initrd.img
 354.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on sdc2

00000000  45 32 53 46 45 0a 0d 46  45 ac c6 46 45 80 ad 45  |E2SFE..FE..FE..E|
00000010  45 b2 91 46 45 72 4d 45  45 7b 49 41 45 bd 71 52  |E..FErMEE{IAE.qR|
00000020  45 69 95 51 45 62 0a 52  45 66 07 50 45 36 ef 50  |Ei.QEb.REf.PE6.P|
00000030  45 40 4a 54 45 30 c8 54  45 93 c5 55 45 73 31 56  |E@JTE0.TE..UEs1V|
00000040  45 19 e0 56 45 1a 7b 55  45 a1 49 69 45 6e 76 67  |E..VE.{UE.IiEnvg|
00000050  45 02 af 68 45 0d bf 65  45 8e d4 68 45 d5 41 69  |E..hE..eE..hE.Ai|
00000060  45 82 cd 67 45 43 9f 4f  45 69 71 4d 45 35 2a 4e  |E..gEC.OEiqME5*N|
00000070  45 2f ea 4b 45 3b 70 4c  45 45 44 4e 45 cb 5d 4c  |E/.KE;pLEEDNE.]L|
00000080  45 58 35 4d 45 a7 e4 40  45 04 ae 3f 45 2f 9e 4a  |EX5ME..@E..?E/.J|
00000090  45 64 fd 49 45 18 3b 4a  45 03 9c 49 45 5d cd 50  |Ed.IE.;JE..IE].P|
000000a0  45 48 27 4f 45 95 1e 4e  45 a8 f0 4e 45 69 a7 4e  |EH'OE..NE..NEi.N|
000000b0  45 71 a5 50 45 e2 63 50  45 f7 79 51 45 0d b7 50  |Eq.PE.cPE.yQE..P|
000000c0  45 be 6c 51 45 ea e1 50  45 72 1a 51 45 f1 d0 4f  |E.lQE..PEr.QE..O|
000000d0  45 12 da 50 45 9d 0e 50  45 bd 1a 50 45 1b 25 53  |E..PE..PE..PE.%S|
000000e0  45 70 d6 53 45 6c ef 53  45 34 a3 53 45 89 bd 52  |Ep.SEl.SE4.SE..R|
000000f0  45 a7 fc 51 45 e5 0b 52  45 b6 cc 51 45 7f 12 4a  |E..QE..RE..QE..J|
00000100  45 f2 b0 49 45 e7 a2 49  45 f5 11 49 45 61 41 48  |E..IE..IE..IEaAH|
00000110  45 de 56 48 45 f6 bc 48  45 a0 1e 48 45 fa c1 47  |E.VHE..HE..HE..G|
00000120  45 bb 12 48 45 92 7f 47  45 62 24 48 45 5b 90 47  |E..HE..GEb$HE[.G|
00000130  45 7b 86 53 45 51 6e 51  45 c7 07 53 45 a2 64 51  |E{.SEQnQE..SE.dQ|
00000140  45 f4 79 53 45 47 46 51  45 7d da 52 45 ad 98 48  |E.ySEGFQE}.RE..H|
00000150  45 cb 99 48 45 a2 ef 48  45 98 10 48 45 2d b8 47  |E..HE..HE..HE-.G|
00000160  45 c8 5b 47 45 d0 b8 4e  45 2c d8 4e 45 d3 7b 50  |E.[GE..NE,.NE.{P|
00000170  45 d2 67 4f 45 7d 1d 51  45 de 07 50 45 d3 97 59  |E.gOE}.QE..PE..Y|
00000180  45 eb ea 58 45 5d e4 56  45 61 53 58 45 7a 15 57  |E..XE].VEaSXEz.W|
00000190  45 97 e2 57 45 8b a0 50  45 8b f8 4d 45 d6 27 50  |E..WE..PE..ME.'P|
000001a0  45 3c 9a 4f 45 20 d4 4c  45 8b 55 4c 45 c8 ed 4f  |E<.OE .LE.ULE..O|
000001b0  45 17 40 51 45 71 14 8d  45 ba f4 89 45 3d 00 fe  |E.@QEq..E...E=..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 1e 13 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 b8  1e 13 00 e8 b7 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sil_ahbiaecebgej2



=======Devices which don't seem to have a corresponding hard drive==============

sdf sdg sdh sdi 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/mapper/sil_ahbiaecebgej2: No such file or directory
hexdump: /dev/mapper/sil_ahbiaecebgej2: No such file or directory #

---

### Post by freemankofi on 2010-08-21
Thanks. I have done it accordingly. Please, let me know if you need additional information.

---

