---
title: "WIN7 doesnt boot after installing Grub"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by inestler on 2010-09-30
After install of Ubuntu 10.04 i cant boot WIN7 from the Grub menu.
Any advice whats going wrong?  

root@asus:~# fdisk -l

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb5bd2b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3890    31245312    7  HPFS/NTFS
/dev/sda2            3890        3892       16154   ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 31.9 GB, 31914983424 bytes
255 heads, 63 sectors/track, 3880 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ac5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3391    27230840+   c  W95 FAT32 (LBA)
/dev/sdb2            3391        3881     3931137    5  Extended
/dev/sdb5            3391        3852     3701760   83  Linux
/dev/sdb6            3852        3881      228352   82  Linux swap / Solaris

---

### Post by Rubi1200 on 2010-09-30
In future, please post the results of the script in this format (it makes it easier for those who want to help you).

Thanks.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 2 in the file /ubuntu-448.bin looks at sector 1 
                       of the same hard drive for core.img, but core.img can 
                       not be found at this location. Grub 2 in the file 
                       /ubuntu-512.bin looks at sector 1 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Windows 7
    Boot files/dirs:   /grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 2 in the file /ubuntu-448.bin looks at sector 1 
                       of the same hard drive for core.img, but core.img can 
                       not be found at this location. Grub 2 in the file 
                       /ubuntu-512.bin looks at sector 1 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    62,492,671    62,490,624   7 HPFS/NTFS
/dev/sda2          62,492,672    62,524,979        32,308  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 31.9 GB, 31914983424 bytes
255 heads, 63 sectors/track, 3880 cylinders, total 62333952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192    54,469,872    54,461,681   c W95 FAT32 (LBA)
/dev/sdb2          54,470,654    62,332,927     7,862,274   5 Extended
/dev/sdb5          54,470,656    61,874,175     7,403,520  83 Linux
/dev/sdb6          61,876,224    62,332,927       456,704  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            249     3,967,487     3,967,239   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7A6E4D526E4D07F9                       ntfs       WIN7                          
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3634-3663                              vfat       SDHC 32GB                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        33657ff9-c47d-47e2-b24a-78f3750706fd   ext4                                     
/dev/sdb6        6162cdb2-20f9-469c-b88b-923b26a6c858   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        58C1-8061                              vfat       SD 2GB                        
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,noatime,nodiratime,commit=60,errors=remount-ro)
/dev/sdb1        /media/SDHC 32GB         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc1        /media/SD 2GB            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/WIN7              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/grub.cfg: ================================

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
search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x600
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
search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
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
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=33657ff9-c47d-47e2-b24a-78f3750706fd ro   quiet splash pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1 elevator=deadline acpi_backlight=vendor acpi_osi=Linux
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=33657ff9-c47d-47e2-b24a-78f3750706fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=33657ff9-c47d-47e2-b24a-78f3750706fd ro   quiet splash pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1 elevator=deadline acpi_backlight=vendor acpi_osi=Linux
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=33657ff9-c47d-47e2-b24a-78f3750706fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a6e4d526e4d07f9
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
insmod 915resolution
  915resolution 5c 1024 600
  set gfxmode=1024x600
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    ccGB: grub.cfg

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
search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x600
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
search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=33657ff9-c47d-47e2-b24a-78f3750706fd ro   quiet splash pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1 elevator=deadline acpi_backlight=vendor acpi_osi=Linux
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=33657ff9-c47d-47e2-b24a-78f3750706fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=33657ff9-c47d-47e2-b24a-78f3750706fd ro   quiet splash pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1 elevator=deadline acpi_backlight=vendor acpi_osi=Linux
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=33657ff9-c47d-47e2-b24a-78f3750706fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=33657ff9-c47d-47e2-b24a-78f3750706fd ro   quiet splash pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1 elevator=deadline acpi_backlight=vendor acpi_osi=Linux
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=33657ff9-c47d-47e2-b24a-78f3750706fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 33657ff9-c47d-47e2-b24a-78f3750706fd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a6e4d526e4d07f9
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
insmod 915resolution
  915resolution 5c 1024 600
  set gfxmode=1024x600
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
# / was on /dev/sdc5 during installation
UUID=33657ff9-c47d-47e2-b24a-78f3750706fd /               ext4    noatime,nodiratime,commit=60,errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=6162cdb2-20f9-469c-b88b-923b26a6c858 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


  28.3GB: boot/grub/core.img
  31.3GB: boot/grub/grub.cfg
  29.9GB: boot/initrd.img-2.6.32-21-generic
  28.0GB: boot/initrd.img-2.6.32-24-generic
  30.6GB: boot/initrd.img-2.6.32-25-generic
  29.7GB: boot/vmlinuz-2.6.32-21-generic
  30.0GB: boot/vmlinuz-2.6.32-24-generic
  30.6GB: boot/vmlinuz-2.6.32-25-generic
  30.6GB: initrd.img
  28.0GB: initrd.img.old
  30.6GB: vmlinuz
  30.0GB: vmlinuz.old
```

---

### Post by thor187 on 2010-09-30
Hi,

When I first loaded Ubuntu with a dual boot up, I had the same problem when trying to boot into win7, I took the windows 7 cd that came with my pc and I put in on start up. Once loaded, select repair "start up" or something like that. It worked for me, give it a try.

---

### Post by oldfred on 2010-09-30
You have installed grub into the boot sectors of windows. The windows boot sector has to have windows in the boot sector. Are you still using the wubi install? 

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

