---
title: "Windows Vista won't load"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by DarkElysium on 2010-06-26
I supposedly installed ubuntu 10.something into a dual boot with windows vista but now windows vista won't load. It says partition can not be found... and from reading other forums I think it is looking in the wrong place... but i got this document. So any help would be good. Thank you.

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  -
    Boot sector info:  

sdc4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   586,110,975   586,108,928   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34       262,177       262,144 Microsoft Windows
/dev/sdc2         264,192   973,090,544   972,826,353 Linux or Data
/dev/sdc3     973,090,816   973,092,863         2,048 Bios Boot Partition
/dev/sdc4     973,092,864 1,929,746,431   956,653,568 Linux or Data
/dev/sdc5   1,929,746,432 1,953,523,711    23,777,280 Linux Swap

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 16.4 GB, 16441671680 bytes
154 heads, 40 sectors/track, 5213 cylinders, total 32112640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             40    32,112,639    32,112,600   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       b78b4e08-bf79-4841-9e67-956dbb96c2a8   ext4                                     
/dev/sda1        C80884CF0884BE46                       ntfs       Matrix                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F8D89643D8960054                       ntfs       Nightingale                   
/dev/sdb: PTTYPE="dos" 
/dev/sdc2        A0BAFA1ABAF9ECA2                       ntfs       Midnight                      
/dev/sdc4        281a9aef-c68f-4210-9615-11663f737f17   ext4                                     
/dev/sdc5        10b037ee-132d-46c2-ac89-c1675cd6901e   swap                                     
/dev/sdc: PTTYPE="gpt" 
/dev/sdd1        D8BE-FF88                              vfat       CORSAIR                       
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc4        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Napoleon_2        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdc2        /media/Midnight          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/CORSAIR           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c80884cf0884be46
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c80884cf0884be46
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c80884cf0884be46
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   6.6GB: boot/grub/grub.cfg
   6.7GB: boot/initrd.img-2.6.32-21-generic
   6.6GB: boot/vmlinuz-2.6.32-21-generic
   6.7GB: initrd.img
   6.6GB: vmlinuz

=========================== sdc4/boot/grub/grub.cfg: ===========================

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
set root='(hd2,4)'
search --no-floppy --fs-uuid --set 281a9aef-c68f-4210-9615-11663f737f17
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
set root='(hd2,4)'
search --no-floppy --fs-uuid --set 281a9aef-c68f-4210-9615-11663f737f17
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,4)'
    search --no-floppy --fs-uuid --set 281a9aef-c68f-4210-9615-11663f737f17
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=281a9aef-c68f-4210-9615-11663f737f17 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,4)'
    search --no-floppy --fs-uuid --set 281a9aef-c68f-4210-9615-11663f737f17
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=281a9aef-c68f-4210-9615-11663f737f17 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,4)'
    search --no-floppy --fs-uuid --set 281a9aef-c68f-4210-9615-11663f737f17
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=281a9aef-c68f-4210-9615-11663f737f17 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,4)'
    search --no-floppy --fs-uuid --set 281a9aef-c68f-4210-9615-11663f737f17
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=281a9aef-c68f-4210-9615-11663f737f17 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,4)'
    search --no-floppy --fs-uuid --set 281a9aef-c68f-4210-9615-11663f737f17
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,4)'
    search --no-floppy --fs-uuid --set 281a9aef-c68f-4210-9615-11663f737f17
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c80884cf0884be46
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc4 during installation
UUID=281a9aef-c68f-4210-9615-11663f737f17 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=10b037ee-132d-46c2-ac89-c1675cd6901e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc4: Location of files loaded by Grub: ===================


 865.5GB: boot/grub/core.img
 953.6GB: boot/grub/grub.cfg
 865.6GB: boot/initrd.img-2.6.32-21-generic
 865.5GB: boot/initrd.img-2.6.32-22-generic
 865.5GB: boot/vmlinuz-2.6.32-21-generic
 498.6GB: boot/vmlinuz-2.6.32-22-generic
 865.5GB: initrd.img
 865.6GB: initrd.img.old
 498.6GB: vmlinuz
 865.5GB: vmlinuz.old

---

### Post by darkod on 2010-06-26
You have a GPT type partition table on sdc. Avoid using GPT unless really necessary.

Boot your 10.04 and see if this can help:
[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)

---

### Post by DarkElysium on 2010-06-26
Still can't boot up windows vista....

---

### Post by darkod on 2010-06-26
Can you boot ubuntu and post the output of:

cat /boot/grub/device.map

---

### Post by DarkElysium on 2010-06-26
well I am in ubuntu now... and it says directory doesn't exist for some reason.

---

### Post by presence1960 on 2010-06-26
Your Lucid install is in sdc4. I would put that that disk (sdc) first in the hard disk boot order in BIOS and save the changes to CMOS. Then boot the Ubuntu 10.04 Live CD/USB. Open a terminal and run ```
sudo mount /dev/sdc4 /mnt
``` This will mount the Lucid partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdc
``` This will put GRUB2 on MBR of sdc. Reboot without Live CD/USB and boot into Ubuntu. Open a terminal and run ```
sudo update-grub
```

This SHOULD add a windows entry to the GRUB menu. If it does not post back, we can fix the MBR of sda so it is a windows MBR from ubuntu.

As far as the GUID partition table goes I don't know if it has any effect on GRUB booting. But give it a try.

---

