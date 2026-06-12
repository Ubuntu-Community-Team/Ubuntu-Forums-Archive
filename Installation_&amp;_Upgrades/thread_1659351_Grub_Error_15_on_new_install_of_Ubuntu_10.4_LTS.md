---
title: "Grub Error 15 on new install of Ubuntu 10.4 LTS"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by dudemanbubba on 2011-01-03
I have been pulling my hair out for hours.  I decided to bite the bullet and upgrade to the 10.4 LTS from 8.10.  Did a complete fresh install and chose to automatically clean off the drive and install the new system from scratch.

I have three hard drives with the system on the smaller 40GB and the other two drives are 500GB and 2TB.

From what I can tell my problem probably stems from having the older Grub 0.97 on the system on another drive, but I can't seem to figure out how to purge it.  When I mount the partitions, there is no /boot folder...

Any help would be appreciated!

The following is the output from the Boot Info Script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,772,159   976,772,097   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 3,907,024,064 3,907,024,002  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 16.0 GB, 16001269760 bytes
5 heads, 32 sectors/track, 195328 cylinders, total 31252480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          8,064    31,252,479    31,244,416   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0b2c7ba8-a15b-45a6-a62a-a39a228bfc30   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7E34ADC934AD84AD                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        b6ac7c38-a867-47ba-a9a6-5fae67f79723   ext3       2 TB Media                    
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        C018-06A3                              vfat       KINGSTON                      
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0b2c7ba8-a15b-45a6-a62a-a39a228bfc30 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  30.3GB: boot/grub/core.img
  21.6GB: boot/grub/grub.cfg
  30.3GB: boot/initrd.img-2.6.32-24-generic
  30.3GB: boot/vmlinuz-2.6.32-24-generic
  30.3GB: initrd.img
  30.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e6 51 12 00 f6 51 12 00  06 52 12 00 16 52 12 00  |.Q...Q...R...R..|
00000010  26 52 12 00 36 52 12 00  46 52 12 00 56 52 12 00  |&R..6R..FR..VR..|
00000020  66 52 12 00 76 52 12 00  86 52 12 00 96 52 12 00  |fR..vR...R...R..|
00000030  a6 52 12 00 b6 52 12 00  c6 52 12 00 d6 52 12 00  |.R...R...R...R..|
00000040  e6 52 12 00 f6 52 12 00  06 53 12 00 16 53 12 00  |.R...R...S...S..|
00000050  90 50 9e 00 36 53 12 00  46 53 12 00 56 53 12 00  |.P..6S..FS..VS..|
00000060  66 53 12 00 76 53 12 00  86 53 12 00 96 53 12 00  |fS..vS...S...S..|
00000070  a6 53 12 00 b6 53 12 00  c6 53 12 00 d6 53 12 00  |.S...S...S...S..|
00000080  e6 53 12 00 f6 53 12 00  06 54 12 00 16 54 12 00  |.S...S...T...T..|
00000090  26 54 12 00 36 54 12 00  46 54 12 00 56 54 12 00  |&T..6T..FT..VT..|
000000a0  66 54 12 00 76 54 12 00  86 54 12 00 96 54 12 00  |fT..vT...T...T..|
000000b0  a6 54 12 00 b6 54 12 00  c6 54 12 00 50 16 a1 00  |.T...T...T..P...|
000000c0  e6 54 12 00 f6 54 12 00  06 55 12 00 16 55 12 00  |.T...T...U...U..|
000000d0  26 55 12 00 36 55 12 00  46 55 12 00 b0 1e 65 00  |&U..6U..FU....e.|
000000e0  66 55 12 00 76 55 12 00  86 55 12 00 96 55 12 00  |fU..vU...U...U..|
000000f0  a6 55 12 00 b6 55 12 00  c6 55 12 00 d6 55 12 00  |.U...U...U...U..|
00000100  e6 55 12 00 f6 55 12 00  06 56 12 00 16 56 12 00  |.U...U...V...V..|
00000110  26 56 12 00 36 56 12 00  46 56 12 00 56 56 12 00  |&V..6V..FV..VV..|
00000120  66 56 12 00 76 56 12 00  86 56 12 00 20 a1 64 00  |fV..vV...V.. .d.|
00000130  a6 56 12 00 b6 56 12 00  c6 56 12 00 d6 56 12 00  |.V...V...V...V..|
00000140  e6 56 12 00 f6 56 12 00  06 57 12 00 16 57 12 00  |.V...V...W...W..|
00000150  26 57 12 00 36 57 12 00  46 57 12 00 56 57 12 00  |&W..6W..FW..VW..|
00000160  66 57 12 00 76 57 12 00  70 78 9e 00 96 57 12 00  |fW..vW..px...W..|
00000170  a6 57 12 00 74 47 1a 00  a0 6d 12 00 70 6d 12 00  |.W..tG...m..pm..|
00000180  c0 6c 12 00 50 6c 12 00  00 00 00 00 00 00 00 00  |.l..Pl..........|
00000190  0e 24 19 00 00 00 00 00  ff ff ff ff 01 00 00 00  |.$..............|
000001a0  80 3e 18 00 f0 44 18 00  90 3e 18 00 00 00 00 00  |.>...D...>......|
000001b0  00 00 00 00 00 00 00 00  01 00 00 00 01 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde 
```

---

### Post by dudemanbubba on 2011-01-03
The 500GB hard drive had nothing on it so I deleted the existing partition and reformatted the drive in an effort to fix any issues of having the old grub remnants lying around.  However, the same issue still appears to exist.  Not sure where to go from here.

I was able to get the system to boot up by "booting to 1st hard drive" option when booting from a LiveCD... The operating system seems to be working fine, except it won't initially boot up properly.

This is the new output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 3,907,024,064 3,907,024,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0b2c7ba8-a15b-45a6-a62a-a39a228bfc30   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        d495ff46-c9ae-496c-ae26-ac0365103138   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        b6ac7c38-a867-47ba-a9a6-5fae67f79723   ext3       2 TB Media                    
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Ubuntu 10.04.1 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/d495ff46-c9ae-496c-ae26-ac0365103138 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/2 TB Media        ext3       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0b2c7ba8-a15b-45a6-a62a-a39a228bfc30 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  30.3GB: boot/grub/core.img
  30.3GB: boot/grub/grub.cfg
  30.3GB: boot/initrd.img-2.6.32-24-generic
  30.3GB: boot/vmlinuz-2.6.32-24-generic
  30.3GB: initrd.img
  30.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e6 51 12 00 f6 51 12 00  06 52 12 00 16 52 12 00  |.Q...Q...R...R..|
00000010  26 52 12 00 36 52 12 00  46 52 12 00 56 52 12 00  |&R..6R..FR..VR..|
00000020  66 52 12 00 76 52 12 00  86 52 12 00 96 52 12 00  |fR..vR...R...R..|
00000030  a6 52 12 00 b6 52 12 00  c6 52 12 00 d6 52 12 00  |.R...R...R...R..|
00000040  e6 52 12 00 f6 52 12 00  06 53 12 00 16 53 12 00  |.R...R...S...S..|
00000050  90 50 9e 00 36 53 12 00  46 53 12 00 56 53 12 00  |.P..6S..FS..VS..|
00000060  66 53 12 00 76 53 12 00  86 53 12 00 96 53 12 00  |fS..vS...S...S..|
00000070  a6 53 12 00 b6 53 12 00  c6 53 12 00 d6 53 12 00  |.S...S...S...S..|
00000080  e6 53 12 00 f6 53 12 00  06 54 12 00 16 54 12 00  |.S...S...T...T..|
00000090  26 54 12 00 36 54 12 00  46 54 12 00 56 54 12 00  |&T..6T..FT..VT..|
000000a0  66 54 12 00 76 54 12 00  86 54 12 00 96 54 12 00  |fT..vT...T...T..|
000000b0  a6 54 12 00 b6 54 12 00  c6 54 12 00 50 16 a1 00  |.T...T...T..P...|
000000c0  e6 54 12 00 f6 54 12 00  06 55 12 00 16 55 12 00  |.T...T...U...U..|
000000d0  26 55 12 00 36 55 12 00  46 55 12 00 b0 1e 65 00  |&U..6U..FU....e.|
000000e0  66 55 12 00 76 55 12 00  86 55 12 00 96 55 12 00  |fU..vU...U...U..|
000000f0  a6 55 12 00 b6 55 12 00  c6 55 12 00 d6 55 12 00  |.U...U...U...U..|
00000100  e6 55 12 00 f6 55 12 00  06 56 12 00 16 56 12 00  |.U...U...V...V..|
00000110  26 56 12 00 36 56 12 00  46 56 12 00 56 56 12 00  |&V..6V..FV..VV..|
00000120  66 56 12 00 76 56 12 00  86 56 12 00 20 a1 64 00  |fV..vV...V.. .d.|
00000130  a6 56 12 00 b6 56 12 00  c6 56 12 00 d6 56 12 00  |.V...V...V...V..|
00000140  e6 56 12 00 f6 56 12 00  06 57 12 00 16 57 12 00  |.V...V...W...W..|
00000150  26 57 12 00 36 57 12 00  46 57 12 00 56 57 12 00  |&W..6W..FW..VW..|
00000160  66 57 12 00 76 57 12 00  70 78 9e 00 96 57 12 00  |fW..vW..px...W..|
00000170  a6 57 12 00 74 47 1a 00  a0 6d 12 00 70 6d 12 00  |.W..tG...m..pm..|
00000180  c0 6c 12 00 50 6c 12 00  00 00 00 00 00 00 00 00  |.l..Pl..........|
00000190  0e 24 19 00 00 00 00 00  ff ff ff ff 01 00 00 00  |.$..............|
000001a0  80 3e 18 00 f0 44 18 00  90 3e 18 00 00 00 00 00  |.>...D...>......|
000001b0  00 00 00 00 00 00 00 00  01 00 00 00 01 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by drs305 on 2011-01-03
Make sure your BIOS is booting your sda drive (40GB) first. If it isn't set up that way, change it.

Your boot files look ok. From your running Ubuntu installation, try repointing the MBR to sda1 and update the grub menu:
```
sudo grub-install /dev/sda
sudo update-grub
```

If this doesn't solve it, boot a LiveCD and purge and reinstall Grub2 using the chroot procedure in this guide:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by dudemanbubba on 2011-01-04
Went through it 4 times.  No luck.  Not sure where to go from here.

It still shows Grub 0.97 on sdb... I deleted the partition and reformatted it.  That puzzles me.

Thanks.

---

### Post by dino99 on 2011-01-04
you have to find & remove : grub (0.97) & menu.lst.

Simply run nautilus to "search" these related files, then check (right click) their properties to know where they are located. Open an other nautilus window to delete them.

When done, update-grub again. An other solution is to open synaptic: remove/purge grub-pc then reinstall it.

---

### Post by drs305 on 2011-01-04
> **dudemanbubba said:**
> Went through it 4 times.  No luck.  Not sure where to go from here.

It still shows Grub 0.97 on sdb... I deleted the partition and reformatted it.  That puzzles me.

Thanks.

If you are chrooting into your Ubuntu installation the purge/reinstall is not going to remove the sdb Grub legacy. But unless your BIOS is pointing to the sdb MBR it should have no effect on your operation.

You can install Grub2 on sdb as well as sda. From a running Ubuntu:
```
sudo grub-install  /dev/sdb
sudo grub-install /dev/sda
```
This will install G2 to both MBRs and will work even though no "--root-directory" is designated in the sdb command. TestDisk will misleadingly show that G2 is installed in sdb and looks to the same drive in sdb8, but it will still work even if sdb is the boot drive.

If you just want to clean up the sdb MBR without putting Grub 2 on it, you can use TestDisk to write it's own signature to the MBR. It won't change the operation of your machine if sdb isn't being used, but it will get rid of the Grub 0.97 designation.

From a running Ubuntu, install TestDisk (it's in the Universe repository):
```
sudo apt-get install testdisk
```
Confirm sdb is your 500GB drive and then run TestDisk to rewrite the sdb MBR:


```
sudo testdisk
```
No Log
Select sdb > Proceed > 
Continue > 
Intel (do not leave on "None") >
MBR Code: Write TestDisk 
MBR Code to First Sector. Y
Write new copy of MBR code: Y (Confirm)
OK
Quit
Quit

---

### Post by dudemanbubba on 2011-01-04
Well, I gave up and went to bed last night where I left off.  When I got up this morning, I checked your last post.  Testdisk utility listed the 500 GB as sda?  I quit out and double checked fdisk -l which showed the same. I am not sure how things could have changed without a reboot overnight.

Anyway, your comment about the bios intrigued me.  Although I did not make any bios changes on the machine which had hardy on it before, it was pointing to the SCSI HD prior to the IDE HD in the boot order.  I changed it and everything started working.

Thank you so much for your help!

I had installed Grub2 on both drives.   Should I remove it from the other drive now?

New boot output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 3,907,024,064 3,907,024,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0b2c7ba8-a15b-45a6-a62a-a39a228bfc30   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        d495ff46-c9ae-496c-ae26-ac0365103138   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        b6ac7c38-a867-47ba-a9a6-5fae67f79723   ext3       2 TB Media                    
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=b1fc945f-b3cb-4ef3-ba2e-24271b2e5a89 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0b2c7ba8-a15b-45a6-a62a-a39a228bfc30 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/core.img
  21.6GB: boot/grub/grub.cfg
  30.4GB: boot/initrd.img-2.6.32-24-generic
  30.4GB: boot/initrd.img-2.6.32-27-generic
  30.4GB: boot/vmlinuz-2.6.32-24-generic
  30.4GB: boot/vmlinuz-2.6.32-27-generic
  30.4GB: initrd.img
  30.4GB: initrd.img.old
  30.4GB: vmlinuz
  30.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e6 51 12 00 f6 51 12 00  06 52 12 00 16 52 12 00  |.Q...Q...R...R..|
00000010  26 52 12 00 36 52 12 00  46 52 12 00 56 52 12 00  |&R..6R..FR..VR..|
00000020  66 52 12 00 76 52 12 00  86 52 12 00 96 52 12 00  |fR..vR...R...R..|
00000030  a6 52 12 00 b6 52 12 00  c6 52 12 00 d6 52 12 00  |.R...R...R...R..|
00000040  e6 52 12 00 f6 52 12 00  06 53 12 00 16 53 12 00  |.R...R...S...S..|
00000050  90 50 9e 00 36 53 12 00  46 53 12 00 56 53 12 00  |.P..6S..FS..VS..|
00000060  66 53 12 00 76 53 12 00  86 53 12 00 96 53 12 00  |fS..vS...S...S..|
00000070  a6 53 12 00 b6 53 12 00  c6 53 12 00 d6 53 12 00  |.S...S...S...S..|
00000080  e6 53 12 00 f6 53 12 00  06 54 12 00 16 54 12 00  |.S...S...T...T..|
00000090  26 54 12 00 36 54 12 00  46 54 12 00 56 54 12 00  |&T..6T..FT..VT..|
000000a0  66 54 12 00 76 54 12 00  86 54 12 00 96 54 12 00  |fT..vT...T...T..|
000000b0  a6 54 12 00 b6 54 12 00  c6 54 12 00 50 16 a1 00  |.T...T...T..P...|
000000c0  e6 54 12 00 f6 54 12 00  06 55 12 00 16 55 12 00  |.T...T...U...U..|
000000d0  26 55 12 00 36 55 12 00  46 55 12 00 b0 1e 65 00  |&U..6U..FU....e.|
000000e0  66 55 12 00 76 55 12 00  86 55 12 00 96 55 12 00  |fU..vU...U...U..|
000000f0  a6 55 12 00 b6 55 12 00  c6 55 12 00 d6 55 12 00  |.U...U...U...U..|
00000100  e6 55 12 00 f6 55 12 00  06 56 12 00 16 56 12 00  |.U...U...V...V..|
00000110  26 56 12 00 36 56 12 00  46 56 12 00 56 56 12 00  |&V..6V..FV..VV..|
00000120  66 56 12 00 76 56 12 00  86 56 12 00 20 a1 64 00  |fV..vV...V.. .d.|
00000130  a6 56 12 00 b6 56 12 00  c6 56 12 00 d6 56 12 00  |.V...V...V...V..|
00000140  e6 56 12 00 f6 56 12 00  06 57 12 00 16 57 12 00  |.V...V...W...W..|
00000150  26 57 12 00 36 57 12 00  46 57 12 00 56 57 12 00  |&W..6W..FW..VW..|
00000160  66 57 12 00 76 57 12 00  70 78 9e 00 96 57 12 00  |fW..vW..px...W..|
00000170  a6 57 12 00 74 47 1a 00  a0 6d 12 00 70 6d 12 00  |.W..tG...m..pm..|
00000180  c0 6c 12 00 50 6c 12 00  00 00 00 00 00 00 00 00  |.l..Pl..........|
00000190  0e 24 19 00 00 00 00 00  ff ff ff ff 01 00 00 00  |.$..............|
000001a0  80 3e 18 00 f0 44 18 00  90 3e 18 00 00 00 00 00  |.>...D...>......|
000001b0  00 00 00 00 00 00 00 00  01 00 00 00 01 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by drs305 on 2011-01-04
> **dudemanbubba said:**
> 
I had installed Grub2 on both drives.   Should I remove it from the other drive now?

Glad you now have it booting! As far as having G2 on the non-OS drive, I'd recommend just leaving it there. It should still work if the boot drive order changes.

If your problems are resolved, you can mark the thread SOLVED via the 'Thread Tools' link near the top right of the original post.

---

### Post by dudemanbubba on 2011-01-04
I seem to be one of those people who time spent resolving problems seems to be inversely proportional to the complexity of the remedy!

Thread marked as solved!  Thanks again!

---

