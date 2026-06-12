---
title: "Dual boot ubutun 10.04.1LTS and Xp, Grub error"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by nickvda on 2010-09-01
Hey, I was trying to dualboot ubuntu and windows xp. Currently have windows xp installed, and installed ubuntu on the same drive as xp on a new partition. Here is my sudo fdisk -l

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50ee804d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7e008134

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      665194   335257744+   7  HPFS/NTFS
/dev/sdb2          665195      969018   153127265+   5  Extended
/dev/sdb5          665195      935661   136315336+  83  Linux
/dev/sdb6          935662      969018    16811896+  82  Linux swap / Solaris

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x46479b03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd2   *           2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sdd5               2      121601   976751968+   7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sde2               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sde5               2       60801   488375968+   7  HPFS/NTFS

Disk /dev/sdf: 1028 MB, 1028128768 bytes
32 heads, 62 sectors/track, 1012 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

```SDB is my drive with xp and ubuntu and the swap. When I install ubuntu (installed from a usb drive), I get a grub rescue [B]no such partition, [B]message. And can't really do anything.

I used this guide
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

to try and get grub reworking, followed the instructions by letter (using sdb instead of sda), but got no results.

For the moment I restored my windows mbr using hiren's boot cd as I need it for work.

Please let me know how to fix this, as I would love to get the dualboot going.

Thanks in advance
[/B][/B]

---

### Post by andrewthomas on 2010-09-01
Go to the following page and follow the instructions and post results in your reply

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by nickvda on 2010-09-03
Here is the log, sorry if it took so long, had some things come up. Would like to point out at this point, grub is not installed, I fixed mbr to xp one, so I could actually use my pc :P. Thanks in advance guys

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   670,515,551   670,515,489   7 HPFS/NTFS
/dev/sda2         670,515,613   976,770,143   306,254,531   5 Extended
/dev/sda5         670,515,615   943,146,287   272,630,673  83 Linux
/dev/sda6         943,146,351   976,770,143    33,623,793  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 2,930,272,064 2,930,272,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc2    *         16,065 1,953,520,064 1,953,504,000   f W95 Ext d (LBA)
/dev/sdc5              16,128 1,953,520,064 1,953,503,937   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd2              16,065   976,768,064   976,752,000   f W95 Ext d (LBA)
/dev/sdd5              16,128   976,768,064   976,751,937   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B43C73323C72EEAC                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b721bcbe-13d2-4db2-ad6d-06b15eac5324   ext4                                     
/dev/sda6                                               swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        361CC0F91CC0B561                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        948AEE88DFB5A0DA                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        8EF82702F826E7E3                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        02BC65F7BC65E59F                       ntfs                                     
/dev/sde: PTTYPE="dos" 
/dev/sdf         58CC-653D                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdf         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set b721bcbe-13d2-4db2-ad6d-06b15eac5324
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set b721bcbe-13d2-4db2-ad6d-06b15eac5324
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b721bcbe-13d2-4db2-ad6d-06b15eac5324
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b721bcbe-13d2-4db2-ad6d-06b15eac5324 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b721bcbe-13d2-4db2-ad6d-06b15eac5324
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b721bcbe-13d2-4db2-ad6d-06b15eac5324 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b721bcbe-13d2-4db2-ad6d-06b15eac5324
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set b721bcbe-13d2-4db2-ad6d-06b15eac5324
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b43c73323c72eeac
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb5       /               ext4    errors=remount-ro 0       1
/dev/sdb6       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 371.3GB: boot/grub/core.img
 362.8GB: boot/grub/grub.cfg
 371.3GB: boot/initrd.img-2.6.32-24-generic
 371.3GB: boot/vmlinuz-2.6.32-24-generic
 371.3GB: initrd.img
 371.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 01 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 10 00 00 00 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ef ff 00 00 00 00 00 00  |................|
00000030  50 55 00 00 00 00 00 00  f7 7f 00 00 00 00 00 00  |PU..............|
00000040  02 00 00 00 08 00 00 00  93 9d e6 74 c7 e6 74 e2  |...........t..t.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 80 01  |ng...NTLDR is ..|
000001c0  01 00 07 fe ff ff 3f 00  00 00 02 67 a8 ae 00 00  |......?....g....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  59 8a 0b b6 b2 66 9b 4a  58 b5 a6 ad 2c 95 89 cd  |Y....f.JX...,...|
00000010  2a 31 75 32 e3 4c 4c a6  8f a9 90 d1 0b af a3 1f  |*1u2.LL.........|
00000020  81 4f d1 a6 c0 0a aa 11  fa 9c fa 08 ba 91 bc 08  |.O..............|
00000030  22 26 13 a0 f7 53 7b 8d  9f 4d 3d 65 bc 3e 65 86  |"&...S{..M=e.>e.|
00000040  d1 9c f4 af 21 23 c9 a0  e7 24 ce d2 7f 96 60 d3  |....!#...$....`.|
00000050  65 c7 bf d6 09 63 17 ea  7e 8e f9 a0 8d 89 1e d5  |e....c..~.......|
00000060  66 46 85 eb 98 91 08 9d  82 12 a6 e3 91 b7 ea de  |fF..............|
00000070  90 5c ba db c4 53 fa fb  a0 50 df f8 e9 28 ca 00  |.\...S...P...(..|
00000080  9c e1 02 fe 88 a1 28 9c  62 9c 83 db 6b ec 08 bb  |......(.b...k...|
00000090  6b cc c3 64 43 a9 68 1d  a4 42 6e 80 97 85 3a 61  |k..dC.h..Bn...:a|
000000a0  ff 10 bd 09 15 fc d6 fc  3a 90 6a a1 22 b6 5b 4c  |........:.j.".[L|
000000b0  fe 7c 0b ca bf d0 3a db  0f b0 2d f2 7d 68 cb f4  |.|....:...-.}h..|
000000c0  f1 b3 8b 27 0e da fb c6  d3 c6 b2 c6 fb c6 2e 79  |...'...........y|
000000d0  a3 1d e5 9e af 1c 8d 6e  a9 a3 c4 bd d9 99 ef 2e  |.......n........|
000000e0  77 56 bb 5a 9c 67 5d 02  e7 39 d7 47 e7 42 57 92  |wV.Z.g]..9.G.BW.|
000000f0  cb eb 2c 74 fd e9 5c e2  92 39 22 5d 99 0e 85 b3  |..,t..\..9"]....|
00000100  72 ac d5 b9 6c ec be 53  6b af 72 fe 6e 5f ea aa  |r...l..Sk.r.n_..|
00000110  b1 db 3e 91 ef 4e b7 ef  72 57 db ae b8 37 d8 46  |..>..N..rW...7.F|
00000120  dd 3e b6 5d 9e c3 56 85  a7 c9 e2 f5 0c 99 a3 bd  |.>.]..V.........|
00000130  99 e6 af bd 95 a6 f3 de  f9 a6 06 ef 10 4c 1f ff  |.............L..|
00000140  0d 56 8c cf 86 cf 4e c8  21 f3 44 3e 94 31 b9 cd  |.V....N.!.D>.1..|
00000150  78 79 b2 db 10 e4 13 6e  d0 fa ac d6 bb 7d 0f e8  |xy.....n.....}..|
00000160  d4 7e e7 b5 cd fe bd 9a  03 01 16 b5 36 a0 59 b5  |.~..........6.Y.|
00000170  1e 51 a9 9c 13 88 57 ce  0e da a0 88 09 7e 23 df  |.Q....W......~#.|
00000180  1f dc 21 bb 1f 6c 96 1a  82 97 49 37 86 48 24 f9  |..!..l....I7.H$.|
00000190  a1 cf 24 58 64 82 a4 18  b9 48 dc 8e 7c 24 f2 41  |..$Xd....H..|$.A|
000001a0  cd 11 c1 c8 e3 a3 23 48  ef 48 1f b2 72 c4 8a 3c  |......#H.H..r..<|
000001b0  3e 12 8d da fa 89 c5 23  38 d4 af 23 cd c8 00 01  |>......#8..#....|
000001c0  c1 ff 83 0f ff ff 02 00  00 00 91 03 40 10 00 fe  |............@...|
000001d0  ff ff 05 fe ff ff 93 03  40 10 30 0f 01 02 00 00  |........@.0.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Mark Phelps on 2010-09-03
Since the two outputs are different, somewhere between doing your list and running the script, it looks like you swapped the boot order of the /sda and /sdb drives -- such that Ubuntu is now on the "second" drive, not the "first".

According to the script results, GRUB is looking for Ubuntu on the first drive (hd1,5) -- so if you are booting from the other drive and Ubuntu is now on the "second" drive, GRUB will be trying boot it from the wrong drive.

Realize, that to use GRUB, it needs to be in the MBR of the boot drive, so repairing GRUB while booting from the other drive will cause GRUB to be written to the MBR of that drive.

Did you try swapping the drive boot order back to the original -- such that Ubuntu is back to being the "first" drive? That should work.

---

### Post by nickvda on 2010-09-03
I didnt change the boot order, so no idea what happened there. WHen you mean change the boot drive order, I am assuming you mean change it in the bios, correct? I will check in a bit and try what you are saying

---

### Post by oldfred on 2010-09-04
I would swear we are seeing grub move drive numbers around. 

I do know that either the script or grub misidentify the drive (same drive is not true) so the grub you have in sde will probably boot the install in sdb. Since UUIDs override the hd1 drive number it still should boot. Try booting from your 120GB drive.

I do prefer having grub installed to the same drive as the system install and having different systems on different drives, just in case a drive fails I still have a way into my system. Of course I have several CDs and USBs that will boot something.

---

