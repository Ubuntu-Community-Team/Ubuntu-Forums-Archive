---
title: "Windows 7 boot error 0xc0000225 after instal of Ubuntu 10.04"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by daksai3 on 2010-10-06
Ok, i really need help with this. this is teh story: i had windows 7 and ubuntu dual booted but then a problem with ubuntu caused me to reinstall it. at teh same time i wanted to change teh partitions so i used gparted while on teh live cd. after i installed ubuntu 10.04 i couldnt access my windows 7 64 bit partition. 

how do i solve my problem? i dont want to have a fresh install of windows 7 as i have a lot of things on it and a lot of programs. 

this is my boot info script. 

  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       192,779       192,717   7 HPFS/NTFS
/dev/sda2             192,780   213,407,688   213,214,909   7 HPFS/NTFS
/dev/sda3         213,407,689   236,236,745    22,829,057   7 HPFS/NTFS
/dev/sda4         236,236,798   505,765,887   269,529,090   5 Extended
/dev/sda5         236,236,800   242,096,127     5,859,328  82 Linux swap / Solaris
/dev/sda6         242,098,176   300,689,407    58,591,232  83 Linux
/dev/sda7         300,691,456   310,454,271     9,762,816  83 Linux
/dev/sda8         310,456,320   505,765,887   195,309,568   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1E9436B394368D71                       ntfs       SYSTEM                        
/dev/sda2        B03C57603C572120                       ntfs       Windows 7                     
/dev/sda3        147C1D777C1D54B8                       ntfs       FACTORY_IMAGE                 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        ee9d3e2e-5637-41c9-a34c-b5a6fa6c2cad   swap                                     
/dev/sda6        184bc56c-eb1b-4621-9a4f-57d5f3473b5b   ext4       Root                          
/dev/sda7        a2e00d9c-7d04-48cd-855b-c95f81ce4b75   ext4       Home                          
/dev/sda8        4C49E3F607A99868                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        28B8-1DEE                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda8        /media/4C49E3F607A99868  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/Root              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/Home              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 184bc56c-eb1b-4621-9a4f-57d5f3473b5b
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 184bc56c-eb1b-4621-9a4f-57d5f3473b5b
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 184bc56c-eb1b-4621-9a4f-57d5f3473b5b
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=184bc56c-eb1b-4621-9a4f-57d5f3473b5b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 184bc56c-eb1b-4621-9a4f-57d5f3473b5b
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=184bc56c-eb1b-4621-9a4f-57d5f3473b5b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 184bc56c-eb1b-4621-9a4f-57d5f3473b5b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 184bc56c-eb1b-4621-9a4f-57d5f3473b5b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1e9436b394368d71
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 147c1d777c1d54b8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=184bc56c-eb1b-4621-9a4f-57d5f3473b5b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=a2e00d9c-7d04-48cd-855b-c95f81ce4b75 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ee9d3e2e-5637-41c9-a34c-b5a6fa6c2cad none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 139.1GB: boot/grub/core.img
 130.6GB: boot/grub/grub.cfg
 139.1GB: boot/initrd.img-2.6.32-25-generic-pae
 139.1GB: boot/vmlinuz-2.6.32-25-generic-pae
 139.1GB: initrd.img
 139.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by ronparent on 2010-10-06
If by chance you used gparted to modify the win 7 partition(s), that could have created problems with win 7. You might try to use the win 7 install dvd to fix the partitions.

---

### Post by oldfred on 2010-10-07
/dev/sda1    * [COLOR=Red]            63[/COLOR]       192,779       192,717   7 HPFS/NTFS

Windows 7 (and now Ubuntu) installs to 2048 as the first sector of sda. XP and old install of Ubuntu used 63. Did you use the gparted that is part of the installer or a separate gparted? Supposedly the installer will not move the start of win7 but gparted may if the checkbox round to cylinders is checked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)


You need to run the win7 repairs as ronparent suggested.

---

