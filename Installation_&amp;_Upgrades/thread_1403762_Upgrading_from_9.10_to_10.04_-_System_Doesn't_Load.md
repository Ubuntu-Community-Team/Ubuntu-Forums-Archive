---
title: "Upgrading from 9.10 to 10.04 - System Doesn't Load"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by Chelinda on 2010-02-10
After upgrading from 9.10 to 10.04 my System no longer boots.  I had a Dual-Boot System.

On Boot I get - " error : the symbol 'grub_puts_' not found     grub rescue> (prompt)

If I run 'insmode /boot/grub/normal.mod' (I get the same error)
If I run  'insmode /boot/grub/ext2.mod' (I get 'The symbol 'grub_xasprinf' not found)
If I run ls /boot (The Kernel File Names look OK)

If I run in Rescue Mode it Reports (The installer could not find any partitions, so you will not be able to mount a root file system.  This may be caused by the Kernel failing to detect your hard disk drive or failing to read the partition table, or the disk may be unpartitioned.  If you wish, you may investigate this from a shell in the installer environment.)

I ran the recommended reporting script and got the following output:-

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdd   <<< This is my USB Flashdrive
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 268211357 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #4 for /boot/grub.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5684c41c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   234,372,284   234,259,830   7 HPFS/NTFS
/dev/sda3         480,214,980   488,392,064     8,177,085   f W95 Ext d (LBA)
/dev/sda5         480,215,043   488,392,064     8,177,022  82 Linux swap / Solaris
/dev/sda4         234,372,285   480,214,979   245,842,695  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   234,372,284   234,356,220   f W95 Ext d (LBA)
/dev/sdb5              16,128    49,913,954    49,897,827   7 HPFS/NTFS
/dev/sdb6          49,914,018   225,809,639   175,895,622  83 Linux
/dev/sdb7         225,809,703   234,372,284     8,562,582   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8220 MB, 8220647936 bytes
16 heads, 63 sectors/track, 15928 cylinders, total 16055953 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cc936

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    16,055,952    16,055,890   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F067-C96C                              vfat       DellUtility                   
/dev/sda2        2AD94214D0A6DE5B                       ntfs       Windoze                       
/dev/sda4        ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74   ext4                                     
/dev/sda5        e1ad31a7-774e-4fc5-afa7-b8704a47054d   swap                                     
/dev/sdb5        01CAA0EFC7D2CF70                       ntfs       Backup of Documents           
/dev/sdb6        5ff33f5b-662b-4cbc-bdd8-b8ac8f7b150b   ext4                                     
/dev/sdb7        647811A2781173D0                       ntfs       Virtual Memory                
/dev/sdd1        74F2-8B3D                              vfat       SANDISK                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda4        /media/ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda2        /media/Windoze           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1        /media/SANDISK           vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect  

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set default="Microsoft Windows XP Professional (on /dev/sda2)"
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
set root=(hd0,4)
search --no-floppy --fs-uuid --set ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74
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
set root=(hd0,4)
search --no-floppy --fs-uuid --set ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=20
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
        recordfail
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74
    echo    Loading Linux 2.6.32-12-generic ...
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.31-19-generic" {
        recordfail
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-19-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74
    echo    Loading Linux 2.6.31-19-generic ...
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 2ad94214d0a6de5b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=ab9e4fb2-2c48-4fd4-bc46-444fe4fb3e74 / ext4 errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=5ff33f5b-662b-4cbc-bdd8-b8ac8f7b150b /home ext4 defaults 0 2
# Entry for /dev/sda5 :
UUID=e1ad31a7-774e-4fc5-afa7-b8704a47054d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/Windoze ntfs-3g defaults,locale=en_GB.UTF-8 0 0

=================== sda4: Location of files loaded by Grub: ===================


 119.9GB: boot/grub/core.img
 119.9GB: boot/grub/grub.cfg
 119.9GB: boot/initrd.img-2.6.31-19-generic
 119.9GB: boot/initrd.img-2.6.32-12-generic
 119.9GB: boot/vmlinuz-2.6.31-19-generic
 119.9GB: boot/vmlinuz-2.6.32-12-generic
 119.9GB: initrd.img
 119.9GB: initrd.img.old
 119.9GB: vmlinuz
 119.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```
sdb6 = /home
sda4 = /
sda5 = SWAP
sda2 = Windows XP

I would really appreciate any help on this matter.

Best Regards
John

---

### Post by kansasnoob on 2010-02-10
I haven't personally had that happen but I saw it in Lucid Development:

[http://ubuntuforums.org/showthread.php?t=1397629&page=3](http://ubuntuforums.org/showthread.php?t=1397629&page=3)

Sadly the OP couldn't explain how he got it working and later Kevbert had to do a fresh install:

[http://ubuntuforums.org/showpost.php?p=8774453&postcount=15](http://ubuntuforums.org/showpost.php?p=8774453&postcount=15)

[http://ubuntuforums.org/showpost.php?p=8784586&postcount=29](http://ubuntuforums.org/showpost.php?p=8784586&postcount=29)

---

### Post by arpanaut on 2010-02-10
Don't know if it will help but over in the 10.4 testing forum there was this discussion... seems like a lot of work being done on grub right now so these kinds of issues are to be expected and common at this point of development

[http://ubuntuforums.org/showthread.php?t=1397629](http://ubuntuforums.org/showthread.php?t=1397629)

good luck

---

