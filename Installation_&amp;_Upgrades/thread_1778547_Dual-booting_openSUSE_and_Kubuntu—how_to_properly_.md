---
title: "Dual-booting openSUSE and Kubuntu—how to properly set up bootloader?"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by szal on 2011-06-09
Hi folks,

After finding no answer on IRC I’ll try to find one here. :) In addition to my pre-existing installation of openSUSE 11.4 I installed Kubuntu 11.04 to my machine. Surprisingly enough the SUSE Grub was not overwritten and I can still boot SUSE fine. I cannot, however, get Kubuntu to boot; tried to set up a chainloader entry in the SUSE Grub, but that doesn’t seem to find valid boot files and errors out stating “Invalid or corrupt executable format”.

As far as I can see, both openSUSE and Kubuntu see my hard drives in the following order:

· sda: 500 GB Samsung on SATA (no OS installed)
· sdb: 120 GB WD on IDE Master (Kubuntu installed to 1st partition (sdb1)
· sdc: 160 GB Samsung on IDE Slave (openSUSE installed to 1st partition (sdc1)

During installation Kubuntu (alternate CD) installed Grub2 to (hd0,0), which should be what is called sda above.

Any help on this matter will be greatly appreciated. Please feel free to ask for any information I can provide to further my case.

Kind regards

szal

---

### Post by ajgreeny on 2011-06-09
Click on the Boot-info-script link in my signature and follow the instructions on that site to download and run the script, then copy back the RESULTS.txt file in code tags (the # in the toolbar of the reply entry box).

That will give us lots on info about the bootloader setup of your system and allow us to suggest answers to your problem; probably simply reinstalling the kubuntu grub2 from a live kubuntu CD will do it, but let's go one step at a time.

---

### Post by szal on 2011-06-09
Thanks for posting, ajgreeny. I ran the script; the result is attached to this posting.

If that helps, I am able to boot Kubuntu using Super GRUB2 Disk, but that is not a preferable state of affairs for long-term use, of course. I’d rather chainload one OS from the other’s bootloader, don’t really matter which from which.

---

### Post by ajgreeny on 2011-06-09
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on boot 
    drive #2 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 9a1c9743-5e52-48c7-b242-4b77ecd5bd5b root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.4 
                       "Celadon" - Kernel ().
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdb2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    31,455,269    31,455,207  83 Linux
/dev/sda2          31,455,270   230,179,319   198,724,050  83 Linux
/dev/sda3         230,179,320   234,372,284     4,192,965  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    31,455,231    31,453,184  83 Linux
/dev/sdb2          31,455,232   167,829,503   136,374,272  83 Linux
/dev/sdb3         167,831,055   310,488,254   142,657,200  83 Linux
/dev/sdb4         310,488,255   312,576,704     2,088,450  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    25,173,854    25,173,792  83 Linux
/dev/sdc2          25,173,855   121,130,099    95,956,245  83 Linux
/dev/sdc3         121,130,100   959,996,204   838,866,105  83 Linux
/dev/sdc4         959,996,205   976,768,064    16,771,860  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9a1c9743-5e52-48c7-b242-4b77ecd5bd5b   ext3       1stroot
/dev/sda2        d71a6160-3330-4b0e-a0d1-db1d0c4b55e1   ext3       1sthome
/dev/sda3        f787a08d-2b82-4ae3-8e8a-d9de76f99700   swap       
/dev/sdb1        e464ab8f-4b89-4886-83d2-907632024686   ext3       2ndroot
/dev/sdb2        66d00a59-1090-4375-a78b-9bd74adb4840   ext3       2ndhome
/dev/sdb3        65ce5b34-5e31-461c-b903-36dc69ed0fe3   ext3       storage3
/dev/sdb4        23365b0a-9af1-4e00-abea-d05fb915f1d0   swap       
/dev/sdc1        25b79cbf-8c0d-43b3-a606-7c513171206c   ext3       3rdroot
/dev/sdc2        eaf33b79-a0fc-4257-9bb7-00072b65b3da   ext3       3rdhome
/dev/sdc3        900ca9a5-ae71-466d-bfdf-59f1e6c4aca5   ext3       storage4
/dev/sdc4        d6e8afdd-4e38-4d6d-beae-71a176fd25c1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda2        /home                    ext3       (rw,commit=0)
/dev/sdb1        /media/2ndroot           ext3       (rw,commit=0)
/dev/sdb2        /media/2ndhome           ext3       (rw,commit=0)
/dev/sdb3        /media/storage3          ext3       (rw,commit=0)
/dev/sdc1        /media/3rdroot           ext3       (rw,commit=0)
/dev/sdc2        /media/3rdhome           ext3       (rw,commit=0)
/dev/sdc3        /media/storage4          ext3       (rw,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 9a1c9743-5e52-48c7-b242-4b77ecd5bd5b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 9a1c9743-5e52-48c7-b242-4b77ecd5bd5b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,71,115; then
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a1c9743-5e52-48c7-b242-4b77ecd5bd5b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9a1c9743-5e52-48c7-b242-4b77ecd5bd5b ro edd=on nomodeset  verbose
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a1c9743-5e52-48c7-b242-4b77ecd5bd5b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9a1c9743-5e52-48c7-b242-4b77ecd5bd5b ro single edd=on nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a1c9743-5e52-48c7-b242-4b77ecd5bd5b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 9a1c9743-5e52-48c7-b242-4b77ecd5bd5b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Desktop -- openSUSE 11.4 - 2.6.39.1-31 (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root e464ab8f-4b89-4886-83d2-907632024686
    linux /boot/vmlinuz-2.6.39.1-31-desktop root=/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part1 splash=silent nomodeset resume=/dev/disk/by-id/ata-SAMSUNG_HD501LJ_S0MUJDWQ141415-part4 splash=off quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.39.1-31-desktop
}
menuentry "Failsafe -- openSUSE 11.4 - 2.6.39.1-31 (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root e464ab8f-4b89-4886-83d2-907632024686
    linux /boot/vmlinuz-2.6.39.1-31-desktop root=/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part1 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.39.1-31-desktop
}
menuentry "Desktop -- openSUSE 11.4 - 2.6.39-30 (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root e464ab8f-4b89-4886-83d2-907632024686
    linux /boot/vmlinuz-2.6.39-30-desktop root=/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part1 splash=silent nomodeset resume=/dev/disk/by-id/ata-SAMSUNG_HD501LJ_S0MUJDWQ141415-part4 splash=off quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.39-30-desktop
}
menuentry "Failsafe -- openSUSE 11.4 - 2.6.39-30 (desktop) (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root e464ab8f-4b89-4886-83d2-907632024686
    linux /boot/vmlinuz-2.6.39-30-desktop root=/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part1 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.39-30-desktop
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=9a1c9743-5e52-48c7-b242-4b77ecd5bd5b /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=d71a6160-3330-4b0e-a0d1-db1d0c4b55e1 /home           ext3    defaults        0       2
# /media/2ndhome was on /dev/sdc2 during installation
UUID=66d00a59-1090-4375-a78b-9bd74adb4840 /media/2ndhome  ext3    defaults        0       2
# /media/2ndroot was on /dev/sdc1 during installation
UUID=e464ab8f-4b89-4886-83d2-907632024686 /media/2ndroot  ext3    defaults        0       2
# /media/3rdhome was on /dev/sda2 during installation
UUID=eaf33b79-a0fc-4257-9bb7-00072b65b3da /media/3rdhome  ext3    defaults        0       2
# /media/3rdroot was on /dev/sda1 during installation
UUID=25b79cbf-8c0d-43b3-a606-7c513171206c /media/3rdroot  ext3    defaults        0       2
# /media/storage3 was on /dev/sdc3 during installation
UUID=65ce5b34-5e31-461c-b903-36dc69ed0fe3 /media/storage3 ext3    defaults        0       2
# /media/storage4 was on /dev/sda3 during installation
UUID=900ca9a5-ae71-466d-bfdf-59f1e6c4aca5 /media/storage4 ext3    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=d6e8afdd-4e38-4d6d-beae-71a176fd25c1 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=f787a08d-2b82-4ae3-8e8a-d9de76f99700 none            swap    sw              0       0
# swap was on /dev/sdc4 during installation
UUID=23365b0a-9af1-4e00-abea-d05fb915f1d0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.336127758 = 4.655881728    boot/grub/core.img                             1
   4.369227886 = 4.691422720    boot/grub/grub.cfg                             2
   3.956851482 = 4.248636928    boot/initrd.img-2.6.38-8-generic               7
   3.910636425 = 4.199013888    boot/vmlinuz-2.6.38-8-generic                  3
   3.956851482 = 4.248636928    initrd.img                                     7
   3.910636425 = 4.199013888    vmlinuz                                        3

=========================== sdb1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Modified by YaST2. Last modification on Wed Jun  8 16:08:32 CEST 2011
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
gfxmenu (hd1,0)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.4 - 2.6.39.1-31
    root (hd1,0)
    kernel /boot/vmlinuz-2.6.39.1-31-desktop root=/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part1 splash=silent nomodeset resume=/dev/disk/by-id/ata-SAMSUNG_HD501LJ_S0MUJDWQ141415-part4 splash=off quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.39.1-31-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.4 - 2.6.39.1-31
    root (hd1,0)
    kernel /boot/vmlinuz-2.6.39.1-31-desktop root=/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part1 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.39.1-31-desktop


###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.4 - 2.6.39-30
    root (hd1,0)
    kernel /boot/vmlinuz-2.6.39-30-desktop root=/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part1 splash=silent nomodeset resume=/dev/disk/by-id/ata-SAMSUNG_HD501LJ_S0MUJDWQ141415-part4 splash=off quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.39-30-desktop


###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.4 - 2.6.39-30 (desktop)
    root (hd1,0)
    kernel /boot/vmlinuz-2.6.39-30-desktop root=/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part1 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.39-30-desktop

###Don't change this comment - YaST2 identifier: Original name: chainload###
title Kubuntu 11.04 Natty Narwhal (chainloader)
    root (hd0,0)
    chainloader (hd2,0)+1
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part1 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/ata-WDC_WD1200JB-75CRA0_WD-WMA8C2926735-part1 /media/1stroot       ext3       defaults              1 2
/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part2 /home                ext3       acl,user_xattr        1 2
/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part3 /media/storage3      ext3       defaults              1 2
/dev/disk/by-id/ata-SAMSUNG_HD501LJ_S0MUJDWQ141415-part4 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD1200JB-75CRA0_WD-WMA8C2926735-part3 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-SAMSUNG_SP1604N_S02DJ10X803665-part4 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD1200JB-75CRA0_WD-WMA8C2926735-part2 /media/1sthome       ext3       defaults              1 2
/dev/disk/by-id/ata-SAMSUNG_HD501LJ_S0MUJDWQ141415-part2 /media/3rdhome       ext3       defaults              1 2
/dev/disk/by-id/ata-SAMSUNG_HD501LJ_S0MUJDWQ141415-part1 /media/3rdroot       ext3       defaults              1 2
/dev/disk/by-id/ata-SAMSUNG_HD501LJ_S0MUJDWQ141415-part3 /media/storage4      ext3       defaults              1 2
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  10.614215851 = 11.396927488   boot/grub/menu.lst                             1
  10.624652863 = 11.408134144   boot/grub/stage2                               2
  10.854949951 = 11.655413760   boot/initrd                                   24
  10.854949951 = 11.655413760   boot/initrd-2.6.39.1-31-desktop               24
  10.782444000 = 11.577561088   boot/initrd-2.6.39-30-desktop                 22
  10.800426483 = 11.596869632   boot/vmlinuz                                  30
  10.800426483 = 11.596869632   boot/vmlinuz-2.6.39.1-31-desktop              30
  10.761524200 = 11.555098624   boot/vmlinuz-2.6.39-30-desktop                 8

========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```
Grub2 seems to be on sdc, according to the first part of the Boot-info-script output, but in another part of the output shows that grub.cfg is on sda, which it isn't, so you may be able to solve all your problems by setting another disk as the first boot device in your machine's BIOS, though which one may be trial and error, as the disk naming has gone a bit off course in some way, perhaps as a result of using the alternate install CD, which talks in terms of hd0, hd1, etc, instead of sda, sdb etc.

I also see that grub2 is looking on sdb (disk#2) for grub menu.lst file, which it should not be using.  Grub2 uses a grub.cfg file in the place of menu.lst, so there is something wrong there, and I am not sure what to suggest to put that right; maybe a reinstalltion of grub2 from the live CD would help, but you don't have one, and I am not sure if you can do it from a running installed kubuntu, nor do I know anything in detail about supergrub to offer any help there.

Try each disk in BIOS until you get to kubuntu's grub2, which is already showing Suse in the grub.cfg file, to see if you can get both OSs to boot.  If thatis no help, come back again and let's see where we go from there.

---

### Post by szal on 2011-06-09
Nice, just changing the HDD order in the BIOS did the trick. :) I can now boot both SUSE and Kubuntu from Kubuntu’s Grub2.

Thanks a bunch.

---

### Post by ajgreeny on 2011-06-09
Great!  Just for my sake, which disk needs to be first boot priority for the correct working of grub?

Can you mark as SOLVED from the thread menu at the top of your original post.

---

### Post by szal on 2011-06-09
> **ajgreeny said:**
> Great!  Just for my sake, which disk needs to be first boot priority for the correct working of grub?
It was sdc (the large SATA disk), to which the installer had installed the Grub2.

> **ajgreeny said:**
> Can you mark as SOLVED from the thread menu at the top of your original post.
Done.

---

