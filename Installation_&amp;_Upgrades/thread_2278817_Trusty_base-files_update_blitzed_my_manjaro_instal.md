---
title: "Trusty base-files update blitzed my manjaro installation; is it GRUB?"
date: 2015-05-19
forum: Installation &amp; Upgrades
---

### Post by Xiguus on 2015-05-19
Hi all,
I have an ASUS laptop with several OS's installed, ie Windows with 12.04 wubi, a 14.04 and a Manjaro 8. Yesterday I ran the software update on the 14.04, which included an update of the Ubuntu base files. When I rebooted the Trusty it rewrote my grub menu. 
I can still boot to the Windows and wubi 12.04 installations, but when I try to boot the Manjaro installation I get various screen messages which finish with "end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)". 
I've searched around a bit and found that this message is typical of a missing initramfs, which doesn't apply in this case as both Manjaro kernels have an initramfs present.
I'm thinking I have a GRUB problem rather than a kernel problem, because each linux has it's own grub.cfg and it's not clear to me how they resolve priority, or how I can get them (back) into a reliable order. "It all seemed to work just fine when the Manjaro boot config was in charge." My bootinfoscript RESULTS.txt is attached: If anyone can give me some advice on how to proceed it will be very much appreciated.
```

                Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Manjaro Linux () ()
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    34,812,854    34,810,807  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     34,813,952   279,007,231   244,193,280   7 NTFS / exFAT / HPFS
/dev/sda3         279,009,278   976,768,064   697,758,787   f W95 Extended (LBA)
/dev/sda5         279,009,280   360,929,279    81,920,000   7 NTFS / exFAT / HPFS
/dev/sda6         360,932,418   627,177,661   266,245,244  83 Linux
/dev/sda7         627,177,663   963,048,554   335,870,892  83 Linux
/dev/sda8         963,048,618   976,768,064    13,719,447  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       dc417f35-8f7a-4d06-bd52-2ac271c7db33   ext4       
/dev/sda1        3C98-AC5D                              vfat       RECOVERY
/dev/sda2        AEB684D3B6849D89                       ntfs       OS
/dev/sda5        3AA6870AA686C5BB                       ntfs       DATA
/dev/sda6        7a091e3e-545a-4e43-ba7c-4da34f7507cf   ext4       UBU14
/dev/sda7        0de56d23-b047-4a1b-9fd7-33f87e182578   ext4       MJOBX
/dev/sda8        68e2b1d1-3827-45fc-a039-486ba2e052d3   swap       SWAP

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda5/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 3AA6870AA686C5BB
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 3AA6870AA686C5BB
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.2.0-83-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3AA6870AA686C5BB
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.2.0-83-generic-pae root=UUID=3AA6870AA686C5BB loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.2.0-83-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-83-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3AA6870AA686C5BB
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.2.0-83-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-83-generic-pae root=UUID=3AA6870AA686C5BB loop=/ubuntu/disks/root.disk ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-83-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-82-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3AA6870AA686C5BB
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.2.0-82-generic-pae root=UUID=3AA6870AA686C5BB loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.2.0-82-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-82-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3AA6870AA686C5BB
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.2.0-82-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-82-generic-pae root=UUID=3AA6870AA686C5BB loop=/ubuntu/disks/root.disk ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-82-generic-pae
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-7a091e3e-545a-4e43-ba7c-4da34f7507cf (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
    linux /boot/vmlinuz-3.13.0-52-generic root=UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-52-generic
}
menuentry "Ubuntu, with Linux 3.13.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-advanced-7a091e3e-545a-4e43-ba7c-4da34f7507cf (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
    linux /boot/vmlinuz-3.13.0-52-generic root=UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-52-generic
}
menuentry "Ubuntu, with Linux 3.13.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-recovery-7a091e3e-545a-4e43-ba7c-4da34f7507cf (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
    linux /boot/vmlinuz-3.13.0-52-generic root=UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf ro recovery nomodeset
    initrd /boot/initrd.img-3.13.0-52-generic
}
menuentry "Manjaro Linux' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-0de56d23-b047-4a1b-9fd7-33f87e182578 (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
    linux /boot/vmlinuz-3.16-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
    initrd /boot/intel-ucode.img
}
menuentry "Manjaro Linux (Kernel 3.16.7.10-1-MANJARO x64)' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.7.10-1-MANJARO x64-advanced-0de56d23-b047-4a1b-9fd7-33f87e182578 (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
    linux /boot/vmlinuz-3.16-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
    initrd /boot/intel-ucode.img
}
menuentry "Manjaro Linux (Kernel 3.16.7.10-1-MANJARO x64 - fallback initramfs)' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.7.10-1-MANJARO x64-fallback-0de56d23-b047-4a1b-9fd7-33f87e182578 (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
    linux /boot/vmlinuz-3.16-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
    initrd /boot/intel-ucode.img
}
menuentry "Manjaro Linux (Kernel 3.14.40-1-MANJARO x64)' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.14.40-1-MANJARO x64-advanced-0de56d23-b047-4a1b-9fd7-33f87e182578 (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
    linux /boot/vmlinuz-3.14-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
    initrd /boot/intel-ucode.img
}
menuentry "Manjaro Linux (Kernel 3.14.40-1-MANJARO x64 - fallback initramfs)' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.14.40-1-MANJARO x64-fallback-0de56d23-b047-4a1b-9fd7-33f87e182578 (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
    linux /boot/vmlinuz-3.14-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
    initrd /boot/intel-ucode.img
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
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda5/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda5/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  19.671958923 = 21.122605056   boot/grub/grub.cfg                             1
  17.124904633 = 18.387726336   boot/initrd.img-3.2.0-82-generic-pae           3
  15.781250000 = 16.944988160   boot/initrd.img-3.2.0-83-generic-pae           2
  15.895320892 = 17.067470848   boot/vmlinuz-3.2.0-82-generic-pae              2
  17.086730957 = 18.346737664   boot/vmlinuz-3.2.0-83-generic-pae              2
  15.781250000 = 16.944988160   initrd.img                                     2
  17.124904633 = 18.387726336   initrd.img.old                                 3
  17.086730957 = 18.346737664   vmlinuz                                        2
  15.895320892 = 17.067470848   vmlinuz.old                                    2

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  7a091e3e-545a-4e43-ba7c-4da34f7507cf
else
  search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-7a091e3e-545a-4e43-ba7c-4da34f7507cf' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  7a091e3e-545a-4e43-ba7c-4da34f7507cf
    else
      search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
    fi
    linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-52-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-7a091e3e-545a-4e43-ba7c-4da34f7507cf' {
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-advanced-7a091e3e-545a-4e43-ba7c-4da34f7507cf' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  7a091e3e-545a-4e43-ba7c-4da34f7507cf
        else
          search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-recovery-7a091e3e-545a-4e43-ba7c-4da34f7507cf' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  7a091e3e-545a-4e43-ba7c-4da34f7507cf
        else
          search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-52-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  7a091e3e-545a-4e43-ba7c-4da34f7507cf
    else
      search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  7a091e3e-545a-4e43-ba7c-4da34f7507cf
    else
      search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-3C98-AC5D' {
    insmod part_msdos
    insmod fat
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3C98-AC5D
    else
      search --no-floppy --fs-uuid --set=root 3C98-AC5D
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-AEB684D3B6849D89' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  AEB684D3B6849D89
    else
      search --no-floppy --fs-uuid --set=root AEB684D3B6849D89
    fi
    parttool ${root} hidden-
    chainloader +1
}
menuentry 'Manjaro Linux (0.8.12) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-0de56d23-b047-4a1b-9fd7-33f87e182578' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
    else
      search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
    fi
    linux /boot/vmlinuz-3.16-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
    initrd /boot/intel-ucode.img
}
submenu 'Advanced options for Manjaro Linux (0.8.12) (on /dev/sda7)' $menuentry_id_option 'osprober-gnulinux-advanced-0de56d23-b047-4a1b-9fd7-33f87e182578' {
    menuentry 'Manjaro Linux (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16-x86_64--0de56d23-b047-4a1b-9fd7-33f87e182578' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
        else
          search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
        fi
        linux /boot/vmlinuz-3.16-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
        initrd /boot/intel-ucode.img
    }
    menuentry 'Manjaro Linux (Kernel 3.16.7.10-1-MANJARO x64) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16-x86_64--0de56d23-b047-4a1b-9fd7-33f87e182578' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
        else
          search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
        fi
        linux /boot/vmlinuz-3.16-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
        initrd /boot/intel-ucode.img
    }
    menuentry 'Manjaro Linux (Kernel 3.16.7.10-1-MANJARO x64 - fallback initramfs) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16-x86_64--0de56d23-b047-4a1b-9fd7-33f87e182578' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
        else
          search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
        fi
        linux /boot/vmlinuz-3.16-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
        initrd /boot/intel-ucode.img
    }
    menuentry 'Manjaro Linux (Kernel 3.14.40-1-MANJARO x64) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.14-x86_64--0de56d23-b047-4a1b-9fd7-33f87e182578' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
        else
          search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
        fi
        linux /boot/vmlinuz-3.14-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
        initrd /boot/intel-ucode.img
    }
    menuentry 'Manjaro Linux (Kernel 3.14.40-1-MANJARO x64 - fallback initramfs) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.14-x86_64--0de56d23-b047-4a1b-9fd7-33f87e182578' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
        else
          search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
        fi
        linux /boot/vmlinuz-3.14-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw quiet splash
        initrd /boot/intel-ucode.img
    }
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
#UUID=ec1904e0-8a66-469a-9d8a-a827276a3107 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 270.313126564 = 290.246509568  boot/grub/grub.cfg                             2
 200.709973335 = 215.510692864  boot/initrd.img-3.13.0-52-generic              1
 200.416096687 = 215.195145216  boot/vmlinuz-3.13.0-52-generic                 2
 200.709973335 = 215.510692864  initrd.img                                     1
 200.416096687 = 215.195145216  vmlinuz                                        2

=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_gpt
insmod part_msdos
if [ -s $prefix/grubenv ]; then
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="${saved_entry}"
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

set menu_color_normal=light-gray/black
set menu_color_highlight=green/black

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos 
insmod ext2
set root='hd0,msdos7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
else
  search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
  insmod gettext
fi
terminal_input console
terminal_output gfxterm
insmod part_msdos 
insmod ext2
set root='hd0,msdos7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
else
  search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
fi
insmod png
background_image -m stretch /usr/share/grub/background.png
if [ x$feature_timeout_style = xy ] ; then
  set timeout_style=menu
  set timeout=5
# Fallback normal timeout code in case the timeout_style feature is
# unavailable.
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Manjaro Linux' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-0de56d23-b047-4a1b-9fd7-33f87e182578' {
    savedefault
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos 
    insmod ext2
    set root='hd0,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
    else
      search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
    fi
    echo    'Loading Linux 3.16.7.10-1-MANJARO x64 ...'
    linux    /boot/vmlinuz-3.16-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/intel-ucode.img /boot/initramfs-3.16-x86_64.img
}
submenu 'Advanced options for Manjaro Linux' $menuentry_id_option 'gnulinux-advanced-0de56d23-b047-4a1b-9fd7-33f87e182578' {
    menuentry 'Manjaro Linux (Kernel: 3.16.7.10-1-MANJARO x64)' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.7.10-1-MANJARO x64-advanced-0de56d23-b047-4a1b-9fd7-33f87e182578' {
    savedefault
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos 
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
        else
          search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
        fi
        echo    'Loading Linux 3.16.7.10-1-MANJARO x64 ...'
        linux    /boot/vmlinuz-3.16-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw  quiet splash
        echo    'Loading initial ramdisk ...'
        initrd    /boot/intel-ucode.img /boot/initramfs-3.16-x86_64.img
    }
    menuentry 'Manjaro Linux (Kernel: 3.16.7.10-1-MANJARO x64 - fallback initramfs)' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.7.10-1-MANJARO x64-fallback-0de56d23-b047-4a1b-9fd7-33f87e182578' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos 
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
        else
          search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
        fi
        echo    'Loading Linux 3.16.7.10-1-MANJARO x64 ...'
        linux    /boot/vmlinuz-3.16-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw  quiet splash
        echo    'Loading initial ramdisk ...'
        initrd    /boot/intel-ucode.img /boot/initramfs-3.16-x86_64-fallback.img
    }
    menuentry 'Manjaro Linux (Kernel: 3.14.40-1-MANJARO x64)' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.14.40-1-MANJARO x64-advanced-0de56d23-b047-4a1b-9fd7-33f87e182578' {
    savedefault
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos 
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
        else
          search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
        fi
        echo    'Loading Linux 3.14.40-1-MANJARO x64 ...'
        linux    /boot/vmlinuz-3.14-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw  quiet splash
        echo    'Loading initial ramdisk ...'
        initrd    /boot/intel-ucode.img /boot/initramfs-3.14-x86_64.img
    }
    menuentry 'Manjaro Linux (Kernel: 3.14.40-1-MANJARO x64 - fallback initramfs)' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.14.40-1-MANJARO x64-fallback-0de56d23-b047-4a1b-9fd7-33f87e182578' {
        load_video
        set gfxpayload=keep
        insmod gzio
        insmod part_msdos 
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
        else
          search --no-floppy --fs-uuid --set=root 0de56d23-b047-4a1b-9fd7-33f87e182578
        fi
        echo    'Loading Linux 3.14.40-1-MANJARO x64 ...'
        linux    /boot/vmlinuz-3.14-x86_64 root=UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 rw  quiet splash
        echo    'Loading initial ramdisk ...'
        initrd    /boot/intel-ucode.img /boot/initramfs-3.14-x86_64-fallback.img
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Vista (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-3C98-AC5D' {
    savedefault
    insmod part_msdos 
    insmod fat
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3C98-AC5D
    else
      search --no-floppy --fs-uuid --set=root 3C98-AC5D
    fi
    chainloader +1
}
menuentry 'Windows Vista (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-AEB684D3B6849D89' {
    savedefault
    insmod part_msdos 
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  AEB684D3B6849D89
    else
      search --no-floppy --fs-uuid --set=root AEB684D3B6849D89
    fi
    chainloader +1
}
menuentry 'Ubuntu 14.04.2 LTS (14.04) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7a091e3e-545a-4e43-ba7c-4da34f7507cf' {
    savedefault
    insmod part_msdos 
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  7a091e3e-545a-4e43-ba7c-4da34f7507cf
    else
      search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
    fi
    linux /boot/vmlinuz-3.13.0-52-generic root=UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-52-generic
}
submenu 'Advanced options for Ubuntu 14.04.2 LTS (14.04) (on /dev/sda6)' $menuentry_id_option 'osprober-gnulinux-advanced-7a091e3e-545a-4e43-ba7c-4da34f7507cf' {
    menuentry 'Ubuntu (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-52-generic--7a091e3e-545a-4e43-ba7c-4da34f7507cf' {
        savedefault
        insmod part_msdos 
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  7a091e3e-545a-4e43-ba7c-4da34f7507cf
        else
          search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
        fi
        linux /boot/vmlinuz-3.13.0-52-generic root=UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-52-generic--7a091e3e-545a-4e43-ba7c-4da34f7507cf' {
        savedefault
        insmod part_msdos 
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  7a091e3e-545a-4e43-ba7c-4da34f7507cf
        else
          search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
        fi
        linux /boot/vmlinuz-3.13.0-52-generic root=UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-52-generic--7a091e3e-545a-4e43-ba7c-4da34f7507cf' {
        savedefault
        insmod part_msdos 
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  7a091e3e-545a-4e43-ba7c-4da34f7507cf
        else
          search --no-floppy --fs-uuid --set=root 7a091e3e-545a-4e43-ba7c-4da34f7507cf
        fi
        linux /boot/vmlinuz-3.13.0-52-generic root=UUID=7a091e3e-545a-4e43-ba7c-4da34f7507cf ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-52-generic
    }
}

### END /etc/grub.d/30_os-prober ###

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

### BEGIN /etc/grub.d/60_memtest86+ ###
if [ "${grub_platform}" == "pc" ]; then
    menuentry "Memory Tester (memtest86+)" --class memtest86 --class gnu --class tool {
        search --fs-uuid --no-floppy --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  0de56d23-b047-4a1b-9fd7-33f87e182578
        linux16 /boot/memtest86+/memtest.bin 
    }
fi
### END /etc/grub.d/60_memtest86+ ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#
UUID=0de56d23-b047-4a1b-9fd7-33f87e182578 / ext4 rw,relatime,data=ordered 0 1
--------------------------------------------------------------------------------

======================= sda7/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: [https://wiki.archlinux.org/index.php/Syslinux](https://wiki.archlinux.org/index.php/Syslinux)
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Set to 1 if you always want to display the boot: prompt 
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to [http://syslinux.zytor.com/wiki/index.php/Doc/menu](http://syslinux.zytor.com/wiki/index.php/Doc/menu)
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
    MENU LABEL Arch Linux
    LINUX ../vmlinuz-linux
    APPEND root=/dev/sda3 rw
    INITRD ../initramfs-linux.img

LABEL archfallback
    MENU LABEL Arch Linux Fallback
    LINUX ../vmlinuz-linux
    APPEND root=/dev/sda3 rw
    INITRD ../initramfs-linux-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 341.706466198 = 366.904524288  boot/grub/grub.cfg                             2
 312.733489513 = 335.795027456  boot/initramfs-3.14-x86_64-fallback.img        2
 449.202361584 = 482.327363072  boot/initramfs-3.14-x86_64.img                 1
 309.749114513 = 332.590579200  boot/initramfs-3.16-x86_64-fallback.img        2
 449.206626415 = 482.331942400  boot/initramfs-3.16-x86_64.img                 1
 449.198134899 = 482.322824704  boot/vmlinuz-3.14-x86_64                       1
 449.194171429 = 482.318568960  boot/vmlinuz-3.16-x86_64                       1

================= sda7: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 449.190421581 = 482.314542592  boot/syslinux/syslinux.cfg                     1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  20 cd 94 a2 85 64 17 29  9f 45 82 bb 49 22 89 8a  | ....d.).E..I"..|
00000010  4a fa 48 ee 46 2d a3 dd  69 f3 e5 99 c0 b8 fa 7b  |J.H.F-..i......{|
00000020  23 6b 39 48 b1 e4 1a 40  d8 47 ab ca 76 21 98 18  |#k9H...@.G..v!..|
00000030  3b 31 50 53 61 83 79 e9  0d 70 62 71 dd b9 3a 63  |;1PSa.y..pbq..:c|
00000040  3e 8a ed 0b 34 95 d0 3c  92 57 81 3f 0b 9c 05 5a  |>...4..<.W.?...Z|
00000050  4a 48 12 87 fe 74 8d de  4f 17 98 9a 8e dc 88 41  |JH...t..O......A|
00000060  54 7a 30 6a de 68 b3 e6  0b 20 29 37 17 e9 e5 7c  |Tz0j.h... )7...||
00000070  01 1c bc db 2c 27 e2 c6  10 0c 22 50 e6 99 9b f6  |....,'...."P....|
00000080  d0 ba c1 58 1d 98 ff dd  cd 68 0e 2c 73 e7 8d dd  |...X.....h.,s...|
00000090  25 df 16 47 d7 1b c2 4b  ba 29 6e c4 e7 db d7 88  |%..G...K.)n.....|
000000a0  43 5f e0 60 5d a3 f7 26  99 63 2e e4 69 3a de 33  |C_.`]..&.c..i:.3|
000000b0  2c 32 52 1f cb 66 04 4c  52 f6 8b 20 5b 9f f1 8c  |,2R..f.LR.. [...|
000000c0  c0 a7 ab fd 4a 24 b7 f9  a0 5d 54 55 be 5a b1 a0  |....J$...]TU.Z..|
000000d0  a0 b9 33 4a 8b 09 1a af  36 28 a2 d2 3e f1 2d e2  |..3J....6(..>.-.|
000000e0  86 17 91 9e 05 75 78 29  b6 28 9d 54 73 ab b8 1e  |.....ux).(.Ts...|
000000f0  81 ae 41 95 93 54 26 80  81 f9 a7 ac e8 52 aa 88  |..A..T&......R..|
00000100  99 f3 11 6d 32 bc d0 ec  1b ca 27 dd 1c aa 47 13  |...m2.....'...G.|
00000110  28 46 2f e8 59 3d 86 c6  87 aa 11 71 99 fa 41 46  |(F/.Y=.....q..AF|
00000120  da 46 1f 8f 0d c5 5d 9f  52 85 ef 2d e4 5e 72 3b  |.F....].R..-.^r;|
00000130  b9 b9 ee 5a 01 4f 7d 72  68 d5 11 3f 4a 2e 5c b2  |...Z.O}rh..?J.\.|
00000140  eb 36 3b de a6 e9 23 ba  55 3c 82 26 2a 98 b4 30  |.6;...#.U<.&*..0|
00000150  fa ff 5b 19 91 11 33 2d  5b 15 82 b6 b7 aa 42 6a  |..[...3-[.....Bj|
00000160  70 10 8d d4 d1 c3 a9 af  21 26 5e 6f c3 8b 2b 7d  |p.......!&^o..+}|
00000170  4a 65 a0 e8 66 44 33 72  d2 5f 6d 90 a1 8b ad 56  |Je..fD3r._m....V|
00000180  19 c7 b9 8c 63 5a 2a c8  9c f1 ea 4d 82 c4 32 5f  |....cZ*....M..2_|
00000190  90 20 b1 8d ae 67 79 77  20 2f 21 fd d0 e8 22 09  |. ...gyw /!...".|
000001a0  d9 88 fc 7f d8 36 fe e8  35 ba 8d da 20 7b 2c 36  |.....6..5... {,6|
000001b0  db c7 42 75 85 f0 da 41  f2 61 8c e4 9b c9 00 fe  |..Bu...A.a......|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 00 e2 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff 05 0c  e2 04 bb 94 de 0f 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 


```

Best Regards,

Xig

---

### Post by grahammechanical on 2015-05-19
The way it works with Linux is that the last Linux to be installed will put its Grub into the MBR which in turn will look for its configuration file in that installation's partition. An Upgrade of the Linux kernel in Ubuntu will write new grub configuration files and put them into /boot/grub. A kernel upgrade will sometimes re-install Grub into the MBR.

Load Ubuntu 14.04.2 and open a terminal and run this command

```
sudo update-grub
```

There will be a printout. Does the list of detected operating systems include Manjaro Linux? If it does then I suspect the problem is not with the Grub of 14.04.2 but with Manjaro itself. From the looks of grub.cfg you should have options to load 4 kernel versions of Manjaro. Have you tried those previous kernels?

Regards.

---

### Post by Xiguus on 2015-05-19
Hi grahammechanical,
Thanks for your prompt response.
update-grub recognizes the Manjaro partition, as here:

```

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Manjaro Linux (0.8.12) on /dev/sda7
done

```

I can mount the partition from 14.04 and have:
```

19144561          May 11 12:07 /MX/boot/initramfs-3.14-x86_64-fallback.img
4537934              May 11 12:07 /MX/boot/initramfs-3.14-x86_64.img
19416436          May 11 12:08 /MX/boot/initramfs-3.16-x86_64-fallback.img
4576806              May 11 12:08 /MX/boot/initramfs-3.16-x86_64.img

```

I don't know what might have happened on May 11, (if anything), but I'm thinking rename the .img to .img.done and the -fallback.img to .img, and seeing what happens. Do you think this is wise, or do I need to rebuild the initramfs from scratch?

Best Regards,

Xig

---

### Post by Xiguus on 2015-05-20
Hi all,

I've had a look at the manjaro forums and found this:

[https://forum.manjaro.org/index.php?topic=20432.0](https://forum.manjaro.org/index.php?topic=20432.0)

Short story is I can boot to my manjaro installation from the grub menu by:[INDENT]1. Select manjaro menu entry
2. **e** to edit
3. Replace line [/INDENT]
[INDENT=2]initrd /boot/intel-ucode.img
[/INDENT]
[INDENT]    with[/INDENT]
[INDENT=2]initrd /boot/initramfs-3.16-x86_64.img[/INDENT]
[INDENT]4. Ctrl-x or F10 to boot[/INDENT]
and it all happens as it should.

The discussion is reasonably complex and I'm going to have a good look at it all and a think about it before I go any further, so I'm still interested in any input that will clarify the issues raised. Simply put, I'm looking for a permanent fix that won't break anything else. Still, progress is encouraging and we're getting agreeably close to a solution...

BR,
Xig

---

### Post by Bucky Ball on 2015-05-20
When you're booted in Manjaro on the hard disk, and you were saying that was controlling grub previously, try 'sudo update-grub' (if that is a valid manjaro command) from there and reboot. Does that now pick up everything or back to square one?

---

### Post by Xiguus on 2015-05-20
Hi BuckyBall,
Thanks for your response.
The answer to your question is "no"; when grub was controlled by manjaro a background was loaded with a manjaro logo, this no longer happens and my feeling is that the controlling grub is now the one managed by the Trusty installation.
Current objective is to make a permanent change to the manjaro menu entry for line initrd, ie:[INDENT]initrd /boot intel-ucode.img /boot/initramfs-3.16-x86_64.img (and whatever it becomes subsequently)
[/INDENT]
which will survive the rough-and-tumble of multi-boot upgrades.
I'm going to install Grub Customiser, which reads - and can edit - the MBR grub, so I don't have to chase around the various grub.cfgs to find out who's in charge. This will happen a bit later today, so "I'll be back..." ;)

Best Regards,
Xig.

---

### Post by Bucky Ball on 2015-05-21
Avoid editing .cfg, as mentioned. Sure, look at the .cfg for details, but edit /etc/default/grub if you need to. ;)

Good luck.

---

### Post by Xiguus on 2015-05-21
Hi Bucky Ball,
I've installed Grub Customize 4.06 to the Manjaro and had a look at what it has and what it does. 
Essentially, it can write my manjaro boot menu to the MBR, which would give a working boot option for the manjaro installation along with items for the other installations (which haven't changed from when they used to work previously), so all very good.
However, I want to back up my MBR before I do this. Although the procedure is apparently identical to what happens with a system upgrade or new install, a safety margin is always useful...
I've found some instructions on backing up and restoring the MBR, as here:[INDENT]Backup:[/INDENT]
[INDENT=2]sudo dd if=/dev/sda of=/home/user/mbr_backup.img bs=512 count=1
[/INDENT]
[INDENT]Restore:[/INDENT]
[INDENT=2]Boot with a LiveCD;
Mount bootdrive and os partition:
[/INDENT]
[INDENT=3]mkdir tmp
mount /dev/sdaX tmp
cd tmp/admin[/INDENT]
[INDENT=2]Restore MBR:
[/INDENT]
[INDENT=3]sudo dd of=/dev/sda if=/home/user/mbr_backup.img bs=512 count=1[/INDENT]
[INDENT=2]Resync the partiton table:
[/INDENT]
[INDENT=3]sudo gptsync[/INDENT]

Does this seem reasonable to you? I don't expect the write to fail but I also don't want to be in a position where the fix is more damaging than the problem.
Thanks for your assistance,

BR,
Xig

---

### Post by oldfred on 2015-05-21
Be very careful using 512, as that includes partition table. If you then change partition table but restore older partition table you will have a mess. Part of why dd's nickname is Data Destroyer. Better to use 446, if you really want to do it.
[https://help.ubuntu.com/community/WindowsDualBoot#Master_Boot_Record_backup_and_replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master_Boot_Record_backup_and_replacement)

I do not recommend backing up MBR, as it is so easy to reinstall grub, if you can boot a live installer or any version of Linux.

Ubuntu puts links to most current kernel in /, so you from grub you can boot link and always boot most current kernel. You can also install grub to partition which normally is not recommended. That would be more as a throw away so that install never updates MBR. But you must have another grub that works and has an entry to other installs.

       It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)
    
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

Some examples of custom grub entries you can use in 40_custom.


 gksudo gedit /etc/grub.d/40_custom
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
menuentry "Boot from USB Drive" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}

 menuentry "/boot/grub/grub.cfg on /dev/sda1" {
insmod ext2 
set root="(hd0,msdos1)"
configfile /boot/grub/grub.cfg
}

---

### Post by Xiguus on 2015-05-22
Hi oldfred,
Thanks very much for your input.
Regarding backing up the mbr with dd, some instructions said bs=512, others bs=448 or 446; I'll take your point, and amend the code to bs=446. Of course, I'm hoping I won't have to use it and if my mbr (or grub) does become totally damaged by any of my later actions I will do as you suggest and try to reinstall from a LiveCD.
As a next step I will follow up your links for custom menus and see whether I can make an entry for manjaro that works with
```

initrd /boot/intel-ucode.img /boot/initramfs-3XX-AAAA.img

```
as it requires.
I've also got some updates waiting, including another for Ubuntu-base, so I'll install them, cross my fingers, and hope it all stays good...;)
Thanks again for your help; I'm thinking we're making progress and it's basically a question of testing some alternatives and making a procedural decision.

Best Regards,
Xig

---

### Post by oldfred on 2015-05-22
You should be able to just copy from Manjaro's grub a boot stanza into Ubuntu's 40_custom. But everytime Manjaro updates with a new kernel you would also have to manually update the entry in Ubuntu's grub.
Does Manjaro have a link to most current kernel in / like most Debian based distributions?

       Copy the entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by Xiguus on 2015-05-22
Hi oldfred,
1. I ran

```
sudo /etc/sbin/dpkg-reconfigure grub-pc
```
to see what it had; no harm done, but it was a bit disconcerting that there was no 'exit don't do' option...;)
2. I followed the instructions here:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
to make a custom menu.[INDENT]a) added a comment to the startup lines (to verify effect) and amended the first 'exec tail' line as described, to now read:
```
echo 1>&2 "Manjaro in the box"
exec tail -n +4 $0

```
b) added the exact Manjaro menuitem block from the Manjaro installation grub.cfg;
c) saved the file as 36_custom (to place the new item at the end of the existing menu)
d) ran **sudo update-grub** as usual; the terminal output showed two instances of 'Manjaro in the box' at the end of the run;
e) logged out, rebooted and selected the new 'Manjaro' entry at the bottom of the menu.
[/INDENT]
and Manjaro opened as required.:KS;)
I'm going to add the rescue items from the Manjaro boot menu and delete the info line; I'll keep the os-prober lines as they are because at the least they'll tell me when I might need to update the kernel references. I probably try to   make these automatic later, but at the moment I'll just sit back in the satisfaction of a fully-working menu.
I'm also going to lock the grub packages - grub, grub-common and grub-pc - in apt. Grub upgrades come fairly slowly, but that way I can ensure that the next one will be applied through the Manjaro installation.
So, to answer the question, "Is it Grub?" - no, as I understand it the bug is actually in os-prober.
Thanks again to the team for your advice and assistance...:D

BR,
Xig

---

### Post by Xiguus on 2015-05-23
Hi all,
Just a footnote to the above...
[LIST]
[*=1]Deleting the info line from the custom file means there is no indication from update-grub that the entry has been recognised; it still appears in the menu, however, if everything else is good. 
[*=1]In the command **tail -n** **+*N* **the *N* refers to the number of lines *before* the inclusion that are carried over; deleting the info line requires this to be reset to **3** - I got a big spill and an 'out of memory' error when I tried later to add the Manjaro rescue submenu to 36_custom (but see next). 
[*=1]The duplicated entries in the update-grub output and in the generated boot menu occurred because I had edited into 40_custom, saved, then saved as 36_custom, so update-grub was reading this information twice; easily fixed, I just returned 40_custom back into a stub. 
[/LIST]
So, still good...;)

Cheers,
Xiguus

---

### Post by oldfred on 2015-05-23
I boot a variety of Ubuntu installs, so I turn off os-prober and often reset grub to not reinstall.

 gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or 
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates, if you uncheck everything then it will not reinstall. Or set to a partition so it is a throw away (only if using another grub). Normally partition install not recommended.
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by Xiguus on 2015-05-23
Hi oldfred,
Thanks for this, these are good tips. ;)
I suppose as users we tend to get the idea that all upgrades are good and that all system functionality should be enabled regardless, but what works well for one situation (a simple Windows/Linux dual-boot, for example) isn't going to work for all.
I've done a search for 'os-prober bug intel-ucode.img' and came up with this (Dec 2014):[INDENT][https://bugs.archlinux.org/task/43254](https://bugs.archlinux.org/task/43254)[/INDENT]
Patches are provided for grub-2.02.beta2-5 (Trusty provides 2.02.beta2-9ubuntu1.1), and os-prober 1.64-1 (Trusty provides 1.63ubuntu1), with fixes in grub-2.02.beta2-8.1 and os-prober-1.65-0.1. This isn't a road I need to travel.;)
The discussion identifies the problem as peculiar to arch-linux multi-installations with kernels 314+: it seems previous systems had included the intel-ucode in the kernel. Moving this code out of the kernel requires it to be loaded in the initrd. It's not at all surprising that third parties haven't kept this issue in scope (although the more general matter of loading multiple img-files in initrd may turn out to be of wider interest ...).
I'm thinking my present arrangement is quite satisfactory and gives me more than enough to work with...:KS
Thanks again,

BR,
Xig

---

