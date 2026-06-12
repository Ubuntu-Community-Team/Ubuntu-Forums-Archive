---
title: "&quot;Disk read error&quot; after installing ubuntu"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by arnab321 on 2011-12-10
I wanted to keep 3 OS's. (i wanted to test ubuntu, and i have to keep XP, as my printer doesnt support win7)

 so i installed them in the following order: first XP, then win7, then ubuntu.
when i had finished installing win 7, the two OS's were booting fine, but after i installed ubuntu 11.10, ubuntu booted fine, but on chainloading windows says "Disk read error. press ctrl+alt+del....". 

for the windows, i had created a 60 mb partition(the first partition), just to keep the boot files. and i installed grub in the MBR. does that have to do anything?

this is my boot_info_script output:


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    85009064 of the same hard drive for core.img. core.img is at this location 
    and looks for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /boot/bcd /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 31. But according to the info from fdisk, 
                       sda5 starts at sector 125767.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 31. But according to the info from fdisk, 
                       sda6 starts at sector 128051669.
    Operating System:  Windows XP
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 31. But according to the info from fdisk, 
                       sda7 starts at sector 138293914.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 31. But according to the info from fdisk, 
                       sda8 starts at sector 201209065.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
169 heads, 31 sectors/track, 59664 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             31       125,735       125,705   7 NTFS / exFAT / HPFS
/dev/sda2             125,765   312,574,456   312,448,692   f W95 Extended (LBA)
/dev/sda5             125,767    84,012,603    83,886,837   7 NTFS / exFAT / HPFS
/dev/sda6         128,051,669   138,293,882    10,242,214   7 NTFS / exFAT / HPFS
/dev/sda7         138,293,914   201,209,033    62,915,120   7 NTFS / exFAT / HPFS
/dev/sda8         201,209,065   312,574,456   111,365,392   7 NTFS / exFAT / HPFS
/dev/sda9          84,013,056   122,040,319    38,027,264  83 Linux
/dev/sda10        122,042,368   128,049,151     6,006,784  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        ACE2-048F                              vfat       BOOT
/dev/sda10       f254304d-68ae-4a51-887e-913ba2127bd6   swap       
/dev/sda5        72F4E031F4DFF577                       ntfs       
/dev/sda6        8670741870741163                       ntfs       xp
/dev/sda7        EE545CF5545CC1CF                       ntfs       Docs
/dev/sda8        0CEC4BF8EC4BDA9A                       ntfs       Storehouse
/dev/sda9        8be5ed82-3db9-492d-9343-b1f3097dfc3e   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
--------------------------------------------------------------------------------

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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set=root 8be5ed82-3db9-492d-9343-b1f3097dfc3e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos9)'
  search --no-floppy --fs-uuid --set=root 8be5ed82-3db9-492d-9343-b1f3097dfc3e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root 8be5ed82-3db9-492d-9343-b1f3097dfc3e
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8be5ed82-3db9-492d-9343-b1f3097dfc3e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root 8be5ed82-3db9-492d-9343-b1f3097dfc3e
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8be5ed82-3db9-492d-9343-b1f3097dfc3e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root 8be5ed82-3db9-492d-9343-b1f3097dfc3e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root 8be5ed82-3db9-492d-9343-b1f3097dfc3e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ace2-048f
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sde2)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd3,msdos2)'
    search --no-floppy --fs-uuid --set=root 4ea8-9c80
    drivemap -s (hd0) ${root}
    chainloader +1
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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=8be5ed82-3db9-492d-9343-b1f3097dfc3e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=f254304d-68ae-4a51-887e-913ba2127bd6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  40.535507202 = 43.524669440   boot/grub/core.img                             1
  56.867855072 = 61.061394432   boot/grub/grub.cfg                             1
  41.998046875 = 45.095059456   boot/initrd.img-3.0.0-12-generic               2
  42.502388000 = 45.636591616   boot/vmlinuz-3.0.0-12-generic                  1
  41.998046875 = 45.095059456   initrd.img                                     2
  42.502388000 = 45.636591616   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  0a 01 00 0e 00 08 20 20  3f 7f c0 80 02 02 00 08  |......  ?.......|
00000010  0f ff e0 20 00 80 80 02  02 00 08 0f ff e0 20 00  |... .......... .|
00000020  80 16 16 01 19 18 0c 02  08 20 fd f0 80 20 82 40  |......... ... .@|
00000030  82 ff e2 88 20 49 20 80  a2 82 03 8a 08 0a 08 24  |.... I ........$|
00000040  08 2f f8 20 80 03 8e 00  0a 29 06 49 27 fa 2c 90  |./. .....).I'.,.|
00000050  48 a2 41 02 09 04 08 24  10 20 90 44 92 7f 8e 3a  |H.A....$. .D...:|
00000060  00 10 40 16 16 01 19 18  43 02 08 88 fd f2 40 20  |..@.....C.....@ |
00000070  8a 40 82 ff a2 88 20 49  20 80 a2 82 03 8a 0b 0a  |.@.... I .......|
00000080  0b f0 08 20 80 20 82 03  8e 0a 0a 2b fe 49 20 82  |... . .....+.I .|
00000090  2c 84 08 a2 10 02 08 40  08 22 00 20 88 04 92 40  |,......@.". ...@|
000000a0  0e 3a 00 10 40 16 16 01  19 18 00 38 00 01 c0 00  |.:..@......8....|
000000b0  0c c0 00 42 80 06 fd c0  60 01 e6 7f f8 e1 00 60  |...B....`......`|
000000c0  04 01 80 1f fe 00 40 00  00 10 02 ff ef fc 81 10  |......@.........|
000000d0  21 c4 38 81 10 22 01 40  28 39 07 2f 05 e0 a0 12  |!.8..".@(9./....|
000000e0  02 07 c0 f8 02 00 40 16  16 01 19 18 0c 02 08 31  |......@........1|
000000f0  ff f0 a0 20 84 80 82 11  43 08 86 8b 24 09 26 90  |... ....C...$.&.|
00000100  26 8a 83 0a 29 f0 08 20  00 20 a0 42 8e 7f 92 29  |&...).. . .B...)|
00000110  04 8b 24 16 38 90 50 a2  41 02 09 04 08 24 10 20  |..$.8.P.A....$. |
00000120  9f c0 82 40 9e 78 00 10  40 16 16 01 19 18 06 02  |...@.x..@.......|
00000130  08 20 fd f0 fc 20 84 20  82 20 a2 89 44 49 28 b0  |. ... . . ..DI(.|
00000140  a2 81 83 8a 04 0a 08 28  08 23 70 20 b1 fb 8e 08  |.......(.#p ....|
00000150  4a 28 42 49 22 8a 2c b1  48 a2 07 02 08 18 08 20  |J(BI".,.H...... |
00000160  40 20 86 04 92 20 0e 3b  00 10 40 16 16 01 19 18  |@ ... .;..@.....|
00000170  18 00 00 44 0c 61 1f ff  85 c0 84 38 82 13 23 ce  |...D.a.....8..#.|
00000180  40 91 a5 02 52 8c 06 4a  30 29 08 43 1c 21 30 01  |@...R..J0).C.!0.|
00000190  8c 00 ca 73 ff cb 41 23  29 04 88 a4 12 02 14 48  |...s..A#)......H|
000001a0  7b d2 20 41 48 80 03 41  ff fe 00 00 00 16 16 01  |{. AH..A........|
000001b0  19 18 06 00 01 11 8e 36  45 f7 91 10 82 44 00 01  |.......6E....D..|
000001c0  01 18 07 a8 df ff 02 00  00 00 f5 02 00 05 00 a8  |................|
000001d0  df ff 05 a8 df ff 71 fe  9f 07 c5 48 9c 00 00 00  |......q....H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".


```

---

### Post by cody1233 on 2011-12-10
The best idea in this case may be to back up and wipe your hard disk and reinstall everything.

---

