---
title: "w7 ubuntu 10.10 dual boot 2 drives"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by djgies on 2010-12-29
Hi, had w7 installed on my netbook, but I want to use ubuntu as my main OS.  My netbook has two hard drives: one 32gb ssd drive where w7 is now, and one 8gb drive where 10.10 is installed.  Grub2 only shows the linux OS and not the w7.  I tried using the w7 recovery disk 3 times and each time it said that the problem could not be fixed automatically.  Then I tried BootRec.exe/fixmbr from the windows console and I was unable to boot to either OS - I'm guessing it tried to erase grub2 and replace it with a dos/ibm mbr?  

How do I get Grub2 to recognize the second hard drive and OS?  How do I get a boot loader onto sdb without repeating the problem I encountered with BootRec

---

### Post by Kirboosy on 2010-12-29
So let me see if I got this straight. You have 2 SSDs. One 8 Gb drive and One 32 Gb drive? 


You had Ubuntu on the small one and you want to move it to the large one. Are both of the drives installed at the same time?

Or do you mean partitions?

---

### Post by djgies on 2010-12-29
I don't want to move anything, just get both OS working.  They are separate drives, not partitions, 8gb is set as master, 32gb as slave.

---

### Post by djgies on 2010-12-29
Also, both drives are installed at the same time, and the 32gb drive shows up in ubuntu as a file system

---

### Post by wilee-nilee on 2010-12-29
First look in my signature and code tag that script.

Then boot a live Ubuntu cd open the gparted partitioner right click on the W7 partition the flags then boot. 

Boot the W7 cd and run the auto repair again 3 times you need an active partition=bootflag for this to work.

---

### Post by djgies on 2010-12-29
Hi, I flagged the drive with w7 on it (sdb1) as boot and did the startup repair using the windows cd three times.  No luck.  

In the system restore options screen of the windows cd no operating systems show up, so I've just been clicking next.  Now when I tried to boot from sdb (from bios menu) I get "bootmgr is missing."  Grub2 still only recognizes linux.  



```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: __________________________________________________  _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________  _______________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________  _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: __________________________________________________  _______________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________  ___

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    14,983,167    14,981,120  83 Linux
/dev/sda2          14,985,214    15,759,359       774,146   5 Extended
/dev/sda5          14,985,216    15,759,359       774,144  82 Linux swap / Solaris


Drive: sdb ___________________ __________________________________________________  ___

Disk /dev/sdb: 32.3 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders, total 63045360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    63,041,535    63,039,488   7 HPFS/NTFS


Drive: sdc ___________________ __________________________________________________  ___

Disk /dev/sdc: 1994 MB, 1994273280 bytes
32 heads, 63 sectors/track, 1932 cylinders, total 3895065 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63     3,894,911     3,894,849   6 FAT16


blkid -c /dev/null: __________________________________________________  __________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3ed52f27-4728-4974-8507-8e62e9d1d839   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b6e785de-f427-48dc-8009-981824aa52ef   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D008EE9D08EE8238                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        62E6-4C65                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/62E6-4C65         vfat        (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,   shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3ed52f27-4728-4974-8507-8e62e9d1d839 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3ed52f27-4728-4974-8507-8e62e9d1d839 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3ed52f27-4728-4974-8507-8e62e9d1d839 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b6e785de-f427-48dc-8009-981824aa52ef none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.8GB: boot/grub/core.img
   4.8GB: boot/grub/grub.cfg
   4.8GB: boot/initrd.img-2.6.35-22-generic
   2.8GB: boot/vmlinuz-2.6.35-22-generic
   4.8GB: initrd.img
   2.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2b 00 2f ec 33 32 32 33  2f ed 33 33 2f 2f 11 33  |+./.3223/.33//.3|
00000010  33 12 39 32 32 2f 2f 2f  2f 30 13 26 11 10 37 36  |3.922////0.&..76|
00000020  37 33 06 07 06 07 06 11  10 17 12 17 23 26 25 06  |73..........#&%.|
00000030  07 23 36 13 36 11 10 27  26 27 26 27 33 16 17 16  |.#6.6..'&'&'3...|
00000040  11 10 01 33 01 01 21 15  23 11 33 15 21 35 33 11  |...3..!.#.3.!53.|
00000050  23 35 01 23 96 4a 4c 43  9c 6b 2b 42 3d 21 56 58  |#5.#.JLC.k+B=!VX|
00000060  61 6c 75 9d 06 9b 3d 9f  74 6c 61 58 56 21 3d 42  |alu...=.tlaXV!=B|
00000070  2b 6a 9e 42 4b f9 b1 96  01 18 01 18 02 39 88 88  |+j.BK........9..|
00000080  fe 5f 88 88 fe 95 85 01  14 f7 01 07 01 06 f2 d6  |._..............|
00000090  d6 36 80 76 59 e5 fe c6  fe c9 ea fe fe 80 d8 cd  |.6.vY...........|
000000a0  cb da 80 01 02 ea 01 37  01 3a e5 59 76 80 36 d9  |.......7.:.Yv.6.|
000000b0  d3 ef fe f7 fe f5 03 70  fb eb 04 15 83 fc 17 86  |.......p........|
000000c0  86 03 e9 7c fb 15 00 04  00 4c ff 6f 07 b8 06 b6  |...|.....L.o....|
000000d0  00 13 00 27 00 38 00 3c  00 3b 40 0c 12 37 21 12  |...'.8.<.;@..7!.|
000000e0  17 37 21 06 17 06 17 28  b8 ff f0 40 0f 30 28 3c  |.7!....(...@.0(<|
000000f0  2d 03 36 4d 31 31 06 2c  3b 34 f3 29 00 2f ed 32  |-.6M11.,;4.)./.2|
00000100  32 32 33 2f ec 17 33 32  38 33 2f 2f 11 33 33 11  |223/..3283//.33.|
00000110  33 2f 2f 2f 30 13 26 11  10 37 36 37 33 06 07 06  |3///0.&..7673...|
00000120  07 06 11 10 17 12 17 23  26 25 06 07 23 36 13 36  |.......#&%..#6.6|
00000130  11 10 27 26 27 26 27 33  16 17 16 11 10 05 13 21  |..'&'&'3.......!|
00000140  15 23 11 33 15 21 35 33  11 23 03 23 01 33 01 11  |.#.3.!53.#.#.3..|
00000150  23 11 96 4a 4c 43 9c 6b  2b 42 3d 21 56 58 61 6c  |#..JLC.k+B=!VXal|
00000160  75 9d 06 9b 3d 9f 74 6c  61 58 56 21 3d 42 2b 6a  |u...=.tlaXV!=B+j|
00000170  9e 42 4b fb 37 bc 02 b8  5f 5f fd c9 5f 5d fd 8c  |.BK.7...__.._]..|
00000180  fe ea a4 03 46 63 01 14  f7 01 07 01 06 f2 d6 d6  |....Fc..........|
00000190  36 80 76 59 e5 fe c6 fe  c9 ea fe fe 80 d8 cd cb  |6.vY............|
000001a0  da 80 01 02 ea 01 37 01  3a e5 59 76 80 36 d9 d3  |......7.:.Yv.6..|
000001b0  ef fe f7 fe f5 44 03 b4  78 fc 00 7a 7a 04 00 c8  |.....D..x..zz...|
000001c0  e5 a4 82 f8 e4 d4 02 00  00 00 00 d0 0b 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by wilee-nilee on 2010-12-29
/dev/sda1    *          2,048    14,983,167    14,981,120  83 Linux
/dev/sda2          14,985,214    15,759,359       774,146   5 Extended
/dev/sda5          14,985,216    15,759,359       774,144  82 Linux swap / Solaris


Drive: sdb ___________________ __________________________________________________  ___

Disk /dev/sdb: 32.3 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders, total 63045360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    63,041,535    63,039,488   7 HPFS/NTFS

You didn't set the flag see that asterisk **(*)** next to sda1 it should be gone and on sdb1

---

### Post by djgies on 2010-12-29
This is the current situation.  Sorry, the previous script was before using gparted.  I've got the asterisk on sdb1.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    14,983,167    14,981,120  83 Linux
/dev/sda2          14,985,214    15,759,359       774,146   5 Extended
/dev/sda5          14,985,216    15,759,359       774,144  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 32.3 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders, total 63045360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    63,041,535    63,039,488   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1994 MB, 1994273280 bytes
32 heads, 63 sectors/track, 1932 cylinders, total 3895065 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63     3,894,911     3,894,849   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3ed52f27-4728-4974-8507-8e62e9d1d839   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b6e785de-f427-48dc-8009-981824aa52ef   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D008EE9D08EE8238                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        62E6-4C65                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/62E6-4C65         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3ed52f27-4728-4974-8507-8e62e9d1d839 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3ed52f27-4728-4974-8507-8e62e9d1d839 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3ed52f27-4728-4974-8507-8e62e9d1d839 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b6e785de-f427-48dc-8009-981824aa52ef none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.8GB: boot/grub/core.img
   4.8GB: boot/grub/grub.cfg
   4.8GB: boot/initrd.img-2.6.35-22-generic
   2.8GB: boot/vmlinuz-2.6.35-22-generic
   4.8GB: initrd.img
   2.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2b 00 2f ec 33 32 32 33  2f ed 33 33 2f 2f 11 33  |+./.3223/.33//.3|
00000010  33 12 39 32 32 2f 2f 2f  2f 30 13 26 11 10 37 36  |3.922////0.&..76|
00000020  37 33 06 07 06 07 06 11  10 17 12 17 23 26 25 06  |73..........#&%.|
00000030  07 23 36 13 36 11 10 27  26 27 26 27 33 16 17 16  |.#6.6..'&'&'3...|
00000040  11 10 01 33 01 01 21 15  23 11 33 15 21 35 33 11  |...3..!.#.3.!53.|
00000050  23 35 01 23 96 4a 4c 43  9c 6b 2b 42 3d 21 56 58  |#5.#.JLC.k+B=!VX|
00000060  61 6c 75 9d 06 9b 3d 9f  74 6c 61 58 56 21 3d 42  |alu...=.tlaXV!=B|
00000070  2b 6a 9e 42 4b f9 b1 96  01 18 01 18 02 39 88 88  |+j.BK........9..|
00000080  fe 5f 88 88 fe 95 85 01  14 f7 01 07 01 06 f2 d6  |._..............|
00000090  d6 36 80 76 59 e5 fe c6  fe c9 ea fe fe 80 d8 cd  |.6.vY...........|
000000a0  cb da 80 01 02 ea 01 37  01 3a e5 59 76 80 36 d9  |.......7.:.Yv.6.|
000000b0  d3 ef fe f7 fe f5 03 70  fb eb 04 15 83 fc 17 86  |.......p........|
000000c0  86 03 e9 7c fb 15 00 04  00 4c ff 6f 07 b8 06 b6  |...|.....L.o....|
000000d0  00 13 00 27 00 38 00 3c  00 3b 40 0c 12 37 21 12  |...'.8.<.;@..7!.|
000000e0  17 37 21 06 17 06 17 28  b8 ff f0 40 0f 30 28 3c  |.7!....(...@.0(<|
000000f0  2d 03 36 4d 31 31 06 2c  3b 34 f3 29 00 2f ed 32  |-.6M11.,;4.)./.2|
00000100  32 32 33 2f ec 17 33 32  38 33 2f 2f 11 33 33 11  |223/..3283//.33.|
00000110  33 2f 2f 2f 30 13 26 11  10 37 36 37 33 06 07 06  |3///0.&..7673...|
00000120  07 06 11 10 17 12 17 23  26 25 06 07 23 36 13 36  |.......#&%..#6.6|
00000130  11 10 27 26 27 26 27 33  16 17 16 11 10 05 13 21  |..'&'&'3.......!|
00000140  15 23 11 33 15 21 35 33  11 23 03 23 01 33 01 11  |.#.3.!53.#.#.3..|
00000150  23 11 96 4a 4c 43 9c 6b  2b 42 3d 21 56 58 61 6c  |#..JLC.k+B=!VXal|
00000160  75 9d 06 9b 3d 9f 74 6c  61 58 56 21 3d 42 2b 6a  |u...=.tlaXV!=B+j|
00000170  9e 42 4b fb 37 bc 02 b8  5f 5f fd c9 5f 5d fd 8c  |.BK.7...__.._]..|
00000180  fe ea a4 03 46 63 01 14  f7 01 07 01 06 f2 d6 d6  |....Fc..........|
00000190  36 80 76 59 e5 fe c6 fe  c9 ea fe fe 80 d8 cd cb  |6.vY............|
000001a0  da 80 01 02 ea 01 37 01  3a e5 59 76 80 36 d9 d3  |......7.:.Yv.6..|
000001b0  ef fe f7 fe f5 44 03 b4  78 fc 00 7a 7a 04 00 c8  |.....D..x..zz...|
000001c0  e5 a4 82 f8 e4 d4 02 00  00 00 00 d0 0b 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by djgies on 2010-12-29
Hey, I'm taking the flag off sda1, and will try the 3 repairs again.

---

### Post by djgies on 2010-12-29
I tried what you suggested.  Still does not boot from bios or grub2, and no operating systems are listed in  the windows recovery menu of the windows cd.  Now the startup repair finishes and says that it has fixed the problem, but ubuntu reboots.    

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    14,983,167    14,981,120  83 Linux
/dev/sda2          14,985,214    15,759,359       774,146   5 Extended
/dev/sda5          14,985,216    15,759,359       774,144  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 32.3 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders, total 63045360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    63,041,535    63,039,488   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1994 MB, 1994273280 bytes
32 heads, 63 sectors/track, 1932 cylinders, total 3895065 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63     3,894,911     3,894,849   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3ed52f27-4728-4974-8507-8e62e9d1d839   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b6e785de-f427-48dc-8009-981824aa52ef   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D008EE9D08EE8238                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        62E6-4C65                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/62E6-4C65         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3ed52f27-4728-4974-8507-8e62e9d1d839 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3ed52f27-4728-4974-8507-8e62e9d1d839 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ed52f27-4728-4974-8507-8e62e9d1d839
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3ed52f27-4728-4974-8507-8e62e9d1d839 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b6e785de-f427-48dc-8009-981824aa52ef none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.8GB: boot/grub/core.img
   4.8GB: boot/grub/grub.cfg
   4.8GB: boot/initrd.img-2.6.35-22-generic
   2.8GB: boot/vmlinuz-2.6.35-22-generic
   4.8GB: initrd.img
   2.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2b 00 2f ec 33 32 32 33  2f ed 33 33 2f 2f 11 33  |+./.3223/.33//.3|
00000010  33 12 39 32 32 2f 2f 2f  2f 30 13 26 11 10 37 36  |3.922////0.&..76|
00000020  37 33 06 07 06 07 06 11  10 17 12 17 23 26 25 06  |73..........#&%.|
00000030  07 23 36 13 36 11 10 27  26 27 26 27 33 16 17 16  |.#6.6..'&'&'3...|
00000040  11 10 01 33 01 01 21 15  23 11 33 15 21 35 33 11  |...3..!.#.3.!53.|
00000050  23 35 01 23 96 4a 4c 43  9c 6b 2b 42 3d 21 56 58  |#5.#.JLC.k+B=!VX|
00000060  61 6c 75 9d 06 9b 3d 9f  74 6c 61 58 56 21 3d 42  |alu...=.tlaXV!=B|
00000070  2b 6a 9e 42 4b f9 b1 96  01 18 01 18 02 39 88 88  |+j.BK........9..|
00000080  fe 5f 88 88 fe 95 85 01  14 f7 01 07 01 06 f2 d6  |._..............|
00000090  d6 36 80 76 59 e5 fe c6  fe c9 ea fe fe 80 d8 cd  |.6.vY...........|
000000a0  cb da 80 01 02 ea 01 37  01 3a e5 59 76 80 36 d9  |.......7.:.Yv.6.|
000000b0  d3 ef fe f7 fe f5 03 70  fb eb 04 15 83 fc 17 86  |.......p........|
000000c0  86 03 e9 7c fb 15 00 04  00 4c ff 6f 07 b8 06 b6  |...|.....L.o....|
000000d0  00 13 00 27 00 38 00 3c  00 3b 40 0c 12 37 21 12  |...'.8.<.;@..7!.|
000000e0  17 37 21 06 17 06 17 28  b8 ff f0 40 0f 30 28 3c  |.7!....(...@.0(<|
000000f0  2d 03 36 4d 31 31 06 2c  3b 34 f3 29 00 2f ed 32  |-.6M11.,;4.)./.2|
00000100  32 32 33 2f ec 17 33 32  38 33 2f 2f 11 33 33 11  |223/..3283//.33.|
00000110  33 2f 2f 2f 30 13 26 11  10 37 36 37 33 06 07 06  |3///0.&..7673...|
00000120  07 06 11 10 17 12 17 23  26 25 06 07 23 36 13 36  |.......#&%..#6.6|
00000130  11 10 27 26 27 26 27 33  16 17 16 11 10 05 13 21  |..'&'&'3.......!|
00000140  15 23 11 33 15 21 35 33  11 23 03 23 01 33 01 11  |.#.3.!53.#.#.3..|
00000150  23 11 96 4a 4c 43 9c 6b  2b 42 3d 21 56 58 61 6c  |#..JLC.k+B=!VXal|
00000160  75 9d 06 9b 3d 9f 74 6c  61 58 56 21 3d 42 2b 6a  |u...=.tlaXV!=B+j|
00000170  9e 42 4b fb 37 bc 02 b8  5f 5f fd c9 5f 5d fd 8c  |.BK.7...__.._]..|
00000180  fe ea a4 03 46 63 01 14  f7 01 07 01 06 f2 d6 d6  |....Fc..........|
00000190  36 80 76 59 e5 fe c6 fe  c9 ea fe fe 80 d8 cd cb  |6.vY............|
000001a0  da 80 01 02 ea 01 37 01  3a e5 59 76 80 36 d9 d3  |......7.:.Yv.6..|
000001b0  ef fe f7 fe f5 44 03 b4  78 fc 00 7a 7a 04 00 c8  |.....D..x..zz...|
000001c0  e5 a4 82 f8 e4 d4 02 00  00 00 00 d0 0b 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by wilee-nilee on 2010-12-29
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

Your script your missing the highlighted part.

So when you installed Ubuntu did you remove a XP per chance?

Also remove that first script or code tag it, it is hard to scroll the page and keep up with the text disproportionately posted. :)

When you installed W7 either you had XP, or the boot partition for W7 was in the sda HD.

---

### Post by djgies on 2010-12-29
Hi, thanks for your help.  I've never had XP on this machine, so the boot partition for w7 must have been on sda.  I don't know what to do next.  Any ideas?  :eek:

---

### Post by wilee-nilee on 2010-12-29
So try this go to the bios and make the sdb as read first.

Then boot the W7 disc to the repair command line and run these commands. Then reboot with sdb still read first and see if it goes straight to W7. If it does then put sda first again then boot Ubuntu and run sudo update-grub there, last. The Ubuntu stuff here is after getting W7 going. Notice as well the link to the W7 forums for a visual of getting to the command line I think you know already but it helps to have a visual sometimes.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Don't worry about the if you still want grub warning.

---

### Post by djgies on 2010-12-29
Hey Thanks!  Just changing the boot order allowed windows recovery to recognize W7, and it did the fix itself (on second time in), so I didn't go into the command prompt.  Now I have 10.10 and w7 both working.

---

### Post by wilee-nilee on 2010-12-29
> **djgies said:**
> Hey Thanks!  Just changing the boot order allowed windows recovery to recognise W7, and it did the fix itself (on second time in), so I didn't go into the command prompt.  Now I have 10.10 and w7 both working.

I wondered about that cool.:)

---

