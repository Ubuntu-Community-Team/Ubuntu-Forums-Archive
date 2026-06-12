---
title: "Installation of Ubuntu failed"
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by Rehaan_Raja on 2015-09-30
I have a 250gb SSD in my laptop.

Before trying to install Ubuntu alongside Windows 8(.1), I had 1 single partition on my SSD with Windows, with about 100 gb unallocated. Note, I didn't even have the "System Reserved" partition.

I ran the Ubuntu installer via USB, chose the option to install Ubuntu alongside Windows 8, to dual boot. After the install was completed, and since, when I boot my laptop, my PC goes straight to Windows 8.1 and skips the dual boot screen.

I rebooted my USB with the Ubuntu iso image and the installer says it doesn't even detect an OS on my machine despite the fact that my PC boots Windows perfectly.

I went to the disk management window and tried to extend the single partition with Windows on it, so that I would have one large single partition with my Windows and an apparently hidden Ubuntu.
For some bizarre reason, it completed the operation by giving me 3 partitions
One with Windows
One healthy 90GB primary partition (I assume this is where Ubuntu is installed? Worth noting, the Ubuntu installer didn't even ask me how much storage I wanted Ubuntu to have)
One healthy 8GB primary partition (I assume this is a SWAP partition which it created automatically?)

Any help? Is there some kind of software I need to use to repair the dual boot 'thing'? - dunno what to call it yet.

Oh and my laptop has an 8GB RAM

---

### Post by yancek on 2015-09-30
To get more details for someone to help, go to the site below and download and run the boot repair software.  Do this from the Ubuntu installation media and select the option to Create Bootinfo summary to post here for someone to help.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2015-09-30
The Ubuntu installer always creates 2 partitions. One for Ubuntu and one for swap. The hard disk had 100 GB of unallocated space and by accepting the Install alongside option you gave the installer the authoprity to use as much of the unallocated space as it wanted. To have more control over how much space is used for Ubuntu we have to use the Something Else option. But that is more complicated.

The next time you ran the installer it could not find any unallocated space. So, it does not show any operating systems because the only option would be to Eraze disk and install Ubuntu. And you might not want that to happen. So the installer does not offer any options for installing.

 If you run the Try Ubuntu session. You could open the Disks utility and that will show you all the partitions on to hard disk. But as to the reason why you do not get an option to load Ubuntu, please read this wiki page,

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Windows 8.1 would have been installed in EFI mode and that means that Ubuntu must also be installed in EFI mode otherwise we can load one OS but not the other. Also Fast startup in Windows must be disabled as well as Qucik Boot/Fast boot.

Regards.

---

### Post by Rehaan_Raja on 2015-09-30
> **grahammechanical said:**
> The Ubuntu installer always creates 2 partitions. One for Ubuntu and one for swap. The hard disk had 100 GB of unallocated space and by accepting the Install alongside option you gave the installer the authoprity to use as much of the unallocated space as it wanted. To have more control over how much space is used for Ubuntu we have to use the Something Else option. But that is more complicated.

The next time you ran the installer it could not find any unallocated space. So, it does not show any operating systems because the only option would be to Eraze disk and install Ubuntu. And you might not want that to happen. So the installer does not offer any options for installing.

 If you run the Try Ubuntu session. You could open the Disks utility and that will show you all the partitions on to hard disk. But as to the reason why you do not get an option to load Ubuntu, please read this wiki page,

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Windows 8.1 would have been installed in EFI mode and that means that Ubuntu must also be installed in EFI mode otherwise we can load one OS but not the other. Also Fast startup in Windows must be disabled as well as Qucik Boot/Fast boot.

Regards.

Hi,

Thanks for the info.
I have Windows installed on an MBR, not as GPT, if that is what you meant by EFI mode.

I'll try the other stuff later and post back my results.

Thanks

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid de3940b8-e7fd-44af-8872-309fac36c8e8 root hd1,msdos5 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Windows 7/8/2012 is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdc.
 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07
    Boot sector info:  Syslinux looks at sector 29630 of /dev/sdd1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   468,856,831   468,854,784   7 NTFS / exFAT / HPFS
/dev/sdb2         264,060,926   468,860,927   204,800,002   5 Extended
/dev/sdb5         264,060,928   452,255,743   188,194,816  83 Linux
/dev/sdb6         452,257,792   468,860,927    16,603,136  82 Linux swap / Solaris

/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb1 overlaps with /dev/sdb5
/dev/sdb1 overlaps with /dev/sdb6

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4076 MB, 4076863488 bytes
255 heads, 63 sectors/track, 495 cylinders, total 7962624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048     7,962,623     7,960,576   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 62.0 GB, 61951967232 bytes
255 heads, 63 sectors/track, 7531 cylinders, total 120999936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048   120,999,935   120,997,888   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        E49472639472385E                       ntfs       
/dev/sdb5        de3940b8-e7fd-44af-8872-309fac36c8e8   ext4       
/dev/sdb6        b8040a5f-8506-46f0-9511-1cb1752b8d06   swap       
/dev/sdc1        5852-1602                              vfat       BOOT-REPAIR
/dev/sdd1        1D13-246B                              vfat       LINUX MINT

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Oct  3 02:20 ata-HGST_HTE725050A7E630_TV650AXF029ZSN -> ../../sda
lrwxrwxrwx 1 root root 10 Oct  3  2015 ata-HGST_HTE725050A7E630_TV650AXF029ZSN-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Oct  3 02:20 ata-KINGSTON_SM2280S3240G_50026B7254076909 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct  3 02:20 ata-KINGSTON_SM2280S3240G_50026B7254076909-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Oct  3  2015 ata-KINGSTON_SM2280S3240G_50026B7254076909-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Oct  3  2015 ata-KINGSTON_SM2280S3240G_50026B7254076909-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Oct  3  2015 ata-KINGSTON_SM2280S3240G_50026B7254076909-part6 -> ../../sdb6
lrwxrwxrwx 1 root root  9 Oct  3 02:20 usb-USB_DISK_2.0_I6JI7UBO9OG9M8PD-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Oct  3  2015 usb-USB_DISK_2.0_I6JI7UBO9OG9M8PD-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Oct  3 02:20 usb-_USB_DISK_3.0_0708513BAC560832-0:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 Oct  3  2015 usb-_USB_DISK_3.0_0708513BAC560832-0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Oct  3 02:20 wwn-0x5000cca77bc10e40 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct  3  2015 wwn-0x5000cca77bc10e40-part1 -> ../../sda1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/mint/BOOT-REPAIR  vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='hd1,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  de3940b8-e7fd-44af-8872-309fac36c8e8
else
  search --no-floppy --fs-uuid --set=root de3940b8-e7fd-44af-8872-309fac36c8e8
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-de3940b8-e7fd-44af-8872-309fac36c8e8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  de3940b8-e7fd-44af-8872-309fac36c8e8
    else
      search --no-floppy --fs-uuid --set=root de3940b8-e7fd-44af-8872-309fac36c8e8
    fi
    linux    /boot/vmlinuz-3.19.0-25-generic root=UUID=de3940b8-e7fd-44af-8872-309fac36c8e8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.19.0-25-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-de3940b8-e7fd-44af-8872-309fac36c8e8' {
    menuentry 'Ubuntu, with Linux 3.19.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-advanced-de3940b8-e7fd-44af-8872-309fac36c8e8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  de3940b8-e7fd-44af-8872-309fac36c8e8
        else
          search --no-floppy --fs-uuid --set=root de3940b8-e7fd-44af-8872-309fac36c8e8
        fi
        echo    'Loading Linux 3.19.0-25-generic ...'
        linux    /boot/vmlinuz-3.19.0-25-generic root=UUID=de3940b8-e7fd-44af-8872-309fac36c8e8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-recovery-de3940b8-e7fd-44af-8872-309fac36c8e8' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  de3940b8-e7fd-44af-8872-309fac36c8e8
        else
          search --no-floppy --fs-uuid --set=root de3940b8-e7fd-44af-8872-309fac36c8e8
        fi
        echo    'Loading Linux 3.19.0-25-generic ...'
        linux    /boot/vmlinuz-3.19.0-25-generic root=UUID=de3940b8-e7fd-44af-8872-309fac36c8e8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-25-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  de3940b8-e7fd-44af-8872-309fac36c8e8
    else
      search --no-floppy --fs-uuid --set=root de3940b8-e7fd-44af-8872-309fac36c8e8
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  de3940b8-e7fd-44af-8872-309fac36c8e8
    else
      search --no-floppy --fs-uuid --set=root de3940b8-e7fd-44af-8872-309fac36c8e8
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-E49472639472385E' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  E49472639472385E
    else
      search --no-floppy --fs-uuid --set=root E49472639472385E
    fi
    parttool ${root} hidden-
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=de3940b8-e7fd-44af-8872-309fac36c8e8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=b8040a5f-8506-46f0-9511-1cb1752b8d06 none            swap    sw              0       0
--------------------------------------------------------------------------------

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

menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
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

=========================== sdd1/boot/grub/grub.cfg: ===========================

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

menuentry "Start Linux Mint 17.2 Cinnamon 64-bit" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/linuxmint.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Start Linux Mint 17.2 Cinnamon 64-bit (compatibility mode)" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/linuxmint.seed boot=casper xforcevesa iso-scan/filename=${iso_path} ramdisk_size=1048576 root=/dev/ram rw noapic noacpi nosplash irqpoll --
    initrd    /casper/initrd.lz
}
menuentry "Check the integrity of the medium" {
    linux    /casper/vmlinuz  boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdd1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig 
 
LABEL loadconfig 
  CONFIG /isolinux/isolinux.cfg 
  APPEND /isolinux/ 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  bc 17 42 29 ad 63 c5 f2  d1 a9 21 eb 28 3e b5 8e  |..B).c....!.(>..|
00000010  dd 82 d2 d8 15 57 3d 45  49 0e cc ee b9 1c a5 b2  |.....W=EI.......|
00000020  9d d6 8e f7 78 e8 80 d2  a3 80 6d 22 c6 fc 33 86  |....x.....m"..3.|
00000030  9e c5 5b 57 ed 45 63 d8  b3 41 e2 13 cb 20 1e 28  |..[W.Ec..A... .(|
00000040  dd 5f 57 5e 24 78 b4 08  2c 2c 56 e3 5e 56 54 b8  |._W^$x..,,V.^VT.|
00000050  76 c6 1d 10 ea 1f a0 5a  c9 6f 05 2e b5 9a 25 a3  |v......Z.o....%.|
00000060  7e 8d 1e d6 d5 c9 78 6a  94 45 bb 8c 22 4c ad a4  |~.....xj.E.."L..|
00000070  9e d6 f8 b3 2a 56 92 fc  4e f9 a9 0d 9f 7d 1c 48  |....*V..N....}.H|
00000080  82 64 8f ac 77 58 e6 fc  8b 3d 15 98 1d b8 51 8f  |.d..wX...=....Q.|
00000090  a3 82 3b 76 a2 ab c9 bd  63 f8 cb 3d c2 c1 5b 05  |..;v....c..=..[.|
000000a0  04 a0 1c 29 46 61 cf 56  d7 1d 5d ec fa 40 43 3b  |...)Fa.V..]..@C;|
000000b0  9b 2e d0 6a 9d bf a6 8d  42 38 b0 1d f3 8f 7d 5c  |...j....B8....}\|
000000c0  93 76 11 9c 40 1f 93 31  f8 a5 25 e7 ef 9e 50 8e  |.v..@..1..%...P.|
000000d0  9c b8 9a ed 2f 8c e2 c0  47 f8 81 06 46 8e 81 9b  |..../...G...F...|
000000e0  64 31 95 70 52 f7 28 fa  3e e1 97 cc 25 16 67 a3  |d1.pR.(.>...%.g.|
000000f0  0b 1d 7d 1e b5 f1 db 29  2a 10 23 76 cf 13 e9 36  |..}....)*.#v...6|
00000100  e5 96 5d ca ba e5 91 7b  54 16 e4 59 79 94 42 d6  |..]....{T..Yy.B.|
00000110  37 34 52 2e 54 56 02 1b  0c 5d 75 28 fc 8e fe e9  |74R.TV...]u(....|
00000120  eb 48 b5 b7 57 a1 d3 5b  b0 d5 8e 08 8b ca 81 72  |.H..W..[.......r|
00000130  c3 68 e6 98 e1 51 a8 9a  49 52 3b 5f e8 d0 46 b1  |.h...Q..IR;_..F.|
00000140  52 23 e0 a5 81 d8 16 c4  c5 cc bc bc 7e e5 8a c3  |R#..........~...|
00000150  a4 0b a8 2c 58 6f 1f fd  f8 f6 55 6c 8d 6c 8f 0e  |...,Xo....Ul.l..|
00000160  3c 40 0f 4d ca b1 01 2c  42 e6 d0 5f a0 59 12 14  |<@.M...,B.._.Y..|
00000170  92 9e db 7d c5 79 ad 74  26 e1 da ce b6 2d 42 61  |...}.y.t&....-Ba|
00000180  b3 0e 70 21 43 33 05 5a  b6 cf a7 4d 64 51 ec cc  |..p!C3.Z...MdQ..|
00000190  d1 20 01 32 cf 5f 30 ca  c7 a8 e1 3c 21 39 b8 93  |. .2._0....<!9..|
000001a0  e0 1c 87 e7 bb 26 6b 8c  43 6c c0 a1 60 d5 27 63  |.....&k.Cl..`.'c|
000001b0  e5 11 1a af 77 a3 73 c8  12 ad 16 e2 0d 82 76 34  |....w.s.......v4|
000001c0  cb 12 90 4d 03 a9 3b 3e  e7 c5 73 f9 ff 15 ef 26  |...M..;>..s....&|
000001d0  1f 03 b4 27 01 14 10 60  72 12 3f 6a 0d 0b f7 d3  |...'...`r.?j....|
000001e0  7e ce 76 72 6d 5d fa ec  07 55 7e 38 96 d2 a9 6f  |~.vrm]...U~8...o|
000001f0  ee 55 3c ea fd e7 a9 d1  f4 f6 1f 92 d6 3a e9 32  |.U<..........:.2|
00000200


=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 9 (/proc/4846/mounts) leaked on lvs invocation. Parent PID 13075: bash
File descriptor 63 (pipe:[49930]) leaked on lvs invocation. Parent PID 13075: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-10-03__02h20 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version :
boot-repair is executed in live-session (Linux Mint 17.2 Rafaela, rafaela, LinuxMint, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/linuxmint.seed boot=casper initrd=/casper/initrd.lz quiet splash -- BOOT_IMAGE=/casper/vmlinuz
ls: cannot access /home/usr/.config: No such file or directory
Windows is hibernated, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sdb1 /mnt/boot-sav/sdb1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sdb1 : Error code 14
mount -r /dev/sdb1 /mnt/boot-sav/sdb1

=================== os-prober:
/dev/sdb1:Windows 8 (loader):Windows:chain
/dev/sdb5:Ubuntu 14.04.3 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sdb1: UUID="E49472639472385E" TYPE="ntfs"
/dev/sdb5: UUID="de3940b8-e7fd-44af-8872-309fac36c8e8" TYPE="ext4"
/dev/sdb6: UUID="b8040a5f-8506-46f0-9511-1cb1752b8d06" TYPE="swap"
/dev/sdc1: LABEL="BOOT-REPAIR" UUID="5852-1602" TYPE="vfat"
/dev/sdd1: LABEL="LINUX MINT" UUID="1D13-246B" TYPE="vfat"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

mkdir: cannot create directory ‘/mnt/boot-sav/sdb1/boot-sav’: Read-only file system
sdb1 is Read-only or full
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sdb5/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug  5 05:20 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Jun 26 11:16 00_header
-rwxr-xr-x 1 root root  6058 May 13 14:51 05_debian_theme
-rwxr-xr-x 1 root root 11608 Jun 26 11:16 10_linux
-rwxr-xr-x 1 root root 10412 Jun 26 11:16 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Jun 26 11:16 30_os-prober
-rwxr-xr-x 1 root root  1416 Jun 26 11:16 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jun 26 11:16 40_custom
-rwxr-xr-x 1 root root   216 Jun 26 11:16 41_custom
-rw-r--r-- 1 root root   483 Jun 26 11:16 README




=================== sdb5/etc/default/grub :

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



=================== No kernel in /media/mint/BOOT-REPAIR/boot:
grub



=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
EFI in dmesg.
[    0.000000] ACPI: UEFI 0x00000000AC3CBA10 000042 (v01                 00000000      00000000)
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.
sdb5    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb5.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/mint/BOOT-REPAIR.

sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-correctEFI,     liveusb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA HGST HTE725050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  500GB  500GB  primary               boot


Error: Can't have overlapping partitions.

Model: USB DISK 2.0 (scsi)
Disk /dev/sdc: 4077MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  4077MB  4076MB  primary  fat32        boot, lba


Model:  USB DISK 3.0 (scsi)
Disk /dev/sdd: 62.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  62.0GB  62.0GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA HGST HTE725050A7;
1:1049kB:500GB:500GB:::boot;

Error: Can't have overlapping partitions.

BYT;
/dev/sdc:4077MB:scsi:512:512:msdos:USB DISK 2.0;
1:1049kB:4077MB:4076MB:fat32::boot, lba;

BYT;
/dev/sdd:62.0GB:scsi:512:512:msdos: USB DISK 3.0;
1:1049kB:62.0GB:62.0GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL    MODEL    UUID
sda   disk          465.8G          HGST HTE
sda1  part          465.8G
sdb   disk          223.6G          KINGSTON
sdb1  part ntfs     223.6G                   E49472639472385E
sdb2  part              1K
sdb5  part ext4      89.8G                   de3940b8-e7fd-44af-8872-309fac36c8e8
sdb6  part swap       7.9G                   b8040a5f-8506-46f0-9511-1cb1752b8d06
sdc   disk            3.8G          DISK 2.0
sdc1  part vfat       3.8G BOOT-REPAIR
5852-1602
sdd   disk           57.7G          USB DISK
sdd1  part vfat      57.7G LINUX MINT
1D13-246B
loop0 loop squashfs   1.5G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0
sdb      0  0  0 running
sdb1     0  0  0         /mnt/boot-sav/sdb1
sdb2     0  0  0
sdb5     0  0  0         /mnt/boot-sav/sdb5
sdb6     0  0  0         [SWAP]
sdc      1  0  1 running
sdc1     1  0  1         /media/mint/BOOT-REPAIR
sdd      1  0  1 running
sdd1     1  0  1         /cdrom
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdd1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=mint)
/dev/sdc1 on /media/mint/BOOT-REPAIR type vfat (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /mnt/boot-sav/sdb5 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 sdb6 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hpet input kmsg kvm log mapper mcelog media0 mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdb5 sdb6 sdc sdc1 sdd sdd1 sg0 sg1 sg2 sg3 shm snapshot snd stderr stdin stdout uhid uinput urandom v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 27 f2 1b 00 00 00 00  |.........'......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  5e 38 72 94 63 72 94 e4  |........^8r.cr..|
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
ls sdc1/efi: /BOOT/grubx64.efi /BOOT/BOOTx64.EFI
ls sdc1: autorun.inf
boot
casper
dists
EFI
install
isolinux
ldlinux.sys
md5sum.txt
pics
pool
preseed
README.diskdefines
syslinux.cfg
ubuntu  . Please report this message to [email]boot.repair@gmail.com[/email]

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 62 03  |.X.SYSLINUX...b.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 78 79 00 4f 1e 00 00  00 00 00 00 02 00 00 00  |.xy.O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 02 16 52 58 4e  4f 20 4e 41 4d 45 20 20  |..)..RXNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d f8 50 50 50 50 cd  13 eb 62 8b 55 aa 8b 75  |.M.PPPP...b.U..u|
000000a0  a8 c1 ee 04 01 f2 83 fa  4f 76 31 81 fa b2 07 73  |........Ov1....s|
000000b0  2b f6 45 b4 7f 75 25 38  4d b8 74 20 66 3d 21 47  |+.E..u%8M.t f=!G|
000000c0  50 54 75 10 80 7d b8 ed  75 0a 66 ff 75 ec 66 ff  |PTu..}..u.f.u.f.|
000000d0  75 e8 eb 0f 51 51 66 ff  75 bc eb 07 51 51 66 ff  |u...QQf.u...QQf.|
000000e0  36 1c 7c b4 08 e8 e9 00  72 13 20 e4 75 0f c1 ea  |6.|.....r. .u...|
000000f0  08 42 89 16 1a 7c 83 e1  3f 89 0e 18 7c fb bb aa  |.B...|..?...|...|
00000100  55 b4 41 e8 cb 00 72 10  81 fb 55 aa 75 0a f6 c1  |U.A...r...U.u...|
00000110  01 74 05 c6 06 46 7d 00  66 b8 08 40 00 00 66 ba  |.t...F}.f..@..f.|
00000120  00 00 00 00 bb 00 80 e8  0e 00 66 81 3e 1c 80 a1  |..........f.>...|
00000130  f3 42 6f 75 74 e9 f8 02  66 03 06 60 7b 66 13 16  |.Bout...f..`{f..|
00000140  64 7b b9 10 00 eb 2b 66  52 66 50 06 53 6a 01 6a  |d{....+fRfP.Sj.j|
00000150  10 89 e6 66 60 b4 42 e8  77 00 66 61 8d 64 10 72  |...f`.B.w.fa.d.r|
00000160  01 c3 66 60 31 c0 e8 68  00 66 61 e2 da c6 06 46  |..f`1..h.fa....F|
00000170  7d 2b 66 60 66 0f b7 36  18 7c 66 0f b7 3e 1a 7c  |}+f`f..6.|f..>.||
00000180  66 f7 f6 31 c9 87 ca 66  f7 f7 66 3d ff 03 00 00  |f..1...f..f=....|
00000190  77 17 c0 e4 06 41 08 e1  88 c5 88 d6 b8 01 02 e8  |w....A..........|
000001a0  2f 00 66 61 72 01 c3 e2  c9 31 f6 8e d6 bc 68 7b  |/.far....1....h{|
000001b0  8e de 66 8f 06 78 00 be  da 7d ac 20 c0 74 09 b4  |..f..x...}. .t..|
000001c0  0e bb 07 00 cd 10 eb f2  31 c0 cd 16 cd 19 f4 eb  |........1.......|
000001d0  fd 8a 16 74 7b 06 cd 13  07 c3 42 6f 6f 74 20 65  |...t{.....Boot e|
000001e0  72 72 6f 72 0d 0a 00 00  00 00 00 00 00 00 00 00  |rror............|
000001f0  00 00 00 00 00 00 00 00  fe 02 b2 3e 18 37 55 aa  |...........>.7U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G  277M  3.6G   8% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      791M  1.5M  789M   1% /run
/dev/sdd1      vfat        58G  1.6G   57G   3% /cdrom
/dev/loop0     squashfs   1.5G  1.5G     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G   20K  3.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.9G  668K  3.9G   1% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sdc1      vfat       3.8G  614M  3.2G  16% /media/mint/BOOT-REPAIR
/dev/sdb1      fuseblk    224G   79G  146G  36% /mnt/boot-sav/sdb1
/dev/sdb5      ext4        89G  3.8G   80G   5% /mnt/boot-sav/sdb5

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc39dd40f

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976769023   488383488    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77ede6bf

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   468856831   234427392    7  HPFS/NTFS/exFAT
/dev/sdb2       264060926   468860927   102400001    5  Extended
/dev/sdb5       264060928   452255743    94097408   83  Linux
/dev/sdb6       452257792   468860927     8301568   82  Linux swap / Solaris

Disk /dev/sdc: 4076 MB, 4076863488 bytes
255 heads, 63 sectors/track, 495 cylinders, total 7962624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01c8b200

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048     7962623     3980288    c  W95 FAT32 (LBA)

Disk /dev/sdd: 62.0 GB, 61951967232 bytes
255 heads, 63 sectors/track, 7531 cylinders, total 120999936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001c798d

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   120999935    60498944    c  W95 FAT32 (LBA)




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sdb5 into the MBRs of all disks (except USB without OS).
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sdb disk!


=================== User settings
The settings chosen by the user will not act on the boot.




pastebinit  packages needed
User refused to install pastebinit
```

---

### Post by yancek on 2015-10-04
The default install for the Grub bootloader with Ubuntu is in the master boot record of the first drive.  In your case that is the 500GB drive which shows one partition with an ntfs filesystem.  Your second drive on which you have windows installed also has Ubuntu.  You have Grub installed to the MBR of the 500GB drive.  Is that what you wanted?  You also have windows code installed to the MBR of the second drive on which you have windows/Ubuntu.  Is that what your intention was or did you want the boot code in the MBR of the smaller disk on which you have windows/Ubuntu?

---

### Post by Rehaan_Raja on 2015-10-04
> **yancek said:**
> The default install for the Grub bootloader with Ubuntu is in the master boot record of the first drive.  In your case that is the 500GB drive which shows one partition with an ntfs filesystem.  Your second drive on which you have windows installed also has Ubuntu.  You have Grub installed to the MBR of the 500GB drive.  Is that what you wanted?  You also have windows code installed to the MBR of the second drive on which you have windows/Ubuntu.  Is that what your intention was or did you want the boot code in the MBR of the smaller disk on which you have windows/Ubuntu?

My laptop has two drives. 

1) 500 GB HDD - Whole Disk Encrypted via truecrypt. No data seems to have been written to it though since the volume mounts without problem.

2) 250 GB SSD - On this I want my Windows installation and Ubuntu installation.

---

### Post by yancek on 2015-10-04
>  250 GB SSD - On this I want my Windows installation and Ubuntu installation. 		

Well, you have that.  You also have windows code in the master boot record of that drive so if that's what you want you will have to manually edit the bcdedit (or whatevery file your windows uses) to add an entry for Ubuntu.  Otherwise, you could simply install grub to the mbr of that device.  Several methods to accomplish this using the install medium of Ubuntu or boot repair are at the link below.  The reason for the problem is that you accepted the default for the bootloader installation which is to the MBR of the first device and that is not what you wanted.  

  [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by Rehaan_Raja on 2015-10-04
> **yancek said:**
> Well, you have that.  You also have windows code in the master boot record of that drive so if that's what you want you will have to manually edit the bcdedit (or whatevery file your windows uses) to add an entry for Ubuntu.  Otherwise, you could simply install grub to the mbr of that device.  Several methods to accomplish this using the install medium of Ubuntu or boot repair are at the link below.  The reason for the problem is that you accepted the default for the bootloader installation which is to the MBR of the first device and that is not what you wanted.  

  [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

[B]1) "if that's what you want you will have to manually edit the bcdedit (or  whatevery file your windows uses) to add an entry for Ubuntu" Don't know how to do that. 

2) "you could simply install grub to the mbr of that device" Don't know how to do that either. Will check out the Ubuntu install  medium but I'm pretty sure I haven't seen something like that in the installation settings or windows. Do you know how to do this?[/B]


[B]So has any data been written to my 500GB HDD? Wouldn't or shouldn't this corrupt my encrypted volume? I have backed up the data just in case.

Anyways, if the first two steps don't work or you don't reply to, would it be fine to delete the two Ubuntu partitions and just use the "something else" option this time?[/B]

****

I have to say though, this problem of Windows recognising the hdd in place of the ssd happens ALL the time when installing windows on an MBR. trying to install Windows on an MBR hence is a pain in the ass. I'm surprised this problem is occurring with Ubuntu as well.
It might be a design flaw with the motherboard; though I don't exclude software flaws - eg. Windows doesn't allow me to install on an MBR SSD without the HDD inserted at the same time. It doesn't need the HDD for anything, but it did a while back format my HDD for the lulz anyways. I lost my data -.-

lol

Would the repair option in the boot repair software do the trick?

---

### Post by Rehaan_Raja on 2015-10-05
Bop

---

### Post by Rehaan_Raja on 2015-10-08
Bop Bop

Hello???

---

### Post by Rehaan_Raja on 2015-10-08
This is starting to get really frustrating for me.

---

### Post by ubfan1 on 2015-10-08
Just to try to keep things going here, not that I'm an expert in Windows 8 dual boot on MBR disks or encryption.
I think 1)bcdedit... was only mentioned as a possibility, but you'd get more help on a Windows bootloader on the superuser forum.  Probably only mentioned if you felt you could do the Windows changes.
2)Install grub to sdb...  Since that seems to be the bootloader which runs.  OK, but that will replace the working Windows bootloader.  Now grub should be able to boot Windows, but since you already have grub installed to hda, why not put that first in the boot order (Done in the BIOS )?  That should be all you need to do to boot grub, which should have both Ubuntu and Windows in its boot menu.  If you really want to install grub onto hdb, from a terminal (live media, ctrl-alt-t) type
sudo grub-install /dev/sdb
Again, I'd try changing the boot order first, the grub should work just the same from either place.
3) The grub bootloader has been written to sda.  That's really outside any normal partition, so hopefully, wont affect your encryption.  Try and mount it would be the easiest test.
You could delete the Ubuntu and Swap partitions and do over, making sure to enter the sdb for the bootloader location instead of accepting the sda default.  The results should be the same as just installing grub to the sdb.
boot-repair does tend to write grub everywhere, so I guess that would also work, your choice.

---

### Post by oldfred on 2015-10-10
You do need to be careful and not use any auto install or repair options. Those default to installing grub to sda or to all drives. That may overwrite something essential in your encrypted sda drive's MBR. And your backups probably did not include MBR as not part of any partition.

If installing Windows it installs a boot partition to the drive set as first in BIOS boot order even if that is not the drive you install into. We have seen users install to sdb and it just overwrites the first 100MB of the Ubuntu install with its boot loader partition. 

Much better to do as ubfan1 suggests and make your install drive as sda. And make sure in BIOS it is seen as first. You may have to change SATA ports and make current sdb as SATA port 0.

---

