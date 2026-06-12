---
title: "Windows update &amp; grub problems"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by vra5107 on 2011-10-30
HI

             I did a windows update and my boot record was overwritten. Would somebody be able to help me with fixing this. 

Attached below is output generated but he script. I tried to make sense of it, but didn't get further. 

I know sda5 is where my Ubuntu is installed but I get the following error.

grub
> root (hd0,4)

Error 21: Selected disk does not exist


Thanks
Venkat

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files:        /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......".A....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 3227114 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   409,609,304   409,607,257   7 NTFS / exFAT / HPFS
/dev/sda2         409,609,366   976,768,064   567,158,699   5 Extended
/dev/sda5         409,609,368   962,341,694   552,732,327  83 Linux
/dev/sda6         962,341,758   976,768,064    14,426,307  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2073 MB, 2073034752 bytes
64 heads, 62 sectors/track, 1020 cylinders, total 4048896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     4,047,359     4,047,298   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D6588EF7588ED5A1                       ntfs       
/dev/sda5        f7c202eb-ed41-47f6-97e3-fc7304ea18d9   ext4       
/dev/sda6        dc5af5e9-ec90-43fe-82bd-40e02eaa591e   swap       
/dev/sdb1        16EE-4E38                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /mnt                     ext4       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: =====================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-18-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=D6588EF7588ED5A1 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

--------------------------------------------------------------------------------

======================== sda1/ubuntu/winboot/menu.lst: =========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ubuntu/disks/boot/grub/menu.lst                1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-11-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-15-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-16-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-17-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-18-generic  1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-11-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-15-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-16-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-17-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-18-generic    1

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f7c202eb-ed41-47f6-97e3-fc7304ea18d9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7c202eb-ed41-47f6-97e3-fc7304ea18d9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root D6588EF7588ED5A1
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

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 345.560859680 = 371.043147776  boot/grub/core.img                             1
 201.300045013 = 216.144277504  boot/grub/grub.cfg                             1
 195.855335236 = 210.298064896  boot/initrd.img-2.6.31-14-generic              1
 196.132686615 = 210.595868672  boot/initrd.img-2.6.31-20-generic              2
 220.472225189 = 236.730249216  boot/initrd.img-2.6.31-21-generic              1
 236.387279510 = 253.818908672  boot/initrd.img-2.6.32-25-generic              2
 323.891193390 = 347.775520768  boot/initrd.img-2.6.38-11-generic              1
 345.614807129 = 371.101073408  boot/initrd.img-3.0.0-12-generic               1
 195.835239410 = 210.276487168  boot/vmlinuz-2.6.31-14-generic                 1
 196.021770477 = 210.476773376  boot/vmlinuz-2.6.31-20-generic                 1
 197.102310181 = 211.636994048  boot/vmlinuz-2.6.31-21-generic                 1
 196.780315399 = 211.291254784  boot/vmlinuz-2.6.32-25-generic                 1
 344.184463501 = 369.565253632  boot/vmlinuz-2.6.38-11-generic                 1
 325.184154510 = 349.163827200  boot/vmlinuz-3.0.0-12-generic                  2
 323.891193390 = 347.775520768  initrd.img.old                                 1
 325.184154510 = 349.163827200  vmlinuz                                        2
 344.184463501 = 369.565253632  vmlinuz.old                                    1

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
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by oldos2er on 2011-10-30
Post moved to its own thread. Please don't post new problems/questions in old threads.

---

### Post by Rubi1200 on 2011-10-31
Hi,
do you know you have a Wubi and a regular Ubuntu install?

Currently, Windows is installed in the MBR.

To dual-boot again you need to reinstall GRUB to the MBR.

Use this guide:
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

In your situation:


```
sudo mount /dev/sda5 /mnt

sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

After this completes reboot and back in Ubuntu run this code to add Windows to GRUB:
```
sudo update-grub

```

---

### Post by vra5107 on 2011-10-31
Thanks for the reply. I ended up backing up my data and reinstalling Ubuntu. Well, this might happen in the future, so your help is invaluable. 

Thanks
Venkat

---

### Post by Rubi1200 on 2011-11-01
No problem, I am glad you found a solution.

Please mark this Solved using the Thread Tools near the top of the page.

---

