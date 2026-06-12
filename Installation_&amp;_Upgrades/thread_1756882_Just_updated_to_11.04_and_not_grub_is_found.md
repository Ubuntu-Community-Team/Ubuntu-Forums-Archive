---
title: "Just updated to 11.04 and not grub is found"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by TimEnid on 2011-05-12
I ran the update and i got a message after restarting saying "grub_dev_" something to that effect, i dont remember because it went away when i restarted again. But anyway, i put in my live cd (10.10) and tried to reinstall grub2 to the drive. In my script it says grub2 is installed on the drive, but when i try to boot, it doesnt boot up. I just get a black screen with a flashing cursor in the top left corner. Only thing is, its not the normal cursor. The cursor is a little bit longer than usua. But here is my Boot Info Summary.
```
=                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for cch.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf
 => Windows is installed in the MBR of /dev/sdl

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdl1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *        112,455    71,167,949    71,055,495  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,417,183,231 1,417,181,184  83 Linux
/dev/sdc2       1,417,185,278 1,465,147,391    47,962,114   5 Extended
/dev/sdc5       1,417,185,280 1,465,147,391    47,962,112  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 681 MB, 681574400 bytes
64 heads, 32 sectors/track, 650 cylinders, total 1331200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  32     1,331,199     1,331,168   b W95 FAT32


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 999.5 GB, 999512825856 bytes
255 heads, 63 sectors/track, 121517 cylinders, total 1952173488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63 1,952,170,604 1,952,170,542   c W95 FAT32 (LBA)


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1499.7 GB, 1499651727360 bytes
255 heads, 63 sectors/track, 182322 cylinders, total 2929007280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63 2,929,002,929 2,929,002,867   7 HPFS/NTFS


Drive: sdl ___________________ _____________________________________________________

Disk /dev/sdl: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdl1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        DC96260D9625E92A                       ntfs       E                             
/dev/sda: PTTYPE="dos" 
/dev/sdb1        86CEFEB2CEFE9A1F                       ntfs       WD                            
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        b84cb6ae-d386-4791-b9f6-556ae47ccd95   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        2369430c-0a78-42b3-803a-ba5175d1164b   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        0F9F-CA59                              vfat       UTIL_HDHXU3                   
/dev/sdd: PTTYPE="dos" 
/dev/sde1        7A6E1E635BBBA6E6                       ntfs       Misc                          
/dev/sde: PTTYPE="dos" 
/dev/sdf1        A8508E6E508E4354                       ntfs       Buffalo 1.5tb                 
/dev/sdf: PTTYPE="dos" 
/dev/sdl1        9AE8021FE801FA71                       ntfs       Iomega 3.0                    
/dev/sdl: PTTYPE="dos" 
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found
error: /dev/sdj: No medium found
error: /dev/sdk: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    echo    'Loading Linux 2.6.38-9-generic ...'
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-9-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root b84cb6ae-d386-4791-b9f6-556ae47ccd95
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=b84cb6ae-d386-4791-b9f6-556ae47ccd95 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=2369430c-0a78-42b3-803a-ba5175d1164b none            swap    sw              0       0
/dev/sdd        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
# mount point for moto xoom
mtpfs /media/xoom fuse user,noauto,allow_other 0 0 

=================== sdc1: Location of files loaded by Grub: ===================


  55.9GB: boot/grub/core.img
 292.2GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.35-22-generic
   1.7GB: boot/initrd.img-2.6.35-23-generic
   1.8GB: boot/initrd.img-2.6.35-24-generic
   1.9GB: boot/initrd.img-2.6.35-25-generic
   1.9GB: boot/initrd.img-2.6.35-27-generic
  46.1GB: boot/initrd.img-2.6.35-28-generic
  71.5GB: boot/initrd.img-2.6.38-9-generic
  55.9GB: boot/vmlinuz-2.6.35-22-generic
  55.9GB: boot/vmlinuz-2.6.35-23-generic
  55.9GB: boot/vmlinuz-2.6.35-24-generic
  56.0GB: boot/vmlinuz-2.6.35-25-generic
  56.0GB: boot/vmlinuz-2.6.35-27-generic
 249.4GB: boot/vmlinuz-2.6.35-28-generic
  74.9GB: boot/vmlinuz-2.6.38-9-generic
  71.5GB: initrd.img
  46.1GB: initrd.img.old
  74.9GB: vmlinuz
 249.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdg sdh sdi sdj sdk 
```
FYI, this is the drive that i have my OS installed on
```
Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,417,183,231 1,417,181,184  83 Linux
/dev/sdc2       1,417,185,278 1,465,147,391    47,962,114   5 Extended
/dev/sdc5       1,417,185,280 1,465,147,391    47,962,112  82 Linux swap  / Solaris
```
can anyone help with this. thanks.

---

### Post by Hedgehog1 on 2011-05-12
> **TimEnid said:**
> ... But anyway, i **put in my live cd (10.10) **and tried to **reinstall grub2 to the drive**. In my script it says grub2 is installed on the drive, but when i try to boot, it doesnt boot up... 

TimEnid,

Grub has changed between 10.10 and 11.04.

Are you in a situation where you can make a Natty/11.04 LiveCD/LiveUSB?

Whatever else happens, we will need you to install the current version of grub on your PC, and the Natty/11.04 LiveCD/LiveUSB? is a must.

While you find a way to download the ISO and make a CD/USB, we will take a look at your script output.

***The Hedge***

:KS

**[SIZE="2"]*Brownie Points for including the script output on the first post!*[/SIZE]**

---

### Post by Hedgehog1 on 2011-05-12
**[SIZE="2"]Using the _Natty_ LiveCD/LiveUSB:[/SIZE]**

Select 'TRY' and please do this:

```
sudo mount /dev/sd**c1** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```


I think that is all you need to be running again...


***The Hedge***

:KS

---

### Post by TimEnid on 2011-05-12
> **Hedgehog1 said:**
> TimEnid,

Grub has changed between 10.10 and 11.04.

Are you in a situation where you can make a Natty/11.04 LiveCD/LiveUSB?

Whatever else happens, we will need you to install the current version of grub on your PC, and the Natty/11.04 LiveCD/LiveUSB? is a must.

While you find a way to download the ISO and make a CD/USB, we will take a look at your script output.

***The Hedge***

:KS

**[SIZE=2]*Brownie Points for including the script output on the first post!*[/SIZE]**
edit: downloading the natty-desktop-amd64.iso now.

---

### Post by TimEnid on 2011-05-12
Ok. I followed the instructions and i get 
"Error: the symbol 'grub_xputs' not found
grub Rescue>_
(Flashing cursor)

---

### Post by TimEnid on 2011-05-12
> **Hedgehog1 said:**
> **[SIZE="2"]Using the _Natty_ LiveCD/LiveUSB:[/SIZE]**

Select 'TRY' and please do this:

```
sudo mount /dev/sd**c1** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```


I think that is all you need to be running again...


***The Hedge***

:KS
that second code, i put sda as you said. Is that correct?

---

### Post by Quackers on 2011-05-12
Which hard drive is first to boot in your bios?

---

### Post by TimEnid on 2011-05-12
> **Quackers said:**
> Which hard drive is first to boot in your bios?

Sdc

---

### Post by Quackers on 2011-05-12
Ok, thanks. That's good.
I'm sure Mr Hedge is still around here and I'm sure he would tell you the same thing, but with the grub_xputs error it is normally necessary to purge and re-install grub. You can use the CHROOT section of the guide below to accomplish this.
The partition you need to mount first is /dev/sdc1 and you should install grub to /dev/sdc, in your circumstances.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by TimEnid on 2011-05-12
fixed. Thanks for the help everyone.

---

### Post by Quackers on 2011-05-12
That was quick :-)
Nice one. And Mr Hedge too!

---

### Post by Hedgehog1 on 2011-05-12
Thanks for holding down the fort while I was away!

Sorry about the sda/sdc thing....  

***The Hedge***

:KS

---

### Post by Quackers on 2011-05-12
No problem. We all have to go away sometimes :-)

---

