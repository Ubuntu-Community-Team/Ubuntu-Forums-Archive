---
title: "How do I add windows 7 to grub?"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by biggerben on 2010-04-10
I started off with one hard disk in my PC, kubuntu 10.04. Now I put in an other hard disk and installed win7 on that (yuk!).

Before I installed win7 I unplugged my linux hard disk so it couldn't overwrite anything (very effective! :)), after the win7 installation plugged the linux HD back in again.

When I boot now, it boots Linux, without a chance of starting Windows. How do I get a dualboot running now?

Is it a simple case of just typing in «sudo grub-update»? I only know grub from the old days where you had to edit menu.lst, so I'm a little confused!

Please note that my Linux has never «seen» the windows paritions!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    23,438,834    23,438,772  83 Linux
/dev/sda2          23,438,835    46,877,669    23,438,835  83 Linux
/dev/sda3         970,711,560   976,768,064     6,056,505   5 Extended
/dev/sda5         970,711,623   976,768,064     6,056,442  82 Linux swap / Solaris
/dev/sda4          46,877,670   970,711,559   923,833,890  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   716,799,999   716,593,152   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        51fcdf74-e81f-466d-832a-d0276d3bf527   ext4                                     
/dev/sda2        8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        6f3d58aa-2147-4860-9e4d-02c6162b720b   ext4                                     
/dev/sda5        25254d10-9445-4cbf-9184-ca9ab0266c98   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0C38CBC338CBA9D2                       ntfs       System Reserved               
/dev/sdb2        5E6AE2456AE21993                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /0910                    ext4       (rw)
/dev/sda4        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
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
search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        linux   /boot/vmlinuz-2.6.32-19-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        echo    Loading Linux 2.6.32-19-generic ...
        linux   /boot/vmlinuz-2.6.32-19-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro single 
        echo    Loading initial ramdisk ...
        initrd  /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        linux   /boot/vmlinuz-2.6.32-18-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-18-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        echo    Loading Linux 2.6.32-18-generic ...
        linux   /boot/vmlinuz-2.6.32-18-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro single 
        echo    Loading initial ramdisk ...
        initrd  /boot/initrd.img-2.6.32-18-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        linux   /boot/vmlinuz-2.6.32-17-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        echo    Loading Linux 2.6.32-17-generic ...
        linux   /boot/vmlinuz-2.6.32-17-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro single 
        echo    Loading initial ramdisk ...
        initrd  /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        linux   /boot/vmlinuz-2.6.32-16-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        echo    Loading Linux 2.6.32-16-generic ...
        linux   /boot/vmlinuz-2.6.32-16-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro single 
        echo    Loading initial ramdisk ...
        initrd  /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-15-generic" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        linux   /boot/vmlinuz-2.6.32-15-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-15-generic
}
menuentry "Ubuntu, with Linux 2.6.32-15-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        echo    Loading Linux 2.6.32-15-generic ...
        linux   /boot/vmlinuz-2.6.32-15-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro single 
        echo    Loading initial ramdisk ...
        initrd  /boot/initrd.img-2.6.32-15-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        linux   /boot/vmlinuz-2.6.32-14-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        echo    Loading Linux 2.6.32-14-generic ...
        linux   /boot/vmlinuz-2.6.32-14-generic root=UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 ro single 
        echo    Loading initial ramdisk ...
        initrd  /boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 51fcdf74-e81f-466d-832a-d0276d3bf527
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda2)" {
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux /boot/vmlinuz-2.6.31-20-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro
        initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda2)" {
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux /boot/vmlinuz-2.6.31-20-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro single
        initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda2)" {
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux /boot/vmlinuz-2.6.31-19-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro
        initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda2)" {
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux /boot/vmlinuz-2.6.31-19-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro single
        initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda2)" {
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux /boot/vmlinuz-2.6.31-17-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro
        initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda2)" {
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux /boot/vmlinuz-2.6.31-17-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro single
        initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda2)" {
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux /boot/vmlinuz-2.6.31-16-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro
        initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda2)" {
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux /boot/vmlinuz-2.6.31-16-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro single
        initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda2)" {
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux /boot/vmlinuz-2.6.31-14-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro
        initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda2)" {
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux /boot/vmlinuz-2.6.31-14-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro single
        initrd /boot/initrd.img-2.6.31-14-generic
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=51fcdf74-e81f-466d-832a-d0276d3bf527 /               ext4    errors=remount-ro 0       1
# /0910 was on /dev/sda2 during installation
UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b /0910           ext4    defaults        0       2
# /backup was on /dev/sdg2 during installation
UUID=e9760287-3a87-4d34-9ad2-6ff419ce59ab /backup         ext4    noauto,user        0       2
# /data was on /dev/sdb1 during installation
UUID=9dc1a9a3-f08a-450d-9239-cf29a05d9ff1 /data           ext4    defaults        0       2
# /home was on /dev/sda4 during installation
UUID=6f3d58aa-2147-4860-9e4d-02c6162b720b /home           ext4    defaults        0       2
# /wow was on /dev/sdg1 during installation
UUID=0A70-3AD9  /wow            vfat    utf8,umask=007,gid=46,noauto,user 0       1
# swap was on /dev/sda5 during installation
UUID=25254d10-9445-4cbf-9184-ca9ab0266c98 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.5GB: boot/grub/core.img
   8.9GB: boot/grub/grub.cfg
   6.0GB: boot/initrd.img-2.6.32-14-generic
   6.1GB: boot/initrd.img-2.6.32-15-generic
   5.8GB: boot/initrd.img-2.6.32-16-generic
   6.0GB: boot/initrd.img-2.6.32-17-generic
   6.3GB: boot/initrd.img-2.6.32-18-generic
   6.3GB: boot/initrd.img-2.6.32-19-generic
   5.4GB: boot/vmlinuz-2.6.32-14-generic
   5.9GB: boot/vmlinuz-2.6.32-15-generic
   6.1GB: boot/vmlinuz-2.6.32-16-generic
   5.6GB: boot/vmlinuz-2.6.32-17-generic
   5.2GB: boot/vmlinuz-2.6.32-18-generic
   5.9GB: boot/vmlinuz-2.6.32-19-generic
   6.3GB: initrd.img
   6.3GB: initrd.img.old
   5.9GB: vmlinuz
   5.2GB: vmlinuz.old

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro   
        initrd  /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro single 
        initrd  /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux   /boot/vmlinuz-2.6.31-19-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro   
        initrd  /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux   /boot/vmlinuz-2.6.31-19-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro single 
        initrd  /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro   
        initrd  /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro single 
        initrd  /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux   /boot/vmlinuz-2.6.31-16-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro   
        initrd  /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux   /boot/vmlinuz-2.6.31-16-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro single 
        initrd  /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro   
        initrd  /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b ro single 
        initrd  /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-12-generic (on /dev/sda1)" {
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set d32db23f-00d9-499e-9ea5-2266da09b998
        linux /boot/vmlinuz-2.6.32-12-generic root=UUID=d32db23f-00d9-499e-9ea5-2266da09b998 ro quiet splash
        initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode) (on /dev/sda1)" {
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set d32db23f-00d9-499e-9ea5-2266da09b998
        linux /boot/vmlinuz-2.6.32-12-generic root=UUID=d32db23f-00d9-499e-9ea5-2266da09b998 ro single
        initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic (on /dev/sda1)" {
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set d32db23f-00d9-499e-9ea5-2266da09b998
        linux /boot/vmlinuz-2.6.32-11-generic root=UUID=d32db23f-00d9-499e-9ea5-2266da09b998 ro quiet splash
        initrd /boot/initrd.img-2.6.32-11-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic (recovery mode) (on /dev/sda1)" {
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set d32db23f-00d9-499e-9ea5-2266da09b998
        linux /boot/vmlinuz-2.6.32-11-generic root=UUID=d32db23f-00d9-499e-9ea5-2266da09b998 ro single
        initrd /boot/initrd.img-2.6.32-11-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (on /dev/sda1)" {
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set d32db23f-00d9-499e-9ea5-2266da09b998
        linux /boot/vmlinuz-2.6.32-10-generic root=UUID=d32db23f-00d9-499e-9ea5-2266da09b998 ro quiet splash
        initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode) (on /dev/sda1)" {
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set d32db23f-00d9-499e-9ea5-2266da09b998
        linux /boot/vmlinuz-2.6.32-10-generic root=UUID=d32db23f-00d9-499e-9ea5-2266da09b998 ro single
        initrd /boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=8e7b9f07-a1a9-4cd4-94e2-b44c7f313c1b /               ext4    errors=remount-ro 0       1
# /alpha was on /dev/sda1 during installation
UUID=d32db23f-00d9-499e-9ea5-2266da09b998 /alpha        ext4    defaults        0       2
#UUID=4c671369-2d44-43a6-8036-5a40357c529e /alpha          ext4    defaults        0       2
# /backup was on /dev/sdg2 during installation
UUID=e9760287-3a87-4d34-9ad2-6ff419ce59ab /backup         ext4    defaults        0       2
# /data was on /dev/sdb1 during installation
UUID=9dc1a9a3-f08a-450d-9239-cf29a05d9ff1 /data           ext4    defaults        0       2
# /home was on /dev/sda4 during installation
UUID=6f3d58aa-2147-4860-9e4d-02c6162b720b /home           ext4    defaults        0       2
# /wow was on /dev/sdg1 during installation
UUID=0A70-3AD9  /wow            vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=25254d10-9445-4cbf-9184-ca9ab0266c98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  15.2GB: boot/grub/core.img
  20.7GB: boot/grub/grub.cfg
  12.9GB: boot/initrd.img-2.6.31-14-generic
  16.9GB: boot/initrd.img-2.6.31-16-generic
  20.1GB: boot/initrd.img-2.6.31-17-generic
  16.0GB: boot/initrd.img-2.6.31-19-generic
  14.2GB: boot/initrd.img-2.6.31-20-generic
  14.4GB: boot/vmlinuz-2.6.31-14-generic
  14.9GB: boot/vmlinuz-2.6.31-16-generic
  16.8GB: boot/vmlinuz-2.6.31-17-generic
  17.2GB: boot/vmlinuz-2.6.31-19-generic
  20.9GB: boot/vmlinuz-2.6.31-20-generic
  14.2GB: initrd.img
  16.0GB: initrd.img.old
  20.9GB: vmlinuz
  17.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 

```

---

### Post by sully0400 on 2010-04-11
After many installs with Ubuntu 8.04 (I run emc2) I found that the best way is to put the windows in first then install Linux last and select the particans manually use "/" for the boot partican and "swap" for swap.

I'm new so take it with a grain of salt

---

### Post by Mark Phelps on 2010-04-11
There's no need to reinstall ... wish folks would stop spreading the myth that MS Windows OSs need to be installed first!  That's only a matter of convenience.

All you should have to do is the following:
1) Set to boot from your Ubuntu drive
2) Open a terminal in Ubuntu and type "sudo update-grub" -- and watch as it searches for kernels and OSs.  It should present a line something like "Windows seven Loader found on (sdb1)".
3) Reboot

When you start up again, your GRUB menu should present you an entry for Win7.

---

### Post by biggerben on 2010-04-11
Wow, that's much easier than it was 3 years ago, providing one knows how that is :)

thanks!

---

### Post by biggerben on 2010-04-11
hmm, quick other question, how do I change this to [solved] properly?

---

### Post by lvleph on 2010-04-11
I believe it is under thread tools.

---

