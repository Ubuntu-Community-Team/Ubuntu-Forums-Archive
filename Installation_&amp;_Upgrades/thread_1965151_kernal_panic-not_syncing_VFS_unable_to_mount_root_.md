---
title: "kernal panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by cyrodil on 2012-04-25
I have 3 OS Win7, and two 10.10 installs each on separate hard drives, not sure what happened to the grub entries or associated boot files or linux image on my previous 10.10 install but it won't boot from /dev/sdc2 but I do have a working system on /dev/sdb.

The output from bootinfoscrip is below, I can see the file system from my other /dev/sdb installation and from a liveCD but just can't boot it?

Any help much appreciated.

Thanks.
```

          Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/grub.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdc2 and looks at sector 1384190896 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 2 for (,msdos2)/boot/grub.
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               4,094 1,953,523,711 1,953,519,618   5 Extended
/dev/sdb5               4,096    25,169,919    25,165,824  82 Linux swap / Solaris
/dev/sdb6    *     25,171,968    25,581,567       409,600  83 Linux
/dev/sdb7          25,583,616    67,526,655    41,943,040  83 Linux
/dev/sdb8          67,528,704   906,389,503   838,860,800  83 Linux
/dev/sdb9         906,391,552 1,953,523,711 1,047,132,160  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048    12,390,399    12,388,352  82 Linux swap / Solaris
/dev/sdc2    *     12,390,400 1,953,523,711 1,941,133,312  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048 1,953,523,711 1,953,521,664  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2C10A7B510A78504                       ntfs       System Reserved
/dev/sda2        7EB4AB0CB4AAC64D                       ntfs       Win7 System
/dev/sdb5        c78e58b5-26d7-441b-b393-ad9060bb894e   swap       swap
/dev/sdb6        7592a540-1108-41da-98d9-881f1b1a8951   ext2       boot
/dev/sdb7        2ab53b51-92f5-415d-bd4b-8f399d08c327   ext4       root
/dev/sdb8        db229e9e-502a-42c3-9ea1-70775ac448cb   ext4       home
/dev/sdb9        d3183964-e9ad-4d67-ab6d-8f4f0565bc63   ext4       var
/dev/sdc1        4bfb2772-4aed-4931-acf5-19fab4d9e5e6   swap       
/dev/sdc2        9e52735c-d9a6-47f0-98a0-14936608ce83   ext4       
/dev/sdd1        c8b1c19f-bf6f-4603-985a-d0f6d26852e8   ext4       Media

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sdb6/grub/grub.cfg: ==============================

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
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set 2ab53b51-92f5-415d-bd4b-8f399d08c327
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
    linux    /vmlinuz-2.6.35-32-generic root=UUID=2ab53b51-92f5-415d-bd4b-8f399d08c327 ro   quiet splash
    initrd    /initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
    echo    'Loading Linux 2.6.35-32-generic ...'
    linux    /vmlinuz-2.6.35-32-generic root=UUID=2ab53b51-92f5-415d-bd4b-8f399d08c327 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
    linux    /vmlinuz-2.6.35-22-generic root=UUID=2ab53b51-92f5-415d-bd4b-8f399d08c327 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=2ab53b51-92f5-415d-bd4b-8f399d08c327 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2C10A7B510A78504
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-32-generic (on /dev/sdc2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 9e52735c-d9a6-47f0-98a0-14936608ce83
    linux /boot/vmlinuz-2.6.35-32-generic root=/dev/sdc2 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.35-32-generic (recovery mode) (on /dev/sdc2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 9e52735c-d9a6-47f0-98a0-14936608ce83
    linux /boot/vmlinuz-2.6.35-32-generic root=/dev/sdc2 ro single
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

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  12.057254791 = 12.946378752   grub/core.img                                  2
  12.167243958 = 13.064478720   grub/grub.cfg                                  1
  12.060770035 = 12.950153216   initrd.img-2.6.35-22-generic                  78
  12.071442604 = 12.961612800   initrd.img-2.6.35-32-generic                  68
  12.019948006 = 12.906320896   vmlinuz-2.6.35-22-generic                     19
  12.013665199 = 12.899574784   vmlinuz-2.6.35-32-generic                     20

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=2ab53b51-92f5-415d-bd4b-8f399d08c327 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb6 during installation
UUID=7592a540-1108-41da-98d9-881f1b1a8951 /boot           ext2    defaults        0       2
# /home was on /dev/sdb8 during installation
UUID=db229e9e-502a-42c3-9ea1-70775ac448cb /home           ext4    defaults        0       2
# /var was on /dev/sdb9 during installation
UUID=d3183964-e9ad-4d67-ab6d-8f4f0565bc63 /var            ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=c78e58b5-26d7-441b-b393-ad9060bb894e none            swap    sw              0       0
# swap was on /dev/sdc1 during installation
UUID=4bfb2772-4aed-4931-acf5-19fab4d9e5e6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sdc2/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos2)'
search --no-floppy --fs-uuid --set 9e52735c-d9a6-47f0-98a0-14936608ce83
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos2)'
search --no-floppy --fs-uuid --set 9e52735c-d9a6-47f0-98a0-14936608ce83
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
menuentry 'Ubuntu, with Linux 2.6.35-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 9e52735c-d9a6-47f0-98a0-14936608ce83
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=9e52735c-d9a6-47f0-98a0-14936608ce83 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 9e52735c-d9a6-47f0-98a0-14936608ce83
    echo    'Loading Linux 2.6.35-32-generic ...'
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=9e52735c-d9a6-47f0-98a0-14936608ce83 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 9e52735c-d9a6-47f0-98a0-14936608ce83
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9e52735c-d9a6-47f0-98a0-14936608ce83 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 9e52735c-d9a6-47f0-98a0-14936608ce83
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9e52735c-d9a6-47f0-98a0-14936608ce83 ro single 
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
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 9e52735c-d9a6-47f0-98a0-14936608ce83
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 9e52735c-d9a6-47f0-98a0-14936608ce83
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2C10A7B510A78504
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-32-generic (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
    linux /vmlinuz-2.6.35-32-generic root=UUID=2ab53b51-92f5-415d-bd4b-8f399d08c327 ro quiet splash
    initrd /initrd.img-2.6.35-32-generic
}
menuentry "Ubuntu, with Linux 2.6.35-32-generic (recovery mode) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
    linux /vmlinuz-2.6.35-32-generic root=UUID=2ab53b51-92f5-415d-bd4b-8f399d08c327 ro single
    initrd /initrd.img-2.6.35-32-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
    linux /vmlinuz-2.6.35-22-generic root=UUID=2ab53b51-92f5-415d-bd4b-8f399d08c327 ro quiet splash
    initrd /initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7592a540-1108-41da-98d9-881f1b1a8951
    linux /vmlinuz-2.6.35-22-generic root=UUID=2ab53b51-92f5-415d-bd4b-8f399d08c327 ro single
    initrd /initrd.img-2.6.35-22-generic
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

=============================== sdc2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc2 during installation
UUID=9e52735c-d9a6-47f0-98a0-14936608ce83 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc1 during installation
UUID=4bfb2772-4aed-4931-acf5-19fab4d9e5e6 none            swap    sw                0       0
# This automounts the Media harddrive for recording mythtv files
UUID=c8b1c19f-bf6f-4603-985a-d0f6d26852e8 /media/sdd1     ext4    defaults          0       2
# /dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 660.033676147 = 708.705763328  boot/grub/core.img                             1
 660.058601379 = 708.732526592  boot/grub/grub.cfg                             1
  28.095676422 = 30.167502848   boot/initrd.img-2.6.35-22-generic              2
  26.158195496 = 28.087148544   boot/initrd.img-2.6.35-32-generic              2
 660.308040619 = 709.000359936  boot/initrd.img-2.6.382.6.35-22-generic        1
 660.301113129 = 708.992921600  boot/initrd.img-vmlinuz-2.6.35-32-generic      1
  27.537242889 = 29.567889408   boot/vmlinuz-2.6.35-22-generic                 2
  26.228664398 = 28.162813952   boot/vmlinuz-2.6.35-32-generic                 2
  26.158195496 = 28.087148544   initrd.img                                     2
  26.228664398 = 28.162813952   vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  70 49 fd 57 67 64 b3 3f  c6 64 07 d0 a7 f0 97 b4  |pI.Wgd.?.d......|
00000010  9c 31 43 e8 68 b6 7a 88  48 13 56 75 d3 58 a9 79  |.1C.h.z.H.Vu.X.y|
00000020  1f c0 2a 7d 48 f2 f7 1f  f9 b4 e6 e7 f3 35 fa 71  |..*}H........5.q|
00000030  2e 46 5b f0 13 ea 18 80  a3 68 4d 83 5f f8 62 30  |.F[......hM._.b0|
00000040  df ff f9 d4 68 85 89 3f  eb f6 01 be 53 27 7f f2  |....h..?....S'..|
00000050  19 80 7d b8 77 1c 47 d4  16 fd df fb f1 19 5f 79  |..}.w.G......._y|
00000060  a3 a0 f9 e2 ed fa 7e b4  5f 64 ec c7 0c cb 15 fb  |......~._d......|
00000070  11 ef a3 35 3c e9 95 47  3b 60 95 ad da 2a 6b 4b  |...5<..G;`...*kK|
00000080  dc 56 5b e2 c1 64 3a 94  d7 f8 db 91 dd e8 8b ff  |.V[..d:.........|
00000090  b9 ac e4 67 4b eb b9 fc  0b 44 e3 0c 0c 22 2f d3  |...gK....D..."/.|
000000a0  e4 94 0f 07 d1 3a fc 3c  80 d6 61 87 69 1d ee 79  |.....:.<..a.i..y|
000000b0  9f 82 cf 3e 2c 2a 2a ca  1c 20 9f 0a ec 3f cf 42  |...>,**.. ...?.B|
000000c0  01 52 89 be 54 d5 26 3d  70 21 86 8a e1 01 76 a1  |.R..T.&=p!....v.|
000000d0  ea 12 0d a0 67 ad 16 4a  5e 81 11 91 7b 1e e2 fc  |....g..J^...{...|
000000e0  af 0f 69 7b 92 67 3a 04  bb de a3 fe db 72 ff 1b  |..i{.g:......r..|
000000f0  1f 12 74 77 ae 4e 77 7f  7c 4f 04 81 99 73 c5 79  |..tw.Nw.|O...s.y|
00000100  c3 5d ed d7 b4 c3 4a 17  4e 77 5a 25 f5 88 11 9e  |.]....J.NwZ%....|
00000110  78 dd 7d 83 37 78 b8 67  a2 fc 67 8e f2 b4 2d 70  |x.}.7x.g..g...-p|
00000120  d0 86 c5 bd 1d b0 53 cd  28 7a 1f c4 8c f6 7a be  |......S.(z....z.|
00000130  d9 13 18 82 3d c4 a3 50  b1 b7 7e 58 ca f7 44 0e  |....=..P..~X..D.|
00000140  ae fb 70 4c e1 53 2d c9  db 3c f2 6f e5 ad 4d f1  |..pL.S-..<.o..M.|
00000150  72 a3 6d 1e 79 8f 14 c0  94 3a 27 ec c1 29 16 2d  |r.m.y....:'..).-|
00000160  5a 55 75 7d 4b a4 61 8f  57 56 71 dd e1 f5 73 8a  |ZUu}K.a.WVq...s.|
00000170  a3 01 72 34 53 9c cd ac  be e1 04 0f 18 65 c9 41  |..r4S........e.A|
00000180  ce 2c 27 74 c8 e7 cf 04  61 04 59 ad 09 7c b5 1f  |.,'t....a.Y..|..|
00000190  65 cc fd 2d df 70 03 7e  4d bf fb be 7d 97 68 4d  |e..-.p.~M...}.hM|
000001a0  ba 11 76 06 8b 50 44 6d  43 4f d4 a3 7f a1 87 94  |..v..PDmCO......|
000001b0  3a e1 ae 3f 21 f2 23 42  9d fd c8 3f 8b fa 00 41  |:..?!.#B...?...A|
000001c0  02 00 82 fe ff ff 02 00  00 00 00 00 80 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 00  80 01 00 48 06 00 00 00  |...........H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by cyrodil on 2012-04-25
I resolved this by the following:

sudo mount /dev/sdax /mnt sudo mount --bind /dev /mnt/dev sudo mount --bind /proc /mnt/proc sudo chroot /mnt
from LiveCD and running update-initramfs -u -k 2.6.35-32-generic, and then update-grub2 to fix grub entries.

---

