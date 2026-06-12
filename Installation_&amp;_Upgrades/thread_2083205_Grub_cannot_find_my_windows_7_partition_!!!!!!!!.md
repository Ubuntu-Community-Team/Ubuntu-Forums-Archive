---
title: "Grub cannot find my windows 7 partition !!!!!!!!"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by zak23 on 2012-11-11
Can any one help me please it's asap for me
i have windows 7 before and i just installed ubuntu 12.04 but grub couldn't detect i don't know what i have to do.
this is my info after executing the file bootinfoscript

```


                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 290200248 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 72 for .
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre7
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       305,234       305,172   6 FAT16
/dev/sda2    *        307,200     4,501,503     4,194,304  82 Linux swap / Solaris
/dev/sda3           4,501,504   239,312,895   234,811,392   7 NTFS / exFAT / HPFS
/dev/sda4         239,316,990   488,388,795   249,071,806   f W95 Extended (LBA)
/dev/sda5         239,316,992   355,194,879   115,877,888  83 Linux
/dev/sda6         355,197,213   488,388,795   133,191,583  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4005 MB, 4005527552 bytes
250 heads, 19 sectors/track, 1647 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,823,295     7,823,233   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D9-050D                              vfat       DellUtility
/dev/sda2        9d71fa78-3244-46a4-bcee-c7164f4b22f8   swap       
/dev/sda3        022C8D822C8D7189                       ntfs       
/dev/sda5        e8f31747-6b8f-4617-8de5-a7f1aaa1a82e   ext4       
/dev/sda6        D8AEA711AEA6E76A                       ntfs       
/dev/sdb1        ECDF-B7DD                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


============================= sda5/grub/grub.cfg: ==============================

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  e8f31747-6b8f-4617-8de5-a7f1aaa1a82e
else
  search --no-floppy --fs-uuid --set=root e8f31747-6b8f-4617-8de5-a7f1aaa1a82e
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e8f31747-6b8f-4617-8de5-a7f1aaa1a82e
else
  search --no-floppy --fs-uuid --set=root e8f31747-6b8f-4617-8de5-a7f1aaa1a82e
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e8f31747-6b8f-4617-8de5-a7f1aaa1a82e' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e8f31747-6b8f-4617-8de5-a7f1aaa1a82e
    else
      search --no-floppy --fs-uuid --set=root e8f31747-6b8f-4617-8de5-a7f1aaa1a82e
    fi
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=e8f31747-6b8f-4617-8de5-a7f1aaa1a82e ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e8f31747-6b8f-4617-8de5-a7f1aaa1a82e' {
    menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-29-generic-pae-advanced-e8f31747-6b8f-4617-8de5-a7f1aaa1a82e' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e8f31747-6b8f-4617-8de5-a7f1aaa1a82e
        else
          search --no-floppy --fs-uuid --set=root e8f31747-6b8f-4617-8de5-a7f1aaa1a82e
        fi
        echo    'Loading Linux 3.2.0-29-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=e8f31747-6b8f-4617-8de5-a7f1aaa1a82e ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-29-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-29-generic-pae-recovery-e8f31747-6b8f-4617-8de5-a7f1aaa1a82e' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e8f31747-6b8f-4617-8de5-a7f1aaa1a82e
        else
          search --no-floppy --fs-uuid --set=root e8f31747-6b8f-4617-8de5-a7f1aaa1a82e
        fi
        echo    'Loading Linux 3.2.0-29-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=e8f31747-6b8f-4617-8de5-a7f1aaa1a82e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-29-generic-pae
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e8f31747-6b8f-4617-8de5-a7f1aaa1a82e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=9d71fa78-3244-46a4-bcee-c7164f4b22f8 none            swap    sw              0       0

--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 138.383434296 = 148.588081152  boot/grub/grub.cfg                             1
 115.757743835 = 124.293931008  boot/initrd.img-3.2.0-29-generic-pae           2
 160.248283386 = 172.065284096  boot/vmlinuz-3.2.0-29-generic-pae              1
 166.252738953 = 178.512519168  grub/grub.cfg                                  1
 115.757743835 = 124.293931008  initrd.img                                     2
 160.248283386 = 172.065284096  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  00 01 00 00 00 00 00 00  da d6 0f 7c 00 55 55 55  |...........|.UUU|
*
00000020  00 01 00 00 00 00 00 00  d0 83 0f 7c ff ff ff ff  |...........|....|
*
00000120  02 00 49 92 c4 89 13 07  10 84 cf 7b ea ba be ab  |..I........{....|
00000130  04 e3 30 64 2c 58 b2 64  ef 7b 24 21 00 60 58 96  |..0d,X.d.{$!.`X.|
00000140  f2 00 03 04 f5 7c 92 24  ef 7b c3 18 d7 2d 02 00  |.....|.$.{...-..|
00000150  04 84 a1 00 db 00 6c db  10 84 cb 5a 2d 00 00 00  |......l....Z-...|
00000160  04 00 7b f2 24 49 92 24  d0 83 0f 7c ff ff ff ff  |..{.$I.$...|....|
00000170  01 0e c0 62 1b b6 61 db  10 84 cf 7b ea ba ba aa  |...b..a....{....|
00000180  d8 01 ef 94 e4 49 92 24  0f 7c 29 4a 78 00 00 00  |.....I.$.|)Jx...|
00000190  f4 00 00 64 0a c9 9d 24  ef 7b 45 29 55 78 00 00  |...d...$.{E)Ux..|
000001a0  fc 05 ec 03 68 1c 90 bb  ef 7b 24 21 0b d5 5e 80  |....h....{$!..^.|
000001b0  f4 00 49 c2 ba 00 30 69  cf 7b c3 18 00 82 00 fe  |..I...0i.{......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 28 e8 06 00 fe  |...........(....|
000001d0  ff ff 05 fe ff ff e0 30  e8 06 de 57 f0 07 00 00  |.......0...W....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically
```

---

### Post by oldfred on 2012-11-12
Did you copy Windows from sda2 or sda3 to sda6? It says its internal PBR -  partition boot sector starts at sector 63 which is normally the first partition of a drive in older systems. New systems start at sector 2048.

Windows 7 often installs to 2 partitions, one a 100MB boot/repair partition and another is your main install. Windows has to have a primary (sda1 thru sda4) NTFS formatted partition with the boot flag to boot, install or repair boot.

Grub does not use boot flag. But some BIOS have to see a boot flag on a primary partition to let you start to boot before grub. You have boot flag on swap which says it probably was the Windows boot partition.  If you have not used swap it may still have your Windows data in it. Testdisk may recover it.

You may be able to repair your install with a new Windows boot partition as sda2 with the two missing boot files from the normal 100MB boot partition and running chkdsk on the sda6 partition to update its internal PBR data. This mostly has to be done from your Windows repairCD or a full Windows install DVD  set.

Windows Boot files, your are missing the boot partition and the two files in red:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

Look at sda2 with testdisk, if no files found, you will just have to reformat sda2 as NTFS with boot flag and run Windows repairs from the Windows disk to repair it.
repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by zak23 on 2012-11-12
thanks you very much for your help, can you please go easy with me.
what the first thing i have to do?
thanks

---

### Post by oldfred on 2012-11-12
If you are not adept at partitioning, repairs and major system changes, it would just be easier to reinstall Windows & Ubuntu. You have a lot of issues, but they should be fixable, no guarantees.
If you have any data not backed up, back that up first.

See if testdisk can see an old NTFS boot partition where swap is now. If found convert back. Try deeper search to see if you can find bootmgr & BCD.
If not found by testdisk, use gparted to delete swap and create a NTFS partition with boot flag. Ubuntu will complain about swap partition until you create a new one & update fstab with new UUID.

Do you have Windows repairCD?

If you have another computer, a friend, or access to another Windows 7 that is either 32 or 64 bit to match yours.

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

You also have some issue here:
```
/dev/sda6         355,197,213   488,388,795   133,191,583  [COLOR=Red]fd[/COLOR] Linux raid autodetect
```Did you turn RAID on somewhere. From Ubuntu's Disk Utility see ifyou can change sda6 back to 07 or NTFS. You do NOT want to reformat.

With gparted shrink your Linux partition and create a new swap.
# Find your UUID:
sudo blkid -c /dev/null -o list

sudo cp /etc/fstab /etc/fstab.backup
#Change UUID of swap to new UUID of swap you created.
gksu gedit /etc/fstab

Probably lots more to do, but lets see where you are at after this.
May be better to run BootInfo. It runs the bootinfoscript, but includes some additional data.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by zak23 on 2012-11-12
that's why i am asking for solution, no why for reinstalling windows, maybe ubuntu.
anyway i gonna give it start right now
thanks

---

### Post by zak23 on 2012-11-12
that's my URL

[http://paste.ubuntu.com/1354055/](http://paste.ubuntu.com/1354055/)

thanks

---

### Post by darkod on 2012-11-12
As oldfred asked, did you move any partitions around while doing the install, especially the win7 partition?

The way it is right now (logical partition) is not how it usually comes on preinstalled machines. It should be primary partition, not logical.

On top of that, the small win7 system reserved partition is missing, and that's where the win7 boot files are. I guess you deleted it and created the ubuntu swap partition over it.

Also from the ubuntu partitions it's clear you installed with manual partitioning (making the partitions yourself), and that's when you deleted it.

If the win7 partition was primary, there is some chance to only repair it and add the boot files. But with your win7 partition being logical, that's impossible. The repair can only work on primary partitions.

You have all four partitions used (three primary and one extended), so you can't convert the win7 to primary.

All in all, the situation is quite complicated and it doesn't look like you can easily save it without reinstalling everything. Especially if you have limited knowledge of partitions and how windows and ubuntu work.

---

### Post by zak23 on 2012-11-12
thank you for your advice, really you gave me some hope, i am not gonna give up i will keep trying untill i find the solution.
 so for the moment i am gonna focus on how to change the SDA6 from logical to primary,

I didn't move any partiton before installing Ubuntu, this how it is before.

ubuntu and windows are the both logical for the moment, so the grub could find ubuntu, 
i believe should be a solution to make grub can detect windows 7 as well.


thanks

---

### Post by darkod on 2012-11-12
If you want to attempt it, here is one suggestion. But the choice is yours, I can't guarantee it will work.

Since sda3 is next to the logical partitions sda5 and sda6, you can use fixparts and convert sda3 into logical too. That will "free one space" for a primary partition.
Then you should be able to convert sda6 to primary since it's at the end of the disk.

Fixparts can do this, read carefully the instructions:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

After sda6 is converted to logical, you will need to open Gparted and set the boot flag on it. If there is a boot flag on any other partition, deactivate it. It should be only on the windows partition.

After that is done, you will need to run the win7 repair process but only to repair the partition, not the MBR (you still want grub2 on the MBR). But lets get there first, later we can discuss the details.

---

### Post by zak23 on 2012-11-12
i don't wanna lose anydata on that partition, i mean SDA3

is there any risk?

---

### Post by zak23 on 2012-11-12
i can't do nothing with my partitions 

i've been looking at MBR sector table, it shows that its not possible to convert any partition 

need other solution please

---

### Post by darkod on 2012-11-12
In theory it just changes the partition type, it doesn't format it or anything.

But there is always risk when handling partitioning, so there is no 100% risk free operation.

If you can, it would be best to make a backup of all the important data to some external disk before starting any attempts to change the partitions.

I just suggested how to change them, into what type, what you do is up to you at the end. :)

---

### Post by darkod on 2012-11-12
If fixparts says it can't convert any of the partitions, sorry, I don't know of another way to convert them.

You might have an error or corruption in the partition table and because of it it doesn't want to make changes to it, I don't know.

---

### Post by oldfred on 2012-11-12
You may have to use fixparts twice, as it would not allow creating the new primary  as long as 4 primaries exist. But if you change the sda3 to logical and then update. Then run it a second time with fixparts may let you change sda6 to primary.

---

### Post by zak23 on 2012-11-12
could you tell me please how can i use Fixpart twice

fixpart is already installed, what commend i have to put

---

### Post by oldfred on 2012-11-12
If you run fixparts will it let you change sda3 to logical. Then save that change, so you only then have 3 primary partitions. 

Then run fixparts again and see if it lets you change sda6 to primary. And save that. 

Then you will have to run Windows repairs.

---

