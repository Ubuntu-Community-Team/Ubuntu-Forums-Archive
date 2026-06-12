---
title: "Help in getting 10.10 restored after unhappy 11.04"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by drmathprog on 2011-05-08
I tried getting 11.04 to install over a working 10.10 (working thanks to lots of help here - thanks!).  11.04 gave me tons of problems, so I'm trying to reinstall 10.10.

I've got the install done, but GRUB 2 is apparently in the wrong place or looking in the wrong place.  I wish I understood how GRUB 2 works, but I don't.  Can anyone help?  Thanks!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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
    Boot files/dirs:   /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 71714223. But according to the info from 
                       fdisk, sdd5 starts at sector 900154143.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   205,036,735   205,036,673   7 HPFS/NTFS
/dev/sda2         205,037,566   490,233,855   285,196,290   5 Extended
/dev/sda5         205,037,568   478,570,495   273,532,928  83 Linux
/dev/sda6         478,572,544   490,233,855    11,661,312  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34   488,397,134   488,397,101 Linux or Data

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63       353,429       353,367  de Dell Utility
/dev/sdd2    *        353,430   450,253,754   449,900,325   7 HPFS/NTFS
/dev/sdd3         900,154,080 1,250,258,624   350,104,545   5 Extended
/dev/sdd5         900,154,143 1,250,258,624   350,104,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        12CC960FCC95ED6B                       ntfs       New Volume                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5fbcd711-482b-42c2-8b56-78e84216c33e   ext4                                     
/dev/sda6        457ac14b-e545-4e22-b4cc-35570414d98f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C0D8362BD8361FD8                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        eb7425ad-f1cc-4e63-a46a-1d558625e5ec   ext4       Linux Data                    
/dev/sdc: PTTYPE="gpt" 
/dev/sdd1        07D4-030A                              vfat       DellUtility                   
/dev/sdd2        1EA8699BA8697267                       ntfs       Windows                       
/dev/sdd3: PTTYPE="dos" 
/dev/sdd5        1EB287D01693A333                       ntfs       Program Files                 
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5fbcd711-482b-42c2-8b56-78e84216c33e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5fbcd711-482b-42c2-8b56-78e84216c33e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5fbcd711-482b-42c2-8b56-78e84216c33e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5fbcd711-482b-42c2-8b56-78e84216c33e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5fbcd711-482b-42c2-8b56-78e84216c33e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5fbcd711-482b-42c2-8b56-78e84216c33e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5fbcd711-482b-42c2-8b56-78e84216c33e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5fbcd711-482b-42c2-8b56-78e84216c33e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdd2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd3,msdos2)'
    search --no-floppy --fs-uuid --set 1ea8699ba8697267
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=5fbcd711-482b-42c2-8b56-78e84216c33e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=457ac14b-e545-4e22-b4cc-35570414d98f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 238.2GB: boot/grub/core.img
 195.3GB: boot/grub/grub.cfg
 187.1GB: boot/initrd.img-2.6.35-22-generic
 105.2GB: boot/vmlinuz-2.6.35-22-generic
 187.1GB: initrd.img
 105.2GB: vmlinuz

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

================================ sdd2/boot.ini: ================================

[boot loader] 
timeout=2 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a4 90 fb 80 9b 46 cc 7c  a7 42 84 b3 9d a7 b8 5e  |.....F.|.B.....^|
00000010  4d 02 ba 56 2c c2 ca 5a  17 29 cc fa 55 9f 76 69  |M..V,..Z.)..U.vi|
00000020  41 e3 fa 28 38 50 b4 10  b2 76 39 7c ce 13 94 8b  |A..(8P...v9|....|
00000030  89 09 f5 2c 49 5a 4c 15  26 33 04 12 33 f6 3f 8b  |...,IZL.&3..3.?.|
00000040  4a 0f 2b be a7 cd 75 a6  dd 48 a8 53 ea 72 b7 ce  |J.+...u..H.S.r..|
00000050  6c 2f 87 8f be 67 aa e7  8e d2 83 5b bf 86 ee e9  |l/...g.....[....|
00000060  0c 3f f7 3b 22 e8 41 c4  76 d7 f0 41 df 50 7e 47  |.?.;".A.v..A.P~G|
00000070  b0 c7 b9 79 87 2f f9 bf  cd f2 e6 54 78 d2 36 ba  |...y./.....Tx.6.|
00000080  2f 75 74 6d bb e4 1c 5b  ea 14 f2 d4 71 29 c3 e1  |/utm...[....q)..|
00000090  ed 75 bb a3 00 5b 62 b9  d5 9d 93 e6 e7 2e d2 ed  |.u...[b.........|
000000a0  42 c8 9a 7e 93 78 30 26  f3 17 42 1a 00 cb b3 84  |B..~.x0&..B.....|
000000b0  96 07 40 08 3c d0 72 10  c8 c2 19 38 6f be 31 79  |..@.<.r....8o.1y|
000000c0  54 bb 12 ab 7a f5 47 16  fe 4d 9c bf 58 e0 0c e6  |T...z.G..M..X...|
000000d0  c6 47 b0 66 9b 98 5b be  4e fd 74 9c 5c 67 37 5e  |.G.f..[.N.t.\g7^|
000000e0  cc 1c 81 0e 0f e7 c4 8c  fc b3 1c 5d 5d 38 1a 94  |...........]]8..|
000000f0  32 b6 e6 f9 98 62 fb 28  f9 e7 70 6d e1 10 e4 c8  |2....b.(..pm....|
00000100  e0 01 c8 c0 93 b4 7e 80  a1 ff c7 8a 81 b0 fa 81  |......~.........|
00000110  2b d4 a1 9b f0 61 c5 dc  e1 fa f6 61 5d d8 c8 c6  |+....a.....a]...|
00000120  80 e1 c1 27 83 8b 1c 06  df e7 0e 9e a9 1c 0c bb  |...'............|
00000130  34 b8 f2 e6 e0 ed 99 41  52 dd 90 c0 7f e4 3d 73  |4......AR.....=s|
00000140  f4 ea a1 f1 4c f9 84 2a  73 0a ce 9d 7e ec 3e b3  |....L..*s...~.>.|
00000150  2e 6d 16 8b 60 17 bd e4  6c bc c5 eb 1a 16 78 03  |.m..`...l.....x.|
00000160  c5 97 37 48 57 5e 57 a8  fc 34 0f 0b f4 c7 cb 00  |..7HW^W..4......|
00000170  ae a9 60 87 70 98 63 0b  42 1c 8c 9e 89 c2 3a d4  |..`.p.c.B.....:.|
00000180  e1 5a 97 e3 9f 38 12 03  5a 49 af 1d 28 e8 a5 d4  |.Z...8..ZI..(...|
00000190  1c 67 da 34 97 e6 de 43  df f0 92 11 41 30 dd 1f  |.g.4...C....A0..|
000001a0  68 9a 76 d0 b4 69 b1 69  c9 10 23 f9 26 c3 2a 9e  |h.v..i.i..#.&.*.|
000001b0  71 6d 3f 23 8f cb d8 75  db ac 68 a1 05 64 00 fe  |qm?#...u..h..d..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c8 4d 10 00 fe  |............M...|
000001d0  ff ff 05 fe ff ff 02 c8  4d 10 00 f8 b1 00 00 00  |........M.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by drmathprog on 2011-05-08
Anyone?

---

### Post by lidex on 2011-05-08
You're not clearly stating what the problem is. Is it not booting? Can't access windows? Missing grub entries? 
As this is not my area of expertise, I will point you here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by ajgreeny on 2011-05-11
I wonder if you have, or have in the past had a RAID setup, as /dev/sdc seems to suggest?[FONT=monospace]
[/FONT]> Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34   488,397,134   488,397,101 Linux or Data

---

