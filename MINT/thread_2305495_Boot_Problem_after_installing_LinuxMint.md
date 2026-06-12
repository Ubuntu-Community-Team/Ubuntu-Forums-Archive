---
title: "Boot Problem after installing LinuxMint"
date: 2015-12-06
forum: MINT
---

### Post by jrgen5 on 2015-12-06
Hello,
i've got a problem after installing Linux Mint on my computer, now when i try to restart the computer i can't start it with windows 10. I've used bootinfoscript but i don't know what to do with the result. Can somebody help me please. (Windows 10 is installed on the sdb1 drive.)
Here's the result :
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17.2 Rafaela
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 Köpfe, 63 Sektoren/Spur, 243201 Zylinder, zusammen 3907029168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,028,094 3,907,024,064 3,905,995,971   f W95 Extended (LBA)
/dev/sda5         615,434,148 1,859,025,734 1,243,591,587   7 NTFS / exFAT / HPFS
/dev/sda6       1,859,025,798 3,907,024,064 2,047,998,267   7 NTFS / exFAT / HPFS
/dev/sda7           1,028,096    65,026,047    63,997,952  82 Linux swap / Solaris
/dev/sda8          65,028,096   129,026,047    63,997,952  83 Linux
/dev/sda9         129,028,096   615,432,191   486,404,096  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 512.1 GB, 512110190592 bytes
255 Köpfe, 63 Sektoren/Spur, 62260 Zylinder, zusammen 1000215216 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,000,212,479 1,000,210,432   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3CE2D33BE2D2F7DA                       ntfs       System Reserved SSD
/dev/sda5        01D1302CFD6C9120                       ntfs       BackupSSD
/dev/sda6        01D1302D0097E070                       ntfs       Datenrest
/dev/sda7        31298143-9192-4c41-8833-f22dccbd3601   swap       
/dev/sda8        824a11c5-012d-41a5-a521-b13958c0cfad   ext4       
/dev/sda9        5c4d9ad6-a2a9-4d06-b69b-12f0561c42ef   ext4       
/dev/sdb1        9CFCD506FCD4DB98                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)
/dev/sda9        /home                    ext4       (rw)
/dev/sdb1        /media/knoppek/9CFCD506FCD4DB98 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  824a11c5-012d-41a5-a521-b13958c0cfad
else
  search --no-floppy --fs-uuid --set=root 824a11c5-012d-41a5-a521-b13958c0cfad
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=de_DE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'Linux Mint 17.2 Cinnamon 64-bit' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-824a11c5-012d-41a5-a521-b13958c0cfad' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  824a11c5-012d-41a5-a521-b13958c0cfad
    else
      search --no-floppy --fs-uuid --set=root 824a11c5-012d-41a5-a521-b13958c0cfad
    fi
    linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=824a11c5-012d-41a5-a521-b13958c0cfad ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-38-generic
}
submenu 'Erweiterte Optionen für Linux Mint 17.2 Cinnamon 64-bit' $menuentry_id_option 'gnulinux-advanced-824a11c5-012d-41a5-a521-b13958c0cfad' {
    menuentry 'Linux Mint 17.2 Cinnamon 64-bit, mit Linux 3.16.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-38-generic-advanced-824a11c5-012d-41a5-a521-b13958c0cfad' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  824a11c5-012d-41a5-a521-b13958c0cfad
        else
          search --no-floppy --fs-uuid --set=root 824a11c5-012d-41a5-a521-b13958c0cfad
        fi
        echo    'Linux 3.16.0-38-generic wird geladen &#8230;'
        linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=824a11c5-012d-41a5-a521-b13958c0cfad ro  quiet splash $vt_handoff
        echo    'Initiale Ramdisk wird geladen &#8230;'
        initrd    /boot/initrd.img-3.16.0-38-generic
    }
    menuentry 'Linux Mint 17.2 Cinnamon 64-bit, with Linux 3.16.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-38-generic-recovery-824a11c5-012d-41a5-a521-b13958c0cfad' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  824a11c5-012d-41a5-a521-b13958c0cfad
        else
          search --no-floppy --fs-uuid --set=root 824a11c5-012d-41a5-a521-b13958c0cfad
        fi
        echo    'Linux 3.16.0-38-generic wird geladen &#8230;'
        linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=824a11c5-012d-41a5-a521-b13958c0cfad ro recovery nomodeset 
        echo    'Initiale Ramdisk wird geladen &#8230;'
        initrd    /boot/initrd.img-3.16.0-38-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  824a11c5-012d-41a5-a521-b13958c0cfad
    else
      search --no-floppy --fs-uuid --set=root 824a11c5-012d-41a5-a521-b13958c0cfad
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  824a11c5-012d-41a5-a521-b13958c0cfad
    else
      search --no-floppy --fs-uuid --set=root 824a11c5-012d-41a5-a521-b13958c0cfad
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (auf /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-3CE2D33BE2D2F7DA' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3CE2D33BE2D2F7DA
    else
      search --no-floppy --fs-uuid --set=root 3CE2D33BE2D2F7DA
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=824a11c5-012d-41a5-a521-b13958c0cfad /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=5c4d9ad6-a2a9-4d06-b69b-12f0561c42ef /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=31298143-9192-4c41-8833-f22dccbd3601 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-fJhxQulp/Tmp_Log: Datei oder Verzeichnis nicht gefunden
  No volume groups found
```

---

### Post by yancek on 2015-12-06
You show only one entry for windows which is sda1 vista/7 and also shows as Recovery.  That doesn't seem right.  The first thing I would suggest is to run:  sudo update-grub from a terminal and watch the output.  You have entries indicating you have xp, vista/7 and a number of ntfs partitions.  How did you install windows 10 on the second drive?  Did you do that your self?   Was it an upgrade of an earlier release?

Your bootinfoscript also shows windows code in the MBR of sdb which is the windows 10 drive.  Have you tried setting that drive to first boot priority in the BIOS?

---

### Post by howefield on 2015-12-06
Thread moved to the "*MINT*" forum and code tags added.

---

