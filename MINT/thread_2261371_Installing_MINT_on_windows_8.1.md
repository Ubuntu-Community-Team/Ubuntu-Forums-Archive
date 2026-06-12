---
title: "Installing MINT on windows 8.1"
date: 2015-01-18
forum: MINT
---

### Post by gor4l on 2015-01-18
I have similar problem, I`ve install linux mint 17 next to windows 8.1. 
Now Windows can`t boot.
When I try run Boot Repair I get massage :
```
The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session
```

---

### Post by howefield on 2015-01-18
Post moved to own thread and "*MINT*" forum so as not to hijack another.

---

### Post by gor4l on 2015-01-18
Here Is log from BootInfo
```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]

[LIST]
[*]  
 
============================= Boot Info Summary: ===============================
 
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 
    502433792 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt10)/boot/grub.
 
sda1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sda2: __________________________________________________________________________
 
    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi
 
sda3: __________________________________________________________________________
 
    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/LrsBootmgr.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi /bootmgr /boot/bcd
 
sda4: __________________________________________________________________________
 
    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
 
sda5: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
 
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
 
    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sda9: __________________________________________________________________________
 
    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 
 
sda10: _________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17.1 Rebecca 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img
 
sda11: _________________________________________________________________________
 
    File system:       swap
    Boot sector type:  -
    Boot sector info: 
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sda1                   1   976,773,167   976,773,167  ee GPT
 
 
GUID Partition Table detected.
 
Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     2,050,047     2,048,000 Windows Recovery Environment (Windows)
/dev/sda2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sda3       2,582,528     4,630,527     2,048,000 -
/dev/sda4       4,630,528     4,892,671       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5       4,892,672   502,433,448   497,540,777 Data partition (Windows/Linux)
/dev/sda6     896,997,376   897,918,975       921,600 Windows Recovery Environment (Windows)
/dev/sda7     897,918,976   950,347,775    52,428,800 Data partition (Windows/Linux)
/dev/sda8     950,347,776   976,773,119    26,425,344 Windows Recovery Environment (Windows)
/dev/sda9     502,433,792   502,435,839         2,048 BIOS Boot partition
/dev/sda10    502,435,840   889,174,015   386,738,176 Data partition (Linux)
/dev/sda11    889,174,016   896,997,375     7,823,360 Swap partition (Linux)
 
"blkid" output: ________________________________________________________________
 
Device           UUID                                   TYPE       LABEL
 
/dev/sda1        5C20BED820BEB7FA                       ntfs       WINRE_DRV
/dev/sda10       4c4a635a-f571-47b1-b9bc-223245d56fff   ext4       
/dev/sda11       42065410-7d5c-48a0-9096-c3a98f1934cd   swap       
/dev/sda2        82C1-98B7                              vfat       SYSTEM_DRV
/dev/sda3        8CC2-99D3                              vfat       LRS_ESP
/dev/sda5        F2D4C7AFD4C7747F                       ntfs       Windows8_OS
/dev/sda6        B21A0AB71A0A789D                       ntfs       
/dev/sda7        8268CFD068CFC161                       ntfs       LENOVO
/dev/sda8        00E0CA9DE0CA9874                       ntfs       PBR_DRV
 
========================= "ls -l /dev/disk/by-id" output: ======================
 
total 0
lrwxrwxrwx 1 root root  9 Jan 18 18:59 ata-ST500LM000-1EJ162_W370XE5V -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 18 18:59 ata-ST500LM000-1EJ162_W370XE5V-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Jan 18 18:48 ata-ST500LM000-1EJ162_W370XE5V-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Jan 18 18:48 ata-ST500LM000-1EJ162_W370XE5V-part11 -> ../../sda11
lrwxrwxrwx 1 root root 10 Jan 18 18:48 ata-ST500LM000-1EJ162_W370XE5V-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan 18 18:48 ata-ST500LM000-1EJ162_W370XE5V-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jan 18 18:48 ata-ST500LM000-1EJ162_W370XE5V-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jan 18 19:02 ata-ST500LM000-1EJ162_W370XE5V-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan 18 18:59 ata-ST500LM000-1EJ162_W370XE5V-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jan 18 18:59 ata-ST500LM000-1EJ162_W370XE5V-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Jan 18 18:59 ata-ST500LM000-1EJ162_W370XE5V-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Jan 18 18:48 ata-ST500LM000-1EJ162_W370XE5V-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Jan 18 18:59 wwn-0x5000c5006acafd55 -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 18 18:59 wwn-0x5000c5006acafd55-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Jan 18 18:48 wwn-0x5000c5006acafd55-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Jan 18 18:48 wwn-0x5000c5006acafd55-part11 -> ../../sda11
lrwxrwxrwx 1 root root 10 Jan 18 18:48 wwn-0x5000c5006acafd55-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan 18 18:48 wwn-0x5000c5006acafd55-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jan 18 18:48 wwn-0x5000c5006acafd55-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jan 18 19:02 wwn-0x5000c5006acafd55-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan 18 18:59 wwn-0x5000c5006acafd55-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jan 18 18:59 wwn-0x5000c5006acafd55-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Jan 18 18:59 wwn-0x5000c5006acafd55-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Jan 18 18:48 wwn-0x5000c5006acafd55-part9 -> ../../sda9
 
================================ Mount points: =================================
 
Device           Mount_Point              Type       Options
 
/dev/sda10       /                        ext4       (rw,errors=remount-ro)
 
 
========================== sda10/boot/grub/grub.cfg: ===========================
 
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
set root='hd0,gpt10'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10   4c4a635a-f571-47b1-b9bc-223245d56fff
else
  search --no-floppy --fs-uuid --set=root 4c4a635a-f571-47b1-b9bc-223245d56fff
fi
    font="/usr/share/grub/unicode.pf2"
fi
 
if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=pl_PL
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
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda10)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt10'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10   4c4a635a-f571-47b1-b9bc-223245d56fff
    else
      search --no-floppy --fs-uuid --set=root 4c4a635a-f571-47b1-b9bc-223245d56fff
    fi
    linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=4c4a635a-f571-47b1-b9bc-223245d56fff ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-37-generic
}
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda10) -- recovery mode' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt10'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10   4c4a635a-f571-47b1-b9bc-223245d56fff
    else
      search --no-floppy --fs-uuid --set=root 4c4a635a-f571-47b1-b9bc-223245d56fff
    fi
    echo    'Wczytywanie systemu Linux 3.13.0-37-generic...'
    linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=4c4a635a-f571-47b1-b9bc-223245d56fff ro recovery nomodeset 
    echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
    initrd    /boot/initrd.img-3.13.0-37-generic
}
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
 
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt10'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10   4c4a635a-f571-47b1-b9bc-223245d56fff
    else
      search --no-floppy --fs-uuid --set=root 4c4a635a-f571-47b1-b9bc-223245d56fff
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt10'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10   4c4a635a-f571-47b1-b9bc-223245d56fff
    else
      search --no-floppy --fs-uuid --set=root 4c4a635a-f571-47b1-b9bc-223245d56fff
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (na /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-8CC2-99D3' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  8CC2-99D3
    else
      search --no-floppy --fs-uuid --set=root 8CC2-99D3
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 8 (loader) (na /dev/sda5)' --class windows --class os $menuentry_id_option 'osprober-chain-F2D4C7AFD4C7747F' {
    insmod part_gpt
    insmod ntfs
    set root='hd0,gpt5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5   F2D4C7AFD4C7747F
    else
      search --no-floppy --fs-uuid --set=root F2D4C7AFD4C7747F
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
 
=============================== sda10/etc/fstab: ===============================
 
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda10 during installation
UUID=4c4a635a-f571-47b1-b9bc-223245d56fff /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=42065410-7d5c-48a0-9096-c3a98f1934cd none            swap    sw              0       0
--------------------------------------------------------------------------------
 
======================== Unknown MBRs/Boot Sectors/etc: ========================
 
Unknown GPT Partiton Type
e7afbfbf4fa38a449a5b6213eb736c22
 
=============================== StdErr Messages: ===============================
 
cat: write error: Broken pipe
File descriptor 9 (/proc/11244/mounts) leaked on lvs invocation. Parent PID 25359: bash
File descriptor 63 (pipe:[28827]) leaked on lvs invocation. Parent PID 25359: bash
  No volume groups found
 
ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-01-18__18h59 ===================
boot-repair version : 4ppa32
boot-sav version : 4ppa32
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version :
File descriptor 9 (/proc/11244/mounts) leaked on lvs invocation. Parent PID 13062: /bin/sh
No volume groups found
boot-repair is executed in installed-session (Linux Mint 17.1 Rebecca, rebecca, LinuxMint, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=4c4a635a-f571-47b1-b9bc-223245d56fff ro quiet splash vt.handoff=7
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operacja niedozwolona
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operacja niedozwolona
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda1 : Error code 14
mount -r /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda6': Operacja niedozwolona
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda6 /mnt/boot-sav/sda6
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda6': Operacja niedozwolona
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda6 : Error code 14
mount -r /dev/sda6 /mnt/boot-sav/sda6
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda7': Operacja niedozwolona
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda7 /mnt/boot-sav/sda7
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda7': Operacja niedozwolona
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda7 : Error code 14
mount -r /dev/sda7 /mnt/boot-sav/sda7
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda8': Operacja niedozwolona
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda8 /mnt/boot-sav/sda8
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda8': Operacja niedozwolona
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda8 : Error code 14
mount -r /dev/sda8 /mnt/boot-sav/sda8
 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
 
 
=================== os-prober:
/dev/sda10:System w u&#380;yciu - Linux Mint 17.1 Rebecca CurrentSession:linux
/dev/sda3:Windows Recovery Environment (loader):Windows:chain
/dev/sda5:Windows 8 (loader):Windows1:chain
 
=================== blkid:
/dev/sda1: LABEL="WINRE_DRV" UUID="5C20BED820BEB7FA" TYPE="ntfs"
/dev/sda2: LABEL="SYSTEM_DRV" UUID="82C1-98B7" TYPE="vfat"
/dev/sda3: LABEL="LRS_ESP" UUID="8CC2-99D3" TYPE="vfat"
/dev/sda5: LABEL="Windows8_OS" UUID="F2D4C7AFD4C7747F" TYPE="ntfs"
/dev/sda6: UUID="B21A0AB71A0A789D" TYPE="ntfs"
/dev/sda7: LABEL="LENOVO" UUID="8268CFD068CFC161" TYPE="ntfs"
/dev/sda8: LABEL="PBR_DRV" UUID="00E0CA9DE0CA9874" TYPE="ntfs"
/dev/sda10: UUID="4c4a635a-f571-47b1-b9bc-223245d56fff" TYPE="ext4"
/dev/sda11: UUID="42065410-7d5c-48a0-9096-c3a98f1934cd" TYPE="swap"
 
 
1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
 
 
UWAGA: na '/dev/sda' wykryto tablic&#281; partycji GPT (GUID Partition Table)! Narz&#281;dzie sfdisk nie obs&#322;uguje GPT. Nale&#380;y u&#380;y&#263; GNU Parteda.
 
 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
 
 
=================== /etc/grub.d/ :
drwxr-xr-x  2 root  root     4096 lis 26 23:46 grub.d
razem 88
-rwxr-xr-x 1 root root  9424 maj 15  2014 00_header
-rwxr-xr-x 1 root root  6058 maj  8  2014 05_debian_theme
-rwxr-xr-x 1 root root  1180 pa&#378; 25 13:17 06_mint_theme
-rwxr-xr-x 1 root root  7500 sty 18 18:48 10_linux
-rwxr-xr-x 1 root root 10634 pa&#378;  1  2012 10_lupin
-rwxr-xr-x 1 root root 10412 maj 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 maj 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 maj 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 maj 15  2014 40_custom
-rwxr-xr-x 1 root root   216 maj 15  2014 41_custom
-rw-r--r-- 1 root root   483 maj 15  2014 README
 
 
 
 
=================== /etc/default/grub :
 
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
 
 
 
=================== No kernel in /mnt/boot-sav/sda2/boot:
boot.sdi
 
 
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda3/EFI/Microsoft/Boot/LrsBootmgr.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda3/EFI/Boot/bootx64.efi
 
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, but it is not setup in EFI-mode for this installed-session.
EFI in dmesg.
[    0.000000] ACPI: UEFI 0000000090ffc000 000236 (v01 LENOVO CB-01    00000001 ACPI 00040000)
SecureBoot disabled.
 
 
=================== PARTITIONS & DISKS:
sda10    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,     64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,     fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,     not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-kernel,    no-os,    is-maybe-EFI,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    is-os,    is-maybe-EFI,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,     is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,     is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
sda7    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda7.
sda8    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda8.
 
sda    : GPT,    BIOS_boot,    has-maybe-EFI,     not-usb,    has-os,    2048 sectors * 512 bytes
 
 
=================== parted -l:
 
Model: ATA ST500LM000-1EJ16 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
 
Number  Start   End     Size    File system     Name                          Flags
1      1049kB  1050MB  1049MB  ntfs            Basic data partition          hidden, diag
2      1050MB  1322MB  273MB   fat32           EFI system partition          boot, hidden
3      1322MB  2371MB  1049MB  fat32           Basic data partition          hidden
4      2371MB  2505MB  134MB                   Microsoft reserved partition  msftres
5      2505MB  257GB   255GB   ntfs            Basic data partition          msftdata
9      257GB   257GB   1049kB                                                bios_grub
10      257GB   455GB   198GB   ext4
11      455GB   459GB   4006MB  linux-swap(v1)
6      459GB   460GB   472MB   ntfs                                          hidden, diag
7      460GB   487GB   26.8GB  ntfs            Basic data partition          msftdata
8      487GB   500GB   13.5GB  ntfs            Basic data partition          hidden, diag
 
=================== parted -lm:
 
BYT;
/dev/sda:500GB:scsi:512:4096:gpt:ATA ST500LM000-1EJ16;
1:1049kB:1050MB:1049MB:ntfs:Basic data partition:hidden, diag;
2:1050MB:1322MB:273MB:fat32:EFI system partition:boot, hidden;
3:1322MB:2371MB:1049MB:fat32:Basic data partition:hidden;
4:2371MB:2505MB:134MB::Microsoft reserved partition:msftres;
5:2505MB:257GB:255GB:ntfs:Basic data partition:msftdata;
9:257GB:257GB:1049kB:::bios_grub;
10:257GB:455GB:198GB:ext4::;
11:455GB:459GB:4006MB:linux-swap(v1)::;
6:459GB:460GB:472MB:ntfs::hidden, diag;
7:460GB:487GB:26.8GB:ntfs:Basic data partition:msftdata;
8:487GB:500GB:13.5GB:ntfs:Basic data partition:hidden, diag;
 
 
 
 
=================== mount:
/dev/sda10 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=iwona)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type vfat (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8 on /mnt/boot-sav/sda8 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
 
 
=================== ls:
/sys/block/sda (filtered):   alignment_offset bdi capability dev device discard_alignment events  events_async events_poll_msecs ext_range holders inflight power queue  range removable ro sda1 sda10 sda11 sda2 sda3 sda4 sda5 sda6 sda7 sda8  sda9 size slaves stat subsystem trace uevent
/dev (filtered):   autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency  cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg log  mapper mcelog mei mem net network_latency network_throughput null port  ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda10 sda11 sda2 sda3  sda4 sda5 sda6 sda7 sda8 sda9 sg0 shm snapshot snd stderr stdin stdout  uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control
ls: nie ma dost&#281;pu do : Nie ma takiego pliku ani katalogu
 
=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 3f 1f 00 00 00 00 00  |.........?......|
00000030  55 4d 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |UM..............|
00000040  f6 00 00 00 01 00 00 00  fa b7 be 20 d8 be 20 5c  |........... .. |
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
 
=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 1f 00  |........?....H..|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 b7 98 c1 82 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
ls sda3/efi: /Microsoft/Boot/zh-tw /Microsoft/Boot/zh-hk  /Microsoft/Boot/zh-cn /Microsoft/Boot/tr-tr /Microsoft/Boot/sv-se  /Microsoft/Boot/ru-ru /Microsoft/Boot/Resources /Microsoft/Boot/pt-pt  /Microsoft/Boot/pt-br /Microsoft/Boot/pl-pl /Microsoft/Boot/nl-nl  /Microsoft/Boot/nb-no /Microsoft/Boot/memtest.efi  /Microsoft/Boot/LrsBootmgr.efi /Microsoft/Boot/ko-kr  /Microsoft/Boot/ja-jp /Microsoft/Boot/it-it /Microsoft/Boot/hu-hu  /Microsoft/Boot/fr-fr /Microsoft/Boot/Fonts /Microsoft/Boot/fi-fi  /Microsoft/Boot/es-es /Microsoft/Boot/en-us /Microsoft/Boot/el-gr  /Microsoft/Boot/de-de /Microsoft/Boot/da-dk /Microsoft/Boot/cs-cz  /Microsoft/Boot/boot.stl /Microsoft/Boot/bootmgr.efi  /Microsoft/Boot/BCD.LOG2 /Microsoft/Boot/BCD.LOG1  /Microsoft/Boot/BCD.LOG /Microsoft/Boot/BCD /Microsoft/Boot  /Boot/bootx64.efi
ls sda3: Boot
bootmgr
bootmgr.efi
EFI
OneKey
Version.txt  . Prosz&#281; zg&#322;o&#347; t&#281; wiadomo&#347;&#263; do boot.repair@gmail.com
ls: nie ma dost&#281;pu do /boot/efi/efi: Nie ma takiego pliku ani katalogu
ls /boot/efi/efi :
Error efitmp. Prosz&#281; zg&#322;o&#347; t&#281; wiadomo&#347;&#263; do boot.repair@gmail.com
 
=================== hexdump -n512 -C /dev/sda3
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 6e 10  |.X.MSDOS5.0...n.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 27 00  |........?....h'.|
00000020  00 40 1f 00 c9 07 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 d3 99 c2 8c 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
 
=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 4a 00  |........?.....J.|
00000020  00 00 00 00 80 00 80 00  a0 de a7 1d 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  7f 74 c7 d4 af c7 d4 f2  |.........t......|
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
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 18 77 35  |........?.....w5|
00000020  00 00 00 00 80 00 80 00  ff 0f 0e 00 00 00 00 00  |................|
00000030  00 96 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  9d 78 0a 1a b7 0a 1a b2  |.........x......|
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
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 85 35  |........?....(.5|
00000020  00 00 00 00 80 00 80 00  ff ff 1f 03 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  61 c1 cf 68 d0 cf 68 82  |........a..h..h.|
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
 
=================== hexdump -n512 -C /dev/sda8
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 a5 38  |........?....(.8|
00000020  00 00 00 00 80 00 80 00  ff 37 93 01 00 00 00 00  |.........7......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  74 98 ca e0 9d ca e0 00  |........t.......|
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
 
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda10     ext4      182G   25G  148G  15% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  1.8G   12K  1.8G   1% /dev
tmpfs          tmpfs     368M  1.4M  367M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.8G  668K  1.8G   1% /run/shm
none           tmpfs     100M   20K  100M   1% /run/user
/dev/sda1      fuseblk  1000M  292M  709M  30% /mnt/boot-sav/sda1
/dev/sda2      vfat      256M   29M  228M  12% /mnt/boot-sav/sda2
/dev/sda3      vfat      996M  520M  477M  53% /mnt/boot-sav/sda3
/dev/sda5      fuseblk   238G   55G  183G  23% /mnt/boot-sav/sda5
/dev/sda6      fuseblk   450M  287M  164M  64% /mnt/boot-sav/sda6
/dev/sda7      fuseblk    25G  4.0G   22G  16% /mnt/boot-sav/sda7
/dev/sda8      fuseblk    13G   10G  2.7G  80% /mnt/boot-sav/sda8
 
=================== fdisk -l:
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x33685c6c
 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.
 
 
 
 
=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to fix packages sign-grub) and reinstall the grub-efi-amd64-signed of sda10, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file
 
 
=================== Blockers in case of suggested repair
The current session is in Legacy mode. Please reboot the computer,  and use this software in an EFI session. Pozwoli to na t&#281; funkcj&#281;. For  example, use a live-USB of Boot-Repair-Disk-64bit (www.sourceforge.net/p/boot-repair-cd), after making sure your BIOS is set up to boot USB in EFI mode.
 
 
=================== Advice in case of suggested repair
Uruchamianie twojego komputera jest w trybie Legacy. Mo&#380;esz spróbowa&#263; zmieni&#263; to do trybu EFI
Czy chcesz kontynuowa&#263;?
 
 
=================== Final advice in case of suggested repair
Prosz&#281; nie zapomnie&#263;aby dokona&#263; BIOS rozruch na sda2/efi/.../grub*.efi plik!
 
Pliki startowe (boot) [System w u&#380;yciu - Linux Mint 17.1 Rebecca]  s&#261; daleko od pocz&#261;tku dysku. Twój BIOS mo&#380;e mie&#263; problemy z ich  znalezieniem. Mo&#380;esz spróbowa&#263; ponownie po utworzeniu /boot partycji (EXT4, >200MB, pocz&#261;tku dysku). Mo&#380;esz to osi&#261;gn&#261;&#263; u&#380;ywaj&#261;c na przyk&#322;ad: gParted. Nast&#281;pnie zaznacz t&#281; partycj&#281; poprzez [Osobna /boot partycja:] opcj&#281; z [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)
 
If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi
 
Uruchamianie twojego komputera jest w trybie Legacy. Mo&#380;esz spróbowa&#263; zmieni&#263; to do trybu EFI
 
 
=================== User settings
The settings chosen by the user will not act on the boot.
 
 
 
 
pastebinit  packages needed
debconf: nie uda&#322;o si&#281; zainicjalizowa&#263; nak&#322;adki: Dialog
debconf: (Nak&#322;adka "dialog" nie mo&#380;e dzia&#322;a&#263; na terminalu "dumb", buforze pow&#322;oki emacsa ani bez terminala steruj&#261;cego.)
debconf: powrót do nak&#322;adki: Readline
debconf: nie uda&#322;o si&#281; zainicjalizowa&#263; nak&#322;adki: Readline
debconf: (Ta nak&#322;adka wymaga terminala steruj&#261;cego.)
debconf: powrót do nak&#322;adki: Teletype
dpkg-preconfigure: nie uda&#322;o si&#281; ponownie otworzy&#263; stdin:
``` 
[/LIST]
 

[\code]

---

### Post by ajgreeny on 2015-01-18
You installed Ubuntu in legacy BIOS mode whereas Windows-8 is installed in UEFI mode, so you will not get Windows to run from that.
See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for details

I don't know Windows-8 at all, but I think the simplest way to proceed is to install Ubuntu again making sure you choose to boot the installation DVD or USB in UEFI mode; usually there are two instances of the DVD or USB drive showing in the list so choose the UEFI one.  

Use the "Something Else" option at partitioning stage, and delete the current Ubuntu partitions, sda10 and sda11, then use the free space to again install Ubuntu.

You may prefer to wait for other answers before doing that; forum member oldfred is the UEFI and boot-repair guru and hopefully he may pop along with a quicker or better answer for you.

---

