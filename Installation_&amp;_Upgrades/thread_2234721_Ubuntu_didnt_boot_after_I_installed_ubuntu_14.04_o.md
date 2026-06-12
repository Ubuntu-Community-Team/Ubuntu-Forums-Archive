---
title: "Ubuntu didnt boot after I installed ubuntu 14.04 on windows 8"
date: 2014-07-16
forum: Installation &amp; Upgrades
---

### Post by ahmedo047 on 2014-07-16
Dear Ubuntu users,

I switched off/disable "Secure boot" and "Fast boot" choices from bios settings. And I installed ubuntu 14.04 on windows 8. I dont meet any error during installation. Unfortunately I don't get an option to choose between Windows 8 and Ubuntu 14.04. On start, I can only boot into  Windows. But I want to meet with Grub, which gives me the option of ubuntu and windows.


I will appreciate any help.

---

### Post by kc1di on 2014-07-16
Try running boot repair [found here.]("https://help.ubuntu.com/community/Boot-Repair") 
Pay close attention to the instructions it gives you and make sure you jot down the web page at the end so if it does not work we can look at the file.

---

### Post by ajgreeny on 2014-07-16
This could be a result of Wubi, which I assume is the way you attempted to install Ubuntu, now being no longer supported; I am actually surprised that you mnaged to install in that way as I did not think it was available in the 14.04 version now.

A proper full partitioned install will be much better and is the best answer for you, I believe.

---

### Post by ahmedo047 on 2014-07-16
I used "boot-repair CD". I saw a message stating that boot repair completed with errors. Therefore my problem is still unsolved :(

---

### Post by yancek on 2014-07-16
The boot repair software has an option to output a text file with the results.  If you selected that option it would be a good idea to post it.  If you did not select it, best run it again and then post it.  The information you have posted so far isn't enough for anyone to do more than guess at a possible solution.

---

### Post by ahmedo047 on 2014-07-17
**The boot repair output:**

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
     480983040 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 112 for .

sda1: __________________________________________________________________________

    File system:       vfat
     Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                        /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda2: __________________________________________________________________________

    File system:       ntfs
     Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
 /dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848     2,050,047     1,843,200 Windows Recovery Environment (Windows)
/dev/sda3       2,050,048     2,312,191       262,144 Microsoft Reserved Partition (Windows)
 /dev/sda4       2,312,192   475,246,591   472,934,400 Data partition (Windows/Linux)
/dev/sda5     480,983,040   480,985,087         2,048 BIOS Boot partition
/dev/sda6     783,718,400 1,911,560,191 1,127,841,792 Data partition (Windows/Linux)
 /dev/sda7   1,911,560,192 1,953,523,711    41,963,520 Windows Recovery Environment (Windows)
/dev/sda8     475,246,592   480,983,039     5,736,448 Swap partition (Linux)
/dev/sda9     480,985,088   783,718,399   302,733,312 Data partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
 /dev/sda1        366D-2A62                              vfat       SYSTEM
/dev/sda2        0E486D94486D7B7B                       ntfs       Recovery
/dev/sda4        1E06CA8A06CA61FF                       ntfs       OS
 /dev/sda6        5CE671B3E6718DD0                       ntfs       Data
/dev/sda7        C028742628741E1A                       ntfs       Restore
/dev/sda8        6ec268e6-4224-4857-a949-af61af634042   swap       
 /dev/sda9        1e1e883b-fa7b-413c-a7a2-6cb55cd09706   ext4       
/dev/sr0                                                iso9660    Ubuntu 14.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda9/boot/grub/grub.cfg: ===========================

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
insmod part_gpt
insmod ext2
set root='hd0,gpt9'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  1e1e883b-fa7b-413c-a7a2-6cb55cd09706
 else
  search --no-floppy --fs-uuid --set=root 1e1e883b-fa7b-413c-a7a2-6cb55cd09706
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
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
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
 menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-1e1e883b-fa7b-413c-a7a2-6cb55cd09706' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
     insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt9'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  1e1e883b-fa7b-413c-a7a2-6cb55cd09706
     else
      search --no-floppy --fs-uuid --set=root 1e1e883b-fa7b-413c-a7a2-6cb55cd09706
    fi
    linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=1e1e883b-fa7b-413c-a7a2-6cb55cd09706 ro  quiet splash $vt_handoff
     initrd    /boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-1e1e883b-fa7b-413c-a7a2-6cb55cd09706' {
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-1e1e883b-fa7b-413c-a7a2-6cb55cd09706' {
         recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  1e1e883b-fa7b-413c-a7a2-6cb55cd09706
        else
          search --no-floppy --fs-uuid --set=root 1e1e883b-fa7b-413c-a7a2-6cb55cd09706
         fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=1e1e883b-fa7b-413c-a7a2-6cb55cd09706 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
         initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-1e1e883b-fa7b-413c-a7a2-6cb55cd09706' {
         recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  1e1e883b-fa7b-413c-a7a2-6cb55cd09706
         else
          search --no-floppy --fs-uuid --set=root 1e1e883b-fa7b-413c-a7a2-6cb55cd09706
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=1e1e883b-fa7b-413c-a7a2-6cb55cd09706 ro recovery nomodeset 
         echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-1e1e883b-fa7b-413c-a7a2-6cb55cd09706' {
         recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  1e1e883b-fa7b-413c-a7a2-6cb55cd09706
        else
          search --no-floppy --fs-uuid --set=root 1e1e883b-fa7b-413c-a7a2-6cb55cd09706
         fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=1e1e883b-fa7b-413c-a7a2-6cb55cd09706 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
         initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-1e1e883b-fa7b-413c-a7a2-6cb55cd09706' {
         recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  1e1e883b-fa7b-413c-a7a2-6cb55cd09706
         else
          search --no-floppy --fs-uuid --set=root 1e1e883b-fa7b-413c-a7a2-6cb55cd09706
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=1e1e883b-fa7b-413c-a7a2-6cb55cd09706 ro recovery nomodeset 
         echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 366D-2A62
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
 search --fs-uuid --no-floppy --set=root 366D-2A62
chainloader (${root})/EFI/Boot/bootx64.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-0E486D94486D7B7B' {
     insmod part_gpt
    insmod ntfs
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0E486D94486D7B7B
     else
      search --no-floppy --fs-uuid --set=root 0E486D94486D7B7B
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 8 (loader) (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-1E06CA8A06CA61FF' {
     insmod part_gpt
    insmod ntfs
    set root='hd0,gpt4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  1E06CA8A06CA61FF
     else
      search --no-floppy --fs-uuid --set=root 1E06CA8A06CA61FF
    fi
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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
 #
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
 #
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=1e1e883b-fa7b-413c-a7a2-6cb55cd09706 /               ext4    errors=remount-ro 0       1
 # swap was on /dev/sda8 during installation
UUID=6ec268e6-4224-4857-a949-af61af634042 none            swap    sw              0       0
UUID=366D-2A62    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-v9t9noXS/Tmp_Log: No such file or directory
File descriptor 9 (/proc/6611/mounts) leaked on lvscan invocation. Parent PID 10934: bash
 File descriptor 63 (pipe:[55417]) leaked on lvscan invocation. Parent PID 10934: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-07-17__07h26 ===================
 boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64)
 ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
The disk contains an unclean file system (0, 0).
 Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
 read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /mnt/boot-sav/sda2
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
 Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
 mount /dev/sda2 : Error code 14
mount -r /dev/sda2 /mnt/boot-sav/sda2
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
 The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4
 The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
 Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda4 : Error code 14
mount -r /dev/sda4 /mnt/boot-sav/sda4
The disk contains an unclean file system (0, 0).
 Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda6': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
 read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda6 /mnt/boot-sav/sda6
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
 Failed to mount '/dev/sda6': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
 mount /dev/sda6 : Error code 14
mount -r /dev/sda6 /mnt/boot-sav/sda6
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda7': Operation not permitted
 The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda7 /mnt/boot-sav/sda7
 The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda7': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
 Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda7 : Error code 14
mount -r /dev/sda7 /mnt/boot-sav/sda7

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2:Windows Recovery Environment (loader):Windows:chain
/dev/sda4:Windows 8 (loader):Windows1:chain
/dev/sda9:Ubuntu 14.04 LTS (14.04):Ubuntu:linux

=================== blkid:
 /dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Ubuntu 14.04 LTS amd64" TYPE="iso9660"
/dev/sda1: LABEL="SYSTEM" UUID="366D-2A62" TYPE="vfat"
/dev/sda2: LABEL="Recovery" UUID="0E486D94486D7B7B" TYPE="ntfs"
 /dev/sda4: LABEL="OS" UUID="1E06CA8A06CA61FF" TYPE="ntfs"
/dev/sda6: LABEL="Data" UUID="5CE671B3E6718DD0" TYPE="ntfs"
/dev/sda7: LABEL="Restore" UUID="C028742628741E1A" TYPE="ntfs"
 /dev/sda8: UUID="6ec268e6-4224-4857-a949-af61af634042" TYPE="swap"
/dev/sda9: UUID="1e1e883b-fa7b-413c-a7a2-6cb55cd09706" TYPE="ext4"


1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

mkdir: cannot create directory ‘/mnt/boot-sav/sda4/boot-sav/log/2014-07-17__07h26boot-repair35’: Read-only file system
sda4 is Read-only or full

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
 Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi

=================== sda9/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 17 01:26 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr 11 10:51 00_header
-rwxr-xr-x 1 root root  6058 Apr 10 15:58 05_debian_theme
 -rwxr-xr-x 1 root root 11608 Apr 11 10:51 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11 10:51 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12 12:31 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11 10:51 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11 10:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 11 10:51 40_custom
-rwxr-xr-x 1 root root   216 Apr 11 10:51 41_custom
-rw-r--r-- 1 root root   483 Apr 11 10:51 README




=================== sda9/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
 #   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
 # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



=================== UEFI/Legacy mode:
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
 SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
 sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
 sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
 sda6    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
 sda7    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda7.
 sda9    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda9.

sda    : GPT,    BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
 Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  106MB   105MB   fat32           EFI system partition          boot
2      106MB   1050MB  944MB   ntfs            Basic data partition          hidden, diag
 3      1050MB  1184MB  134MB                   Microsoft reserved partition  msftres
4      1184MB  243GB   242GB   ntfs            Basic data partition          msftdata
8      243GB   246GB   2937MB  linux-swap(v1)
 5      246GB   246GB   1049kB                                                bios_grub
9      246GB   401GB   155GB   ext4
6      401GB   979GB   577GB   ntfs            Basic data partition          msftdata
7      979GB   1000GB  21.5GB  ntfs            Basic data partition          hidden, diag


                                                                            Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                            Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA ST1000LM024 HN-M;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot;
 2:106MB:1050MB:944MB:ntfs:Basic data partition:hidden, diag;
3:1050MB:1184MB:134MB::Microsoft reserved partition:msftres;
4:1184MB:243GB:242GB:ntfs:Basic data partition:msftdata;
8:243GB:246GB:2937MB:linux-swap(v1)::;
 5:246GB:246GB:1049kB:::bios_grub;
9:246GB:401GB:155GB:ext4::;
6:401GB:979GB:577GB:ntfs:Basic data partition:msftdata;
7:979GB:1000GB:21.5GB:ntfs:Basic data partition:hidden, diag;

                                                                            Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                            Error: Can't have a partition outside the disk!


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
 udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
 /dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
 tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
 none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
 /dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
 /dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9 on /mnt/boot-sav/sda9 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent
 /sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
 /sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
 /dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 rts51x1 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sdb sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhost-net video0 zero
 ls /dev/mapper:  control
ls /mnt/boot-sav/sda1/1:

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
 00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 62 2a 6d 36 4e  4f 20 4e 41 4d 45 20 20  |..)b*m6NO NAME  |
 00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
 00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
 000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
 000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
 00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
 00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
 00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
 000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
 00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff 1f 1c 00 00 00 00 00  |................|
 00000030  00 2c 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |.,..............|
00000040  f6 00 00 00 01 00 00 00  7b 7b 6d 48 94 6d 48 0e  |........{{mH.mH.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
 00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
 00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
 000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
 000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
 00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
 00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
 00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
 000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda4
 00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 23 00  |........?....H#.|
00000020  00 00 00 00 80 00 80 00  ff 67 30 1c 00 00 00 00  |.........g0.....|
 00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  ff 61 ca 06 8a ca 06 1e  |.........a......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
 00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
 00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
 000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
 000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
 00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
 00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
 00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
 000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda6
 00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 98 b6 2e  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 7f 39 43 00 00 00 00  |..........9C....|
 00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  d0 8d 71 e6 b3 71 e6 5c  |..........q..q.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
 00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
 00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
 000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
 000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
 00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
 00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
 00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
 000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda7
 00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 18 f0 71  |........?......q|
00000020  00 00 00 00 80 00 80 00  ff 4f 80 02 00 00 00 00  |.........O......|
 00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  1a 1e 74 28 26 74 28 c0  |..........t(&t(.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
 00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
 00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
 000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
 000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
 00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
 00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
 00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
 000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G  119M  3.8G   4% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      787M  1.3M  786M   1% /run
 /dev/sr0       iso9660    964M  964M     0 100% /cdrom
/dev/loop0     squashfs   923M  923M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G  1.2M  3.9G   1% /tmp
 none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      3.9G   80K  3.9G   1% /run/shm
none           tmpfs      100M   52K  100M   1% /run/user
/dev/sda1      vfat        96M   25M   72M  26% /mnt/boot-sav/sda1
 /dev/sda2      fuseblk    900M  422M  479M  47% /mnt/boot-sav/sda2
/dev/sda4      fuseblk    226G   42G  184G  19% /mnt/boot-sav/sda4
/dev/sda6      fuseblk    538G  157M  538G   1% /mnt/boot-sav/sda6
/dev/sda7      fuseblk     21G   14G  6.3G  69% /mnt/boot-sav/sda7
 /dev/sda9      ext4       142G  3.4G  132G   3% /mnt/boot-sav/sda9

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
 Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x881c76f8

Device Boot      Start         End      Blocks   Id  System
 /dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.


EFI detected. Please check the options.
Partition outside the disk detected.
=================== Advices
 The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?

=================== Recommended repair
Recommended-Repair
This setting will purge (in order to fix packages sign-grub upgrade version) and reinstall the grub-efi-amd64-signed of sda9, using the following options: upgrade-grub       sda1/boot/efi,
 Additional repair will be performed: unhide-bootmenu-10s    backup-and-rename-efi-files


/boot/efi added in sda9/fstab
Created sda9/boot/efi
Mount sda1 on /mnt/boot-sav/sda9/boot/efi
ls /mnt/boot-sav/sda9/boot/efi/1:
 No sda9/boot/efi/efi/ ubuntu/mint folder
chroot /mnt/boot-sav/sda9 apt-get -y --force-yes update
Purge the GRUB of sda9
Install last GRUB version in /mnt/boot-sav/sda9/etc/apt/sources.list
chroot /mnt/boot-sav/sda9 apt-get -y --force-yes update
 grub-efi-amd64-signed available

The following extra packages will be installed:
efibootmgr grub-efi-amd64 grub-efi-amd64-bin sbsigntool secureboot-db
The following packages will be REMOVED:
grub-gfxpayload-lists grub-pc
 The following NEW packages will be installed:
efibootmgr grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed
sbsigntool secureboot-db
0 upgraded, 6 newly installed, 2 to remove and 297 not upgraded.
DEBCHECK debOK, grub-efi-amd64-signed
 DEBCHECK debOK
shim-signed available
linux-signed-generic available
Please type: sudo chroot "/mnt/boot-sav/sda9" dpkg --configure -ansudo chroot "/mnt/boot-sav/sda9" apt-get install -fynsudo chroot "/mnt/boot-sav/sda9" apt-get purge -y --force-yes grub* shim-signed linux-signed*
 Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda9/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda9/boot/efi/EFI/Boot/bootx64.efi

=================== sda9/etc/grub.d/ :
 drwxr-xr-x  2 root root    4096 Jul 17 07:28 grub.d
total 4
-rwxr-xr-x 1 root root 1992 Mar 12 12:31 20_memtest86+


/boot/efi detected in the fstab of sda9: UUID=366D-2A62     (sda1)
shim-signed available
 linux-signed-generic available
Then type: sudo chroot "/mnt/boot-sav/sda9" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda9/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
 Presence of EFI/Boot file detected: /mnt/boot-sav/sda9/boot/efi/EFI/Boot/bootx64.efi

=================== sda9/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 17 07:31 grub.d
drwxr-xr-x  2 root root    4096 Jul 17 07:28 grub.d.bak
 total 72
-rwxr-xr-x 1 root root  9424 Apr 11 10:51 00_header
-rwxr-xr-x 1 root root  6058 Apr 10 15:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 Apr 11 10:51 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11 10:51 20_linux_xen
 -rwxr-xr-x 1 root root 11692 Apr 11 10:51 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11 10:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 11 10:51 40_custom
-rwxr-xr-x 1 root root   216 Apr 11 10:51 41_custom
-rw-r--r-- 1 root root   483 Apr 11 10:51 README




=================== sda9/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
 # For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
 # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of sda9: UUID=366D-2A62     (sda1)
Unhide GRUB boot menu in sda9/etc/default/grub
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda9/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
 Presence of EFI/Boot file detected: /mnt/boot-sav/sda9/boot/efi/EFI/Boot/bootx64.efi

=================== sda9/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 17 07:31 grub.d
drwxr-xr-x  2 root root    4096 Jul 17 07:28 grub.d.bak
 total 72
-rwxr-xr-x 1 root root  9424 Apr 11 10:51 00_header
-rwxr-xr-x 1 root root  6058 Apr 10 15:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 Apr 11 10:51 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11 10:51 20_linux_xen
 -rwxr-xr-x 1 root root 11692 Apr 11 10:51 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11 10:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 11 10:51 40_custom
-rwxr-xr-x 1 root root   216 Apr 11 10:51 41_custom
-rw-r--r-- 1 root root   483 Apr 11 10:51 README




=================== sda9/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
 # For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
 # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of sda9: UUID=366D-2A62     (sda1)

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
 Subsystem: ASUSTeK Computer Inc. Device [1043:11cd]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
 grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.
,.
GRUB too old for SecureBoot. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

chroot /mnt/boot-sav/sda9 efibootmgr -v
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.

chroot /mnt/boot-sav/sda9 uname -r
 Kernel: 3.13.0-24-generic
WinEFI detected. Do you want to activate [Backup and rename Windows EFI files]? no (if any choice fails, please retry with the other)

Reinstall the grub-efi of sda9
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.
 grub-install : exit code of grub-install :1
Error: no grub*.efi generated. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

Add /mnt/boot-sav/sda9/boot/efi efi entries in /mnt/boot-sav/sda9/etc/grub.d/25_custom
 Adding custom /mnt/boot-sav/sda9/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Adding custom /mnt/boot-sav/sda9/boot/efi/EFI/Boot/bootx64.efi
sda1/bootx64.efi already added
sda1/bootmgfw.efi already added

---- Grub-install verbose
 /usr/sbin/grub-install: 1: /usr/sbin/grub-install: cannot create n\F0 \F0    T T @T @DD P\E5td \8C\D2\8C\D2L\8C\D2Ll9l9 Q\E5td  R\E5td \F0= \F0=n\F0=n     /lib64/ld-linux-x86-64.so.2   GNU      GNUm: Directory nonexistent
 +  ELF     @    @@@@@\F8 \F8    8 8 @8 @     @@d: d:    \F0= \F0=n\F0=n\9E{ \81     
/usr/sbin/grub-install: 1: /usr/sbin/grub-install:  ELF    : not found
/usr/sbin/grub-install: 2: /usr/sbin/grub-install: Syntax error: ")" unexpected
 --------
/usr/sbin/grub-install : exit code of grub-install :2
---- End of grub-install verbose


chroot /mnt/boot-sav/sda9 efibootmgr -v
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
 Try 'modprobe efivars' as root.

chroot /mnt/boot-sav/sda9 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
 Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found Windows Recovery Environment (loader) on /dev/sda2
Found Windows 8 (loader) on /dev/sda4
The disk contains an unclean file system (0, 0).
 Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
 read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /mnt/boot-sav/sda2
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
 Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
 mount /dev/sda2 : Error code 14
mount -r /dev/sda2 /mnt/boot-sav/sda2
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
 The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4
 The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
 Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda4 : Error code 14
mount -r /dev/sda4 /mnt/boot-sav/sda4
Unhide GRUB boot menu in sda9/boot/grub/grub.cfg

An error occurred during the repair.

You can now reboot your computer.


You may want to retry after activating the [Backup and rename Windows EFI files] option.

The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
```

---

### Post by kc1di on 2014-07-17
Did you try the last two lines given in the output. 
> You may want to retry after activating the [Backup and rename Windows EFI files] option.

The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.

The error was that it could not mount sda3 because of an unknown files system

---

### Post by ahmedo047 on 2014-07-17
I don't know how to fix this problem "You may want to retry after activating the [Backup and rename Windows EFI files] option." Where is this option?

And I looked at the bios settings of pc but I couldn't find "Legacy mode" option there.

---

### Post by yancek on 2014-07-17
You have windows files on the efi partition (sda1) but none for Ubuntu so what it I believe it is saying is you need both uefi or both mbr.  I don't use uefi so can't help with that but other members here should be able to help.

---

### Post by kc1di on 2014-07-18
As yancek said , you have to install them both with either mbr or uefi, you can't mix them.

---

### Post by oldfred on 2014-07-18
Please use code tags for long text posted.
You can easily add code tags with Advanced editor and # in edit panel.

As posted above you have Ubuntu booting in BIOS mode & Windows in UEFI mode.
The only way you can dual boot is from UEFI menu. You should be able to turn on BIOS/Legacy/CSM mode and boot Ubuntu and then turn on UEFI mode and boot Windows. Some auto switch and let you use one time boot key which is a bit easier.

But grub menu will only boot systems installed in same boot mode as Ubuntu. UEFI and BIOS are not compatible and you cannot switch boot modes once started in one mode.

You can use Boot-Repair to convert a Ubuntu in BIOS mode to UEFI mode. It uninstalls grub-pc (BIOS boot) and installs grub-efi or now grub-efi-amd64 or grub-efi-amd64-signed for UEFI boot.

---

### Post by ahmedo047 on 2014-07-18
Thanks for your replies.
I formatted my drive. I partitioned my drive into three partitions on Asus laptop using Windows 7. I installed Win 7 on sda1, then I installed ubuntu 14.04 on sda3. Everything is normal so far.
I restarted PC. Eventually I saw "grub-menu" including both ubuntu and windows 7 options.  On start, I entered windows 7, it was opened weirdly. I heard the opening sound of windows but I didnt see it (desktop). I restarted PC. I entered Ubuntu. I removed "grub" using some commands. Then I installed "boot-repair". 

Boot-Repair --> Advanced options --> "GRUB options" tab --> tick "*Purge* and *Reinstall Grub* 2 " --> Apply
But I got an error about OS. Then I typed the following commands on Ubuntu terminal

sudo mount /dev/sda3 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install /dev/sda

I restarted PC again. Now I see "grub>" on black screen. 
What should I properly installed "grub menu"?

Thanks in advance

---

### Post by yancek on 2014-07-18
>   On start, I entered windows 7, it was opened weirdly. I heard the  opening sound of windows but I didnt see it (desktop). I restarted PC. I  entered Ubuntu. I removed "grub" using some commands. Then I installed  "boot-repair". 

If after selecting to boot windows 7, you did not see the Desktop, that is a problem that is totally unrelated to Ubuntu or Grub.  Once selecting windows 7 from the boot menu, you are on windows 7.  Something is wrong on your windows partition and reinstalling or modifying Grub is unlikely to help.  You don't indicate if you installed both systems as mbr or gpt.  Not being a windows user, I don't have any idea how you would repair your windows system so you could see the Desktop.  Someone else should be able to advise.

---

### Post by oldfred on 2014-07-18
Post a link to the BootInfo report from Boot-Repair.

If system boots in both UEFI and BIOS you have to be consistent in how you boot installers and repairCDs or flash drives. UEFI & BIOS are not compatible, so once you start to boot in one mode you cannot change to the other.
If you boot installer in UEFI mode it installs in that mode with gpt partitioning. IF BIOS it uses MBR partitioning.
Windows only boots from gpt partitioning with UEFI.
Both Windows & Ubuntu only boot from MBR partitioned drives with BIOS.

---

### Post by ahmedo047 on 2014-07-18
I didnt boot installer them in UEFI mode. After I installed Win7, I used the below command using ubuntu live CD (I used 'TRY' of ubuntu): 
sudo sgdisk --zap /dev/sda

I think this command converted 'gpt' all partitions? Then I installed Ubuntu. 

Is this procedure wrong? If yes, which procedure do you suggest?
If I have to MBR partitioned drives, how can I create MBR partitons?

---

### Post by oldfred on 2014-07-18
Better to use fixparts to remove extraneous gpt data.
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


I think the zap just deletes all partitions. So did it show the MBR partitions for Windows afterwards?

And normally you use sgdisk to convert MBR to gpt.
see also:
 man sgdisk
 and
 man gdisk

I have used gparted. It defaults to MBR(msdos), but before you start partitioning you can select under device, advanced and select type of partitioning.

---

### Post by ahmedo047 on 2014-07-19
Firstly I converted MBR partititons all drives using "sudo gdisk /dev/sda". Please see the below images:

[https://www.dropbox.com/s/ck86spi597laq19/1.png](https://www.dropbox.com/s/ck86spi597laq19/1.png)
[https://www.dropbox.com/s/qc4su7zantvjznt/2.png](https://www.dropbox.com/s/qc4su7zantvjznt/2.png)
[https://www.dropbox.com/s/6o8claaxar1je0w/3.png](https://www.dropbox.com/s/6o8claaxar1je0w/3.png)

Then I reinstalled Windows 7 and Ubuntu 14.04, respectively.
PC was opened. On start I chose windows. I heard the  opening sound of windows but I couldnt see it (desktop) again. I turn off PC using the power switch of laptop. Then I turn on PC. And Windows was normally opened. This time I normally turn PC off in windows. And I turn on PC again. Unfortunately I heard the  opening sound of windows again but I couldnt see it (desktop) again. By the Way, ubuntu opens normally.

Where is my mistake?

---

### Post by oldfred on 2014-07-19
It looks to me that you correctly converted drive to MBR, and installed both Windows & Ubuntu in BIOS/MBR mode.

But you need to make sure UEFI is only in CSM/BIOS/Legacy mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Otherwise it just may be Windows issues. 
Often chkdsk is first then to try, and make sure you do not hibernate.
Beyond that the Windows forums may know more?

      
 [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by ahmedo047 on 2014-07-19
Now I want to install Windows 8. Then I will try to install Ubuntu on external USB drive. But I couldnt achieve to install Win8. Firstly I deleted all disc using Gparted tool implemented Ubuntu live CD. I created two partitons. And I converted to UEFI both partition using fdisk ("t" and "ef" flags). I have laptop's rescue CD. I get the  following error when I tried to install Windows 8 on UEFI mode using the  rescue CD:
"unable to reset your pc a required partition is missing"
 
I think I have a problem about partitions type because Ubuntu uses ext4. What do you suggest me?

---

### Post by oldfred on 2014-07-19
You cannot use fdisk with gpt partitions and Windows in UEFI mode only installs to drives with gpt partitioning.
Windows also only installs in BIOS mode to MBR(msdos) partitions.

You need to make drive gpt partitioned.          I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

But if creating partitions in advance you need several different ones that are not common with BIOS installs.

      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Also on external drive be sure to use gpt partitioning and include the efi partition at or near beginning of drive so Ubuntu has its own efi partition. Otherwise it may install efi boot files to Windows efi partition on hard drive and you then cannot separately boot external.

Not just a flash drive, but any dual boot external or internal:

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by ahmedo047 on 2014-07-22
Problem is solved. Thanks oldfred.
Solution:
1) I converted to gpt all partitions (sda1,sda2 and sda3) using Gparted.
2) I installed Win8.1 on sda1 (not recovery disc) on UEFI mode. 
3) I installed Ubuntu 14.04 on sda2 on UEFI mode.

---

