---
title: "Grub error 15 (yet again)"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by pistachepastis on 2011-05-02
Hi all,

I am trying to restore my system to Ubuntu 10.10, using a system backup made with REMASTERSYS. 

When I reboot, I get the message:
GRUB
error:15

I found many threads discussing this issue, most notably here:
[http://ubuntuforums.org/showthread.php?t=1470597]("http://ubuntuforums.org/showthread.php?t=1470597")[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Unfortunately, the problem persists.

I ran the Boot Info Script (found here [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/") )

The output reads:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    58,605,119    58,605,057   7 HPFS/NTFS
/dev/sda2         117,210,240   175,831,424    58,621,185   7 HPFS/NTFS
/dev/sda3          58,605,181   117,210,239    58,605,059   5 Extended
/dev/sda5          58,605,183    68,372,639     9,767,457  82 Linux swap / Solaris
/dev/sda6          68,372,703   117,210,239    48,837,537  83 Linux
/dev/sda4         175,831,425   234,436,544    58,605,120  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4089 MB, 4089446400 bytes
126 heads, 62 sectors/track, 1022 cylinders, total 7987200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,983,863     7,983,802   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       ae1ae9fc-2578-46c6-a570-6bfd00c4247d   ext3                                     
/dev/sda1        88D6AB75D6AB61E4                       ntfs       windows                       
/dev/sda2        7C3AAED93AAE9026                       ntfs       data                          
/dev/sda3: PTTYPE="dos" 
/dev/sda4        ecb4e816-240e-4a13-b1a2-dbb6ae4442bd   ext3                                     
/dev/sda5        9e3c3953-2053-4ca9-bc09-81389f124619   swap                                     
/dev/sda6        5dca5b14-ffc4-40d6-98a7-44d9582d9299   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A26B-BB20                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /media/cdrom             vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5dca5b14-ffc4-40d6-98a7-44d9582d9299 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=ecb4e816-240e-4a13-b1a2-dbb6ae4442bd /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=9e3c3953-2053-4ca9-bc09-81389f124619 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  35.4GB: boot/initrd.img-2.6.35-22-generic
  35.4GB: boot/initrd.img-2.6.35-23-generic
  35.4GB: boot/initrd.img-2.6.35-24-generic
  35.4GB: boot/initrd.img-2.6.35-25-generic
  35.4GB: boot/initrd.img-2.6.35-27-generic
  35.3GB: boot/initrd.img-2.6.35-28-generic
  35.5GB: boot/vmlinuz-2.6.35-22-generic
  35.5GB: boot/vmlinuz-2.6.35-23-generic
  35.5GB: boot/vmlinuz-2.6.35-24-generic
  35.5GB: boot/vmlinuz-2.6.35-25-generic
  35.5GB: boot/vmlinuz-2.6.35-27-generic
  35.5GB: boot/vmlinuz-2.6.35-28-generic
  35.3GB: initrd.img
  35.4GB: initrd.img.old
  35.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  48 8f fb 73 9e 73 a6 36  e8 ea aa b3 b5 5d df da  |H..s.s.6.....]..|
00000010  35 c5 3e 05 c7 f7 ba 1c  1f ca 1e be 5d 5b 20 1a  |5.>.........][ .|
00000020  a8 2b 1f da 3e b4 52 60  cb 4e c5 72 1d f5 cb 77  |.+..>.R`.N.r...w|
00000030  6d 8b 6d 31 de 6e 9c 88  dd 66 63 8c 72 2b e4 b0  |m.m1.n...fc.r+..|
00000040  a2 1d fb b5 91 ec 79 6b  ad b3 3a f1 d7 ec 8d f5  |......yk..:.....|
00000050  fa e8 3e 69 e2 9a 67 6f  fc 45 73 c9 c4 4a 49 e6  |..>i..go.Es..JI.|
00000060  b3 f4 95 6b 0f fe 5e 1c  dd 08 3d 35 f3 eb b0 2e  |...k..^...=5....|
00000070  6d 6c 8c 46 19 d7 b1 58  53 8c 7e 8a d5 4e 85 78  |ml.F...XS.~..N.x|
00000080  e5 91 c3 f6 dc fa f9 56  a7 d3 84 ae 53 83 4d 5d  |.......V....S.M]|
00000090  b6 15 2c 1b 7c ed 64 87  df 25 de b7 a4 3c 1b 35  |..,.|.d..%...<.5|
000000a0  69 7a be ed fe 73 9c f8  e1 0f ad a1 ab 31 3a 07  |iz...s.......1:.|
000000b0  b5 9f b7 28 f5 5e ee 89  de c4 bb 64 5c e7 f6 e4  |...(.^.....d\...|
000000c0  d7 95 5b 6b 97 5d 4c b3  46 0f 04 b0 9c 79 78 3f  |..[k.]L.F....yx?|
000000d0  a8 e2 8f 39 8b 74 8a ff  0a 52 0d 9c 4a 3c a1 5a  |...9.t...R..J<.Z|
000000e0  b2 a8 12 2f e5 83 33 70  75 35 29 f1 cb 86 aa 7a  |.../..3pu5)....z|
000000f0  31 a1 8c 43 11 9d 6f 93  c9 e3 82 8c 76 22 e1 df  |1..C..o.....v"..|
00000100  27 fb 5d 2d 05 8e 6c 84  2f 5c f6 7f cb 5a a3 f2  |'.]-..l./\...Z..|
00000110  ee 5f bd 7e 09 76 a1 63  4e c3 63 c1 fd fc 1d 8e  |._.~.v.cN.c.....|
00000120  c5 e0 fd 65 4f 67 c9 0a  cb e5 bd 2a b2 82 f4 89  |...eOg.....*....|
00000130  34 c7 ab 4b 97 7e e8 9d  24 79 55 64 ac 76 e5 80  |4..K.~..$yUd.v..|
00000140  62 c1 8e 3e 41 27 41 b5  22 73 cc fc ba 13 39 8e  |b..>A'A."s....9.|
00000150  e8 e2 9e 15 35 f5 8e d1  fb c3 2d d3 4d 5e b7 b4  |....5.....-.M^..|
00000160  b9 c5 9c 9b ee 14 f2 e3  09 35 2e 87 d5 c9 f3 f2  |.........5......|
00000170  8b 4d a3 bf b2 4f 10 a8  3c ff dc 61 d4 a8 45 c0  |.M...O..<..a..E.|
00000180  9b 54 41 91 3d 32 2a 19  eb 21 99 2f ca 6a f2 90  |.TA.=2*..!./.j..|
00000190  c2 74 d2 ca 6c 4c e5 f5  db d7 af 68 89 92 b9 3d  |.t..lL.....h...=|
000001a0  76 bc a5 57 8a 6a 1a e4  74 cd 87 55 85 0a 47 64  |v..W.j..t..U..Gd|
000001b0  83 08 6e 90 bc 88 e0 35  20 19 c7 25 e7 7d 00 fe  |..n....5 ..%.}..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 21 0a 95 00 00 fe  |..........!.....|
000001d0  ff ff 05 fe ff ff 23 0a  95 00 e0 33 e9 02 00 00  |......#....3....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 7e 00 00 00 00 00  |........>.~.....|
00000020  ba d2 79 00 68 1e 00 00  00 00 00 00 02 00 00 00  |..y.h...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 20 bb 6b a2 20  20 20 20 20 20 20 20 20  |..) .k.         |
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
00000100  7d 00 66 b8 28 49 69 00  66 ba 00 00 00 00 bb 00  |}.f.(Ii.f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e dd ca 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

Any idea what's wrong with this?

Thanks in advance!

---

### Post by lechien73 on 2011-05-02
Grub error 15 is a "file not found" error. According to your results.txt file, you have Grub 0.97 installed. This would be looking for the menu.lst file, which is not present.

I would suggest that you boot from a Live CD and then re-install Grub 2.

You can do this by issuing:

```
sudo mount /dev/sda6 /mnt
```

followed by:

```
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by pistachepastis on 2011-05-02
Great, Lechien73, that did it!!

A follow-up, if you allow me.

The Grub-menu now doesn't include a Windows XP boot-up option.
Any idea how to include that?

---

### Post by ksprasad on 2011-05-02
run,
 
sudo update-grub
 
Regards,
ksprasad

---

### Post by lechien73 on 2011-05-02
> **pistachepastis said:**
> Great, Lechien73, that did it!!


Wonderful :) glad it helped. Please could you use the "Thread Tools" menu at the top of this page to mark this as [Solved] when you've followed ksprasad's suggestion to locate Windows XP.

Thanks

---

### Post by pistachepastis on 2011-05-02
mmm, unfortunately, ksprasad windows fix didn't help.
(I marked the thread as solved, because my main problem IS solved)

---

### Post by ksprasad on 2011-05-02
> **pistachepastis said:**
> mmm, unfortunately, ksprasad windows fix didn't help.

 
sorry :(. But since you have windows vista/7, I think win xp option will come in vista/7 boot loader. so, is there any option for vista/7??
 
Regards,
ksprasad

---

### Post by pistachepastis on 2011-05-02
I was able to put Windows XP in grub menu again like this:

```

sudo gedit /boot/grub/menu.lst

```

then added the following lines to the menu.lst
```

title Windows XP Professional
root (hd0,0)
makeactive
chainloader +1

```

When I rebooted, Windows XP was present on the list again

---

