---
title: "Can't get back into Windows8 after installing 13.04"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by ThyRellik on 2013-05-10
Ok so i had windows 8 installed on my custom pc i then created a partion on a secondary "media" drive and installed ubuntu 13.04 but now i can not get back to windows 8
i have attempted to use windows 8 repair as well as the Boot-Repair from within ubuntu here is the info boot repair gave me

```
============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/nvidia_checaaae and 
    looks at sector 1 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 94 for .


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img


sdb3: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sdb5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


nvidia_checaaae1: ______________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM


nvidia_checaaae2: ______________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   625,139,711   624,932,864   7 NTFS / exFAT / HPFS




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1               2,048   292,970,797   292,968,750   7 NTFS / exFAT / HPFS
/dev/sdb2    *    292,972,544   476,565,503   183,592,960  83 Linux
/dev/sdb3         476,567,550   488,396,799    11,829,250   5 Extended
/dev/sdb5         476,567,552   488,396,799    11,829,248  82 Linux swap / Solaris




Drive: nvidia_checaaae _____________________________________________________________________


Disk /dev/mapper/nvidia_checaaae: 320.1 GB, 320072908800 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/mapper/nvidia_checaaae1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/nvidia_checaaae2            206,848   625,139,711   624,932,864   7 NTFS / exFAT / HPFS




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        5242C1D842C1C149                       ntfs       System Reserved
/dev/sda2        AAEA2DB3EA2D7CA7                       ntfs       
/dev/sdb1        74BCB51BBCB4D8B6                       ntfs       Data
/dev/sdb2        bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6   ext4       
/dev/sdb5        09495252-52c7-49b4-b176-b1f3fabc1d65   swap       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sdb2        /                        ext4       (rw,errors=remount-ro)




=========================== sdb2/boot/grub/grub.cfg: ===========================


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
set root='hd1,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
else
  search --no-floppy --fs-uuid --set=root bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
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
  set timeout=10
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
    else
      search --no-floppy --fs-uuid --set=root bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
    fi
    linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-19-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6' {
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
        else
          search --no-floppy --fs-uuid --set=root bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
        else
          search --no-floppy --fs-uuid --set=root bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
    else
      search --no-floppy --fs-uuid --set=root bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
    else
      search --no-floppy --fs-uuid --set=root bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
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


=============================== sdb2/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=09495252-52c7-49b4-b176-b1f3fabc1d65 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sdb2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


 145.835708618 = 156.589899776  boot/grub/grub.cfg                             1
 146.054325104 = 156.824637440  boot/grub/i386-pc/core.img                     1
 140.572372437 = 150.938435584  boot/vmlinuz-3.8.0-19-generic                  1
 140.572372437 = 150.938435584  vmlinuz                                        1
 141.512279510 = 151.947653120  boot/initrd.img-3.8.0-19-generic               1
 141.512279510 = 151.947653120  initrd.img                                     1
 141.512279510 = 151.947653120  initrd.img.old                                 1


========================== nvidia_checaaae1/boot.ini: ==========================


--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
--------------------------------------------------------------------------------


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sdb3


00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff fd 2c ad  |..............,.|
00000010  69 26 db 73 0c cc 1e f0  84 14 b1 a4 2d e9 4a 45  |i&.s........-.JE|
00000020  bb 74 73 68 76 6e da 66  6f 34 21 a4 46 60 b9 96  |.tshvn.fo4!.F`..|
00000030  df 08 3e 76 36 dc 52 e5  81 4a 46 25 4f a7 61 cb  |..>v6.R..JF%O.a.|
00000040  58 56 86 fb 45 e2 16 33  80 59 0b bc e0 b5 36 ab  |XV..E..3.Y....6.|
00000050  20 a7 7f 63 53 13 6f 2c  b9 22 6a 26 08 e4 fc cc  | ..cS.o,."j&....|
00000060  41 8c 44 88 98 22 82 64  82 db 6e 15 47 43 43 82  |A.D..".d..n.GCC.|
00000070  da 34 88 93 ba 4c 72 80  f1 21 73 b1 98 a6 70 a5  |.4...Lr..!s...p.|
00000080  be 3e 13 47 b6 22 5c 79  e5 93 63 76 53 5d d1 c9  |.>.G."\y..cvS]..|
00000090  01 7d 16 84 c9 55 28 aa  e9 c9 ba c4 25 c6 26 ea  |.}...U(.....%.&.|
000000a0  4e b1 fc 7a b6 fc c9 46  a5 fe f9 64 f0 e0 ec e1  |N..z...F...d....|
000000b0  bf 88 fd 64 5b f4 61 cc  a5 f0 fc c1 79 82 b3 46  |...d[.a.....y..F|
000000c0  d6 95 0a 9b d8 76 54 3b  6a dc fb a8 fa 8f 22 47  |.....vT;j....."G|
000000d0  1c 39 bf 58 e2 7e a5 5b  b4 9b 4d 39 89 c8 15 47  |.9.X.~.[..M9...G|
000000e0  92 54 36 97 9f 1d c7 de  b6 8e 5d 76 e8 f7 74 a7  |.T6.......]v..t.|
000000f0  4a a3 04 95 fe da 5a c9  24 26 96 84 44 57 36 43  |J.....Z.$&..DW6C|
00000100  92 7c 25 98 df d2 22 5d  9e 33 6b b8 d2 b6 2a e6  |.|%..."].3k...*.|
00000110  7a 8f 75 16 04 8e 35 ab  e4 2d 90 ae 8b 1e b0 9f  |z.u...5..-......|
00000120  bb c2 1a c5 05 91 5e cc  a9 b5 9f b1 5f 10 26 6a  |......^....._.&j|
00000130  46 3f 6f 8f 1e fb 82 ce  9c d4 08 2c cc b1 62 44  |F?o........,..bD|
00000140  57 b0 30 30 bf 5e 4a 28  e4 9a ee a3 b0 ab e4 64  |W.00.^J(.......d|
00000150  5d c6 cc 36 a7 09 1e 41  51 c0 ae a7 a4 48 10 54  |]..6...AQ....H.T|
00000160  6d 92 a3 13 ed ce 95 f4  d5 2a e2 87 be 70 bb 53  |m........*...p.S|
00000170  2a ac e4 49 1e 07 3b 13  09 c6 7e 32 ee 3c 52 56  |*..I..;...~2.<RV|
00000180  73 0f c4 5b 33 0b 49 a6  92 46 8b 7a d3 d5 50 f4  |s..[3.I..F.z..P.|
00000190  24 47 e2 9e 76 f5 c1 90  8b 5b ac 12 76 7b 1e 0a  |$G..v....[..v{..|
000001a0  f6 a7 0c 44 52 34 4b 2a  ac 49 45 14 ea 5e 85 96  |...DR4K*.IE..^..|
000001b0  c7 a5 cc 22 15 3f 08 87  fe 6d 8d cc 65 55 00 fe  |...".?...m..eU..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 b4 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




=============================== StdErr Messages: ===============================


cat: write error: Broken pipe


ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-05-10__13h06 ===================
boot-repair version : 3.198~ppa16~raring
boot-sav version : 3.198~ppa16~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.198~ppa16~raring
boot-repair is executed in installed-session (Ubuntu 13.04, raring, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6 ro quiet splash vt.handoff=7


=================== os-prober:
/dev/sdb2:The OS now in use - Ubuntu 13.04 CurrentSession:linux


=================== blkid:
/dev/sda1: LABEL="System Reserved" UUID="5242C1D842C1C149" TYPE="ntfs"
/dev/sda2: UUID="AAEA2DB3EA2D7CA7" TYPE="ntfs"
/dev/sdb1: LABEL="Data" UUID="74BCB51BBCB4D8B6" TYPE="ntfs"
/dev/sdb2: UUID="bc294a8d-ef51-42fc-b2e5-4ae7389f9ee6" TYPE="ext4"
/dev/sdb5: UUID="09495252-52c7-49b4-b176-b1f3fabc1d65" TYPE="swap"




1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


Windows not detected by os-prober on sda2.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.




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








=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 May 10 11:27 grub.d
total 76
-rwxr-xr-x 1 root root  7541 Apr  9 04:29 00_header
-rwxr-xr-x 1 root root  5974 Apr  9 03:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9 04:29 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9 04:29 20_linux_xen
-rwxr-xr-x 1 root root  1688 Dec  5 09:32 20_memtest86+
-rwxr-xr-x 1 root root 10976 Apr  9 04:29 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9 04:29 30_uefi-firmware
-rwxr-xr-x 1 root root   300 May 10 11:27 40_custom
-rwxr-xr-x 1 root root   214 Apr  9 04:29 40_custom~
-rwxr-xr-x 1 root root   216 Apr  9 04:29 41_custom
-rw-r--r-- 1 root root   483 Apr  9 04:29 README
-rw-r--r-- 1 root root     0 May 10 11:27 Untitled Document 1




=================== /etc/grub.d/40_custom :


menuentry "windows" {
insmod chain
set root=(hd1)
drivemap -s hd0 hd1
chainloader +1




=================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
SecureBoot disabled.




=================== PARTITIONS & DISKS:
sdb2    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.


sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes




=================== parted -l:


Model: ATA WDC WD3200AAJS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
1      1049kB  106MB  105MB  primary  ntfs         boot
2      106MB   320GB  320GB  primary  ntfs




Model: ATA ST9250320AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
1      1049kB  150GB  150GB   primary   ntfs
2      150GB   244GB  94.0GB  primary   ext4            boot
3      244GB   250GB  6057MB  extended
5      244GB   250GB  6057MB  logical   linux-swap(v1)


=================== parted -lm:


BYT;
/dev/sda:320GB:scsi:512:512:msdos:ATA WDC WD3200AAJS-0;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:320GB:320GB:ntfs::;


BYT;
/dev/sdb:250GB:scsi:512:512:msdos:ATA ST9250320AS;
1:1049kB:150GB:150GB:ntfs::;
2:150GB:244GB:94.0GB:ext4::boot;
3:244GB:250GB:6057MB:::;
5:244GB:250GB:6057MB:linux-swap(v1)::;




=================== mount:
/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
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
gvfsd-fuse on /run/user/john/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=john)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)




=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrom1 cdrw cdrw1 char console core cpu cpu_dma_latency disk dri dvd dvd1 dvdrw dvdrw1 ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdb2 sdb3 sdb5 sg0 sg1 sg2 sg3 shm snapshot snd sr0 sr1 stderr stdin stdout uinput urandom usb vga_arbiter vhost-net zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  49 c1 c1 42 d8 c1 42 52  |........I..B..BR|
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
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff b7 3f 25 00 00 00 00  |..........?%....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  a7 7c 2d ea b3 2d ea aa  |.........|-..-..|
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
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200


=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  20 59 76 11 00 00 00 00  |........ Yv.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  b6 d8 b4 bc 1b b5 bc 74  |...............t|
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


=================== df -Th:


Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb2      ext4       87G  3.6G   79G   5% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  2.8G   12K  2.8G   1% /dev
tmpfs          tmpfs     572M  888K  571M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     2.8G   72K  2.8G   1% /run/shm
none           tmpfs     100M   36K  100M   1% /run/user
/dev/sda1      fuseblk   100M   31M   70M  31% /mnt/boot-sav/sda1
/dev/sda2      fuseblk   298G  148G  151G  50% /mnt/boot-sav/sda2
/dev/sdb1      fuseblk   140G   61G   79G  44% /mnt/boot-sav/sdb1


=================== fdisk -l:


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaff83e3b


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   625139711   312466432    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf8000000


Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   292970797   146484375    7  HPFS/NTFS/exFAT
/dev/sdb2   *   292972544   476565503    91796480   83  Linux
/dev/sdb3       476567550   488396799     5914625    5  Extended
/dev/sdb5       476567552   488396799     5914624   82  Linux swap / Solaris






=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sdb2 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s


=================== Settings chosen by the user
Custom-Repair
This setting will reinstall the grub2 of sdb2 into the MBRs of all disks (except USB without OS), using the following options:       set-windows-as-default
Additional repair will be performed: unhide-bootmenu-10s




umount: /mnt/boot-sav/sda2: not mounted


Reinstall the GRUB of sdb2 into all MBRs of disks with OS or not-USB
grub-install (GRUB) 2.00-13ubuntu3,grub-install (GRUB) 2.


Reinstall the GRUB of sdb2 into the MBR of sda
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0
grub-install (GRUB) 2.00-13ubuntu3,grub-install (GRUB) 2.


Reinstall the GRUB of sdb2 into the MBR of sdb
/usr/sbin/grub-bios-setup: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0
FlexNet detected. Please backup your data before this operation. Do you want to continue? yes
dd if=/dev/sdb of=/var/log/boot-sav/log/2013-05-10__13h06boot-repair16/sdb/before_wiping.img bs=512 count=2047 seek=1
2047+0 records in
2047+0 records out
WIPE sdb : 2047 sectors * 512 bytes
dd if=/dev/zero of=/dev/sdb bs=512 count=2047 seek=1
2047+0 records in
2047+0 records out
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0


update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
error: out of memory.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 231
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.done
Warning: no Windows in /boot/grub/grub.cfg


An error occurred during the repair.


You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (250GB) disk!


```
The boot files of [The OS now in use - Ubuntu 13.04] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by oldfred on 2013-05-10
Please use Code Tags on long posts. Better to use Boot-Repair and just post link it creates to the BootInfo report.
Using advanced editor you can just highlight code or long text and click on # to auto add code tags.

I do not know RAID. And you are showing fakeRaid with XP in the first partition and a Widows 7 (or 8?)  in the second.
Grub install also is reporting flexnet which used to be a big issue, but grub has a work around. Better with two drives to leave the Windows boot loader on the Windows drive using flexnet and put grub2's boot loader in the Ubuntu drive.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by William D. on 2013-05-17
I can't fix your problem, however I can tell you how I did Windows 8 and Ubuntu without any problems at all.
Two seperate Hard Drives.  I have Windows 8 installed on a SSD and Ubuntu installed on a SATA.  Also have Windows 7 installed on a Third SATA dive.   Three Seperate Hard Drives NOT partitions.
When I turn on the Computer, I press the F12 key and a menu comes up and I select which hard drive to boot off of.

---

