---
title: "Cannot use Vista after installing Ubuntu (dual boot)"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by JoshuaHardcastle on 2010-09-01
I have decided to take the plunge and try going from Windows Vista to a dual boot Ubuntu, however after a few attempts at installing, I now have a menu to select my OS, which has 2 different versions of Ubuntu.  One  Ubuntu version works correctly, where as selecting vista takes me to a different menu to select my OS.  This menu has Vista and only one version of Ubuntu, and neither work.  

I have been looking through lots of help pages but I find myself getting more confused the more I read.  I have got myself in a bit of a pickle here and would warmly welcome any assistance anyone can give me. 

I have enclosed the output from the boot info script below:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 645073312 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   522,741,759   522,739,712   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   122,896,362   122,894,315   7 HPFS/NTFS
/dev/sdb3         122,897,311   976,768,064   853,870,754   5 Extended
/dev/sdb5         122,897,313   544,130,823   421,233,511  83 Linux
/dev/sdb6         957,104,568   976,768,064    19,663,497  82 Linux swap / Solaris
/dev/sdb7         544,131,072   940,275,711   396,144,640  83 Linux
/dev/sdb8         940,277,760   957,104,127    16,826,368  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000215724032 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953546336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,536,129 1,953,536,067   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D0E0CBEAE0CBD53E                       ntfs       Corpus                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0A3C6F6A3C6F502D                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        9ae5e8e4-f37a-44b1-8e89-59e040776229   ext2                                     
/dev/sdb6        0cd38ae7-1ff6-4987-b35b-456a86fd094e   swap                                     
/dev/sdb7        a7e263c5-0119-478a-9563-3727b2c2fb9b   ext2       NuUbuntu                      
/dev/sdb8        a5e60803-214e-49eb-8272-1f3a8b3be012   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        540A-3BE0                              vfat       IOMEGA_HDD                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext2       (rw,errors=remount-ro)
/dev/sdc1        /media/IOMEGA_HDD        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1        /media/0A3C6F6A3C6F502D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 9ae5e8e4-f37a-44b1-8e89-59e040776229
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
search --no-floppy --fs-uuid --set 9ae5e8e4-f37a-44b1-8e89-59e040776229
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
    search --no-floppy --fs-uuid --set 9ae5e8e4-f37a-44b1-8e89-59e040776229
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9ae5e8e4-f37a-44b1-8e89-59e040776229 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9ae5e8e4-f37a-44b1-8e89-59e040776229
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9ae5e8e4-f37a-44b1-8e89-59e040776229 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9ae5e8e4-f37a-44b1-8e89-59e040776229
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9ae5e8e4-f37a-44b1-8e89-59e040776229
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 0a3c6f6a3c6f502d
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb7)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set a7e263c5-0119-478a-9563-3727b2c2fb9b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=a7e263c5-0119-478a-9563-3727b2c2fb9b ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb7)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set a7e263c5-0119-478a-9563-3727b2c2fb9b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=a7e263c5-0119-478a-9563-3727b2c2fb9b ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb5       /               ext2    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=0cd38ae7-1ff6-4987-b35b-456a86fd094e none            swap    sw              0       0
# swap was on /dev/sdb8 during installation
UUID=a5e60803-214e-49eb-8272-1f3a8b3be012 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 113.4GB: boot/grub/core.img
 113.3GB: boot/grub/grub.cfg
 113.3GB: boot/initrd.img-2.6.32-24-generic
 113.3GB: boot/vmlinuz-2.6.32-24-generic
 113.3GB: initrd.img
 113.3GB: vmlinuz

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set root='(hd1,7)'
search --no-floppy --fs-uuid --set a7e263c5-0119-478a-9563-3727b2c2fb9b
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
set root='(hd1,7)'
search --no-floppy --fs-uuid --set a7e263c5-0119-478a-9563-3727b2c2fb9b
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
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set a7e263c5-0119-478a-9563-3727b2c2fb9b
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a7e263c5-0119-478a-9563-3727b2c2fb9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set a7e263c5-0119-478a-9563-3727b2c2fb9b
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a7e263c5-0119-478a-9563-3727b2c2fb9b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set a7e263c5-0119-478a-9563-3727b2c2fb9b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set a7e263c5-0119-478a-9563-3727b2c2fb9b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 0a3c6f6a3c6f502d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=a7e263c5-0119-478a-9563-3727b2c2fb9b /               ext2    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=0cd38ae7-1ff6-4987-b35b-456a86fd094e none            swap    sw              0       0
# swap was on /dev/sdb8 during installation
UUID=a5e60803-214e-49eb-8272-1f3a8b3be012 none            swap    sw              0       0

=================== sdb7: Location of files loaded by Grub: ===================


 358.9GB: boot/grub/core.img
 358.9GB: boot/grub/grub.cfg
 358.8GB: boot/initrd.img-2.6.32-24-generic
 358.7GB: boot/vmlinuz-2.6.32-24-generic
 358.8GB: initrd.img
 358.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  0a 0b 0c 0d 0e 0f 10 11  12 13 14 15 16 17 18 19  |................|
00000010  1a 1b 1c 1d 1e 1f 20 21  22 23 24 25 26 27 28 29  |...... !"#$%&'()|
00000020  2a 2b 2c 2d 2e 2f 30 31  32 33 34 35 36 37 38 39  |*+,-./0123456789|
00000030  3a 3b 3c 3d 3e 3f 40 41  42 43 44 45 46 47 48 49  |:;<=>?@ABCDEFGHI|
00000040  4a 4b 4c 4d 4e 4f 50 51  52 53 54 55 56 57 58 59  |JKLMNOPQRSTUVWXY|
00000050  5a 5b 5c 5d 5e 5f 60 61  62 63 64 65 66 67 68 69  |Z[\]^_`abcdefghi|
00000060  6a 6b 6c 6d 6e 6f 70 71  72 73 74 75 76 77 78 79  |jklmnopqrstuvwxy|
00000070  7a 7b 7c 7d 7e 7f 80 81  82 83 84 85 86 87 88 89  |z{|}~...........|
00000080  8a 8b 8c 8d 8e 8f 90 91  92 93 94 95 96 97 98 99  |................|
00000090  9a 9b 9c 9d 9e 9f a0 a1  a2 a3 a4 a5 a6 a7 a8 a9  |................|
000000a0  aa ab ac ad ae af b0 b1  b2 b3 b4 b5 b6 b7 b8 b9  |................|
000000b0  ba bb bc bd be bf c0 c1  c2 c3 c4 c5 c6 c7 c8 c9  |................|
000000c0  ca cb cc cd ce cf d0 d1  d2 d3 d4 d5 d6 d7 d8 d9  |................|
000000d0  da db dc dd de df e0 e1  e2 e3 e4 e5 e6 e7 e8 e9  |................|
000000e0  ea eb ec ed ee ef f0 f1  f2 f3 f4 f5 f6 f7 f8 f9  |................|
000000f0  fa fb fc fd fe ff 00 01  02 03 04 05 06 07 08 09  |................|
00000100  0a 0b 0c 0d 0e 0f 10 11  12 13 14 15 16 17 18 19  |................|
00000110  1a 1b 1c 1d 1e 1f 20 21  22 23 24 25 26 27 28 29  |...... !"#$%&'()|
00000120  2a 2b 2c 2d 2e 2f 30 31  32 33 34 35 36 37 38 39  |*+,-./0123456789|
00000130  3a 3b 3c 3d 3e 3f 40 41  42 43 44 45 46 47 48 49  |:;<=>?@ABCDEFGHI|
00000140  4a 4b 4c 4d 4e 4f 50 51  52 53 54 55 56 57 58 59  |JKLMNOPQRSTUVWXY|
00000150  5a 5b 5c 5d 5e 5f 60 61  62 63 64 65 66 67 68 69  |Z[\]^_`abcdefghi|
00000160  6a 6b 6c 6d 6e 6f 70 71  72 73 74 75 76 77 78 79  |jklmnopqrstuvwxy|
00000170  7a 7b 7c 7d 7e 7f 80 81  82 83 84 85 86 87 88 89  |z{|}~...........|
00000180  8a 8b 8c 8d 8e 8f 90 91  92 93 94 95 96 97 98 99  |................|
00000190  9a 9b 9c 9d 9e 9f a0 a1  a2 a3 a4 a5 a6 a7 a8 a9  |................|
000001a0  aa ab ac ad ae af b0 b1  b2 b3 b4 b5 b6 b7 b8 b9  |................|
000001b0  ba bb bc bd be bf c0 c1  c2 c3 c4 c5 c6 c7 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 67 83 1b 19 00 fe  |..........g.....|
000001d0  ff ff 05 fe ff ff da fd  b8 31 c8 0a 2c 01 00 00  |.........1..,...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Kind regards,
Joshua

---

### Post by arrange on 2010-09-01
```
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 645073312 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

```The problem is that you installed Grub to the boot sector of your Vista partition (**sdb1**). Once you repair the boot sector, it should work. See for instance
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
/FixBoot

---

### Post by wilee-nilee on 2010-09-01
Generally this is what is advised for having grub in the NTFS boot.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Also you should have sdb as being read first at boot.

You must be a hardcore MS person to put the 2 Ubuntu into ext2 
partitions.

You also have two swaps in sdb, take a look at your hard drive from gparted once you have yourself all working.

---

### Post by JoshuaHardcastle on 2010-09-01
Thank you chaps for your fast and efficacious replies.  What was becoming a big problem for me and was stressing me out was quickly resolved, and I appreciate your help greatly.  

I went with all of wilee-nilee's suggestions and now have a single linux install, single swap.  sdb is the only one that boots now too.

You [WN] mentioned that I must be a hardcore MS person.  I am just ignorant when it comes to linux matters, and I read somewhere prior to install that the ext2 format was what I should use.  FWIW I have now formatted it as an ext3.  I do not know if that is any better, or the merits or failings of each type.  

All the best,
Joshua

---

### Post by wilee-nilee on 2010-09-01
Ext4 is what has been used since Karmic with auto installs from the live cd and by most users, Ext3 is fine though

Did you remove the MS? If you didn't it should be in your grub menu.

---

### Post by JoshuaHardcastle on 2010-09-02
Ahh - thanks for the info.  I will keep ext3 until I need to reinstall again, and I will make the change then. 

I did not remove the vista, and it does show up the GRUB menu.  I need it for some work I do (legacy software).  I tried out wine which works for some of the MS programs I use, but not for all.  My initial impressions are that Ubuntu seems considerably faster than my vista.

I am now up and running, and in the process of setting up prefs and migrating some of my work over for linux.  I have been playing with some basic settings to help orientate myself to linux.

TBH it seems like a bit of a steep learning curve, but as they say "that which does not kill us makes us stronger".  My partner has also taken the plunge with ubuntu (no dual boot though) too, so I look forward to participating (asking loads of questions) here in the future.  If I'm not around here, you will know it was the penguin who dun'it.

All the best,
Joshua

---

