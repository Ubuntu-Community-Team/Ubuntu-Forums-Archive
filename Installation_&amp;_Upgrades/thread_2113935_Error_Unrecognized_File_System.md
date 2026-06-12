---
title: "Error: Unrecognized File System"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by cojacfar on 2013-02-08
I just installed Ubuntu 12.10 with the Live Disk alongside my previous install of Windows 7. My partitions might be kind of messy because I tried to install several times, but kept getting this problem. 

Basically, after GRUB 2 boots up if I select Windows 7 OR Ubuntu I get 

 ```
Error: Unknown Filesystem
Press any key to continue 
```It eventually actually boots to whichever OS I choose.

Sometimes however I get 
  ```
Error: Unknown Filesystem
Error: Attempt to read or write outside of disk 'hd1'
```

If I get that message, I have to hard restart my computer as it will not continue past.

This is the boot script results.txt

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Windows is installed in the MBR of /dev/sdb.

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   250,066,943   249,860,096   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   771,971,071   771,969,024   7 NTFS / exFAT / HPFS
/dev/sdb2         771,971,072   812,931,071    40,960,000   7 NTFS / exFAT / HPFS
/dev/sdb3         812,933,118   976,771,071   163,837,954   5 Extended
/dev/sdb5         812,933,120   904,852,851    91,919,732  83 Linux
/dev/sdb6         960,090,112   976,771,071    16,680,960  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        987AA3D87AA3B204                       ntfs       System Reserved
/dev/sda2        38D0A6E8D0A6AB96                       ntfs       
/dev/sdb1        ACB06A41B06A125E                       ntfs       
/dev/sdb2        B034D84F34D81A64                       ntfs       LINUX BOOT
/dev/sdb5        3e118f74-f229-45a1-bcf3-5f59a37d0be4   ext4       
/dev/sdb6        11a3e463-c58a-4f73-9abf-ec0066ce35f1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='hd1,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4
else
  search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4
    else
      search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4
    fi
    linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-23-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {
    menuentry 'Ubuntu, with Linux 3.5.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-23-generic-advanced-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4
        else
          search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4
        fi
        echo    'Loading Linux 3.5.0-23-generic ...'
        linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-23-generic-recovery-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4
        else
          search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4
        fi
        echo    'Loading Linux 3.5.0-23-generic ...'
        linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4
        else
          search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4
        else
          search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4
    else
      search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4
    else
      search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-987AA3D87AA3B204' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  987AA3D87AA3B204
    else
      search --no-floppy --fs-uuid --set=root 987AA3D87AA3B204
    fi
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-ACB06A41B06A125E' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  ACB06A41B06A125E
    else
      search --no-floppy --fs-uuid --set=root ACB06A41B06A125E
    fi
    chainloader +1
}
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=11a3e463-c58a-4f73-9abf-ec0066ce35f1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.5.0-17-generic               3
               =                boot/initrd.img-3.5.0-23-generic               1
               =                boot/vmlinuz-3.5.0-17-generic                  2
               =                boot/vmlinuz-3.5.0-23-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by cojacfar on 2013-02-08
Attempted to do boot repair. For some reason I can't set it to use my SSD (sda, 128GB) to be the boot from? I guess this doesn't matter.

Anyways, changed my platter drive to be the one it starts up to. Did not work. Went into Grub-rescue. This is the boot report it gave:


```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]   ============================= Boot Info Summary: ===============================   => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and uses an      embedded config file:          ---------------------------------------------------------------------------     search.fs_uuid 3e118f74-f229-45a1-bcf3-5f59a37d0be4 root hd1,msdos5       set prefix=($root)/boot/grub     ---------------------------------------------------------------------------     -----.  => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and looks      in partition 1 for (,msdos5)/boot/grub.  sda1: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows 7/2008: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:        /bootmgr /Boot/BCD  sda2: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows 7/2008: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows 7     Boot files:        /Windows/System32/winload.exe  sdb1: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows 7/2008: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows 7     Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe  sdb2: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows 7/2008: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:          sdb3: __________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:   sdb5: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:  Ubuntu 12.10      Boot files:        /boot/grub/grub.cfg /etc/fstab                         /boot/grub/i386-pc/core.img  sdb6: __________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:   ============================ Drive/Partition Info: =============================  Drive: sda _____________________________________________________________________  Disk /dev/sda: 128.0 GB, 128035676160 bytes 255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS /dev/sda2             206,848   250,066,943   249,860,096   7 NTFS / exFAT / HPFS   Drive: sdb _____________________________________________________________________  Disk /dev/sdb: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sdb1    *          2,048   771,971,071   771,969,024   7 NTFS / exFAT / HPFS /dev/sdb2         771,971,072   812,931,071    40,960,000   7 NTFS / exFAT / HPFS /dev/sdb3         812,933,118   976,771,071   163,837,954   5 Extended /dev/sdb5         812,933,120   904,852,851    91,919,732  83 Linux /dev/sdb6         960,090,112   976,771,071    16,680,960  82 Linux swap / Solaris   "blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/loop0                                              squashfs    /dev/sda1        987AA3D87AA3B204                       ntfs       System Reserved /dev/sda2        38D0A6E8D0A6AB96                       ntfs        /dev/sdb1        ACB06A41B06A125E                       ntfs        /dev/sdb2        B034D84F34D81A64                       ntfs       LINUX BOOT /dev/sdb5        3e118f74-f229-45a1-bcf3-5f59a37d0be4   ext4        /dev/sdb6        11a3e463-c58a-4f73-9abf-ec0066ce35f1   swap        /dev/sr0                                                iso9660    Ubuntu 12.10 i386  ================================ Mount points: =================================  Device           Mount_Point              Type       Options  /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sr0         /cdrom                   iso9660    (ro,noatime)   =========================== sdb5/boot/grub/grub.cfg: ===========================  -------------------------------------------------------------------------------- # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0"  if [ x"${feature_menuentry_id}" = xy ]; then   menuentry_id_option="--id" else   menuentry_id_option="" fi  export menuentry_id_option  if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   if [ x$feature_all_video_module = xy ]; then     insmod all_video   else     insmod efi_gop     insmod efi_uga     insmod ieee1275_fb     insmod vbe     insmod vga     insmod video_bochs     insmod video_cirrus   fi }  if [ x$feature_default_font_path = xy ] ; then    font=unicode else insmod part_msdos insmod ext2 set root='hd1,msdos5' if [ x$feature_platform_search_hint = xy ]; then   search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4 else   search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4 fi     font="/usr/share/grub/unicode.pf2" fi  if loadfont $font ; then   set gfxmode=auto   load_video   insmod gfxterm   set locale_dir=$prefix/locale   set lang=en_US   insmod gettext fi terminal_output gfxterm if [ "${recordfail}" = 1 ]; then   set timeout=10 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray if background_color 44,0,30; then   clear fi ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### function gfxmode {     set gfxpayload="${1}"     if [ "${1}" = "keep" ]; then         set vt_handoff=vt.handoff=7     else         set vt_handoff=     fi } if [ "${recordfail}" != 1 ]; then   if [ -e ${prefix}/gfxblacklist.txt ]; then     if hwmatch ${prefix}/gfxblacklist.txt 3; then       if [ ${match} = 0 ]; then         set linux_gfx_mode=keep       else         set linux_gfx_mode=text       fi     else       set linux_gfx_mode=text     fi   else     set linux_gfx_mode=keep   fi else   set linux_gfx_mode=text fi export linux_gfx_mode if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-3e118f74-f229-45a1-bcf3-5f59a37d0be4' { recordfail     gfxmode $linux_gfx_mode     insmod gzio     insmod part_msdos     insmod ext2     set root='hd1,msdos5'     if [ x$feature_platform_search_hint = xy ]; then       search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4     else       search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4     fi     linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 ro   quiet splash $vt_handoff     initrd    /boot/initrd.img-3.5.0-23-generic } submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {     menuentry 'Ubuntu, with Linux 3.5.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-23-generic-advanced-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {     recordfail         gfxmode $linux_gfx_mode         insmod gzio         insmod part_msdos         insmod ext2         set root='hd1,msdos5'         if [ x$feature_platform_search_hint = xy ]; then           search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4         else           search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4         fi         echo    'Loading Linux 3.5.0-23-generic ...'         linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 ro   quiet splash $vt_handoff         echo    'Loading initial ramdisk ...'         initrd    /boot/initrd.img-3.5.0-23-generic     }     menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-23-generic-recovery-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {     recordfail         insmod gzio         insmod part_msdos         insmod ext2         set root='hd1,msdos5'         if [ x$feature_platform_search_hint = xy ]; then           search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4         else           search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4         fi         echo    'Loading Linux 3.5.0-23-generic ...'         linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 ro recovery nomodeset          echo    'Loading initial ramdisk ...'         initrd    /boot/initrd.img-3.5.0-23-generic     }     menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {     recordfail         gfxmode $linux_gfx_mode         insmod gzio         insmod part_msdos         insmod ext2         set root='hd1,msdos5'         if [ x$feature_platform_search_hint = xy ]; then           search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4         else           search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4         fi         echo    'Loading Linux 3.5.0-17-generic ...'         linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 ro   quiet splash $vt_handoff         echo    'Loading initial ramdisk ...'         initrd    /boot/initrd.img-3.5.0-17-generic     }     menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-3e118f74-f229-45a1-bcf3-5f59a37d0be4' {     recordfail         insmod gzio         insmod part_msdos         insmod ext2         set root='hd1,msdos5'         if [ x$feature_platform_search_hint = xy ]; then           search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4         else           search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4         fi         echo    'Loading Linux 3.5.0-17-generic ...'         linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 ro recovery nomodeset          echo    'Loading initial ramdisk ...'         initrd    /boot/initrd.img-3.5.0-17-generic     } }  ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_linux_xen ###  ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" {     insmod part_msdos     insmod ext2     set root='hd1,msdos5'     if [ x$feature_platform_search_hint = xy ]; then       search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4     else       search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4     fi     linux16    /boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" {     insmod part_msdos     insmod ext2     set root='hd1,msdos5'     if [ x$feature_platform_search_hint = xy ]; then       search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3e118f74-f229-45a1-bcf3-5f59a37d0be4     else       search --no-floppy --fs-uuid --set=root 3e118f74-f229-45a1-bcf3-5f59a37d0be4     fi     linux16    /boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-987AA3D87AA3B204' {     insmod part_msdos     insmod ntfs     set root='hd0,msdos1'     if [ x$feature_platform_search_hint = xy ]; then       search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  987AA3D87AA3B204     else       search --no-floppy --fs-uuid --set=root 987AA3D87AA3B204     fi     chainloader +1 } menuentry 'Windows 7 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-ACB06A41B06A125E' {     insmod part_msdos     insmod ntfs     set root='hd1,msdos1'     if [ x$feature_platform_search_hint = xy ]; then       search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  ACB06A41B06A125E     else       search --no-floppy --fs-uuid --set=root ACB06A41B06A125E     fi     chainloader +1 } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/30_uefi-firmware ### ### END /etc/grub.d/30_uefi-firmware ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  ${config_directory}/custom.cfg ]; then   source ${config_directory}/custom.cfg elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ### --------------------------------------------------------------------------------  =============================== sdb5/etc/fstab: ================================  -------------------------------------------------------------------------------- # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> # / was on /dev/sdb5 during installation UUID=3e118f74-f229-45a1-bcf3-5f59a37d0be4 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sdb6 during installation UUID=11a3e463-c58a-4f73-9abf-ec0066ce35f1 none            swap    sw              0       0 --------------------------------------------------------------------------------  =================== sdb5: Location of files loaded by Grub: ====================             GiB - GB             File                                 Fragment(s)   399.777599335 = 429.257928704  boot/grub/grub.cfg                             1  399.828151703 = 429.312208896  boot/grub/i386-pc/core.img                     1  388.207031250 = 416.834125824  boot/vmlinuz-3.5.0-17-generic                  2  389.161071777 = 417.858519040  boot/vmlinuz-3.5.0-23-generic                  1  389.161071777 = 417.858519040  vmlinuz                                        1  389.161071777 = 417.858519040  vmlinuz.old                                    1  388.986682892 = 417.671270400  boot/initrd.img-3.5.0-17-generic               3  390.049186707 = 418.812125184  boot/initrd.img-3.5.0-23-generic               2  390.049186707 = 418.812125184  initrd.img                                     2  =============================== StdErr Messages: ===============================  cat: write error: Broken pipe cat: write error: Broken pipe File descriptor 8 (/proc/6632/mounts) leaked on lvscan invocation. Parent PID 19657: bash   No volume groups found  ADDITIONAL INFORMATION : =================== log of boot-repair 2013-02-09__01h16 =================== boot-repair version : 3.197~ppa30~quantal boot-sav version : 3.197~ppa30~quantal glade2script version : 3.2.2~ppa45~quantal boot-sav-extra version : 3.197~ppa30~quantal boot-repair is executed in live-session (Ubuntu 12.10, quantal, Ubuntu, i686) CPU op-mode(s):        32-bit, 64-bit file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity 2 /boot folders exist in /mnt/boot-sav/sda1 and may disturb os-prober, we rename boot into oldbooot  =================== os-prober: /dev/sda1:Windows 7 (loader):Windows:chain /dev/sdb1:Windows 7 (loader):Windows1:chain /dev/sdb5:Ubuntu 12.10 (12.10):Ubuntu:linux  =================== blkid: /dev/loop0: TYPE="squashfs" /dev/sda1: LABEL="System Reserved" UUID="987AA3D87AA3B204" TYPE="ntfs" /dev/sda2: UUID="38D0A6E8D0A6AB96" TYPE="ntfs" /dev/sr0: LABEL="Ubuntu 12.10 i386" TYPE="iso9660" /dev/sdb1: UUID="ACB06A41B06A125E" TYPE="ntfs" /dev/sdb2: LABEL="LINUX BOOT" UUID="B034D84F34D81A64" TYPE="ntfs" /dev/sdb5: UUID="3e118f74-f229-45a1-bcf3-5f59a37d0be4" TYPE="ext4" /dev/sdb6: UUID="11a3e463-c58a-4f73-9abf-ec0066ce35f1" TYPE="swap"   2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.  Windows not detected by os-prober on sda2. Warning: extended partition does not start at a cylinder boundary. DOS and Linux will interpret the contents differently.   =================== sdb5/etc/default/grub :  # If you change this file, run 'update-grub' afterwards to update # /boot/grub/grub.cfg. # For full documentation of the options in this file, see: #   info -f grub -n 'Simple configuration'  GRUB_DEFAULT=0 #GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=10 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX=""  # Uncomment to enable BadRAM filtering, modify to suit your needs # This works with Linux (no patch required) and with any kernel that obtains # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...) #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"  # Uncomment to disable graphical terminal (grub-pc only) #GRUB_TERMINAL=console  # The resolution used on graphical terminal # note that you can use only modes which your graphic card supports via VBE # you can see them in real GRUB with the command `vbeinfo' #GRUB_GFXMODE=640x480  # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux #GRUB_DISABLE_LINUX_UUID=true  # Uncomment to disable generation of recovery mode menu entries #GRUB_DISABLE_RECOVERY="true"  # Uncomment to get a beep at grub start #GRUB_INIT_TUNE="480 440 1"     =================== sdb5/etc/grub.d/ : drwxr-xr-x  2 root root    4096 Feb  8 22:13 grub.d total 72 -rwxr-xr-x 1 root root  7541 Oct 14 17:37 00_header -rwxr-xr-x 1 root root  5488 Oct  4 09:30 05_debian_theme -rwxr-xr-x 1 root root 10891 Oct 14 17:37 10_linux -rwxr-xr-x 1 root root 10258 Oct 14 17:37 20_linux_xen -rwxr-xr-x 1 root root  1688 Oct 11 14:10 20_memtest86+ -rwxr-xr-x 1 root root 10976 Oct 14 17:37 30_os-prober -rwxr-xr-x 1 root root  1426 Oct 14 17:37 30_uefi-firmware -rwxr-xr-x 1 root root   214 Oct 14 17:37 40_custom -rwxr-xr-x 1 root root   216 Oct 14 17:37 41_custom -rw-r--r-- 1 root root   483 Oct 14 17:37 README    =================== sdb5recordfail=1/grub/grubenv : recordfail=1    =================== UEFI/Legacy mode: This live-session is not EFI-compatible. SecureBoot maybe enabled.   =================== PARTITIONS & DISKS: sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1. sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2. sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1. sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb2. sdb5    : sdb,    not-sepboot,    grubenv-ng    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb5.  sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes   =================== parted -l:  Model: ATA KINGSTON SV200S3 (scsi) Disk /dev/sda: 128GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End    Size   Type     File system  Flags 1      1049kB  106MB  105MB  primary  ntfs         boot 2      106MB   128GB  128GB  primary  ntfs   Model: ATA Hitachi HDP72505 (scsi) Disk /dev/sdb: 500GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End    Size    Type      File system     Flags 1      1049kB  395GB  395GB   primary   ntfs            boot 2      395GB   416GB  21.0GB  primary   ntfs 3      416GB   500GB  83.9GB  extended 5      416GB   463GB  47.1GB  logical   ext4 6      492GB   500GB  8541MB  logical   linux-swap(v1)                                                                               Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.                                                                             Error: Can't have a partition outside the disk!  =================== parted -lm:  BYT; /dev/sda:128GB:scsi:512:512:msdos:ATA KINGSTON SV200S3; 1:1049kB:106MB:105MB:ntfs::boot; 2:106MB:128GB:128GB:ntfs::;  BYT; /dev/sdb:500GB:scsi:512:512:msdos:ATA Hitachi HDP72505; 1:1049kB:395GB:395GB:ntfs::boot; 2:395GB:416GB:21.0GB:ntfs::; 3:416GB:500GB:83.9GB:::; 5:416GB:463GB:47.1GB:ext4::; 6:492GB:500GB:8541MB:linux-swap(v1)::;                                                                              Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.                                                                             Error: Can't have a partition outside the disk!   =================== mount: /cow on / type overlayfs (rw) proc on /proc type proc (rw,noexec,nosuid,nodev) sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) udev on /dev type devtmpfs (rw,mode=0755) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) /dev/sr0 on /cdrom type iso9660 (ro,noatime) /dev/loop0 on /rofs type squashfs (ro,noatime) none on /sys/fs/fuse/connections type fusectl (rw) none on /sys/kernel/debug type debugfs (rw) none on /sys/kernel/security type securityfs (rw) tmpfs on /tmp type tmpfs (rw,nosuid,nodev) none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) none on /run/shm type tmpfs (rw,nosuid,nodev) none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu) /dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) /dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) /dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) /dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) /dev/sdb5 on /mnt/boot-sav/sdb5 type ext4 (rw)   =================== ls: /sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent /sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb5 sdb6 size slaves stat subsystem trace uevent /sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent /dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdb2 sdb3 sdb5 sdb6 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb vga_arbiter vhost-net zero ls /dev/mapper:  control  =================== hexdump -n512 -C /dev/sda1 00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....| 00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......| 00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................| 00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............| 00000040  f6 00 00 00 01 00 00 00  04 b2 a3 7a d8 a3 7a 98  |...........z..z.| 00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..| 00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N| 00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...| 00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......| 00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........| 000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..| 000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.| 000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............| 000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-| 000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..| 000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf| 00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..| 00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.| 00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...| 00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...| 00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.| 00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........| 00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......| 00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.| 00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A | 00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error | 000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM| 000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...| 000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr| 000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct| 000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re| 000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.| 00000200  =================== hexdump -n512 -C /dev/sda2 00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....| 00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..| 00000020  00 00 00 00 80 00 80 00  ff 8f e4 0e 00 00 00 00  |................| 00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................| 00000040  f6 00 00 00 01 00 00 00  96 ab a6 d0 e8 a6 d0 38  |...............8| 00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..| 00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N| 00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...| 00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......| 00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........| 000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..| 000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.| 000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............| 000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-| 000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..| 000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf| 00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..| 00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.| 00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...| 00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...| 00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.| 00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........| 00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......| 00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.| 00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A | 00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error | 000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM| 000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...| 000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr| 000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct| 000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re| 000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.| 00000200  =================== hexdump -n512 -C /dev/sdb1 00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....| 00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......| 00000020  00 00 00 00 80 00 80 00  ff 4f 03 2e 00 00 00 00  |.........O......| 00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................| 00000040  f6 00 00 00 01 00 00 00  5e 12 6a b0 41 6a b0 ac  |........^.j.Aj..| 00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..| 00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N| 00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...| 00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......| 00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........| 000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..| 000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.| 000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............| 000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-| 000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..| 000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf| 00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..| 00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.| 00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...| 00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...| 00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.| 00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........| 00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......| 00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.| 00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A | 00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error | 000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM| 000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...| 000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr| 000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct| 000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re| 000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.| 00000200  =================== hexdump -n512 -C /dev/sdb2 00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....| 00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 58 03 2e  |........?....X..| 00000020  00 00 00 00 80 00 80 00  ff ff 70 02 00 00 00 00  |..........p.....| 00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................| 00000040  f6 00 00 00 01 00 00 00  64 1a d8 34 4f d8 34 b0  |........d..4O.4.| 00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..| 00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N| 00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...| 00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......| 00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........| 000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..| 000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.| 000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............| 000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-| 000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..| 000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf| 00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..| 00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.| 00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...| 00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...| 00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.| 00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........| 00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......| 00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.| 00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A | 00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error | 000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM| 000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...| 000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr| 000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct| 000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re| 000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.| 00000200  =================== df -Th:  Filesystem     Type       Size  Used Avail Use% Mounted on /cow           overlayfs  4.0G  122M  3.9G   4% / udev           devtmpfs   4.0G   12K  4.0G   1% /dev tmpfs          tmpfs      1.6G  904K  1.6G   1% /run /dev/sr0       iso9660    754M  754M     0 100% /cdrom /dev/loop0     squashfs   723M  723M     0 100% /rofs tmpfs          tmpfs      4.0G   28K  4.0G   1% /tmp none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock none           tmpfs      4.0G   76K  4.0G   1% /run/shm none           tmpfs      100M   44K  100M   1% /run/user /dev/sda1      fuseblk    100M   30M   71M  30% /mnt/boot-sav/sda1 /dev/sda2      fuseblk    120G   79G   41G  67% /mnt/boot-sav/sda2 /dev/sdb1      fuseblk    369G  330G   39G  90% /mnt/boot-sav/sdb1 /dev/sdb2      fuseblk     20G   89M   20G   1% /mnt/boot-sav/sdb2 /dev/sdb5      ext4        44G  3.6G   38G   9% /mnt/boot-sav/sdb5  =================== fdisk -l:  Disk /dev/sda: 128.0 GB, 128035676160 bytes 255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0xf37f81a3  Device Boot      Start         End      Blocks   Id  System /dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT /dev/sda2          206848   250066943   124930048    7  HPFS/NTFS/exFAT  Disk /dev/sdb: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x29aedd09  Device Boot      Start         End      Blocks   Id  System /dev/sdb1   *        2048   771971071   385984512    7  HPFS/NTFS/exFAT /dev/sdb2       771971072   812931071    20480000    7  HPFS/NTFS/exFAT /dev/sdb3       812933118   976771071    81918977    5  Extended /dev/sdb5       812933120   904852851    45959866   83  Linux /dev/sdb6       960090112   976771071     8340480   82  Linux swap / Solaris   User choice: Is sdb (500GB) a removable disk? no Partition outside the disk detected.  =================== Recommended repair Recommended-Repair This setting will reinstall the grub2 of sdb5 into the MBRs of all disks (except USB without OS). Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot   Quantity of real Windows: 2  Reinstall the GRUB of sdb5 into all MBRs of disks with OS or not-USB grub-install (GRUB) 2.00-7ubuntu11,grub-install (GRUB) 2.  Reinstall the GRUB of sdb5 into the MBR of sda Installation finished. No error reported. grub-install /dev/sda: exit code of grub-install /dev/sda:0 grub-install (GRUB) 2.00-7ubuntu11,grub-install (GRUB) 2.  Reinstall the GRUB of sdb5 into the MBR of sdb Installation finished. No error reported. grub-install /dev/sdb: exit code of grub-install /dev/sdb:0  chroot /mnt/boot-sav/sdb5 update-grub Generating grub.cfg ... Found linux image: /boot/vmlinuz-3.5.0-23-generic Found initrd image: /boot/initrd.img-3.5.0-23-generic Found linux image: /boot/vmlinuz-3.5.0-17-generic Found initrd image: /boot/initrd.img-3.5.0-17-generic Found memtest86+ image: /boot/memtest86+.bin Found Windows 7 (loader) on /dev/sda1 Found Windows 7 (loader) on /dev/sdb1 Unhide GRUB boot menu in sdb5/boot/grub/grub.cfg  Boot successfully repaired.  You can now reboot your computer. Please do not forget to make your BIOS boot on sdb (500GB) disk! 
```EDIT: This paste is not playing well with CODE tagging. Here is a link to the paste bin: [http://paste.ubuntu.com/1631397/](http://paste.ubuntu.com/1631397/)  (Is there a better way to format this? <href> takes don't work [not surprising].)

---

### Post by cojacfar on 2013-02-09
Currently, I can boot into Windows/Ubuntu fine but randomly it does not work.

When it does work I still got 

> Attempting to read or write outside of disk 'hd0'
Attempting to read or write outside of disk 'hd0'
Attempting to read or write outside of disk 'hd0'
Attempting to read or write outside of disk 'hd0'
Stack Overflow

Then Ubuntu actually started, hah.

---

### Post by coffeecat on 2013-02-09
*Thread moved to **Installation & Upgrades**.*

.. at request of OP.

---

