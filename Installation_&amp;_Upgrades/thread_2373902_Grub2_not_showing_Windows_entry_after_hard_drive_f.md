---
title: "Grub2 not showing Windows entry after hard drive failure"
date: 2017-10-10
forum: Installation &amp; Upgrades
---

### Post by tracy6 on 2017-10-10
My hard drive started showing signs of failure recently. This single hard drive had a dual boot system that had Windows 7 and Ubuntu 16.04.  I was backed up, so I was OK, right?  Right!
I backed up my Windows partition using Acronis True Image with a sector by sector scheme and had the backup stored on an external USB drive.  I also had Ubuntu stored on that same USB drive having backed up the home directory using the Ubuntu program "Backups".

Well, long story short, I had beaucoup problems with the restoration of the data. But finally, it took after repartitioning the new hard drive with the Acronis Rescue disk.  I installed Windows from the USB drive and then requested that the MBR be restored.

Upon rebooting, there was no grub (I thought this might have been stored by Acronis in the MBR), only a >grub rescue prompt.  Anyway, the repartitioning left me the original partition area for the Ubuntu which I installed from a Live CD.  I then restored my Linux backup using the restore function of "Backups".  I then used "Boot-repair" from the Live CD to fix the grub.

Upon reboot, I found that the only entry in the grub was the Ubuntu partition, and the Ubuntu advanced and Mem86 entries.  No Windows.  I updated the grub.  No change.  Os-prober saw no windows information.  I followed another suggestion in the forums to make a 15_Windows file, make it executable, and then update the grub.  Still nothing.  I stopped at that point to get more advice as I know my way around Linux but I'm certainly no expert.

Here is the output of fdisk -l:

```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 470018047 470016000 224.1G  7 HPFS/NTFS/exFAT
/dev/sda2       470020094 976771071 506750978 241.7G  5 Extended
/dev/sda5       470020096 479782911   9762816   4.7G 83 Linux
/dev/sda6       479784960 495407103  15622144   7.5G 82 Linux swap / Solaris
/dev/sda7       495409152 976771071 481361920 229.5G 83 Linux


```

I also ran BootInfoScript.  Here is the output of that:

```
                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   470,018,047   470,016,000   7 NTFS / exFAT / HPFS
/dev/sda2         470,020,094   976,771,071   506,750,978   5 Extended
/dev/sda5         470,020,096   479,782,911     9,762,816  83 Linux
/dev/sda6         479,784,960   495,407,103    15,622,144  82 Linux swap / Solaris
/dev/sda7         495,409,152   976,771,071   481,361,920  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E85823B358238004                       ntfs       Drive C
/dev/sda5        71c9e993-a48b-4038-a553-d1ac0b8628f7   ext4       
/dev/sda6        06184aba-2183-46f5-8e25-4ad5b230db90   swap       
/dev/sda7        d3b1a377-c67b-4578-ba0f-00e0c416adb9   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda7        /home                    ext4       (rw,relatime,data=ordered)


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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  71c9e993-a48b-4038-a553-d1ac0b8628f7
else
  search --no-floppy --fs-uuid --set=root 71c9e993-a48b-4038-a553-d1ac0b8628f7
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
  set timeout=30
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-71c9e993-a48b-4038-a553-d1ac0b8628f7' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  71c9e993-a48b-4038-a553-d1ac0b8628f7
    else
      search --no-floppy --fs-uuid --set=root 71c9e993-a48b-4038-a553-d1ac0b8628f7
    fi
    linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=71c9e993-a48b-4038-a553-d1ac0b8628f7 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-21-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-71c9e993-a48b-4038-a553-d1ac0b8628f7' {
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-71c9e993-a48b-4038-a553-d1ac0b8628f7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  71c9e993-a48b-4038-a553-d1ac0b8628f7
        else
          search --no-floppy --fs-uuid --set=root 71c9e993-a48b-4038-a553-d1ac0b8628f7
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=71c9e993-a48b-4038-a553-d1ac0b8628f7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-71c9e993-a48b-4038-a553-d1ac0b8628f7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  71c9e993-a48b-4038-a553-d1ac0b8628f7
        else
          search --no-floppy --fs-uuid --set=root 71c9e993-a48b-4038-a553-d1ac0b8628f7
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=71c9e993-a48b-4038-a553-d1ac0b8628f7 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-71c9e993-a48b-4038-a553-d1ac0b8628f7' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  71c9e993-a48b-4038-a553-d1ac0b8628f7
        else
          search --no-floppy --fs-uuid --set=root 71c9e993-a48b-4038-a553-d1ac0b8628f7
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=71c9e993-a48b-4038-a553-d1ac0b8628f7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  71c9e993-a48b-4038-a553-d1ac0b8628f7
    else
      search --no-floppy --fs-uuid --set=root 71c9e993-a48b-4038-a553-d1ac0b8628f7
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  71c9e993-a48b-4038-a553-d1ac0b8628f7
    else
      search --no-floppy --fs-uuid --set=root 71c9e993-a48b-4038-a553-d1ac0b8628f7
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=71c9e993-a48b-4038-a553-d1ac0b8628f7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=d3b1a377-c67b-4578-ba0f-00e0c416adb9 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=06184aba-2183-46f5-8e25-4ad5b230db90 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  90 92 83 3c 74 5c 8b 3c  b1 37 8c 3c cc dd 7a 3c  |...<t\.<.7.<..z<|
00000010  bb 2d 7b 3c 86 be 83 3c  d3 0e 62 3c 82 0e 2d 3c  |.-{<...<..b<..-<|
00000020  49 e2 12 3c bf 3a 09 3c  eb ee 13 3c 07 69 2b 3c  |I..<.:.<...<.i+<|
00000030  c6 29 47 3c c8 a4 89 3c  a5 61 bf 3c e8 96 d2 3c  |.)G<...<.a.<...<|
00000040  03 e5 c8 3c 3d f1 d7 3c  f7 7f fa 3c ce 26 00 3d  |...<=..<...<.&.=|
00000050  92 8f ec 3c ac 7f ea 3c  45 2f fa 3c 95 5e f2 3c  |...<...<E/.<.^.<|
00000060  9b 36 d2 3c 7a d7 bd 3c  e2 40 ad 3c aa 31 84 3c  |.6.<z..<.@.<.1.<|
00000070  9e 63 34 3c b4 01 14 3c  26 1f f7 3b 9b 85 9b 3b  |.c4<...<&..;...;|
00000080  a6 ec 3e 3b df 6f 78 3b  1c af db 3b c9 33 0e 3c  |..>;.ox;...;.3.<|
00000090  ac 58 02 3c bf 1e 04 3c  06 15 3b 3c 59 83 69 3c  |.X.<...<..;<Y.i<|
000000a0  f9 93 76 3c 5b 02 89 3c  ed 15 95 3c 25 62 88 3c  |..v<[..<...<%b.<|
000000b0  ef 3c 63 3c 2a 85 36 3c  33 6f cf 3b 14 8a 55 39  |.<c<*.6<3o.;..U9|
000000c0  c8 03 6a bb 47 5c a4 bb  33 a0 eb bb 5c 92 20 bc  |..j.G\..3...\. .|
000000d0  63 60 20 bc 36 62 fc bb  7f b1 d3 bb b7 67 97 bb  |c` .6b.......g..|
000000e0  aa 81 89 3a 42 fb 0b 3c  f8 2e 5f 3c 61 5a 83 3c  |...:B..<.._<aZ.<|
000000f0  da 56 94 3c 20 3e a8 3c  3c 3f b1 3c b1 cb a3 3c  |.V.< >.<<?.<...<|
00000100  23 c2 8b 3c c3 f9 72 3c  6a 35 50 3c a7 8d 1f 3c  |#..<..r<j5P<...<|
00000110  ce 08 ec 3b 54 e5 ef 3b  41 99 27 3c 88 51 45 3c  |...;T..;A.'<.QE<|
00000120  16 45 24 3c 22 10 13 3c  f2 b3 50 3c a6 d3 76 3c  |.E$<"..<..P<..v<|
00000130  6d 15 37 3c fd e0 be 3b  3c db e1 39 f3 a6 30 bc  |m.7<...;<..9..0.|
00000140  2e 18 e9 bc d8 23 43 bd  c4 b4 87 bd 4e b8 ac bd  |.....#C.....N...|
00000150  b6 2f cf bd 62 74 ed bd  e0 75 01 be 49 8f 04 be  |./..bt...u..I...|
00000160  19 47 00 be 83 c4 f0 bd  f3 6b dc bd 25 43 bd bd  |.G.......k..%C..|
00000170  c0 d2 93 bd 59 b5 5e bd  61 6d 2f bd 93 65 08 bd  |....Y.^.am/..e..|
00000180  41 4a d7 bc 97 fb e4 bc  1a a5 15 bd 8c ea 3f bd  |AJ............?.|
00000190  d2 af 7c bd e8 16 a7 bd  be 9f c9 bd 0d 93 e0 bd  |..|.............|
000001a0  40 a0 f5 bd 9c d7 02 be  bb c3 02 be e1 c7 f8 bd  |@...............|
000001b0  2d 30 e9 bd 34 8b d4 bd  11 e2 b4 bd f6 1e 00 fe  |-0..4...........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f8 94 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f8  94 00 00 68 ee 00 00 00  |...........h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-YnE7BHmj/Tmp_Log: No such file or directory


```

Some of this looks a little strange to me, but again, I'm no expert.

Anyone have any idea what might be going on here?

---

### Post by oldfred on 2017-10-10
You do not show a BCD in your Windows install.
Windows 7 typically has two partitions, a small 100MB boot partition with bootmgr & BCD and then main install. You do not have to have the separate boot partition if you have the boot files &  boot flag on main install partition. Vista upgrades only have one partition. One reason for separate boot partition was so you could encrypt the main install.

       Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe  

If you have a copy of /boot/BCD, copy it back into your  system.
From Windows repair console:

 BootRec.exe /RebuildBcd

---

### Post by tracy6 on 2017-10-11
You nailed it oldfred.  I was not even aware of the boot partition that Windows uses beyond MBR, and therefore, I didn't know what you were talking about.  I did some research on BCD, etc. and learned some stuff I didn't know.  I was able to make the Windows partition visible and then it was easy to update grub to include both OS's.

Thanks for the help.

---

### Post by oldfred on 2017-10-11
Glad you figured it out.
You can change to Solved.

---

