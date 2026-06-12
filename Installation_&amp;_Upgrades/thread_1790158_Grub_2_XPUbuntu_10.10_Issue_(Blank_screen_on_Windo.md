---
title: "Grub 2 XP/Ubuntu 10.10 Issue (Blank screen on Windows boot)"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by apmarcus on 2011-06-24
Howdy,

Friend of mine had an XP install and Ubuntu 10.10 dual booting using Grub 2.  He tried to extend the partition for XP to take up some unallocated hd space, something went terribly terribly wrong.  I am trying to remedy it right now.  Finally got Ubuntu cooperating again after a re-install 'Alongside another OS' option.

Grub 2 recognizes the two OS's installed, but when XP is selected it blanks the screen and then reloads the Grub2 OS selection screen.  Any idea?  Attempts to fix the MBR via a Windows disc have result in BSOD on the reinstall disc's attempt to load.  New to fiddling with Ubuntu, just trying to help out my friend.  Here is the RESULTS.txt from Boot Info Script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 118896455 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 1 for (,msdos1)/boot/grub. 
                       According to the info in the boot sector, sda1 has 
                       395431846 sectors, but according to the info from 
                       fdisk, it has 395439911 sectors.
    Operating System:  Windows XP
    Boot files:        /boot/grub/grub.cfg /boot.ini /ntldr /NTDETECT.COM 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 395448695.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   395,439,974   395,439,912   7 NTFS / exFAT / HPFS
/dev/sda2         395,448,693   488,396,799    92,948,107   f W95 Extended (LBA)
/dev/sda5         395,448,695   427,421,179    31,972,485  83 Linux
/dev/sda6         475,650,048   488,396,799    12,746,752  82 Linux swap / Solaris
/dev/sda7         427,421,696   473,546,751    46,125,056  83 Linux
/dev/sda8         473,548,800   475,635,711     2,086,912  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        180C57CA0C57A214                       ntfs       
/dev/sda5        0F5404910F540491                       ntfs       E2
/dev/sda6        4dac0ce6-9366-4b76-b95a-494ce9b5859e   swap       
/dev/sda7        06ced363-7ad0-43f5-ad62-557ab726d79f   ext4       
/dev/sda8        d072cdd9-e57d-4334-827d-68d14bb9b0b6   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=06ced363-7ad0-43f5-ad62-557ab726d79f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=06ced363-7ad0-43f5-ad62-557ab726d79f ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 180c57ca0c57a214
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
--------------------------------------------------------------------------------

================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-2.6.35-22-generic              1
            ?? = ??             boot/vmlinuz-2.6.35-22-generic                 1

=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=06ced363-7ad0-43f5-ad62-557ab726d79f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=06ced363-7ad0-43f5-ad62-557ab726d79f ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 180c57ca0c57a214
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
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=06ced363-7ad0-43f5-ad62-557ab726d79f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=d072cdd9-e57d-4334-827d-68d14bb9b0b6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 217.999378204 = 234.075049984  boot/grub/core.img                             1
 208.057067871 = 223.399575552  boot/grub/grub.cfg                             1
 204.716796875 = 219.812986880  boot/initrd.img-2.6.35-22-generic              2
 218.004714966 = 234.080780288  boot/vmlinuz-2.6.35-22-generic                 1
 204.716796875 = 219.812986880  initrd.img                                     2
 218.004714966 = 234.080780288  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  34 03 19 c4 81 40 50 46  d0 92 d4 2a c5 ca 31 41  |4....@PF...*..1A|
00000010  42 94 cc 29 04 cf 1a 01  9d 43 67 4c 32 43 52 75  |B..).....CgL2CRu|
00000020  2a 15 5e c9 85 e0 84 30  22 07 0a bc 26 0c e1 50  |*.^....0"...&..P|
00000030  71 67 0f ab 66 a5 a8 4b  71 24 02 80 b9 bb 45 c2  |qg..f..Kq$....E.|
00000040  12 9c c9 99 99 14 20 80  08 00 00 00 2c c4 02 50  |...... .....,..P|
00000050  03 31 93 33 22 82 33 32  41 99 49 9c c4 99 41 70  |.1.3".32A.I...Ap|
00000060  83 25 4d a0 76 94 95 b8  12 31 32 29 32 11 c8 70  |.%M.v....12)2..p|
00000070  57 f7 c9 34 88 0a c3 19  70 96 20 61 26 61 90 07  |W..4....p. a&a..|
00000080  3b 9c cd 89 43 29 45 8b  50 65 ca b9 e4 30 c6 5d  |;...C)E.Pe...0.]|
00000090  b2 4c 17 f3 e1 b0 48 a2  0a aa 8a 5c 28 a0 35 a5  |.L....H....\(.5.|
000000a0  10 8c 31 23 d4 52 18 51  29 2c 43 10 1e 19 99 99  |..1#.R.Q),C.....|
000000b0  39 33 a6 bb b8 25 73 10  09 43 29 a7 4b 38 8b a6  |93...%s..C).K8..|
000000c0  68 44 4a a6 28 83 38 3d  44 53 94 0b 44 99 cf c6  |hDJ.(.8=DS..D...|
000000d0  c7 ee b0 40 46 ce 0c 01  04 19 59 2c cb 2a 56 d4  |...@F.....Y,.*V.|
000000e0  ba d1 70 a2 d4 4c 69 1c  8d fd 88 1a 59 a4 4a 2b  |..p..Li.....Y.J+|
000000f0  5c 85 58 a9 8f 51 66 1f  1a 5e 22 86 61 98 05 f5  |\.X..Qf..^".a...|
00000100  40 26 71 20 d9 99 1c a1  11 c2 a4 c9 a2 2c 2c 5c  |@&q .........,,\|
00000110  28 0b 87 79 95 28 29 95  b4 56 79 6c fa f8 3e 79  |(..y.()..Vyl..>y|
00000120  1a 13 b2 22 32 45 c1 96  42 60 d1 7d c8 3e a7 9c  |..."2E..B`.}.>..|
00000130  26 15 60 82 a8 47 b1 18  7c 0e ae 0c 50 66 90 27  |&.`..G..|...Pf.'|
00000140  84 6b e1 5a 08 95 30 e0  20 4b 22 67 52 c8 20 6e  |.k.Z..0. K"gR. n|
00000150  34 85 c6 18 7c 4c e2 90  92 22 e2 a1 16 9e ec 61  |4...|L...".....a|
00000160  c4 3b d1 42 ce 64 c3 8a  99 36 65 56 42 40 32 99  |.;.B.d...6eVB@2.|
00000170  66 d2 18 86 6e 49 40 00  ca 1a 22 15 04 10 11 0b  |f...nI@...".....|
00000180  f1 52 dc 8b cd 29 34 19  94 c1 29 44 60 30 88 40  |.R...)4...)D`0.@|
00000190  16 36 c3 90 8b a1 35 f2  95 0c 64 4c 76 38 1d 81  |.6....5...dLv8..|
000001a0  42 6d a1 c6 d2 43 ce e9  95 a3 54 9a 4e c3 9c 86  |Bm...C....T.N...|
000001b0  a3 10 11 51 84 7a ea d2  ec da ec de 65 74 00 fe  |...Q.z......et..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 85 dc e7 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 72 91  c7 04 19 b5 c2 00 00 00  |......r.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

Any help would be greatly appreciated.

Thanks

-Aaron

---

### Post by oldfred on 2011-06-24
You have grub2 installed to the windows NTFS partition boot sector. That has to contain windows boot code as it is part of winodws booting.

You also have /boot/grub files/folders in the root of XP. You can delete those. I think it is only win7 that has a /Boot folder that can get confused with the /boot as windows is not case sensitive.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also run windows fixBoot command if the backup is destroyed also.

---

### Post by apmarcus on 2011-06-24
So I removed the /boot directories in the XP root.  I tried the testdisk but the BackupBS was not an option, the backup boot sector was corrupted.  I repaired the Backup Bootsector, now the selection of the windows option in grub leads to the grub emergency console, not a rebooting of grub.  Ubuntu still boots.  I tried an XP disc, it corrupts and BSODs so no fixboot, Windows 7 is unable to identify a valid windows install, so no bootrect.  Any other ideas?

---

### Post by apmarcus on 2011-06-24
Here are the new results.txt after doing that stuff.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 118896455 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 1 for (,msdos1)/boot/grub. 
                       According to the info in the boot sector, sda1 has 
                       395431846 sectors, but according to the info from 
                       fdisk, it has 395439911 sectors.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 395448695.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   395,439,974   395,439,912   7 NTFS / exFAT / HPFS
/dev/sda2         395,448,693   488,396,799    92,948,107   f W95 Extended (LBA)
/dev/sda5         395,448,695   427,421,179    31,972,485  83 Linux
/dev/sda6         475,650,048   488,396,799    12,746,752  82 Linux swap / Solaris
/dev/sda7         427,421,696   473,546,751    46,125,056  83 Linux
/dev/sda8         473,548,800   475,635,711     2,086,912  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        180C57CA0C57A214                       ntfs       
/dev/sda5        0F5404910F540491                       ntfs       E2
/dev/sda6        4dac0ce6-9366-4b76-b95a-494ce9b5859e   swap       
/dev/sda7        06ced363-7ad0-43f5-ad62-557ab726d79f   ext4       
/dev/sda8        d072cdd9-e57d-4334-827d-68d14bb9b0b6   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=06ced363-7ad0-43f5-ad62-557ab726d79f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=06ced363-7ad0-43f5-ad62-557ab726d79f ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 06ced363-7ad0-43f5-ad62-557ab726d79f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 180c57ca0c57a214
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
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=06ced363-7ad0-43f5-ad62-557ab726d79f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=d072cdd9-e57d-4334-827d-68d14bb9b0b6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 217.999378204 = 234.075049984  boot/grub/core.img                             1
 220.087947845 = 236.317634560  boot/grub/grub.cfg                             1
 204.716796875 = 219.812986880  boot/initrd.img-2.6.35-22-generic              2
 218.004714966 = 234.080780288  boot/vmlinuz-2.6.35-22-generic                 1
 204.716796875 = 219.812986880  initrd.img                                     2
 218.004714966 = 234.080780288  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  34 03 19 c4 81 40 50 46  d0 92 d4 2a c5 ca 31 41  |4....@PF...*..1A|
00000010  42 94 cc 29 04 cf 1a 01  9d 43 67 4c 32 43 52 75  |B..).....CgL2CRu|
00000020  2a 15 5e c9 85 e0 84 30  22 07 0a bc 26 0c e1 50  |*.^....0"...&..P|
00000030  71 67 0f ab 66 a5 a8 4b  71 24 02 80 b9 bb 45 c2  |qg..f..Kq$....E.|
00000040  12 9c c9 99 99 14 20 80  08 00 00 00 2c c4 02 50  |...... .....,..P|
00000050  03 31 93 33 22 82 33 32  41 99 49 9c c4 99 41 70  |.1.3".32A.I...Ap|
00000060  83 25 4d a0 76 94 95 b8  12 31 32 29 32 11 c8 70  |.%M.v....12)2..p|
00000070  57 f7 c9 34 88 0a c3 19  70 96 20 61 26 61 90 07  |W..4....p. a&a..|
00000080  3b 9c cd 89 43 29 45 8b  50 65 ca b9 e4 30 c6 5d  |;...C)E.Pe...0.]|
00000090  b2 4c 17 f3 e1 b0 48 a2  0a aa 8a 5c 28 a0 35 a5  |.L....H....\(.5.|
000000a0  10 8c 31 23 d4 52 18 51  29 2c 43 10 1e 19 99 99  |..1#.R.Q),C.....|
000000b0  39 33 a6 bb b8 25 73 10  09 43 29 a7 4b 38 8b a6  |93...%s..C).K8..|
000000c0  68 44 4a a6 28 83 38 3d  44 53 94 0b 44 99 cf c6  |hDJ.(.8=DS..D...|
000000d0  c7 ee b0 40 46 ce 0c 01  04 19 59 2c cb 2a 56 d4  |...@F.....Y,.*V.|
000000e0  ba d1 70 a2 d4 4c 69 1c  8d fd 88 1a 59 a4 4a 2b  |..p..Li.....Y.J+|
000000f0  5c 85 58 a9 8f 51 66 1f  1a 5e 22 86 61 98 05 f5  |\.X..Qf..^".a...|
00000100  40 26 71 20 d9 99 1c a1  11 c2 a4 c9 a2 2c 2c 5c  |@&q .........,,\|
00000110  28 0b 87 79 95 28 29 95  b4 56 79 6c fa f8 3e 79  |(..y.()..Vyl..>y|
00000120  1a 13 b2 22 32 45 c1 96  42 60 d1 7d c8 3e a7 9c  |..."2E..B`.}.>..|
00000130  26 15 60 82 a8 47 b1 18  7c 0e ae 0c 50 66 90 27  |&.`..G..|...Pf.'|
00000140  84 6b e1 5a 08 95 30 e0  20 4b 22 67 52 c8 20 6e  |.k.Z..0. K"gR. n|
00000150  34 85 c6 18 7c 4c e2 90  92 22 e2 a1 16 9e ec 61  |4...|L...".....a|
00000160  c4 3b d1 42 ce 64 c3 8a  99 36 65 56 42 40 32 99  |.;.B.d...6eVB@2.|
00000170  66 d2 18 86 6e 49 40 00  ca 1a 22 15 04 10 11 0b  |f...nI@...".....|
00000180  f1 52 dc 8b cd 29 34 19  94 c1 29 44 60 30 88 40  |.R...)4...)D`0.@|
00000190  16 36 c3 90 8b a1 35 f2  95 0c 64 4c 76 38 1d 81  |.6....5...dLv8..|
000001a0  42 6d a1 c6 d2 43 ce e9  95 a3 54 9a 4e c3 9c 86  |Bm...C....T.N...|
000001b0  a3 10 11 51 84 7a ea d2  ec da ec de 65 74 00 fe  |...Q.z......et..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 85 dc e7 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 72 91  c7 04 19 b5 c2 00 00 00  |......r.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by oldfred on 2011-06-24
Testdisk also has a rebuild NTFS boot sector function somewhere in the area that you were in for the recover of the backup. That I think only makes a generic NTFS which may not be bootable, but then the windows fixboot should work. 

[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Rebuilding An NTFS Boot Sector On An NTFS Partition

---

### Post by apmarcus on 2011-06-24
I selected the 'Rebuild BS' (I'm assuming this is what you were referring to).  It said the extrapolated boot sector and current one are identical.  The backup was corrupt before, and the primary wasn't, so i copied the primary over the backup since it was corrupted.  It says both boot sectors are 'OK', but it still sends me to grub recovery console.  If i select the repair MFT, it gives me this error:

../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
                                    Aborted


Which concerns me.  Any further ideas?  When I do the rebuild BS, it seems to access the MFT and MFTmirr though, and no problems, it doesnt have any size issues or anything.  So I'm feeling a bit stuck.

-Aaron

---

### Post by apmarcus on 2011-06-24
And no, Win7 still can't see the Windows install.

---

### Post by apmarcus on 2011-06-24
When I select Analyse, it comes up with fewer partitions, almost implying that there is redundancy running around which might cause problems, should I write the new structure to disk or leave it alone?

---

### Post by oldfred on 2011-06-24
Testdisk looks at the partition history and finds old partitions. Useful if you want to recvor a partition. But your issue seems to be the grub2 boot loader installed to the partition boot sector. 

Normally testdisk or windows will rewrite the boot sector to fix it. Sometimes additional repairs are then required to make it bootable. But you do not seem to be able to see partition at all with windows. And test disk does not not to rebuild it.

I just noticed you said win7 does not see it. Win7 will not repair a XP install, the boot sectors are different. Boot sector format has been pretty much the same up to XP, the Vista and 7 have a different version.

It is not saying boot sectors are ok, just that the backup matches the primary. Since you now copied it you have the grub version in both. You need the windows version.

Are these the commands you are running from a XP disk.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by apmarcus on 2011-06-24
The problem with that, is that the windows xp recovery disc BSODs as it loads.  I've tried two different discs and the same result.

---

### Post by oldfred on 2011-06-24
Do Windows XP disks work on other computers or is it a CD reader issue?

Do you get an error number on the blue screen?

---

### Post by apmarcus on 2011-06-24
I will go get the error # now.  I don't know if they work on others, but its the same error both times.  Would be very odd if two discs from different places did the same thing.

---

### Post by apmarcus on 2011-06-24
Just downloaded a XP Recovery Console .iso and burned it to a disc, this is the error stuff I got.

STOP: 0x0000007E (0xC0000005, 0xF748E0BF, 0xF78DA208, 0xF78D9F08 )

pci.sys Address F748E0BF base @ F7487000 Datestamp 3b7d855c

---

### Post by apmarcus on 2011-06-24
Here is from the XP disc (legit one, not a recovery console only disc).

STOP: 0x0000007B (0xF78D2524, 0xC0000034, 0x00000000, 0x00000000)

---

### Post by oldfred on 2011-06-24
Did you change BIOS. Perhaps you  changed to AHCI mode perhaps? When I changed to AHCI my XP stopped working. If your install has the extra drivers, but the repair CD does not that may explain it.

[http://support.microsoft.com/kb/330182](http://support.microsoft.com/kb/330182)

---

### Post by westie457 on 2011-06-24
Hi a couple of questions:-

1  Has the Windows XP installation been fully updated before this issue arose?

2 Is the install disk a plain original or one that has a service pack numder attached?  eg Windows XP SP1

---

### Post by oldfred on 2011-06-24
Maybe some minor fixes will then let testdisk rebuild boot sector.

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk".

---

### Post by oldfred on 2011-06-24
You have two totally unrelated issues. One is that you have grub installed to the windows boot partition, which prevents windows from working. 

The other issue is that you have a non-working windows repairCd or a non-working CD drive. It also could be BIOS settings preventing the Windows CD from working. 

Of course you cannot fix the first problem because of the second problem.

And for some reason the backup partition boot sector was damaged, so the normal way to repair with testdisk from Linux does not work.

There are other repair CDs that may have tools to fix a NTFS boot partition, but I do not know them. I might try a windows forum for recommendations.

This has a boot build:
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)
possibably fixboot:
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

---

### Post by westie457 on 2011-06-25
You could try any or all options available _[here]("http://www.supergrubdisk.org/")_

I have just used SuperGrubDisk on my spare pc to check some of it's capabilities. The pc dual-boots Windows 7 and 11.04 (Natty). It found all of the drives, partitions and operating-systems. Though I did not check if it can re-write the MBR of Windows there is an option there to do so.

Further thoughts.  If your friends XP is on a SATA/SCSI Drive and the install disc is a plain XP Home you will get the BSOD as it does not have the required drivers.

If you can get hold of an XP Pro one with at least SP1 integrated you will have a better chance of recovering.

One other thing, try cleaning the lens in the CD/DVD drive and the CD as well. Both obvious and easily over-looked.

---

