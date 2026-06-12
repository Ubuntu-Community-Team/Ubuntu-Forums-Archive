---
title: "Installing Ubuntu 11.04"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by tommy2k10 on 2011-05-19
I have got a test machine with Windows XP, Vista and 7 on.  I want to install Linux on it as well, which I did using the option to install it alongside my current OS's.  However, now I cannot find it!  I have got a bootloader menu, but Linux isn't on it!  What shall i do?

---

### Post by oldfred on 2011-05-19
From liveCD run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
New Version 060 has improved formating and requires code tags to make it legible. It is also a .zip file that you have to extract to get the script.

---

### Post by tommy2k10 on 2011-05-20
```
      Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 90bb4ebe-f179-42b2-a3fc-5714f700370d root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => No boot loader? is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file 
                       /NST/nst_linux-9A7E87E501A8627EF0DF28F8CBF5E9DA.mbr 
                       looks at sector 1 of the same hard drive for core.img, 
                       but core.img can not be found at this location. Grub2 
                       (v1.97-1.98) in the file 
                       /NST/nst_linux-DA798A0F651A4B2BBBF13EFDC34699F6.mbr 
                       looks at sector 1 of the same hard drive for core.img, 
                       but core.img can not be found at this location. Grub2 
                       (v1.97-1.98) in the file /NST/nst_linux.mbr looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  Windows 7
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdd3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        

sdd6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd6 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd8: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sde8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde10: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 36.7 GB, 36703932928 bytes
66 heads, 19 sectors/track, 57166 cylinders, total 71687369 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *     17,786,880    71,686,163    53,899,284   7 NTFS / exFAT / HPFS
/dev/sda2               2,046    17,786,879    17,784,834   5 Extended
/dev/sda5               2,048    13,725,695    13,723,648  83 Linux
/dev/sda6          13,727,744    17,786,879     4,059,136  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 36.7 GB, 36703932928 bytes
255 heads, 63 sectors/track, 4462 cylinders, total 71687369 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    71,665,964    71,665,902   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 18.2 GB, 18210037760 bytes
255 heads, 63 sectors/track, 2213 cylinders, total 35566480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    35,535,779    35,535,717   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS
/dev/sdd2    *    102,398,310   205,776,584   103,378,275   7 NTFS / exFAT / HPFS
/dev/sdd3         205,776,646   488,392,064   282,615,419   f W95 Extended (LBA)
/dev/sdd5         205,776,648   310,215,149   104,438,502   7 NTFS / exFAT / HPFS
/dev/sdd6         310,215,213   413,641,619   103,426,407   7 NTFS / exFAT / HPFS
/dev/sdd7         413,641,683   485,227,259    71,585,577  83 Linux
/dev/sdd8         485,227,323   488,392,064     3,164,742  82 Linux swap / Solaris


Drive: sde _____________________________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63    97,765,687    97,765,625   7 NTFS / exFAT / HPFS
/dev/sde2          97,767,422   488,396,799   390,629,378   5 Extended
/dev/sde5          97,767,424   114,272,865    16,505,442  83 Linux
/dev/sde6         473,667,584   488,396,799    14,729,216  82 Linux swap / Solaris
/dev/sde7         114,274,304   120,372,655     6,098,352  83 Linux
/dev/sde8         469,600,256   473,661,439     4,061,184  82 Linux swap / Solaris
/dev/sde9         120,373,248   465,534,975   345,161,728  83 Linux
/dev/sde10        465,537,024   469,596,159     4,059,136  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  32     3,903,487     3,903,456   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        52DCD1D0DCD1AF0B                       ntfs       
/dev/sda5        9d1ef853-708e-43c6-88b5-1a6ab8ba43de   ext4       
/dev/sdb1        8EA82330A823166D                       ntfs       Windows 7 Beta
/dev/sdc1        CE2CEE5B2CEE3E59                       ntfs       
/dev/sdd1        01C9EA8B80749ED0                       ntfs       Windows Vista
/dev/sdd2        2CE4F805E4F7CF58                       ntfs       Windows 7
/dev/sdd5        2A2063812063533D                       ntfs       Windows XP
/dev/sdd6        C6FCC979FCC963F1                       ntfs       
/dev/sdd7        05aa68b2-b685-4729-886f-c5a165108412   ext4       
/dev/sde1        24B0F943B0F91BCC                       ntfs       Backup drive
/dev/sde5        148f93b4-1449-4b39-97d3-3d451dbc869f   ext4       
/dev/sde7        557db2e6-2e9b-4ba8-977c-48ccca784083   ext4       
/dev/sde8        ed279151-e14b-4fb8-85fe-11157957f9d8   swap       
/dev/sde9        90bb4ebe-f179-42b2-a3fc-5714f700370d   ext4       
/dev/sdf1        1C52-9AF5                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/52DCD1D0DCD1AF0B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/CE2CEE5B2CEE3E59  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd6        /media/C6FCC979FCC963F1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd7        /media/05aa68b2-b685-4729-886f-c5a165108412 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sde5        /media/148f93b4-1449-4b39-97d3-3d451dbc869f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sde9        /media/90bb4ebe-f179-42b2-a3fc-5714f700370d ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdf1        /media/1C52-9AF5         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Windows XP on E:\" /fastdetect
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 52DCD1D0DCD1AF0B
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root CE2CEE5B2CEE3E59
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root 2CE4F805E4F7CF58
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=f3fa9e6a-84d2-49ef-86d3-a644996d60d4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0
/dev/mapper/cryptswap3 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.527080536 = 4.860915712    boot/grub/core.img                             1
   4.525043488 = 4.858728448    boot/grub/grub.cfg                             1
   3.055664062 = 3.280994304    boot/initrd.img-2.6.38-8-generic               2
   4.523906708 = 4.857507840    boot/vmlinuz-2.6.38-8-generic                  1
   3.055664062 = 3.280994304    initrd.img                                     2
   4.523906708 = 4.857507840    vmlinuz                                        1

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
--------------------------------------------------------------------------------

================================ sdd2/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
--------------------------------------------------------------------------------

=========================== sdd7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 2ce4f805e4f7cf58
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 52dcd1d0dcd1af0b
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sde1)" {
    insmod ntfs
    set root=(hd4,1)
    search --no-floppy --fs-uuid --set ce2cee5b2cee3e59
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdd7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=05aa68b2-b685-4729-886f-c5a165108412 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=68b92ef6-f0d5-45fd-b870-0ffed1a88600 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdd7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 202.645410061 = 217.588852224  boot/grub/core.img                             1
 202.645497799 = 217.588946432  boot/grub/grub.cfg                             1
 197.805753231 = 212.392310272  boot/initrd.img-2.6.31-14-generic              1
 197.790223598 = 212.375635456  boot/vmlinuz-2.6.31-14-generic                 1
 197.805753231 = 212.392310272  initrd.img                                     1
 197.790223598 = 212.375635456  vmlinuz                                        1

=========================== sde5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd4,5)'
search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
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
set root='(hd4,5)'
search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
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
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 52dcd1d0dcd1af0b
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set ce2cee5b2cee3e59
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" {
    insmod ntfs
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set 2ce4f805e4f7cf58
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdd7)" {
    insmod ext2
    set root='(hd3,7)'
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdd7)" {
    insmod ext2
    set root='(hd3,7)'
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sde5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde5 during installation
UUID=148f93b4-1449-4b39-97d3-3d451dbc869f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde6 during installation
UUID=56a65c81-5b45-4c58-9918-876154604fda none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sde5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  46.664646149 = 50.105782272   boot/grub/core.img                             1
  48.018348694 = 51.559309312   boot/grub/grub.cfg                             1
  46.672069550 = 50.113753088   boot/initrd.img-2.6.32-24-generic              1
  46.888523102 = 50.346168320   boot/vmlinuz-2.6.32-24-generic                 1
  46.672069550 = 50.113753088   initrd.img                                     1
  46.888523102 = 50.346168320   vmlinuz                                        1

=============================== sde7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde7 during installation
UUID=557db2e6-2e9b-4ba8-977c-48ccca784083 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde8 during installation
UUID=ed279151-e14b-4fb8-85fe-11157957f9d8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=========================== sde9/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos9)'
search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos9)'
search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=90bb4ebe-f179-42b2-a3fc-5714f700370d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=90bb4ebe-f179-42b2-a3fc-5714f700370d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 52DCD1D0DCD1AF0B
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root CE2CEE5B2CEE3E59
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root 2CE4F805E4F7CF58
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sde9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde9 during installation
UUID=90bb4ebe-f179-42b2-a3fc-5714f700370d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde10 during installation
#UUID=76f998dc-6634-48c3-bf4d-bf220d0cfd1b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sde9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 195.532978058 = 209.951936512  boot/grub/core.img                             1
 149.535785675 = 160.562827264  boot/grub/grub.cfg                             1
  83.687500000 = 89.858768896   boot/initrd.img-2.6.38-8-generic               3
 195.531253815 = 209.950085120  boot/vmlinuz-2.6.38-8-generic                  1
  83.687500000 = 89.858768896   initrd.img                                     3
 195.531253815 = 209.950085120  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  1f 00 7e 00 73 f0 00 3c  00 13 f9 80 00 e7 bb c0  |..~.s..<........|
00000010  7c 00 1e 00 3f 00 3e 00  73 f8 00 3c 00 33 f1 87  ||...?.>.s..<.3..|
00000020  80 e3 3b 7f e0 f8 0e 0f  80 ff 00 3e 00 43 f8 00  |..;........>.C..|
00000030  3c 00 33 f1 87 00 f0 3b  f8 cc 9f 1f 80 ff 00 3e  |<.3....;.......>|
00000040  00 03 fc 00 3e 00 03 e0  00 00 e0 39 ff cd ff 3e  |....>......9...>|
00000050  f0 f8 00 2f 03 01 fe 60  3e 00 03 ef 00 0f e0 7b  |.../...`>......{|
00000060  7f dc ff 7c 20 f0 00 3f  03 00 7e 60 1c 00 03 ff  |...| ..?..~`....|
00000070  83 99 f8 ff 7f f8 7e f8  00 60 00 3f 03 00 7f e0  |......~..`.?....|
00000080  d8 00 03 df 87 f8 81 ff  39 f8 7f e1 00 c0 00 77  |........9......w|
00000090  03 00 3f e0 f0 00 03 df  83 d0 c1 f7 39 f1 ff c1  |..?.........9...|
000000a0  c0 00 00 7f 67 80 00 3b  e1 e0 01 83 cf 80 81 c1  |....g..;........|
000000b0  ff 7d f3 ff f0 c0 00 00  67 80 00 39 e1 c0 1f 83  |.}......g..9....|
000000c0  ff 80 00 c3 ff 7c e7 83  fc e0 00 00 77 86 00 7c  |.....|......w..||
000000d0  e1 91 99 01 bf 80 00 c1  fe 7c 07 03 fe e0 00 00  |.........|......|
000000e0  77 8e 12 1f f1 81 80 00  3f c0 00 c1 de 6e 07 03  |w.......?....n..|
000000f0  ff c0 60 00 67 80 3f 1f  ff 00 00 00 3f c0 01 e0  |..`.g.?.....?...|
00000100  fe ee 0f 03 ff c0 c0 00  23 c0 7f ff ff 80 00 00  |........#.......|
00000110  3d e0 0f c0 df ee 0f 01  cf c0 00 00 63 e0 7f fc  |=...........c...|
00000120  7f 86 00 7f 00 3d f8 7f  03 df 8e 0e 01 ee 40 00  |.....=........@.|
00000130  00 61 f1 ff f8 3f 8c 00  03 81 f8 7f c7 9f 0c 1e  |.a...?..........|
00000140  05 ff 70 00 00 61 ff 80  3c 1f 8c 00 03 81 f0 7b  |..p..a..<......{|
00000150  ef 0c 00 1e 01 ff f8 00  00 40 ff 00 0e 03 8c 00  |.........@......|
00000160  03 81 b0 3c 4f 00 00 3c  01 f9 f8 80 00 c0 ff 00  |...<O..<........|
00000170  07 63 80 00 00 38 00 1c  6f f0 00 7c 01 f8 f8 00  |.c...8..o..|....|
00000180  01 c0 7f 80 00 e1 80 00  00 3c 00 09 fe fc 00 38  |.........<.....8|
00000190  05 f7 f8 00 01 c0 3f 80  0c 41 80 00 0c 38 e0 00  |......?..A...8..|
000001a0  fe 7c 00 6c 38 07 c3 98  00 03 81 ff e0 01 c1 c0  |.|.l8...........|
000001b0  00 0e 30 60 40 1f 8c 00  78 06 03 f0 00 07 00 20  |..0`@...x...... |
000001c0  21 00 83 62 cc 56 02 00  00 00 00 68 d1 00 00 62  |!..b.V.....h...b|
000001d0  cd 56 05 fe ff ff 02 68  d1 00 00 f8 3d 00 00 00  |.V.....h....=...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdd3

00000000  55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  |UUUUUUUUUUUUUUUU|
*
000001b0  55 55 55 55 55 55 55 55  55 55 55 55 55 55 00 01  |UUUUUUUUUUUUUU..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 e6 9a 39 06 00 fe  |............9...|
000001d0  ff ff 05 fe ff ff e8 9a  39 06 a6 29 2a 06 00 00  |........9..)*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sde2

00000000  77 09 71 09 c3 08 ba 08  27 08 22 08 9f 07 93 07  |w.q.....'.".....|
00000010  13 07 0a 07 c0 06 b7 06  65 06 57 06 1e 06 11 06  |........e.W.....|
00000020  fe 05 f1 05 e4 05 d6 05  de 05 cf 05 e4 05 d7 05  |................|
00000030  d7 05 cf 05 d6 05 cc 05  db 05 d4 05 e3 05 dc 05  |................|
00000040  f7 05 ef 05 ef 05 e6 05  fe 05 f2 05 0f 06 02 06  |................|
00000050  1a 06 0e 06 24 06 16 06  37 06 29 06 11 06 02 06  |....$...7.).....|
00000060  f9 05 e9 05 be 05 af 05  43 05 38 05 ed 04 e7 04  |........C.8.....|
00000070  59 04 51 04 c6 03 c3 03  48 03 46 03 92 02 91 02  |Y.Q.....H.F.....|
00000080  11 02 0e 02 91 01 8e 01  0b 01 0a 01 ac 00 aa 00  |................|
00000090  3f 00 3e 00 09 00 04 00  ca ff c2 ff a2 ff a1 ff  |?.>.............|
000000a0  b1 ff af ff ac ff af ff  dc ff dc ff e7 ff e9 ff  |................|
000000b0  0e 00 0e 00 74 00 76 00  b2 00 b2 00 25 01 2a 01  |....t.v.....%.*.|
000000c0  a1 01 a1 01 26 02 22 02  cc 02 c2 02 5b 03 51 03  |....&.".....[.Q.|
000000d0  ec 03 e4 03 71 04 6a 04  d8 04 d3 04 33 05 2b 05  |....q.j.....3.+.|
000000e0  6e 05 68 05 93 05 8e 05  b3 05 ae 05 bc 05 b7 05  |n.h.............|
000000f0  c4 05 c1 05 b9 05 b1 05  bf 05 b6 05 b7 05 ae 05  |................|
00000100  bc 05 b6 05 db 05 d6 05  1a 06 16 06 92 06 88 06  |................|
00000110  18 07 10 07 cf 07 c4 07  a0 08 95 08 49 09 3c 09  |............I.<.|
00000120  15 0a 0a 0a b0 0a a2 0a  43 0b 38 0b ae 0b a6 0b  |........C.8.....|
00000130  e2 0b d5 0b 09 0c fd 0b  22 0c 17 0c 1f 0c 12 0c  |........".......|
00000140  18 0c 0f 0c fd 0b f1 0b  09 0c fa 0b ed 0b e1 0b  |................|
00000150  ac 0b 9e 0b 79 0b 6b 0b  09 0b fe 0a b0 0a a3 0a  |....y.k.........|
00000160  52 0a 47 0a fa 09 e9 09  b6 09 a6 09 7c 09 69 09  |R.G.........|.i.|
00000170  53 09 41 09 46 09 39 09  3c 09 2e 09 4b 09 40 09  |S.A.F.9.<...K.@.|
00000180  4c 09 41 09 50 09 44 09  61 09 54 09 4e 09 44 09  |L.A.P.D.a.T.N.D.|
00000190  53 09 49 09 2d 09 25 09  0e 09 08 09 db 08 d0 08  |S.I.-.%.........|
000001a0  95 08 8d 08 75 08 6f 08  1f 08 1a 08 e6 07 df 07  |....u.o.........|
000001b0  8c 07 84 07 28 07 21 07  a3 06 a2 06 07 06 00 fe  |....(.!.........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 62 da fb 00 00 fe  |..........b.....|
000001d0  ff ff 05 fe ff ff 02 b0  67 16 00 d8 e0 00 00 00  |........g.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by oldfred on 2011-05-20
With many drives & partitions, I like to keep a system on each drive and have its boot loader in the MBR of that drive. Then in BIOS select to default boot the install I use the most.

You have grub2's boot loader in sda and it boots the install in sde9. That grub.cfg shows the other installs as optional boots.

But you have also installed grub to a windows partition. Grub does not like to be in partitions as it is less reliable as it has to use blocklists, but never should be in a windows partition as windows has to have its code in that partition. With multiple drives like you have just install a version grub to each drive for each install and have a windows boot loader in the windows drive. Set BIOS to boot the grub install you use most. For any drive with both win & Ubuntu you have to decide which you want as default. I would reinstall windows boot loader to sda.

Boot into each Ubuntu install and install grub2's boot loader to the MBR.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
[COLOR=DarkRed]sudo grub-install /dev/sdb[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
[COLOR=DarkRed]sudo dpkg-reconfigure grub-pc[/COLOR]
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

For your windows in sdd2:
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by corrytonapple on 2011-05-20
It may be something like:
```
linux-image-2.6.35-28
```
Instead of saying "Ubuntu Linux 11.04", though you can get it to say that if you follow a simple thread I can give you.

---

### Post by tommy2k10 on 2011-05-25
I have managed to get the GRUB bootloader back!  However, now for the next problem:
Version 11.04 isn't there!  It is the version I had on there: 9.10.  
Can I upgrade to 11.04 from within 9.10!
If not, how can I ensure GRUB doesn't disappear again when I uninstall 9.10?!

---

### Post by oldfred on 2011-05-25
You showed an install of 11.04. Have you tried this.

sudo update-grub

this is for Maverick and Natty screens are slightly different but the process is the same.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by tommy2k10 on 2011-05-25
I did sudo update-grub.

I got:

Ubuntu-Linux 2.6.31-14-generic
Ubuntu-Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) on /dev/sda2
'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux
'Ubuntu, with Linux 2.6.32-24-generic' --recovery mode --class gnu-linux
'Ubuntu, with Linux 2.6.32-8-generic' --class ubuntu --class gnu-linux
'Ubuntu, with Linux 2.6.32-8-generic' --recovery mode --class gnu-linux
Windows Vista (loader) on /dev/sdc1
'Ubuntu, with Linux 2.6.32-8-generic' --class ubuntu --class gnu-linux
'Ubuntu, with Linux 2.6.32-8-generic' --recovery mode --class gnu-linux
Microsoft Windows XP Professional on /dev/sde1

When I choose any of the Ubuntu kernels (except 2.6.31-14, I get:

Error: No argument specified
Error: File Not Found
Error: You need to load the kernel first

---

### Post by oldfred on 2011-05-25
Both sda5 & sde9 show installs of 11.04. What grub2 partition did you use to reinstall grub2's boot loader to the MBR?

And which drive are you booting with BIOS or one time boot key? If the os-prober from 9.10 is not finding the newer installs use a 11.04 livecd and install from sda5 to sda's MBR and from sde9 to sde's MBR.

It looks like you are booting sdd7 or your 9.10 install?

Example is sda5, also change sda5 & sda to sde9 & sde for your other install.
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by tommy2k10 on 2011-05-26
I am not that experienced with Linux.
When I installed 11.04, it gave me the options to either install alongside Windows, install using the entire disk, or manually resize the partiitions.  I installed alongside Windows, but it gave me no further options about partitions.
I am booting with the first 250GB disk.

---

### Post by oldfred on 2011-05-26
Anytime you have more than one drive, you need to manually partition. That way you have control over exact sizes and locations of each partition and get the choice on where to install grub2's boot loader which should be the MBR of the same drive you install Ubuntu to.

The screens are slightly different for Natty as this is Maverick, but the process is the same.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

If you need exact instructions to reinstall the correct grub2 boot loader to the correct MBR, repost the boot info script. Also which of the two installs is your main install. You may want to keep the other for testing major changes before implementing in your working install.

---

### Post by tommy2k10 on 2011-05-31
I tried to change the partition type to Ext4 on the disk I was booting from, and now all it says is unknown filesystem and then I get <grub rescue...!
The boot info script is attached here:


#                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 90bb4ebe-f179-42b2-a3fc-5714f700370d root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => No boot loader? is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file 
                       /NST/nst_linux-9A7E87E501A8627EF0DF28F8CBF5E9DA.mbr 
                       looks at sector 1 of the same hard drive for core.img, 
                       but core.img can not be found at this location. Grub2 
                       (v1.97-1.98) in the file 
                       /NST/nst_linux-DA798A0F651A4B2BBBF13EFDC34699F6.mbr 
                       looks at sector 1 of the same hard drive for core.img, 
                       but core.img can not be found at this location. Grub2 
                       (v1.97-1.98) in the file /NST/nst_linux.mbr looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  Windows 7
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdd3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        

sdd6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd6 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd8: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sde8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde10: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 36.7 GB, 36703932928 bytes
66 heads, 19 sectors/track, 57166 cylinders, total 71687369 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *     17,786,880    71,686,163    53,899,284   7 NTFS / exFAT / HPFS
/dev/sda2               2,046    17,786,879    17,784,834   5 Extended
/dev/sda5               2,048    13,725,695    13,723,648  83 Linux
/dev/sda6          13,727,744    17,786,879     4,059,136  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 36.7 GB, 36703932928 bytes
255 heads, 63 sectors/track, 4462 cylinders, total 71687369 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    71,665,964    71,665,902   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 18.2 GB, 18210037760 bytes
255 heads, 63 sectors/track, 2213 cylinders, total 35566480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    35,535,779    35,535,717   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS
/dev/sdd2    *    102,398,310   205,776,584   103,378,275   7 NTFS / exFAT / HPFS
/dev/sdd3         205,776,646   488,392,064   282,615,419   f W95 Extended (LBA)
/dev/sdd5         205,776,648   310,215,149   104,438,502   7 NTFS / exFAT / HPFS
/dev/sdd6         310,215,213   413,641,619   103,426,407   7 NTFS / exFAT / HPFS
/dev/sdd7         413,641,683   485,227,259    71,585,577  83 Linux
/dev/sdd8         485,227,323   488,392,064     3,164,742  82 Linux swap / Solaris


Drive: sde _____________________________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63    97,765,687    97,765,625   7 NTFS / exFAT / HPFS
/dev/sde2          97,767,422   488,396,799   390,629,378   5 Extended
/dev/sde5          97,767,424   114,272,865    16,505,442  83 Linux
/dev/sde6         473,667,584   488,396,799    14,729,216  82 Linux swap / Solaris
/dev/sde7         114,274,304   120,372,655     6,098,352  83 Linux
/dev/sde8         469,600,256   473,661,439     4,061,184  82 Linux swap / Solaris
/dev/sde9         120,373,248   465,534,975   345,161,728  83 Linux
/dev/sde10        465,537,024   469,596,159     4,059,136  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  32     3,903,487     3,903,456   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        52DCD1D0DCD1AF0B                       ntfs       
/dev/sda5        9d1ef853-708e-43c6-88b5-1a6ab8ba43de   ext4       
/dev/sdb1        8EA82330A823166D                       ntfs       Windows 7 Beta
/dev/sdc1        CE2CEE5B2CEE3E59                       ntfs       
/dev/sdd1        01C9EA8B80749ED0                       ntfs       Windows Vista
/dev/sdd2        2CE4F805E4F7CF58                       ntfs       Windows 7
/dev/sdd5        2A2063812063533D                       ntfs       Windows XP
/dev/sdd6        C6FCC979FCC963F1                       ntfs       
/dev/sdd7        05aa68b2-b685-4729-886f-c5a165108412   ext4       
/dev/sde1        24B0F943B0F91BCC                       ntfs       Backup drive
/dev/sde5        148f93b4-1449-4b39-97d3-3d451dbc869f   ext4       
/dev/sde7        557db2e6-2e9b-4ba8-977c-48ccca784083   ext4       
/dev/sde8        ed279151-e14b-4fb8-85fe-11157957f9d8   swap       
/dev/sde9        90bb4ebe-f179-42b2-a3fc-5714f700370d   ext4       
/dev/sdf1        1C52-9AF5                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/52DCD1D0DCD1AF0B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/CE2CEE5B2CEE3E59  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd6        /media/C6FCC979FCC963F1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd7        /media/05aa68b2-b685-4729-886f-c5a165108412 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sde5        /media/148f93b4-1449-4b39-97d3-3d451dbc869f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sde9        /media/90bb4ebe-f179-42b2-a3fc-5714f700370d ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdf1        /media/1C52-9AF5         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Windows XP on E:\" /fastdetect
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 52DCD1D0DCD1AF0B
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root CE2CEE5B2CEE3E59
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root 2CE4F805E4F7CF58
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=f3fa9e6a-84d2-49ef-86d3-a644996d60d4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0
/dev/mapper/cryptswap3 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.527080536 = 4.860915712    boot/grub/core.img                             1
   4.525043488 = 4.858728448    boot/grub/grub.cfg                             1
   3.055664062 = 3.280994304    boot/initrd.img-2.6.38-8-generic               2
   4.523906708 = 4.857507840    boot/vmlinuz-2.6.38-8-generic                  1
   3.055664062 = 3.280994304    initrd.img                                     2
   4.523906708 = 4.857507840    vmlinuz                                        1

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
--------------------------------------------------------------------------------

================================ sdd2/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
--------------------------------------------------------------------------------

=========================== sdd7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 2ce4f805e4f7cf58
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 52dcd1d0dcd1af0b
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sde1)" {
    insmod ntfs
    set root=(hd4,1)
    search --no-floppy --fs-uuid --set ce2cee5b2cee3e59
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdd7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=05aa68b2-b685-4729-886f-c5a165108412 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=68b92ef6-f0d5-45fd-b870-0ffed1a88600 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdd7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 202.645410061 = 217.588852224  boot/grub/core.img                             1
 202.645497799 = 217.588946432  boot/grub/grub.cfg                             1
 197.805753231 = 212.392310272  boot/initrd.img-2.6.31-14-generic              1
 197.790223598 = 212.375635456  boot/vmlinuz-2.6.31-14-generic                 1
 197.805753231 = 212.392310272  initrd.img                                     1
 197.790223598 = 212.375635456  vmlinuz                                        1

=========================== sde5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd4,5)'
search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
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
set root='(hd4,5)'
search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
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
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 52dcd1d0dcd1af0b
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set ce2cee5b2cee3e59
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" {
    insmod ntfs
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set 2ce4f805e4f7cf58
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdd7)" {
    insmod ext2
    set root='(hd3,7)'
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdd7)" {
    insmod ext2
    set root='(hd3,7)'
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sde5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde5 during installation
UUID=148f93b4-1449-4b39-97d3-3d451dbc869f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde6 during installation
UUID=56a65c81-5b45-4c58-9918-876154604fda none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sde5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  46.664646149 = 50.105782272   boot/grub/core.img                             1
  48.018348694 = 51.559309312   boot/grub/grub.cfg                             1
  46.672069550 = 50.113753088   boot/initrd.img-2.6.32-24-generic              1
  46.888523102 = 50.346168320   boot/vmlinuz-2.6.32-24-generic                 1
  46.672069550 = 50.113753088   initrd.img                                     1
  46.888523102 = 50.346168320   vmlinuz                                        1

=============================== sde7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde7 during installation
UUID=557db2e6-2e9b-4ba8-977c-48ccca784083 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde8 during installation
UUID=ed279151-e14b-4fb8-85fe-11157957f9d8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=========================== sde9/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos9)'
search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos9)'
search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=90bb4ebe-f179-42b2-a3fc-5714f700370d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=90bb4ebe-f179-42b2-a3fc-5714f700370d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 52DCD1D0DCD1AF0B
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root CE2CEE5B2CEE3E59
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root 2CE4F805E4F7CF58
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sde9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde9 during installation
UUID=90bb4ebe-f179-42b2-a3fc-5714f700370d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde10 during installation
#UUID=76f998dc-6634-48c3-bf4d-bf220d0cfd1b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sde9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 195.532978058 = 209.951936512  boot/grub/core.img                             1
 149.535785675 = 160.562827264  boot/grub/grub.cfg                             1
  83.687500000 = 89.858768896   boot/initrd.img-2.6.38-8-generic               3
 195.531253815 = 209.950085120  boot/vmlinuz-2.6.38-8-generic                  1
  83.687500000 = 89.858768896   initrd.img                                     3
 195.531253815 = 209.950085120  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  1f 00 7e 00 73 f0 00 3c  00 13 f9 80 00 e7 bb c0  |..~.s..<........|
00000010  7c 00 1e 00 3f 00 3e 00  73 f8 00 3c 00 33 f1 87  ||...?.>.s..<.3..|
00000020  80 e3 3b 7f e0 f8 0e 0f  80 ff 00 3e 00 43 f8 00  |..;........>.C..|
00000030  3c 00 33 f1 87 00 f0 3b  f8 cc 9f 1f 80 ff 00 3e  |<.3....;.......>|
00000040  00 03 fc 00 3e 00 03 e0  00 00 e0 39 ff cd ff 3e  |....>......9...>|
00000050  f0 f8 00 2f 03 01 fe 60  3e 00 03 ef 00 0f e0 7b  |.../...`>......{|
00000060  7f dc ff 7c 20 f0 00 3f  03 00 7e 60 1c 00 03 ff  |...| ..?..~`....|
00000070  83 99 f8 ff 7f f8 7e f8  00 60 00 3f 03 00 7f e0  |......~..`.?....|
00000080  d8 00 03 df 87 f8 81 ff  39 f8 7f e1 00 c0 00 77  |........9......w|
00000090  03 00 3f e0 f0 00 03 df  83 d0 c1 f7 39 f1 ff c1  |..?.........9...|
000000a0  c0 00 00 7f 67 80 00 3b  e1 e0 01 83 cf 80 81 c1  |....g..;........|
000000b0  ff 7d f3 ff f0 c0 00 00  67 80 00 39 e1 c0 1f 83  |.}......g..9....|
000000c0  ff 80 00 c3 ff 7c e7 83  fc e0 00 00 77 86 00 7c  |.....|......w..||
000000d0  e1 91 99 01 bf 80 00 c1  fe 7c 07 03 fe e0 00 00  |.........|......|
000000e0  77 8e 12 1f f1 81 80 00  3f c0 00 c1 de 6e 07 03  |w.......?....n..|
000000f0  ff c0 60 00 67 80 3f 1f  ff 00 00 00 3f c0 01 e0  |..`.g.?.....?...|
00000100  fe ee 0f 03 ff c0 c0 00  23 c0 7f ff ff 80 00 00  |........#.......|
00000110  3d e0 0f c0 df ee 0f 01  cf c0 00 00 63 e0 7f fc  |=...........c...|
00000120  7f 86 00 7f 00 3d f8 7f  03 df 8e 0e 01 ee 40 00  |.....=........@.|
00000130  00 61 f1 ff f8 3f 8c 00  03 81 f8 7f c7 9f 0c 1e  |.a...?..........|
00000140  05 ff 70 00 00 61 ff 80  3c 1f 8c 00 03 81 f0 7b  |..p..a..<......{|
00000150  ef 0c 00 1e 01 ff f8 00  00 40 ff 00 0e 03 8c 00  |.........@......|
00000160  03 81 b0 3c 4f 00 00 3c  01 f9 f8 80 00 c0 ff 00  |...<O..<........|
00000170  07 63 80 00 00 38 00 1c  6f f0 00 7c 01 f8 f8 00  |.c...8..o..|....|
00000180  01 c0 7f 80 00 e1 80 00  00 3c 00 09 fe fc 00 38  |.........<.....8|
00000190  05 f7 f8 00 01 c0 3f 80  0c 41 80 00 0c 38 e0 00  |......?..A...8..|
000001a0  fe 7c 00 6c 38 07 c3 98  00 03 81 ff e0 01 c1 c0  |.|.l8...........|
000001b0  00 0e 30 60 40 1f 8c 00  78 06 03 f0 00 07 00 20  |..0`@...x...... |
000001c0  21 00 83 62 cc 56 02 00  00 00 00 68 d1 00 00 62  |!..b.V.....h...b|
000001d0  cd 56 05 fe ff ff 02 68  d1 00 00 f8 3d 00 00 00  |.V.....h....=...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdd3

00000000  55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  |UUUUUUUUUUUUUUUU|
*
000001b0  55 55 55 55 55 55 55 55  55 55 55 55 55 55 00 01  |UUUUUUUUUUUUUU..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 e6 9a 39 06 00 fe  |............9...|
000001d0  ff ff 05 fe ff ff e8 9a  39 06 a6 29 2a 06 00 00  |........9..)*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sde2

00000000  77 09 71 09 c3 08 ba 08  27 08 22 08 9f 07 93 07  |w.q.....'.".....|
00000010  13 07 0a 07 c0 06 b7 06  65 06 57 06 1e 06 11 06  |........e.W.....|
00000020  fe 05 f1 05 e4 05 d6 05  de 05 cf 05 e4 05 d7 05  |................|
00000030  d7 05 cf 05 d6 05 cc 05  db 05 d4 05 e3 05 dc 05  |................|
00000040  f7 05 ef 05 ef 05 e6 05  fe 05 f2 05 0f 06 02 06  |................|
00000050  1a 06 0e 06 24 06 16 06  37 06 29 06 11 06 02 06  |....$...7.).....|
00000060  f9 05 e9 05 be 05 af 05  43 05 38 05 ed 04 e7 04  |........C.8.....|
00000070  59 04 51 04 c6 03 c3 03  48 03 46 03 92 02 91 02  |Y.Q.....H.F.....|
00000080  11 02 0e 02 91 01 8e 01  0b 01 0a 01 ac 00 aa 00  |................|
00000090  3f 00 3e 00 09 00 04 00  ca ff c2 ff a2 ff a1 ff  |?.>.............|
000000a0  b1 ff af ff ac ff af ff  dc ff dc ff e7 ff e9 ff  |................|
000000b0  0e 00 0e 00 74 00 76 00  b2 00 b2 00 25 01 2a 01  |....t.v.....%.*.|
000000c0  a1 01 a1 01 26 02 22 02  cc 02 c2 02 5b 03 51 03  |....&.".....[.Q.|
000000d0  ec 03 e4 03 71 04 6a 04  d8 04 d3 04 33 05 2b 05  |....q.j.....3.+.|
000000e0  6e 05 68 05 93 05 8e 05  b3 05 ae 05 bc 05 b7 05  |n.h.............|
000000f0  c4 05 c1 05 b9 05 b1 05  bf 05 b6 05 b7 05 ae 05  |................|
00000100  bc 05 b6 05 db 05 d6 05  1a 06 16 06 92 06 88 06  |................|
00000110  18 07 10 07 cf 07 c4 07  a0 08 95 08 49 09 3c 09  |............I.<.|
00000120  15 0a 0a 0a b0 0a a2 0a  43 0b 38 0b ae 0b a6 0b  |........C.8.....|
00000130  e2 0b d5 0b 09 0c fd 0b  22 0c 17 0c 1f 0c 12 0c  |........".......|
00000140  18 0c 0f 0c fd 0b f1 0b  09 0c fa 0b ed 0b e1 0b  |................|
00000150  ac 0b 9e 0b 79 0b 6b 0b  09 0b fe 0a b0 0a a3 0a  |....y.k.........|
00000160  52 0a 47 0a fa 09 e9 09  b6 09 a6 09 7c 09 69 09  |R.G.........|.i.|
00000170  53 09 41 09 46 09 39 09  3c 09 2e 09 4b 09 40 09  |S.A.F.9.<...K.@.|
00000180  4c 09 41 09 50 09 44 09  61 09 54 09 4e 09 44 09  |L.A.P.D.a.T.N.D.|
00000190  53 09 49 09 2d 09 25 09  0e 09 08 09 db 08 d0 08  |S.I.-.%.........|
000001a0  95 08 8d 08 75 08 6f 08  1f 08 1a 08 e6 07 df 07  |....u.o.........|
000001b0  8c 07 84 07 28 07 21 07  a3 06 a2 06 07 06 00 fe  |....(.!.........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 62 da fb 00 00 fe  |..........b.....|
000001d0  ff ff 05 fe ff ff 02 b0  67 16 00 d8 e0 00 00 00  |........g.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by oldfred on 2011-05-31
Could you please put your results.txt in code tags. It is hard to read.

When adding code tags on edit it is easier to click the advanced button at the bottom to get the full edit panel at the top. Then highlight the entire results.txt with mouse and click on the # on the right side of the edit panel on top. You can also manually type the code tags but have to put code in brackets [] at the begining and have /code in brackets[] at the end.

---

### Post by tommy2k10 on 2011-05-31
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 90bb4ebe-f179-42b2-a3fc-5714f700370d root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => No boot loader? is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file 
                       /NST/nst_linux-9A7E87E501A8627EF0DF28F8CBF5E9DA.mbr 
                       looks at sector 1 of the same hard drive for core.img, 
                       but core.img can not be found at this location. Grub2 
                       (v1.97-1.98) in the file 
                       /NST/nst_linux-DA798A0F651A4B2BBBF13EFDC34699F6.mbr 
                       looks at sector 1 of the same hard drive for core.img, 
                       but core.img can not be found at this location. Grub2 
                       (v1.97-1.98) in the file /NST/nst_linux.mbr looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  Windows 7
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdd3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        

sdd6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd6 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd8: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sde8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde10: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 36.7 GB, 36703932928 bytes
66 heads, 19 sectors/track, 57166 cylinders, total 71687369 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *     17,786,880    71,686,163    53,899,284   7 NTFS / exFAT / HPFS
/dev/sda2               2,046    17,786,879    17,784,834   5 Extended
/dev/sda5               2,048    13,725,695    13,723,648  83 Linux
/dev/sda6          13,727,744    17,786,879     4,059,136  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 36.7 GB, 36703932928 bytes
255 heads, 63 sectors/track, 4462 cylinders, total 71687369 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    71,665,964    71,665,902   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 18.2 GB, 18210037760 bytes
255 heads, 63 sectors/track, 2213 cylinders, total 35566480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    35,535,779    35,535,717   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS
/dev/sdd2    *    102,398,310   205,776,584   103,378,275   7 NTFS / exFAT / HPFS
/dev/sdd3         205,776,646   488,392,064   282,615,419   f W95 Extended (LBA)
/dev/sdd5         205,776,648   310,215,149   104,438,502   7 NTFS / exFAT / HPFS
/dev/sdd6         310,215,213   413,641,619   103,426,407   7 NTFS / exFAT / HPFS
/dev/sdd7         413,641,683   485,227,259    71,585,577  83 Linux
/dev/sdd8         485,227,323   488,392,064     3,164,742  82 Linux swap / Solaris


Drive: sde _____________________________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63    97,765,687    97,765,625   7 NTFS / exFAT / HPFS
/dev/sde2          97,767,422   488,396,799   390,629,378   5 Extended
/dev/sde5          97,767,424   114,272,865    16,505,442  83 Linux
/dev/sde6         473,667,584   488,396,799    14,729,216  82 Linux swap / Solaris
/dev/sde7         114,274,304   120,372,655     6,098,352  83 Linux
/dev/sde8         469,600,256   473,661,439     4,061,184  82 Linux swap / Solaris
/dev/sde9         120,373,248   465,534,975   345,161,728  83 Linux
/dev/sde10        465,537,024   469,596,159     4,059,136  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  32     3,903,487     3,903,456   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        52DCD1D0DCD1AF0B                       ntfs       
/dev/sda5        9d1ef853-708e-43c6-88b5-1a6ab8ba43de   ext4       
/dev/sdb1        8EA82330A823166D                       ntfs       Windows 7 Beta
/dev/sdc1        CE2CEE5B2CEE3E59                       ntfs       
/dev/sdd1        01C9EA8B80749ED0                       ntfs       Windows Vista
/dev/sdd2        2CE4F805E4F7CF58                       ntfs       Windows 7
/dev/sdd5        2A2063812063533D                       ntfs       Windows XP
/dev/sdd6        C6FCC979FCC963F1                       ntfs       
/dev/sdd7        05aa68b2-b685-4729-886f-c5a165108412   ext4       
/dev/sde1        24B0F943B0F91BCC                       ntfs       Backup drive
/dev/sde5        148f93b4-1449-4b39-97d3-3d451dbc869f   ext4       
/dev/sde7        557db2e6-2e9b-4ba8-977c-48ccca784083   ext4       
/dev/sde8        ed279151-e14b-4fb8-85fe-11157957f9d8   swap       
/dev/sde9        90bb4ebe-f179-42b2-a3fc-5714f700370d   ext4       
/dev/sdf1        1C52-9AF5                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/52DCD1D0DCD1AF0B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/CE2CEE5B2CEE3E59  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd6        /media/C6FCC979FCC963F1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd7        /media/05aa68b2-b685-4729-886f-c5a165108412 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sde5        /media/148f93b4-1449-4b39-97d3-3d451dbc869f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sde9        /media/90bb4ebe-f179-42b2-a3fc-5714f700370d ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdf1        /media/1C52-9AF5         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Windows XP on E:\" /fastdetect
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 52DCD1D0DCD1AF0B
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root CE2CEE5B2CEE3E59
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root 2CE4F805E4F7CF58
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=f3fa9e6a-84d2-49ef-86d3-a644996d60d4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0
/dev/mapper/cryptswap3 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.527080536 = 4.860915712    boot/grub/core.img                             1
   4.525043488 = 4.858728448    boot/grub/grub.cfg                             1
   3.055664062 = 3.280994304    boot/initrd.img-2.6.38-8-generic               2
   4.523906708 = 4.857507840    boot/vmlinuz-2.6.38-8-generic                  1
   3.055664062 = 3.280994304    initrd.img                                     2
   4.523906708 = 4.857507840    vmlinuz                                        1

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
--------------------------------------------------------------------------------

================================ sdd2/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
--------------------------------------------------------------------------------

=========================== sdd7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 2ce4f805e4f7cf58
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 52dcd1d0dcd1af0b
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sde1)" {
    insmod ntfs
    set root=(hd4,1)
    search --no-floppy --fs-uuid --set ce2cee5b2cee3e59
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdd7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=05aa68b2-b685-4729-886f-c5a165108412 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=68b92ef6-f0d5-45fd-b870-0ffed1a88600 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdd7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 202.645410061 = 217.588852224  boot/grub/core.img                             1
 202.645497799 = 217.588946432  boot/grub/grub.cfg                             1
 197.805753231 = 212.392310272  boot/initrd.img-2.6.31-14-generic              1
 197.790223598 = 212.375635456  boot/vmlinuz-2.6.31-14-generic                 1
 197.805753231 = 212.392310272  initrd.img                                     1
 197.790223598 = 212.375635456  vmlinuz                                        1

=========================== sde5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd4,5)'
search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
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
set root='(hd4,5)'
search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
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
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd4,5)'
    search --no-floppy --fs-uuid --set 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 52dcd1d0dcd1af0b
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set ce2cee5b2cee3e59
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" {
    insmod ntfs
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set 2ce4f805e4f7cf58
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdd7)" {
    insmod ext2
    set root='(hd3,7)'
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdd7)" {
    insmod ext2
    set root='(hd3,7)'
    search --no-floppy --fs-uuid --set 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sde5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde5 during installation
UUID=148f93b4-1449-4b39-97d3-3d451dbc869f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde6 during installation
UUID=56a65c81-5b45-4c58-9918-876154604fda none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sde5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  46.664646149 = 50.105782272   boot/grub/core.img                             1
  48.018348694 = 51.559309312   boot/grub/grub.cfg                             1
  46.672069550 = 50.113753088   boot/initrd.img-2.6.32-24-generic              1
  46.888523102 = 50.346168320   boot/vmlinuz-2.6.32-24-generic                 1
  46.672069550 = 50.113753088   initrd.img                                     1
  46.888523102 = 50.346168320   vmlinuz                                        1

=============================== sde7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde7 during installation
UUID=557db2e6-2e9b-4ba8-977c-48ccca784083 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde8 during installation
UUID=ed279151-e14b-4fb8-85fe-11157957f9d8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=========================== sde9/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos9)'
search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos9)'
search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=90bb4ebe-f179-42b2-a3fc-5714f700370d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=90bb4ebe-f179-42b2-a3fc-5714f700370d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos9)'
    search --no-floppy --fs-uuid --set=root 90bb4ebe-f179-42b2-a3fc-5714f700370d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 52DCD1D0DCD1AF0B
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d1ef853-708e-43c6-88b5-1a6ab8ba43de
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=9d1ef853-708e-43c6-88b5-1a6ab8ba43de ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root CE2CEE5B2CEE3E59
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdd2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root 2CE4F805E4F7CF58
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdd7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos7)'
    search --no-floppy --fs-uuid --set=root 05aa68b2-b685-4729-886f-c5a165108412
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=05aa68b2-b685-4729-886f-c5a165108412 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sde5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos5)'
    search --no-floppy --fs-uuid --set=root 148f93b4-1449-4b39-97d3-3d451dbc869f
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=148f93b4-1449-4b39-97d3-3d451dbc869f ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sde9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde9 during installation
UUID=90bb4ebe-f179-42b2-a3fc-5714f700370d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde10 during installation
#UUID=76f998dc-6634-48c3-bf4d-bf220d0cfd1b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sde9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 195.532978058 = 209.951936512  boot/grub/core.img                             1
 149.535785675 = 160.562827264  boot/grub/grub.cfg                             1
  83.687500000 = 89.858768896   boot/initrd.img-2.6.38-8-generic               3
 195.531253815 = 209.950085120  boot/vmlinuz-2.6.38-8-generic                  1
  83.687500000 = 89.858768896   initrd.img                                     3
 195.531253815 = 209.950085120  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  1f 00 7e 00 73 f0 00 3c  00 13 f9 80 00 e7 bb c0  |..~.s..<........|
00000010  7c 00 1e 00 3f 00 3e 00  73 f8 00 3c 00 33 f1 87  ||...?.>.s..<.3..|
00000020  80 e3 3b 7f e0 f8 0e 0f  80 ff 00 3e 00 43 f8 00  |..;........>.C..|
00000030  3c 00 33 f1 87 00 f0 3b  f8 cc 9f 1f 80 ff 00 3e  |<.3....;.......>|
00000040  00 03 fc 00 3e 00 03 e0  00 00 e0 39 ff cd ff 3e  |....>......9...>|
00000050  f0 f8 00 2f 03 01 fe 60  3e 00 03 ef 00 0f e0 7b  |.../...`>......{|
00000060  7f dc ff 7c 20 f0 00 3f  03 00 7e 60 1c 00 03 ff  |...| ..?..~`....|
00000070  83 99 f8 ff 7f f8 7e f8  00 60 00 3f 03 00 7f e0  |......~..`.?....|
00000080  d8 00 03 df 87 f8 81 ff  39 f8 7f e1 00 c0 00 77  |........9......w|
00000090  03 00 3f e0 f0 00 03 df  83 d0 c1 f7 39 f1 ff c1  |..?.........9...|
000000a0  c0 00 00 7f 67 80 00 3b  e1 e0 01 83 cf 80 81 c1  |....g..;........|
000000b0  ff 7d f3 ff f0 c0 00 00  67 80 00 39 e1 c0 1f 83  |.}......g..9....|
000000c0  ff 80 00 c3 ff 7c e7 83  fc e0 00 00 77 86 00 7c  |.....|......w..||
000000d0  e1 91 99 01 bf 80 00 c1  fe 7c 07 03 fe e0 00 00  |.........|......|
000000e0  77 8e 12 1f f1 81 80 00  3f c0 00 c1 de 6e 07 03  |w.......?....n..|
000000f0  ff c0 60 00 67 80 3f 1f  ff 00 00 00 3f c0 01 e0  |..`.g.?.....?...|
00000100  fe ee 0f 03 ff c0 c0 00  23 c0 7f ff ff 80 00 00  |........#.......|
00000110  3d e0 0f c0 df ee 0f 01  cf c0 00 00 63 e0 7f fc  |=...........c...|
00000120  7f 86 00 7f 00 3d f8 7f  03 df 8e 0e 01 ee 40 00  |.....=........@.|
00000130  00 61 f1 ff f8 3f 8c 00  03 81 f8 7f c7 9f 0c 1e  |.a...?..........|
00000140  05 ff 70 00 00 61 ff 80  3c 1f 8c 00 03 81 f0 7b  |..p..a..<......{|
00000150  ef 0c 00 1e 01 ff f8 00  00 40 ff 00 0e 03 8c 00  |.........@......|
00000160  03 81 b0 3c 4f 00 00 3c  01 f9 f8 80 00 c0 ff 00  |...<O..<........|
00000170  07 63 80 00 00 38 00 1c  6f f0 00 7c 01 f8 f8 00  |.c...8..o..|....|
00000180  01 c0 7f 80 00 e1 80 00  00 3c 00 09 fe fc 00 38  |.........<.....8|
00000190  05 f7 f8 00 01 c0 3f 80  0c 41 80 00 0c 38 e0 00  |......?..A...8..|
000001a0  fe 7c 00 6c 38 07 c3 98  00 03 81 ff e0 01 c1 c0  |.|.l8...........|
000001b0  00 0e 30 60 40 1f 8c 00  78 06 03 f0 00 07 00 20  |..0`@...x...... |
000001c0  21 00 83 62 cc 56 02 00  00 00 00 68 d1 00 00 62  |!..b.V.....h...b|
000001d0  cd 56 05 fe ff ff 02 68  d1 00 00 f8 3d 00 00 00  |.V.....h....=...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdd3

00000000  55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  |UUUUUUUUUUUUUUUU|
*
000001b0  55 55 55 55 55 55 55 55  55 55 55 55 55 55 00 01  |UUUUUUUUUUUUUU..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 e6 9a 39 06 00 fe  |............9...|
000001d0  ff ff 05 fe ff ff e8 9a  39 06 a6 29 2a 06 00 00  |........9..)*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sde2

00000000  77 09 71 09 c3 08 ba 08  27 08 22 08 9f 07 93 07  |w.q.....'.".....|
00000010  13 07 0a 07 c0 06 b7 06  65 06 57 06 1e 06 11 06  |........e.W.....|
00000020  fe 05 f1 05 e4 05 d6 05  de 05 cf 05 e4 05 d7 05  |................|
00000030  d7 05 cf 05 d6 05 cc 05  db 05 d4 05 e3 05 dc 05  |................|
00000040  f7 05 ef 05 ef 05 e6 05  fe 05 f2 05 0f 06 02 06  |................|
00000050  1a 06 0e 06 24 06 16 06  37 06 29 06 11 06 02 06  |....$...7.).....|
00000060  f9 05 e9 05 be 05 af 05  43 05 38 05 ed 04 e7 04  |........C.8.....|
00000070  59 04 51 04 c6 03 c3 03  48 03 46 03 92 02 91 02  |Y.Q.....H.F.....|
00000080  11 02 0e 02 91 01 8e 01  0b 01 0a 01 ac 00 aa 00  |................|
00000090  3f 00 3e 00 09 00 04 00  ca ff c2 ff a2 ff a1 ff  |?.>.............|
000000a0  b1 ff af ff ac ff af ff  dc ff dc ff e7 ff e9 ff  |................|
000000b0  0e 00 0e 00 74 00 76 00  b2 00 b2 00 25 01 2a 01  |....t.v.....%.*.|
000000c0  a1 01 a1 01 26 02 22 02  cc 02 c2 02 5b 03 51 03  |....&.".....[.Q.|
000000d0  ec 03 e4 03 71 04 6a 04  d8 04 d3 04 33 05 2b 05  |....q.j.....3.+.|
000000e0  6e 05 68 05 93 05 8e 05  b3 05 ae 05 bc 05 b7 05  |n.h.............|
000000f0  c4 05 c1 05 b9 05 b1 05  bf 05 b6 05 b7 05 ae 05  |................|
00000100  bc 05 b6 05 db 05 d6 05  1a 06 16 06 92 06 88 06  |................|
00000110  18 07 10 07 cf 07 c4 07  a0 08 95 08 49 09 3c 09  |............I.<.|
00000120  15 0a 0a 0a b0 0a a2 0a  43 0b 38 0b ae 0b a6 0b  |........C.8.....|
00000130  e2 0b d5 0b 09 0c fd 0b  22 0c 17 0c 1f 0c 12 0c  |........".......|
00000140  18 0c 0f 0c fd 0b f1 0b  09 0c fa 0b ed 0b e1 0b  |................|
00000150  ac 0b 9e 0b 79 0b 6b 0b  09 0b fe 0a b0 0a a3 0a  |....y.k.........|
00000160  52 0a 47 0a fa 09 e9 09  b6 09 a6 09 7c 09 69 09  |R.G.........|.i.|
00000170  53 09 41 09 46 09 39 09  3c 09 2e 09 4b 09 40 09  |S.A.F.9.<...K.@.|
00000180  4c 09 41 09 50 09 44 09  61 09 54 09 4e 09 44 09  |L.A.P.D.a.T.N.D.|
00000190  53 09 49 09 2d 09 25 09  0e 09 08 09 db 08 d0 08  |S.I.-.%.........|
000001a0  95 08 8d 08 75 08 6f 08  1f 08 1a 08 e6 07 df 07  |....u.o.........|
000001b0  8c 07 84 07 28 07 21 07  a3 06 a2 06 07 06 00 fe  |....(.!.........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 62 da fb 00 00 fe  |..........b.....|
000001d0  ff ff 05 fe ff ff 02 b0  67 16 00 d8 e0 00 00 00  |........g.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-05-31
If you changed partition type you have to do that as part of your reinstall. There may be some ways to change ext2 to ext3 and then to ext4, but it is not just changing type with gparted. Normally reformating erases all data but the ext2, ext3, & ext4 are the same basic file system with features added.

You also have grub installed to a windows boot sector damaging windows. Windows has to have its boot code in the windows partition boot sector.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Also check for /boot/grub in addition to /Boot

---

