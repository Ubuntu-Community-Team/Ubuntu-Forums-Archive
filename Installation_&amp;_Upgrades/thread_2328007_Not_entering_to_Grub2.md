---
title: "Not entering to Grub2"
date: 2016-06-16
forum: Installation &amp; Upgrades
---

### Post by trjrtjgg on 2016-06-16
I've installed the Ubuntu and Grub2 by following this method [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
But unable to enter the grub2... 
I've also tried boot-repair several times but it's still not working.


this is a dump of boot-info. 
sda1 is Microsoft Reserved partition.

The messsage below shows "1421916160 of the same hard drive for core.img, but core.img can not be  found at this location."
but, 1421916160 sector is ranged in sda2(NTFS partition). This is strange. Neither sda3(ubuntu and blocklists) nor sda4(bios-boot partition)...?
```
 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector 
    1421916160 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdb.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       1421651967 sectors, but according to the info from 
                       fdisk, it has 5716619263 sectors.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda3 and looks at sector 1431758616 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 16.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda4: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sdb2 has 
                       1565300735 sectors, but according to the info from 
                       fdisk, it has 5860268031 sectors.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32776 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                    34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sda2               264,192 5,716,883,455 5,716,619,264 Data partition (Windows/Linux)
/dev/sda3         5,716,889,600 7,814,035,455 2,097,145,856 Data partition (Linux)
/dev/sda4         5,716,883,456 5,716,889,599         6,144 BIOS Boot partition

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                    34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2               264,192 5,860,532,223 5,860,268,032 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 7.5 GiB, 8054112256 bytes, 15730688 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    15,730,687    15,728,640   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1                                                          
/dev/sda2        340E15EB0E15A6C0                       ntfs       4hdd
/dev/sda3        e1fe3d70-b463-40df-b9a1-3f8a3dd567fe   ext4       
/dev/sda4                                                          
/dev/sdb1                                                          
/dev/sdb2        A44EFE8E4EFE588E                       ntfs       3hdd
/dev/sdc1        568B-46DF                              vfat       UBUNTU 16_0

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jun 16 15:44 ata-HGST_HUS724040ALA640_PN2334PBJKJD8T -> ../../sda
lrwxrwxrwx 1 root root 10 Jun 16 15:44 ata-HGST_HUS724040ALA640_PN2334PBJKJD8T-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun 16 15:44 ata-HGST_HUS724040ALA640_PN2334PBJKJD8T-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun 16 15:44 ata-HGST_HUS724040ALA640_PN2334PBJKJD8T-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jun 16 15:44 ata-HGST_HUS724040ALA640_PN2334PBJKJD8T-part4 -> ../../sda4
lrwxrwxrwx 1 root root  9 Jun 16 15:44 ata-TOSHIBA_DT01ACA300_942EWNLGS -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun 16 15:44 ata-TOSHIBA_DT01ACA300_942EWNLGS-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jun 16 15:44 ata-TOSHIBA_DT01ACA300_942EWNLGS-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 Jun 16 15:44 usb-SMI_USB_DISK-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jun 16 15:44 usb-SMI_USB_DISK-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jun 16 15:44 wwn-0x5000039ff4e27fae -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun 16 15:44 wwn-0x5000039ff4e27fae-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jun 16 15:44 wwn-0x5000039ff4e27fae-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 Jun 16 15:44 wwn-0x5000cca23de426dd -> ../../sda
lrwxrwxrwx 1 root root 10 Jun 16 15:44 wwn-0x5000cca23de426dd-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun 16 15:44 wwn-0x5000cca23de426dd-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun 16 15:44 wwn-0x5000cca23de426dd-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jun 16 15:44 wwn-0x5000cca23de426dd-part4 -> ../../sda4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
else
  search --no-floppy --fs-uuid --set=root e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=ko_KR
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e1fe3d70-b463-40df-b9a1-3f8a3dd567fe' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
    else
      search --no-floppy --fs-uuid --set=root e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
    fi
    linux    /boot/vmlinuz-4.4.0-24-generic root=UUID=e1fe3d70-b463-40df-b9a1-3f8a3dd567fe ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-24-generic
}
submenu 'Ubuntu&#50857; &#44256;&#44553; &#49444;&#51221;' $menuentry_id_option 'gnulinux-advanced-e1fe3d70-b463-40df-b9a1-3f8a3dd567fe' {
    menuentry '&#47532;&#45573;&#49828; Ubuntu&#44032; &#51080;&#45716;, 4.4.0-24-generic&#51077;&#45768;&#45796;' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-24-generic-advanced-e1fe3d70-b463-40df-b9a1-3f8a3dd567fe' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        else
          search --no-floppy --fs-uuid --set=root e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        fi
        echo    '&#47532;&#45573;&#49828; 4.4.0-24-generic&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        linux    /boot/vmlinuz-4.4.0-24-generic root=UUID=e1fe3d70-b463-40df-b9a1-3f8a3dd567fe ro  quiet splash $vt_handoff
        echo    '&#52395; &#47016; &#46356;&#49828;&#53356;&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        initrd    /boot/initrd.img-4.4.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-24-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-24-generic-init-upstart-e1fe3d70-b463-40df-b9a1-3f8a3dd567fe' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        else
          search --no-floppy --fs-uuid --set=root e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        fi
        echo    '&#47532;&#45573;&#49828; 4.4.0-24-generic&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        linux    /boot/vmlinuz-4.4.0-24-generic root=UUID=e1fe3d70-b463-40df-b9a1-3f8a3dd567fe ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    '&#52395; &#47016; &#46356;&#49828;&#53356;&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        initrd    /boot/initrd.img-4.4.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-24-generic-recovery-e1fe3d70-b463-40df-b9a1-3f8a3dd567fe' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        else
          search --no-floppy --fs-uuid --set=root e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        fi
        echo    '&#47532;&#45573;&#49828; 4.4.0-24-generic&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        linux    /boot/vmlinuz-4.4.0-24-generic root=UUID=e1fe3d70-b463-40df-b9a1-3f8a3dd567fe ro recovery nomodeset 
        echo    '&#52395; &#47016; &#46356;&#49828;&#53356;&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        initrd    /boot/initrd.img-4.4.0-24-generic
    }
    menuentry '&#47532;&#45573;&#49828; Ubuntu&#44032; &#51080;&#45716;, 4.4.0-21-generic&#51077;&#45768;&#45796;' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-e1fe3d70-b463-40df-b9a1-3f8a3dd567fe' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        else
          search --no-floppy --fs-uuid --set=root e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        fi
        echo    '&#47532;&#45573;&#49828; 4.4.0-21-generic&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=e1fe3d70-b463-40df-b9a1-3f8a3dd567fe ro  quiet splash $vt_handoff
        echo    '&#52395; &#47016; &#46356;&#49828;&#53356;&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-e1fe3d70-b463-40df-b9a1-3f8a3dd567fe' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        else
          search --no-floppy --fs-uuid --set=root e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        fi
        echo    '&#47532;&#45573;&#49828; 4.4.0-21-generic&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=e1fe3d70-b463-40df-b9a1-3f8a3dd567fe ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    '&#52395; &#47016; &#46356;&#49828;&#53356;&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-e1fe3d70-b463-40df-b9a1-3f8a3dd567fe' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        else
          search --no-floppy --fs-uuid --set=root e1fe3d70-b463-40df-b9a1-3f8a3dd567fe
        fi
        echo    '&#47532;&#45573;&#49828; 4.4.0-21-generic&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=e1fe3d70-b463-40df-b9a1-3f8a3dd567fe ro recovery nomodeset 
        echo    '&#52395; &#47016; &#46356;&#49828;&#53356;&#47484; &#48520;&#47084;&#50741;&#45768;&#45796; ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=e1fe3d70-b463-40df-b9a1-3f8a3dd567fe /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

2730.728721619 = 2932.097638400 boot/grub/grub.cfg                             1
2730.732471466 = 2932.101664768 boot/grub/i386-pc/core.img                     1
2726.211608887 = 2927.247425536 boot/vmlinuz-4.4.0-21-generic                  1
2726.870628357 = 2927.955042304 boot/vmlinuz-4.4.0-24-generic                  1
2726.870628357 = 2927.955042304 vmlinuz                                        1
2726.211608887 = 2927.247425536 vmlinuz.old                                    1
2730.076438904 = 2931.397255168 boot/initrd.img-4.4.0-21-generic               3
2728.901569366 = 2930.135748608 boot/initrd.img-4.4.0-24-generic               2
2728.901569366 = 2930.135748608 initrd.img                                     2
2730.076438904 = 2931.397255168 initrd.img.old                                 3

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig 
 
LABEL loadconfig 
  CONFIG /isolinux/isolinux.cfg 
  APPEND /isolinux/ 
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/7423/mounts) leaked on lvs invocation. Parent PID 15879: bash
File descriptor 63 (pipe:[56614]) leaked on lvs invocation. Parent PID 15879: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 2016-06-16__15h44 ===================
boot-info version : 4ppa38
boot-sav version : 4ppa38
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa38
boot-info is executed in live-session (Ubuntu 16.04 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --- maybe-ubiquity
ls: cannot access '/home/usr/.config': No such file or directory
NTFS signature is missing.
Failed to mount '/dev/sda4': Invalid argument
The device '/dev/sda4' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sda4 : Error code 12
mount -r /dev/sda4 /mnt/boot-sav/sda4
NTFS signature is missing.
Failed to mount '/dev/sda4': Invalid argument
The device '/dev/sda4' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sda4 : Error code 12
Partition 1 does not start on physical sector boundary.

=================== os-prober:
/dev/sda3:Ubuntu 16.04 LTS (16.04):Ubuntu:linux

=================== blkid:
/dev/sda2: LABEL="4hdd" UUID="340E15EB0E15A6C0" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="8a576fdb-1107-48be-9198-725be79f933d"
/dev/sda3: UUID="e1fe3d70-b463-40df-b9a1-3f8a3dd567fe" TYPE="ext4" PTTYPE="dos" PARTUUID="c886239e-c8e8-4f8f-9dcd-0619cc38eeaa"
/dev/sdb2: LABEL="3hdd" UUID="A44EFE8E4EFE588E" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="dec5e2be-1eb2-4ff6-abbf-e0fb41dfbc01"
/dev/sdc1: LABEL="UBUNTU 16_0" UUID="568B-46DF" TYPE="vfat" PARTUUID="0002903d-01"
/dev/loop0: TYPE="squashfs"
/dev/sda1: PARTLABEL="Microsoft reserved partition" PARTUUID="6d3d49d5-9260-40c5-a51d-cc85f4e51c92"
/dev/sda4: PARTUUID="c447f857-6a5c-486b-8ce3-dcd5ae98819f"
/dev/sdb1: PARTLABEL="Microsoft reserved partition" PARTUUID="45b53fc2-1e37-4c4b-b2c5-d68e3c14e06b"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

NTFS signature is missing.
Failed to mount '/dev/sda4': Invalid argument
The device '/dev/sda4' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sda4 : Error code 12
mount -r /dev/sda4 /mnt/boot-sav/sda4
NTFS signature is missing.
Failed to mount '/dev/sda4': Invalid argument
The device '/dev/sda4' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sda4 : Error code 12
Partition 1 does not start on physical sector boundary.

=================== sda3/etc/grub.d/ :
drwxr-xr-x  2 root root    4096  6&#50900; 16 13:59 grub.d
drwxr-xr-x  2 root root    4096  6&#50900; 16 10:25 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9791  4&#50900; 15 22:00 00_header
-rwxr-xr-x 1 root root  6258  3&#50900; 15 18:08 05_debian_theme
-rwxr-xr-x 1 root root 12261  4&#50900; 15 22:00 10_linux
-rwxr-xr-x 1 root root 11082  4&#50900; 15 22:00 20_linux_xen
-rwxr-xr-x 1 root root 11692  4&#50900; 15 22:00 30_os-prober
-rwxr-xr-x 1 root root  1418  4&#50900; 15 22:00 30_uefi-firmware
-rwxr-xr-x 1 root root   214  4&#50900; 15 22:00 40_custom
-rwxr-xr-x 1 root root   216  4&#50900; 15 22:00 41_custom
-rw-r--r-- 1 root root   483  4&#50900; 15 22:00 README




=================== sda3/etc/default/grub :

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
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb2.
sda4    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.

sda    : GPT,    BIOS_boot,    has-no-EFIpart,     not-usb,    has-os,    34 sectors * 512 bytes
sdb    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    34 sectors * 512 bytes


=================== parted -l:

Model: ATA HGST HUS724040AL (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                          Flags
1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
2      135MB   2927GB  2927GB  ntfs         Basic data partition          msftdata
4      2927GB  2927GB  3146kB                                             bios_grub
3      2927GB  4001GB  1074GB  ext4


Model: ATA TOSHIBA DT01ACA3 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                          Flags
1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
2      135MB   3001GB  3000GB  ntfs         Basic data partition          msftdata


Model: SMI USB DISK (scsi)
Disk /dev/sdc: 8054MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  8054MB  8053MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:4001GB:scsi:512:512:gpt:ATA HGST HUS724040AL:;
1:17.4kB:134MB:134MB::Microsoft reserved partition:msftres;
2:135MB:2927GB:2927GB:ntfs:Basic data partition:msftdata;
4:2927GB:2927GB:3146kB:::bios_grub;
3:2927GB:4001GB:1074GB:ext4::;

BYT;
/dev/sdb:3001GB:scsi:512:4096:gpt:ATA TOSHIBA DT01ACA3:;
1:17.4kB:134MB:134MB::Microsoft reserved partition:msftres;
2:135MB:3001GB:3000GB:ntfs:Basic data partition:msftdata;

BYT;
/dev/sdc:8054MB:scsi:512:512:msdos:SMI USB DISK:;
1:1049kB:8054MB:8053MB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE    SIZE LABEL
sda   disk           3.7T
sda1  part           128M
sda2  part ntfs      2.7T 4hdd
sda3  part ext4     1000G
sda4  part             3M
sdb   disk           2.7T
sdb1  part           128M
sdb2  part ntfs      2.7T 3hdd
sdc   disk           7.5G
sdc1  part vfat      7.5G UBUNTU 16_0
loop0 loop squashfs  1.3G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0         /mnt/boot-sav/sda3
sda4     1  0  0
sdb      1  0  0 running
sdb1     1  0  0
sdb2     1  0  0         /mnt/boot-sav/sdb2
sdc      1  0  1 running
sdc1     1  0  1         /cdrom
loop0    1  1  0         /rofs


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=16432648k,nr_inodes=4108162,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=3289460k,mode=755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd,nsroot=/)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,nsroot=/)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices,nsroot=/)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer,nsroot=/)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio,nsroot=/)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory,nsroot=/)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,nsroot=/)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,nsroot=/)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio,nsroot=/)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,nsroot=/)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct,nsroot=/)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=3289460k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type ext4 (rw,relatime,data=ordered)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda4 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fb1 fd full fuse hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-15 i2c-16 i2c-17 i2c-18 i2c-19 i2c-2 i2c-20 i2c-21 i2c-22 i2c-23 i2c-24 i2c-25 i2c-26 i2c-27 i2c-28 i2c-29 i2c-3 i2c-30 i2c-31 i2c-32 i2c-33 i2c-34 i2c-35 i2c-36 i2c-37 i2c-38 i2c-39 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg kvm lightnvm log mapper mcelog mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sdb sdb1 sdb2 sdc sdc1 sg0 sg1 sg2 shm snapshot snd stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 04 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff af bc 54 01 00 00 00  |...........T....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  c0 a6 15 0e eb 15 0e 34  |...............4|
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

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 04 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 97 4c 5d 01 00 00 00  |..........L]....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  8e 58 fe 4e 8e fe 4e a4  |.........X.N..N.|
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
Partition 1 does not start on physical sector boundary.

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs   16G     0   16G   0% /dev
tmpfs          tmpfs     3.2G  9.7M  3.2G   1% /run
/dev/sdc1      vfat      7.5G  1.4G  6.2G  19% /cdrom
/dev/loop0     squashfs  1.4G  1.4G     0 100% /rofs
/cow           overlay    16G  111M   16G   1% /
tmpfs          tmpfs      16G  180K   16G   1% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs      16G     0   16G   0% /sys/fs/cgroup
tmpfs          tmpfs      16G  268K   16G   1% /tmp
tmpfs          tmpfs     3.2G   64K  3.2G   1% /run/user/999
/dev/sda2      fuseblk   2.7T  481G  2.2T  18% /mnt/boot-sav/sda2
/dev/sda3      ext4      985G  4.6G  930G   1% /mnt/boot-sav/sda3
/dev/sdb2      fuseblk   2.8T  1.5T  1.3T  54% /mnt/boot-sav/sdb2

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.3 GiB, 1433468928 bytes, 2799744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F535C23A-C143-474F-B283-2D3AEA2B3992

Device          Start        End    Sectors  Size Type
/dev/sda1          34     262177     262144  128M Microsoft reserved
/dev/sda2      264192 5716883455 5716619264  2.7T Microsoft basic data
/dev/sda3  5716889600 7814035455 2097145856 1000G Linux filesystem
/dev/sda4  5716883456 5716889599       6144    3M BIOS boot

Partition table entries are not in disk order.


Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 75C965BF-5141-4D25-A5EA-4E12A9CA61C5

Device      Start        End    Sectors  Size Type
/dev/sdb1      34     262177     262144  128M Microsoft reserved
/dev/sdb2  264192 5860532223 5860268032  2.7T Microsoft basic data



Disk /dev/sdc: 7.5 GiB, 8054112256 bytes, 15730688 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0002903d

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 15730687 15728640  7.5G  c W95 FAT32 (LBA)




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to) and reinstall the grub2 of sda3 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s




```

---

### Post by grahammechanical on 2016-06-16
Is that a BIOS boot system motherboard but with a GPT partitioned hard drive? With a BIOS boot system and a GPT drive Grub is not installed into the MBR but into the bios_boot partition. With a BIOS boot system and a MBR partition drive Grub is installed into the MBR and there is no bios_boot partition. Although there may be a /boot partition. Which is something else.

You seem to have Grub installed in the MBR of sda and a bios_boot partition (sda4) with Grub core image. As well as that, Grub is also installed in the sda3 partition. And no swap partition.

Regards

---

### Post by ubfan1 on 2016-06-16
You might need the bios_boot partition first, before the other hugh partitions.  There might be a problem for BIOS addressing its core.img so far into the disk.  Just like the old /boot issue used to cause problems for the kernels on "large" disks.

---

### Post by dgdrg on 2016-06-17
Thank you all (I'm author of this thread. forgot the password.)
I removed the grub2 bios(legacy).

> 
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
sudo dd if=/dev/zero of=/dev/sda3 bs=446 count=1
deleted the bios-boot partition


then, installed grub2 as EFI by following this([http://ubuntuforums.org/showthread.php?t=2223856&page=3](http://ubuntuforums.org/showthread.php?t=2223856&page=3)), and then, it works well :D

---

