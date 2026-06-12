---
title: "Win7+Ubuntu dual boot issue; No GRUB."
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by SirWatt on 2011-10-14
I'm trying to set up Win 7 and Ubuntu on my hd, but so far I haven't had any luck with getting GRUB to show up. It just boots straight to Windows.

I've tried a couple of Ubuntu installs already. First, with a live-cd and using the option to automatically install Ubuntu side to side with Windows, second, manually partitioning and installing Ubuntu. Both times I got a fatal error saying that it failed to install the bootloader.

Then I made a live-usb, installed Ubuntu 2 more times (playing with different partition setups) and although I didn't get the fatal error this time around, it just booted straight to windows.

I did a little googling and found out about 'Boot Repair', but it didn't help.

I don't know pretty much anything about linux so I don't know what else to try now. :( I'll appreciate any help.

I am using an Asus P8P67 motherboard with UEFI and also 2 HDD set up in Raid 0.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/mapper/isw_bgcbcjbja_HDD.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30824 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

isw_bgcbcjbja_HDD1: ____________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr

isw_bgcbcjbja_HDD2: ____________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

isw_bgcbcjbja_HDD3: ____________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

isw_bgcbcjbja_HDD4: ____________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_bgcbcjbja_HDD5: ____________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

isw_bgcbcjbja_HDD6: ____________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4051 MB, 4051697664 bytes
128 heads, 42 sectors/track, 1472 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *            984     7,913,471     7,912,488   c W95 FAT32 (LBA)


Drive: isw_bgcbcjbja_HDD _____________________________________________________________________

Disk /dev/mapper/isw_bgcbcjbja_HDD: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bgcbcjbja_HDD1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bgcbcjbja_HDD2            206,848   419,637,247   419,430,400   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bgcbcjbja_HDD3        419,637,248   459,637,247    40,000,000  83 Linux
/dev/mapper/isw_bgcbcjbja_HDD4        459,637,758 1,953,535,487 1,493,897,730   5 Extended
/dev/mapper/isw_bgcbcjbja_HDD5        459,637,760   467,637,247     7,999,488  82 Linux swap / Solaris
/dev/mapper/isw_bgcbcjbja_HDD6        467,637,760 1,953,535,487 1,485,897,728  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_bgcbcjbja_HDD1 94243F13243EF836                       ntfs       Sistema Reservado
/dev/mapper/isw_bgcbcjbja_HDD2 BC2C542B2C53DF48                       ntfs       
/dev/mapper/isw_bgcbcjbja_HDD3 3571794d-5da4-427b-b4c8-d471819a596c   ext4       
/dev/mapper/isw_bgcbcjbja_HDD5 705810c4-59d6-42a9-b78c-22cd05626ed1   swap       
/dev/mapper/isw_bgcbcjbja_HDD6 16357409-4922-4d9a-b3ec-d4886be3a910   ext4       
/dev/sda                                                isw_raid_member 
/dev/sdc1        11FE-263D                              vfat       PENDRIVE

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bgcbcjbja_HDD
isw_bgcbcjbja_HDD1
isw_bgcbcjbja_HDD2
isw_bgcbcjbja_HDD3
isw_bgcbcjbja_HDD5
isw_bgcbcjbja_HDD6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=================== isw_bgcbcjbja_HDD1/grldr embedded menu: ====================

--------------------------------------------------------------------------------
?g\FD/z\ACJ\DEq\A6Y\E5bF\8C\A5I\C8_\BC\CA\FF\FE(\9F\92\CDe\CC/J\82^\F02&#951;\A6\D7\83u%#\93\C0N\E9\AFq\EE&#52109;\AA1
\E2\91\EE\E3\87\DD\D4<\ABv2V\B3\9C&#1311;Oi_\E7\92x\D3oT[\8BT\95ga&#590;@\8D\A2 6G&j-T\99\946\F0\D2\F6\A5\F1\EA\C8gC7>F\FCD\B5\B7\DFv:\BE[\CE\EF0\EA\DDN".\9B\FBHBj&#708;\F7\B7[\92\88\8C\F6
\8C\91]`<
\FAW\84\E8\BE\CBq\91\83=\E8|\A36\E7\9F\CD\F4\D6'P\DA
--------------------------------------------------------------------------------

==================== isw_bgcbcjbja_HDD3/boot/grub/grub.cfg: ====================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd3,msdos3)'
search --no-floppy --fs-uuid --set=root 3571794d-5da4-427b-b4c8-d471819a596c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd3,msdos3)'
  search --no-floppy --fs-uuid --set=root 3571794d-5da4-427b-b4c8-d471819a596c
  set locale_dir=($root)/boot/grub/locale
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
    set root='(hd3,msdos3)'
    search --no-floppy --fs-uuid --set=root 3571794d-5da4-427b-b4c8-d471819a596c
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3571794d-5da4-427b-b4c8-d471819a596c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos3)'
    search --no-floppy --fs-uuid --set=root 3571794d-5da4-427b-b4c8-d471819a596c
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3571794d-5da4-427b-b4c8-d471819a596c ro recovery nomodeset 
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
    set root='(hd3,msdos3)'
    search --no-floppy --fs-uuid --set=root 3571794d-5da4-427b-b4c8-d471819a596c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos3)'
    search --no-floppy --fs-uuid --set=root 3571794d-5da4-427b-b4c8-d471819a596c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/isw_bgcbcjbja_HDD1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root 94243F13243EF836
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

======================== isw_bgcbcjbja_HDD3/etc/fstab: =========================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_bgcbcjbja_HDD3 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bgcbcjbja_HDD6 /home           ext4    defaults        0       2
/dev/mapper/isw_bgcbcjbja_HDD5 none            swap    sw              0       0
--------------------------------------------------------------------------------

============ isw_bgcbcjbja_HDD3: Location of files loaded by Grub: =============

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_bgcbcjbja_HDD4



=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
hexdump: /dev/mapper/isw_bgcbcjbja_HDD4: No such file or directory
hexdump: /dev/mapper/isw_bgcbcjbja_HDD4: No such file or directory
mdadm: No arrays found in config file or automatically


```

---

