---
title: "win7 doesn't boot after upgrade to 10.4..."
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by dino.tee on 2010-05-03
I did the upgrade,
during the upgrade grup pc suggested to check all the partitions, so I did.

Now
when I start I can see the various Ubuntu kernels,
windows Vista (loader) which I believe is really the recovery tool from acer:
windows 7 (loader)

If I hit one of the last two, I get the black screen with everlasting blinking cursor!

Before hitting windows 7 was pointing to another boot loader (i guess the acer recovery/windos7 boot loader).

HELLLLLLLLLPPPPPPPPPP
I want my win7 back!!

Thanks

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 551306867 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 551306867 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 551306867 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 551311675 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 551311675 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 byte
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    25,167,871    25,165,824  27 Hidden HPFS/NTFS
/dev/sda2    *     25,167,872    25,372,671       204,800   7 HPFS/NTFS
/dev/sda3          25,372,672   130,657,219   105,284,548   7 HPFS/NTFS
/dev/sda4         130,657,282   625,137,344   494,480,063   f W95 Ext d (LBA)
/dev/sda5         130,657,283   551,023,173   420,365,891   7 HPFS/NTFS
/dev/sda6         623,289,933   625,137,344     1,847,412  82 Linux swap / Solaris
/dev/sda7         551,029,563   623,289,869    72,260,307  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 8168 MB, 8168931328 byte
255 testine, 63 settori/tracce, 993 cilindri, totale 15954944 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    15,165,359    15,165,297   b W95 FAT32
/dev/sdb2          15,165,360    15,952,544       787,185   5 Extended
/dev/sdb5          15,165,423    15,952,544       787,122  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3C78CC1C78CBD2B6                       ntfs       PQSERVICE                     
/dev/sda2        B4EECD62EECD1D8C                       ntfs       SYSTEM RESERVED               
/dev/sda3        01CA821229641ED0                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        01CA82128DD41870                       ntfs                                     
/dev/sda6        89941d39-4746-4228-8d09-ed3db7a05c1b   swap                                     
/dev/sda7        ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        40FC-BCEC                              vfat       SD DATA                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        7283a3df-1591-4d9f-8949-94cb5b99ca4b   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=5)
/dev/sdb1        /media/SD DATA           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda3        /media/Acer              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7
set locale_dir=($root)/boot/grub/locale
set lang=it
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
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7
    echo    'Caricamento Linux 2.6.32-21-generic...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, con Linux 2.6.31-20-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7
    echo    'Caricamento Linux 2.6.31-20-generic...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3c78cc1c78cbd2b6
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b4eecd62eecd1d8c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=ba7f0942-02e8-476a-b15d-e3e1ce7cb7b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=89941d39-4746-4228-8d09-ed3db7a05c1b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 282.2GB: boot/grub/core.img
 285.4GB: boot/grub/grub.cfg
 282.5GB: boot/initrd.img-2.6.31-20-generic
 285.3GB: boot/initrd.img-2.6.32-21-generic
 291.2GB: boot/vmlinuz-2.6.31-20-generic
 284.9GB: boot/vmlinuz-2.6.32-21-generic
 285.3GB: initrd.img
 282.5GB: initrd.img.old
 284.9GB: vmlinuz
 291.2GB: vmlinuz.old

---

### Post by dino.tee on 2010-05-03
anyone any help??

---

### Post by oldfred on 2010-05-03
Someone posted the instructions and they actually are not clear but mean to say to install to every hard drive and NOT to install to every partition.

There are many threads with the same issue. Most users seem to also miss read the instructions and overwrite the windows PBR.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also run fixboot from a windows repair CD, but most find the above instructions work well.

---

