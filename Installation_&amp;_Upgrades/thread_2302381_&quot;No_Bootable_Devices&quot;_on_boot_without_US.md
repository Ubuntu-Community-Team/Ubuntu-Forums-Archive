---
title: "&quot;No Bootable Devices&quot; on boot without USB DVD drive plugged in"
date: 2015-11-09
forum: Installation &amp; Upgrades
---

### Post by dallas10 on 2015-11-09
Hello,

I tried to install ubuntu on my older laptop. Everything seemed to have worked at first as it booted fine the first time. The next time I tried to boot it without my USB DVD drive I received "no bootable devices" at boot. I have installed multiple times with both custom and default formatting and I still ran into the same issue. 

It doesn't render my computer unusable but it's definitely annoying having to bring my drive everywhere. 

Of note: 
The DVD drive can be empty and the computer still boots.
Acer Aspire 5810T with 64bit install (tried both 15.10 and 14.04).
The boot program does not seem to recognize any USB installation sticks I've tried.

Thanks for the help.

---

### Post by ajgreeny on 2015-11-10
It will help us if you run the boot-info script from Boot-Repair in my signature below, and show us the pastebin link that you get from that.

I suspect that grub was not installed into the hard drive of your machine or you still have the boot priority wrongly set.

---

### Post by dallas10 on 2015-11-21
```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

ubuntu-vg-root: ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

ubuntu-vg-swap_1: ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   625,141,759   624,640,002   5 Extended
/dev/sda5             501,760   625,141,759   624,640,000  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/ubuntu--vg-root f61d5bb5-e21b-402c-8911-75a29ce85272   ext4       
/dev/mapper/ubuntu--vg-swap_1 809d286d-d1a8-4995-8475-2aea645d89e7   swap       
/dev/sda1        522b343e-aec5-463f-aa71-e48761637cf2   ext2       
/dev/sda5        wegv1f-2pwv-IvHK-Eky3-iDKu-A0Rx-OexB7t LVM2_member 

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Nov 21 10:16 ata-WDC_WD3200BEVT-22ZCT0_WD-WXH409913055 -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 21 10:16 ata-WDC_WD3200BEVT-22ZCT0_WD-WXH409913055-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 21 10:16 ata-WDC_WD3200BEVT-22ZCT0_WD-WXH409913055-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov 21 10:16 ata-WDC_WD3200BEVT-22ZCT0_WD-WXH409913055-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Nov 21 10:16 dm-name-ubuntu--vg-root -> ../../dm-0
lrwxrwxrwx 1 root root 10 Nov 21 10:16 dm-name-ubuntu--vg-swap_1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Nov 21 10:16 dm-uuid-LVM-FSWS2TRGa9oqQSobtdVH7tiAMYGpYmFW131KhCKRiaIMxdKK0lTX67LMVss16J21 -> ../../dm-0
lrwxrwxrwx 1 root root 10 Nov 21 10:16 dm-uuid-LVM-FSWS2TRGa9oqQSobtdVH7tiAMYGpYmFWb00TY56jcb8bI80yA3tsYKRDGozwvxBv -> ../../dm-1
lrwxrwxrwx 1 root root 10 Nov 21 10:16 lvm-pv-uuid-wegv1f-2pwv-IvHK-Eky3-iDKu-A0Rx-OexB7t -> ../../sda5
lrwxrwxrwx 1 root root  9 Nov 21 10:16 wwn-0x15642599505598238721x -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 21 10:16 wwn-0x15642599505598238721x-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 21 10:16 wwn-0x15642599505598238721x-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov 21 10:16 wwn-0x15642599505598238721x-part5 -> ../../sda5

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
ubuntu--vg-root
ubuntu--vg-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/ubuntu--vg-root /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda1        /boot                    ext2       (rw,relatime)


============================= sda1/grub/grub.cfg: ==============================

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
insmod lvm
insmod ext2
set root='lvmid/FSWS2T-RGa9-oqQS-obtd-VH7t-iAMY-GpYmFW/131KhC-KRia-IMxd-KK0l-TX67-LMVs-s16J21'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='lvmid/FSWS2T-RGa9-oqQS-obtd-VH7t-iAMY-GpYmFW/131KhC-KRia-IMxd-KK0l-TX67-LMVs-s16J21'  f61d5bb5-e21b-402c-8911-75a29ce85272
else
  search --no-floppy --fs-uuid --set=root f61d5bb5-e21b-402c-8911-75a29ce85272
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f61d5bb5-e21b-402c-8911-75a29ce85272' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
    else
      search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
    fi
    linux    /vmlinuz-3.19.0-15-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.19.0-15-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-f61d5bb5-e21b-402c-8911-75a29ce85272' {
    menuentry 'Ubuntu, with Linux 3.19.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-advanced-f61d5bb5-e21b-402c-8911-75a29ce85272' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
        else
          search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /vmlinuz-3.19.0-15-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-15-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-init-upstart-f61d5bb5-e21b-402c-8911-75a29ce85272' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
        else
          search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /vmlinuz-3.19.0-15-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-recovery-f61d5bb5-e21b-402c-8911-75a29ce85272' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
        else
          search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /vmlinuz-3.19.0-15-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-15-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
    else
      search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
    fi
    knetbsd    /memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
    else
      search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
    fi
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  f0 d8 a0 58 37 ba a8 39  a5 2b 35 76 82 54 cf a6  |...X7..9.+5v.T..|
00000010  63 f5 62 7c fa dc 02 61  6e d6 66 70 c1 59 b1 9d  |c.b|...an.fp.Y..|
00000020  e8 ca 04 f6 e4 1a f4 cc  7a e1 35 77 c9 a5 d8 a8  |........z.5w....|
00000030  26 23 63 15 1e c2 05 92  23 db 5f 21 0b 6e 44 9a  |&#c.....#._!.nD.|
00000040  b8 76 c3 7c 42 82 8b ff  a9 08 32 81 14 c3 ef 0e  |.v.|B.....2.....|
00000050  4e 50 0a e6 45 ee e6 a9  4e fb 8c b4 4e 0a ea c4  |NP..E...N...N...|
00000060  c5 c1 1e 05 ee c7 00 77  d5 de 95 f7 86 d1 32 d9  |.......w......2.|
00000070  81 87 42 c0 ec d7 89 49  90 f7 c2 7c ea 71 ba e2  |..B....I...|.q..|
00000080  74 58 62 49 89 0a e5 a4  c6 66 ff 87 ba 00 78 62  |tXbI.....f....xb|
00000090  96 25 4f 0d 4a f0 f1 cd  25 1a 90 d7 f1 73 0e 46  |.%O.J...%....s.F|
000000a0  a2 7e e6 ad 37 47 73 da  57 72 db 16 39 1e c3 e0  |.~..7Gs.Wr..9...|
000000b0  44 fa d8 d4 1e bf ed f3  7e cb 1d c4 e3 52 0a e5  |D.......~....R..|
000000c0  3c 9d 5d cc 4a 33 a4 0b  c2 b5 98 95 ef a3 0b e7  |<.].J3..........|
000000d0  3e fd fe f3 d4 7e 52 35  46 f6 2e cd e1 5d 9e af  |>....~R5F....]..|
000000e0  db 90 cf 59 17 86 5d 99  b3 74 03 5f f2 0d d7 36  |...Y..]..t._...6|
000000f0  35 7e 2d 93 0f 1c b8 ef  f5 cf 42 79 ec a4 af f0  |5~-.......By....|
00000100  e4 c0 42 9b dd 06 13 11  1b 65 51 b4 84 ff 3a 19  |..B......eQ...:.|
00000110  4b 29 4d b6 93 43 bd db  2c 00 83 ce 01 60 fd 50  |K)M..C..,....`.P|
00000120  0c c8 98 7b e0 dc 1f 50  6e ab 9a 88 b3 e8 33 de  |...{...Pn.....3.|
00000130  3c 23 99 30 21 d2 d7 15  f5 4d 36 d2 e0 cf 4d 7c  |<#.0!....M6...M||
00000140  e5 2a 9a a7 c8 13 4c 64  44 51 95 84 5a f0 24 ce  |.*....LdDQ..Z.$.|
00000150  65 1a 85 94 de f0 14 26  1a 64 3d 17 ef 9b f2 79  |e......&.d=....y|
00000160  f5 fe 68 b0 43 67 86 ce  5c 99 ba 2e 96 12 e5 c1  |..h.Cg..\.......|
00000170  41 ed 4d 21 8a 41 89 83  06 ac 84 b5 4d ce 4e e4  |A.M!.A......M.N.|
00000180  81 6e 3d c2 14 0e 7c 03  60 e8 c0 a2 be 33 f6 cc  |.n=...|.`....3..|
00000190  6b 4d 60 ce 84 60 d7 cf  35 7e b7 06 36 e2 25 75  |kM`..`..5~..6.%u|
000001a0  7a ec ee 95 1e 4d 9f 5e  8a 74 d3 9d 7d fe 56 54  |z....M.^.t..}.VT|
000001b0  75 57 d8 2c 1a ff 96 8d  bf 6c 1e 1d fc ff 00 3b  |uW.,.....l.....;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 40 3b 25 00 00  |...........@;%..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on ubuntu-vg-root


Unknown BootLoader on ubuntu-vg-swap_1



=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 9 (/proc/5076/mounts) leaked on lvs invocation. Parent PID 11543: bash
File descriptor 63 (pipe:[39078]) leaked on lvs invocation. Parent PID 11543: bash
File descriptor 9 (/proc/5076/mounts) leaked on lvchange invocation. Parent PID 11899: bash
File descriptor 63 (pipe:[39078]) leaked on lvchange invocation. Parent PID 11899: bash
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root
  Volume group "ubuntu-vg-root" not found
  Skipping volume group ubuntu-vg-root
hexdump: /dev/mapper/ubuntu-vg-root: No such file or directory
hexdump: /dev/mapper/ubuntu-vg-root: No such file or directory
File descriptor 9 (/proc/5076/mounts) leaked on lvchange invocation. Parent PID 11899: bash
File descriptor 63 (pipe:[39078]) leaked on lvchange invocation. Parent PID 11899: bash
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1
  Volume group "ubuntu-vg-swap_1" not found
  Skipping volume group ubuntu-vg-swap_1
hexdump: /dev/mapper/ubuntu-vg-swap_1: No such file or directory
hexdump: /dev/mapper/ubuntu-vg-swap_1: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-11-21__10h15 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
BLKID BEFORE LVM ACTIVATION:
/dev/sda1: UUID="522b343e-aec5-463f-aa71-e48761637cf2" TYPE="ext2" PARTUUID="21f00e49-01"
/dev/sda5: UUID="wegv1f-2pwv-IvHK-Eky3-iDKu-A0Rx-OexB7t" TYPE="LVM2_member" PARTUUID="21f00e49-05"
/dev/mapper/ubuntu--vg-root: UUID="f61d5bb5-e21b-402c-8911-75a29ce85272" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="809d286d-d1a8-4995-8475-2aea645d89e7" TYPE="swap"
MODPROBE
VGSCAN
File descriptor 9 (/proc/5076/mounts) leaked on vgscan invocation. Parent PID 5084: /bin/bash
Reading all physical volumes.  This may take a while...
Found volume group "ubuntu-vg" using metadata type lvm2
VGCHANGE
File descriptor 9 (/proc/5076/mounts) leaked on vgchange invocation. Parent PID 5084: /bin/bash
2 logical volume(s) in volume group "ubuntu-vg" now active
File descriptor 9 (/proc/5076/mounts) leaked on lvscan invocation. Parent PID 5084: /bin/bash
LVSCAN:
ACTIVE            '/dev/ubuntu-vg/root' [293.90 GiB] inherit
ACTIVE            '/dev/ubuntu-vg/swap_1' [3.93 GiB] inherit
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Is there RAID on this computer? no
File descriptor 9 (/proc/5076/mounts) leaked on lvs invocation. Parent PID 6893: /bin/sh
boot-repair is executed in installed-session (Ubuntu 15.04, vivid, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/vmlinuz-3.19.0-15-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
Set sda as corresponding disk of mapper/ubuntu--vg-root
Set sda as corresponding disk of mapper/ubuntu--vg-root

=================== os-prober:
/dev/mapper/ubuntu--vg-root:The OS now in use - Ubuntu 15.04 CurrentSession:linux

=================== blkid:
/dev/sda1: UUID="522b343e-aec5-463f-aa71-e48761637cf2" TYPE="ext2" PARTUUID="21f00e49-01"
/dev/sda5: UUID="wegv1f-2pwv-IvHK-Eky3-iDKu-A0Rx-OexB7t" TYPE="LVM2_member" PARTUUID="21f00e49-05"
/dev/mapper/ubuntu--vg-root: UUID="f61d5bb5-e21b-402c-8911-75a29ce85272" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="809d286d-d1a8-4995-8475-2aea645d89e7" TYPE="swap"

Set sda as corresponding disk of mapper/ubuntu--vg-root

1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

sfdisk: Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 22  2015 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr  6  2015 00_header
-rwxr-xr-x 1 root root  6058 Feb 11  2015 05_debian_theme
-rwxr-xr-x 1 root root 12261 Apr  6  2015 10_linux
-rwxr-xr-x 1 root root 11082 Apr  6  2015 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar  6  2015 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr  6  2015 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr  6  2015 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  6  2015 40_custom
-rwxr-xr-x 1 root root   216 Apr  6  2015 41_custom
-rw-r--r-- 1 root root   483 Apr  6  2015 README




=================== /etc/default/grub :

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



/boot detected in the fstab of mapper/ubuntu--vg-root: UUID=522b343e-aec5-463f-aa71-e48761637cf2  (sda1)

=================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
mapper/ubuntu--vg-root    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
sda1    : sda,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /boot.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type      File system  Flags
1      1049kB  256MB  255MB  primary   ext2         boot
2      257MB   320GB  320GB  extended
5      257MB   320GB  320GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 316GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End    Size   File system  Flags
1      0.00B  316GB  316GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4219MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End     Size    File system     Flags
1      0.00B  4219MB  4219MB  linux-swap(v1)

=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:512:msdos:ATA WDC WD3200BEVT-2:;
1:1049kB:256MB:255MB:ext2::boot;
2:257MB:320GB:320GB:::;
5:257MB:320GB:320GB:::lvm;

BYT;
/dev/mapper/ubuntu--vg-root:316GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:316GB:316GB:ext4::;

BYT;
/dev/mapper/ubuntu--vg-swap_1:4219MB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:4219MB:4219MB:linux-swap(v1)::;

=================== lsblk:
KNAME TYPE FSTYPE        SIZE LABEL MODEL            UUID
sda   disk             298.1G       WDC WD3200BEVT-2
sda1  part ext2          243M                        522b343e-aec5-463f-aa71-e48761637cf2
sda2  part                 1K
sda5  part LVM2_member 297.9G                        wegv1f-2pwv-IvHK-Eky3-iDKu-A0Rx-OexB7t
dm-0  lvm  ext4        293.9G                        f61d5bb5-e21b-402c-8911-75a29ce85272
dm-1  lvm  swap            4G                        809d286d-d1a8-4995-8475-2aea645d89e7

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /boot
sda2     1  0  0
sda5     1  0  0
dm-0     1  0  0 running /
dm-1     1  0  0 running [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=1976212k,nr_inodes=494053,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=397568k,mode=755)
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=21,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot type ext2 (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=397568k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dm-0 dm-1 dri ecryptfs fb0 fd full fuse hpet hugepages i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 initctl input kmsg log mapper mcelog media0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sg0 shm snapshot snd stderr stdin stdout ubuntu-vg uhid uinput urandom v4l vfio vga_arbiter vhci vhost-net video0 xconsole zero
ls /dev/mapper:  control ubuntu--vg-root ubuntu--vg-swap_1
ls: cannot access : No such file or directory

=================== df -Th:

Filesystem                  Type      Size  Used Avail Use% Mounted on
udev                        devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs                       tmpfs     389M  6.0M  383M   2% /run
/dev/mapper/ubuntu--vg-root ext4      290G  4.1G  271G   2% /
tmpfs                       tmpfs     1.9G  156K  1.9G   1% /dev/shm
tmpfs                       tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                       tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1                   ext2      236M   42M  182M  19% /boot
cgmfs                       tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs                       tmpfs     389M   88K  389M   1% /run/user/1000

=================== fdisk -l:

Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x21f00e49

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    499711    497664   243M 83 Linux
/dev/sda2       501758 625141759 624640002 297.9G  5 Extended
/dev/sda5       501760 625141759 624640000 297.9G 8e Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 293.9 GiB, 315575238656 bytes, 616357888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mapper/ubuntu--vg-swap_1: 4 GiB, 4219469824 bytes, 8241152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to enable-lvm) and reinstall the grub2 of mapper/ubuntu--vg-root into the MBR of sda, using the following options:        sda1/boot,
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.
```

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 305690 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

ubuntu-vg-root: ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

ubuntu-vg-swap_1: ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   625,141,759   624,640,002   5 Extended
/dev/sda5             501,760   625,141,759   624,640,000  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/ubuntu--vg-root f61d5bb5-e21b-402c-8911-75a29ce85272   ext4       
/dev/mapper/ubuntu--vg-swap_1 809d286d-d1a8-4995-8475-2aea645d89e7   swap       
/dev/sda1        522b343e-aec5-463f-aa71-e48761637cf2   ext2       
/dev/sda5        wegv1f-2pwv-IvHK-Eky3-iDKu-A0Rx-OexB7t LVM2_member 

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Nov 21 10:33 ata-WDC_WD3200BEVT-22ZCT0_WD-WXH409913055 -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 21 10:33 ata-WDC_WD3200BEVT-22ZCT0_WD-WXH409913055-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 21 10:33 ata-WDC_WD3200BEVT-22ZCT0_WD-WXH409913055-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov 21 10:33 ata-WDC_WD3200BEVT-22ZCT0_WD-WXH409913055-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Nov 21 10:22 dm-name-ubuntu--vg-root -> ../../dm-0
lrwxrwxrwx 1 root root 10 Nov 21 10:22 dm-name-ubuntu--vg-swap_1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Nov 21 10:22 dm-uuid-LVM-FSWS2TRGa9oqQSobtdVH7tiAMYGpYmFW131KhCKRiaIMxdKK0lTX67LMVss16J21 -> ../../dm-0
lrwxrwxrwx 1 root root 10 Nov 21 10:22 dm-uuid-LVM-FSWS2TRGa9oqQSobtdVH7tiAMYGpYmFWb00TY56jcb8bI80yA3tsYKRDGozwvxBv -> ../../dm-1
lrwxrwxrwx 1 root root 10 Nov 21 10:33 lvm-pv-uuid-wegv1f-2pwv-IvHK-Eky3-iDKu-A0Rx-OexB7t -> ../../sda5
lrwxrwxrwx 1 root root  9 Nov 21 10:33 wwn-0x15642599505598238721x -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 21 10:33 wwn-0x15642599505598238721x-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 21 10:33 wwn-0x15642599505598238721x-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov 21 10:33 wwn-0x15642599505598238721x-part5 -> ../../sda5

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
ubuntu--vg-root
ubuntu--vg-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/ubuntu--vg-root /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda1        /boot                    ext2       (rw,relatime)


============================= sda1/grub/grub.cfg: ==============================

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
insmod lvm
insmod ext2
set root='lvmid/FSWS2T-RGa9-oqQS-obtd-VH7t-iAMY-GpYmFW/131KhC-KRia-IMxd-KK0l-TX67-LMVs-s16J21'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='lvmid/FSWS2T-RGa9-oqQS-obtd-VH7t-iAMY-GpYmFW/131KhC-KRia-IMxd-KK0l-TX67-LMVs-s16J21'  f61d5bb5-e21b-402c-8911-75a29ce85272
else
  search --no-floppy --fs-uuid --set=root f61d5bb5-e21b-402c-8911-75a29ce85272
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
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
if background_color 44,0,30,0; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f61d5bb5-e21b-402c-8911-75a29ce85272' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
    else
      search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
    fi
    linux    /vmlinuz-3.19.0-33-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.19.0-33-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-f61d5bb5-e21b-402c-8911-75a29ce85272' {
    menuentry 'Ubuntu, with Linux 3.19.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-advanced-f61d5bb5-e21b-402c-8911-75a29ce85272' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
        else
          search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
        fi
        echo    'Loading Linux 3.19.0-33-generic ...'
        linux    /vmlinuz-3.19.0-33-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-33-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-init-upstart-f61d5bb5-e21b-402c-8911-75a29ce85272' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
        else
          search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
        fi
        echo    'Loading Linux 3.19.0-33-generic ...'
        linux    /vmlinuz-3.19.0-33-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-recovery-f61d5bb5-e21b-402c-8911-75a29ce85272' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
        else
          search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
        fi
        echo    'Loading Linux 3.19.0-33-generic ...'
        linux    /vmlinuz-3.19.0-33-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-advanced-f61d5bb5-e21b-402c-8911-75a29ce85272' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
        else
          search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /vmlinuz-3.19.0-15-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-15-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-init-upstart-f61d5bb5-e21b-402c-8911-75a29ce85272' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
        else
          search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /vmlinuz-3.19.0-15-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-recovery-f61d5bb5-e21b-402c-8911-75a29ce85272' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  522b343e-aec5-463f-aa71-e48761637cf2
        else
          search --no-floppy --fs-uuid --set=root 522b343e-aec5-463f-aa71-e48761637cf2
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /vmlinuz-3.19.0-15-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.19.0-15-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
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

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  f0 d8 a0 58 37 ba a8 39  a5 2b 35 76 82 54 cf a6  |...X7..9.+5v.T..|
00000010  63 f5 62 7c fa dc 02 61  6e d6 66 70 c1 59 b1 9d  |c.b|...an.fp.Y..|
00000020  e8 ca 04 f6 e4 1a f4 cc  7a e1 35 77 c9 a5 d8 a8  |........z.5w....|
00000030  26 23 63 15 1e c2 05 92  23 db 5f 21 0b 6e 44 9a  |&#c.....#._!.nD.|
00000040  b8 76 c3 7c 42 82 8b ff  a9 08 32 81 14 c3 ef 0e  |.v.|B.....2.....|
00000050  4e 50 0a e6 45 ee e6 a9  4e fb 8c b4 4e 0a ea c4  |NP..E...N...N...|
00000060  c5 c1 1e 05 ee c7 00 77  d5 de 95 f7 86 d1 32 d9  |.......w......2.|
00000070  81 87 42 c0 ec d7 89 49  90 f7 c2 7c ea 71 ba e2  |..B....I...|.q..|
00000080  74 58 62 49 89 0a e5 a4  c6 66 ff 87 ba 00 78 62  |tXbI.....f....xb|
00000090  96 25 4f 0d 4a f0 f1 cd  25 1a 90 d7 f1 73 0e 46  |.%O.J...%....s.F|
000000a0  a2 7e e6 ad 37 47 73 da  57 72 db 16 39 1e c3 e0  |.~..7Gs.Wr..9...|
000000b0  44 fa d8 d4 1e bf ed f3  7e cb 1d c4 e3 52 0a e5  |D.......~....R..|
000000c0  3c 9d 5d cc 4a 33 a4 0b  c2 b5 98 95 ef a3 0b e7  |<.].J3..........|
000000d0  3e fd fe f3 d4 7e 52 35  46 f6 2e cd e1 5d 9e af  |>....~R5F....]..|
000000e0  db 90 cf 59 17 86 5d 99  b3 74 03 5f f2 0d d7 36  |...Y..]..t._...6|
000000f0  35 7e 2d 93 0f 1c b8 ef  f5 cf 42 79 ec a4 af f0  |5~-.......By....|
00000100  e4 c0 42 9b dd 06 13 11  1b 65 51 b4 84 ff 3a 19  |..B......eQ...:.|
00000110  4b 29 4d b6 93 43 bd db  2c 00 83 ce 01 60 fd 50  |K)M..C..,....`.P|
00000120  0c c8 98 7b e0 dc 1f 50  6e ab 9a 88 b3 e8 33 de  |...{...Pn.....3.|
00000130  3c 23 99 30 21 d2 d7 15  f5 4d 36 d2 e0 cf 4d 7c  |<#.0!....M6...M||
00000140  e5 2a 9a a7 c8 13 4c 64  44 51 95 84 5a f0 24 ce  |.*....LdDQ..Z.$.|
00000150  65 1a 85 94 de f0 14 26  1a 64 3d 17 ef 9b f2 79  |e......&.d=....y|
00000160  f5 fe 68 b0 43 67 86 ce  5c 99 ba 2e 96 12 e5 c1  |..h.Cg..\.......|
00000170  41 ed 4d 21 8a 41 89 83  06 ac 84 b5 4d ce 4e e4  |A.M!.A......M.N.|
00000180  81 6e 3d c2 14 0e 7c 03  60 e8 c0 a2 be 33 f6 cc  |.n=...|.`....3..|
00000190  6b 4d 60 ce 84 60 d7 cf  35 7e b7 06 36 e2 25 75  |kM`..`..5~..6.%u|
000001a0  7a ec ee 95 1e 4d 9f 5e  8a 74 d3 9d 7d fe 56 54  |z....M.^.t..}.VT|
000001b0  75 57 d8 2c 1a ff 96 8d  bf 6c 1e 1d fc ff 00 3b  |uW.,.....l.....;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 40 3b 25 00 00  |...........@;%..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on ubuntu-vg-root


Unknown BootLoader on ubuntu-vg-swap_1



=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 9 (/proc/12650/mounts) leaked on lvs invocation. Parent PID 6177: bash
File descriptor 63 (pipe:[46663]) leaked on lvs invocation. Parent PID 6177: bash
File descriptor 9 (/proc/12650/mounts) leaked on lvchange invocation. Parent PID 6574: bash
File descriptor 63 (pipe:[46663]) leaked on lvchange invocation. Parent PID 6574: bash
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root
  Volume group "ubuntu-vg-root" not found
  Skipping volume group ubuntu-vg-root
hexdump: /dev/mapper/ubuntu-vg-root: No such file or directory
hexdump: /dev/mapper/ubuntu-vg-root: No such file or directory
File descriptor 9 (/proc/12650/mounts) leaked on lvchange invocation. Parent PID 6574: bash
File descriptor 63 (pipe:[46663]) leaked on lvchange invocation. Parent PID 6574: bash
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1
  Volume group "ubuntu-vg-swap_1" not found
  Skipping volume group ubuntu-vg-swap_1
hexdump: /dev/mapper/ubuntu-vg-swap_1: No such file or directory
hexdump: /dev/mapper/ubuntu-vg-swap_1: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-11-21__10h22 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
BLKID BEFORE LVM ACTIVATION:
/dev/sda1: UUID="522b343e-aec5-463f-aa71-e48761637cf2" TYPE="ext2" PARTUUID="21f00e49-01"
/dev/sda5: UUID="wegv1f-2pwv-IvHK-Eky3-iDKu-A0Rx-OexB7t" TYPE="LVM2_member" PARTUUID="21f00e49-05"
/dev/mapper/ubuntu--vg-root: UUID="f61d5bb5-e21b-402c-8911-75a29ce85272" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="809d286d-d1a8-4995-8475-2aea645d89e7" TYPE="swap"
MODPROBE
VGSCAN
File descriptor 9 (/proc/12650/mounts) leaked on vgscan invocation. Parent PID 12657: /bin/bash
Reading all physical volumes.  This may take a while...
Found volume group "ubuntu-vg" using metadata type lvm2
VGCHANGE
File descriptor 9 (/proc/12650/mounts) leaked on vgchange invocation. Parent PID 12657: /bin/bash
2 logical volume(s) in volume group "ubuntu-vg" now active
File descriptor 9 (/proc/12650/mounts) leaked on lvscan invocation. Parent PID 12657: /bin/bash
LVSCAN:
ACTIVE            '/dev/ubuntu-vg/root' [293.90 GiB] inherit
ACTIVE            '/dev/ubuntu-vg/swap_1' [3.93 GiB] inherit
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Is there RAID on this computer? no
File descriptor 9 (/proc/12650/mounts) leaked on lvs invocation. Parent PID 14453: /bin/sh
boot-repair is executed in installed-session (Ubuntu 15.04, vivid, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/vmlinuz-3.19.0-15-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
Set sda as corresponding disk of mapper/ubuntu--vg-root
Set sda as corresponding disk of mapper/ubuntu--vg-root

=================== os-prober:
/dev/mapper/ubuntu--vg-root:The OS now in use - Ubuntu 15.04 CurrentSession:linux

=================== blkid:
/dev/sda1: UUID="522b343e-aec5-463f-aa71-e48761637cf2" TYPE="ext2" PARTUUID="21f00e49-01"
/dev/sda5: UUID="wegv1f-2pwv-IvHK-Eky3-iDKu-A0Rx-OexB7t" TYPE="LVM2_member" PARTUUID="21f00e49-05"
/dev/mapper/ubuntu--vg-root: UUID="f61d5bb5-e21b-402c-8911-75a29ce85272" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="809d286d-d1a8-4995-8475-2aea645d89e7" TYPE="swap"

Set sda as corresponding disk of mapper/ubuntu--vg-root

1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

sfdisk: Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 22  2015 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr  6  2015 00_header
-rwxr-xr-x 1 root root  6058 Feb 11  2015 05_debian_theme
-rwxr-xr-x 1 root root 12261 Apr  6  2015 10_linux
-rwxr-xr-x 1 root root 11082 Apr  6  2015 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar  6  2015 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr  6  2015 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr  6  2015 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  6  2015 40_custom
-rwxr-xr-x 1 root root   216 Apr  6  2015 41_custom
-rw-r--r-- 1 root root   483 Apr  6  2015 README




=================== /etc/default/grub :

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



/boot detected in the fstab of mapper/ubuntu--vg-root: UUID=522b343e-aec5-463f-aa71-e48761637cf2  (sda1)

=================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
mapper/ubuntu--vg-root    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
sda1    : sda,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /boot.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type      File system  Flags
1      1049kB  256MB  255MB  primary   ext2         boot
2      257MB   320GB  320GB  extended
5      257MB   320GB  320GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 316GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End    Size   File system  Flags
1      0.00B  316GB  316GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4219MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End     Size    File system     Flags
1      0.00B  4219MB  4219MB  linux-swap(v1)

=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:512:msdos:ATA WDC WD3200BEVT-2:;
1:1049kB:256MB:255MB:ext2::boot;
2:257MB:320GB:320GB:::;
5:257MB:320GB:320GB:::lvm;

BYT;
/dev/mapper/ubuntu--vg-root:316GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:316GB:316GB:ext4::;

BYT;
/dev/mapper/ubuntu--vg-swap_1:4219MB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:4219MB:4219MB:linux-swap(v1)::;

=================== lsblk:
KNAME TYPE FSTYPE        SIZE LABEL MODEL            UUID
sda   disk             298.1G       WDC WD3200BEVT-2
sda1  part ext2          243M                        522b343e-aec5-463f-aa71-e48761637cf2
sda2  part                 1K
sda5  part LVM2_member 297.9G                        wegv1f-2pwv-IvHK-Eky3-iDKu-A0Rx-OexB7t
dm-0  lvm  ext4        293.9G                        f61d5bb5-e21b-402c-8911-75a29ce85272
dm-1  lvm  swap            4G                        809d286d-d1a8-4995-8475-2aea645d89e7

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /boot
sda2     1  0  0
sda5     1  0  0
dm-0     1  0  0 running /
dm-1     1  0  0 running [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=1976212k,nr_inodes=494053,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=397568k,mode=755)
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=21,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot type ext2 (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=397568k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dm-0 dm-1 dri ecryptfs fb0 fd full fuse hpet hugepages i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 initctl input kmsg log mapper mcelog media0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sg0 shm snapshot snd stderr stdin stdout ubuntu-vg uhid uinput urandom v4l vfio vga_arbiter vhci vhost-net video0 xconsole zero
ls /dev/mapper:  control ubuntu--vg-root ubuntu--vg-swap_1
ls: cannot access : No such file or directory

=================== df -Th:

Filesystem                  Type      Size  Used Avail Use% Mounted on
udev                        devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs                       tmpfs     389M  6.0M  383M   2% /run
/dev/mapper/ubuntu--vg-root ext4      290G  4.1G  271G   2% /
tmpfs                       tmpfs     1.9G  156K  1.9G   1% /dev/shm
tmpfs                       tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                       tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1                   ext2      236M   42M  182M  19% /boot
cgmfs                       tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs                       tmpfs     389M   92K  389M   1% /run/user/1000

=================== fdisk -l:

Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x21f00e49

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    499711    497664   243M 83 Linux
/dev/sda2       501758 625141759 624640002 297.9G  5 Extended
/dev/sda5       501760 625141759 624640000 297.9G 8e Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 293.9 GiB, 315575238656 bytes, 616357888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mapper/ubuntu--vg-swap_1: 4 GiB, 4219469824 bytes, 8241152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes



=================== Recommended repair
The default repair of the Boot-Repair utility will purge (in order to enable-lvm) and reinstall the grub2 of mapper/ubuntu--vg-root into the MBR of sda, using the following options:        sda1/boot,
Additional repair will be performed: unhide-bootmenu-10s


apt-get -y --force-yes update
Purge the GRUB of mapper/ubuntu--vg-root
grub-pc available

The following extra packages will be installed:
grub-common grub-pc-bin grub2-common
Suggested packages:
multiboot-doc grub-emu xorriso desktop-base
The following packages will be upgraded:
grub-common grub-pc grub-pc-bin grub2-common
4 upgraded, 0 newly installed, 0 to remove and 292 not upgraded.
DEBCHECK debOK, grub-pc
DEBCHECK debOK
shim-signed available
linux-signed-generic available
Please type: sudo dpkg --configure -ansudo apt-get install -fynsudo apt-get install -y --force-yes lvm2nsudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Nov 21 10:28 grub.d
total 4
-rwxr-xr-x 1 root root 1992 Mar  6  2015 20_memtest86+


/boot detected in the fstab of mapper/ubuntu--vg-root: UUID=522b343e-aec5-463f-aa71-e48761637cf2  (sda1)
Then type: sudo apt-get install -y --force-yes grub-pc linux-generic

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Nov 21 10:30 grub.d
drwxr-xr-x  2 root root    4096 Nov 21 10:28 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 Oct 12 07:19 00_header
-rwxr-xr-x 1 root root  6058 Feb 11  2015 05_debian_theme
-rwxr-xr-x 1 root root 12261 Oct 12 07:19 10_linux
-rwxr-xr-x 1 root root 11082 Oct 12 07:19 20_linux_xen
-rwxr-xr-x 1 root root 11692 Oct 12 07:19 30_os-prober
-rwxr-xr-x 1 root root  1416 Oct 12 07:19 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 12 07:19 40_custom
-rwxr-xr-x 1 root root   216 Oct 12 07:19 41_custom
-rw-r--r-- 1 root root   483 Oct 12 07:19 README




=================== /etc/default/grub :

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



/boot detected in the fstab of mapper/ubuntu--vg-root: UUID=522b343e-aec5-463f-aa71-e48761637cf2  (sda1)
Unhide GRUB boot menu in mapper/ubuntu--vg-root/etc/default/grub

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Nov 21 10:30 grub.d
drwxr-xr-x  2 root root    4096 Nov 21 10:28 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 Oct 12 07:19 00_header
-rwxr-xr-x 1 root root  6058 Feb 11  2015 05_debian_theme
-rwxr-xr-x 1 root root 12261 Oct 12 07:19 10_linux
-rwxr-xr-x 1 root root 11082 Oct 12 07:19 20_linux_xen
-rwxr-xr-x 1 root root 11692 Oct 12 07:19 30_os-prober
-rwxr-xr-x 1 root root  1416 Oct 12 07:19 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 12 07:19 40_custom
-rwxr-xr-x 1 root root   216 Oct 12 07:19 41_custom
-rw-r--r-- 1 root root   483 Oct 12 07:19 README




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



/boot detected in the fstab of mapper/ubuntu--vg-root: UUID=522b343e-aec5-463f-aa71-e48761637cf2  (sda1)

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
Subsystem: Acer Incorporated [ALI] Device [1025:022b]
Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-22ubuntu1.2,grub-install (GRUB) 2.

Reinstall the GRUB of mapper/ubuntu--vg-root into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

update-grub
Generating grub configuration file ...
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3474: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3474: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3474: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3474: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3485: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3485: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3485: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3485: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3497: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3497: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3497: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3497: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on vgs [EMAIL="invocation.SET@_progressbar1.pulse"]invocation.SET@_progressbar1.pulse[/EMAIL]()
Parent PID 3508: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3508: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3508: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3508: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3564: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3564: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3564: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3564: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3998: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3998: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on vgs invocation. Parent PID 3998: /usr/sbin/grub-probe
File descriptor 63 (pipe:[46663]) leaked on vgs invocation. Parent PID 3998: /usr/sbin/grub-probe
File descriptor 9 (/proc/12650/mounts) leaked on lvs invocation. Parent PID 4091: /bin/sh
File descriptor 63 (pipe:[46663]) leaked on lvs invocation. Parent PID 4091: /bin/sh
Unhide GRUB boot menu in mapper/ubuntu--vg-root/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
```

Sorry for the large posts but it wouldn't let me attach the text files. The top one is the boot-info before repair and the lower one is the boot-info after boot repair. I still have the same issue. 

Thanks

---

### Post by oldfred on 2015-11-21
You can use code tags or the # icon in the forum's advanced editor.
Or just attach the links to the pastebin that Boot-Repair provides.

Did repair let you boot?

---

### Post by dallas10 on 2015-11-22
I still have to have my DVD drive attached to boot.

---

### Post by oldfred on 2015-11-23
You are not getting grub installed to sda, do not install to a partition like sda1.

Run Boot-Repair's advanced mode and do the full uninstall/reinstall of grub. Make sure your LVM is mounted and /boot option ticked so they are included.

---

### Post by dallas10 on 2015-11-25
> **oldfred said:**
> You are not getting grub installed to sda, do not install to a partition like sda1.

Run Boot-Repair's advanced mode and do the full uninstall/reinstall of grub. Make sure your LVM is mounted and /boot option ticked so they are included.

paste.ubuntu.com/13499934
Still doesn't work. Maybe I misinterpreted - by uninstall you meant purge right? And I ticked all options in the install step.

---

### Post by dallas10 on 2015-11-25
I'm pretty sure GRUB is installed as it still opens when my cd drive is connected. Just to be clear it isn't LiveCD that opens when it is connected.

---

### Post by oldfred on 2015-11-25
[http://paste.ubuntu.com/13499934/](http://paste.ubuntu.com/13499934/)

It says grub is installed with no error.

Are you perhaps booting thru grub, but have another issue. Grub menu will not normally show if only one system, not dual boot.
Hold shift key from BIOS until grub menu appears. If that works, you may need a boot parameter for your Intel video.

Do not use nomodeset, but use one of the Intel boot parameters. But add it like the examples shown on nomodeset.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

      
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

---

