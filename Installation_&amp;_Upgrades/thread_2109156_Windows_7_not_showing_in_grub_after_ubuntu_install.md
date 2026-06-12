---
title: "Windows 7 not showing in grub after ubuntu install"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by tanab on 2013-01-26
After installing ubuntu 12 windows 7 is not showing in my grub anymore can you help?
  i have done a grub-update etc.
  this is my boot script info


```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Lilo is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/lilo.conf /boot/map

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 115.0 GB, 115033153536 bytes
255 heads, 63 sectors/track, 13985 cylinders, total 224674128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   224,671,743   224,669,696   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048   195,311,615   195,309,568 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   104,857,599   104,855,552   7 NTFS / exFAT / HPFS
/dev/sdc2         104,859,647 1,948,286,383 1,843,426,737   f W95 Extended (LBA)
/dev/sdc5         104,859,648 1,948,286,383 1,843,426,736   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   976,751,999   976,751,937   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8058C68B58C67F80                       ntfs       OCZ SSD
/dev/sdb1        11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5   ext4       
/dev/sdc1        D088697688695BCA                       ntfs       Firefox Downloads
/dev/sdc5        F40A8D220A8CE2CA                       ntfs       Overige
/dev/sdd1        00CC96FACC96E964                       ntfs       WD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/toby/OCZ SSD      fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/toby/Firefox Downloads fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc5        /media/toby/Overige      fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1        /media/toby/WD           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
insmod part_gpt
insmod ext2
set root='hd1,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1 --hint-efi=hd1,gpt1 --hint-baremetal=ahci1,gpt1  11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
else
  search --no-floppy --fs-uuid --set=root 11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1 --hint-efi=hd1,gpt1 --hint-baremetal=ahci1,gpt1  11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
    else
      search --no-floppy --fs-uuid --set=root 11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
    fi
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1 --hint-efi=hd1,gpt1 --hint-baremetal=ahci1,gpt1  11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
        else
          search --no-floppy --fs-uuid --set=root 11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5' {
    recordfail
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1 --hint-efi=hd1,gpt1 --hint-baremetal=ahci1,gpt1  11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
        else
          search --no-floppy --fs-uuid --set=root 11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1 --hint-efi=hd1,gpt1 --hint-baremetal=ahci1,gpt1  11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
    else
      search --no-floppy --fs-uuid --set=root 11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1 --hint-efi=hd1,gpt1 --hint-baremetal=ahci1,gpt1  11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
    else
      search --no-floppy --fs-uuid --set=root 11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
menuentry "Windows 8" {
    set root='(hd0,gpt1)'
    chainloader /EFI/microsoft/BOOT/bootmgfw.efi
}
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5 /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

============================= sdb1/etc/lilo.conf: ==============================

--------------------------------------------------------------------------------
# /etc/lilo.conf  -   systemwide LILO configuration (LILO 23)
# details see in manpages: lilo(8) and lilo.conf(5)

# +-------------------------------------------------------------+
# |                        !! Reminder !!                       |
# |                                                             |
# | Don't forget to run 'lilo' after you make changes to this   |
# | conffile or you have installed a new kernel.                |
# +-------------------------------------------------------------+


# #################### LILO global section ######################

# With all newer systems (until year 2004) you can use the RAM
# above 15 MB. This option allows the use of this range of RAM.
#large-memory

# With all newer systems you can boot from any partition on disks 
# with more than 1024 cylinders. This option allows the use of 
# partitions above 1024 cylinders.
lba32

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
# With newer kernel you should use the ID of the boot device, which
# can be found here: /dev/disks/by-id/ata*.
#boot = /dev/sdb
boot = /dev/disk/by-id/ata-Hitachi_HDS722020ALA330_JK1171YAGVD55N

# This option may be needed for some software RAID installs.
#raid-extra-boot = mbr-only

# Enable map compaction.  This tries to merge read requests for 
# adjacent sectors into a single read request. This drastically 
# reduces load time and keeps the map smaller.  Using 'compact' 
# is especially recommended when booting from a floppy disk.  
# It is disabled here by default because it doesn't always work.
#compact

# Set the verbose level for bootloader installation. Value range:
# 0 to 5. Default value is 0.
#verbose = 1

# Specifies the location of the map file. Lilo creates the (sector) 
# map file of direct sector addresses which are independent of any
# filesystem.
map = /boot/map

# ---------------------------------------------------------------

# Specifies the menu interface. You have the choice between:
#   text: simple text menu with black background and white text
#   menu: configurable text menu with background and text colors.
#   bmp:  graphical menu with 640x480 bitmap background.
install = menu

# A) Customized boot message for choice 'text'.
# For the simple text menu you can set an extra message in the 
# created file. Its text will be displayed before boot prompt.
#message = /boot/message.txt

# B) Configuration of the scheme for choice 'menu'.
# Use following coding: <text>:<highlight>:<border>:<title>
# The first character of each part sets the text frontcolor, 
# the second character of earch part sets the text backcolor,
# an upper-case character sets bold face text (frontcolor).
# i.g. 'menu-scheme=wm:rw:wm:Wm'. Possible colors: 
# k=black, b=blue, g=green, c=cyan, r=red, m=magenta, y=yellow, w=white.
menu-scheme = Wb:Yr:Wb:Wb
#menu-title = " DESDEMONA Boot-Manager "

# C) Configuration of the image for choice 'bmp'.
# For the graphical menu you need a bitmap file, which needs a special
# menu configuration in the file header (see: lilo -E). Ideally you 
# use one of the delivered images of the lilo package.
#   with 16 colors:    onlyblue, tuxlogo, inside
#   with 256 colors:   coffee
#   for Debian:        debianlilo, debian, debian-de
#bitmap = /boot/tuxlogo.bmp

# ---------------------------------------------------------------

# Specifies the number of deciseconds (0.1 seconds) how long LILO 
# should wait before booting the first image.  LILO doesn't wait if
# 'delay' is omitted or set to zero. You do not see the defined menu.
#delay = 20

# Prompt to start one certain kernel from the displayed menu.
# It is very recommeded to also set 'timeout'. Without timeout boot 
# will not take place unless you hit return. Timeout is the number
# of deciseconds (0.1 seconds) after there the default image will 
# be started. With 'single-key' alias numbers for each menu line can
# be used.
prompt
timeout = 100
#single-key

# ---------------------------------------------------------------

# Specifying the VGA text mode that should be selected when booting.
# The following values are recognized (case is ignored):
#   vga=normal    80x25 text mode (default)
#   vga=extended  80x50 text mode (abbreviated to 'ext')
#   vga=ask       stop and ask for user input: choice of text mode
#   vga=<mode>    use the corresponding text mode number. A list of  
#                   available modes can be obtained by booting with  
#                   vga=ask'  and then pressing [Enter].
# Another way is the use of frame buffer mode. Then the kernel 
# will switch from the normal vga text mode (80x25) to the frame
# buffer mode (if frame buffer support is in the kernel):
#   vga=0x314      800x600 @ 16 bit
#   vga=0x317     1024x768 @ 16 bit
#   vga=0x318     1024x768 @ 24 bit
#vga = ask
vga = normal
#vga = 0x317

# ---------------------------------------------------------------

# Kernel command line options that apply to all installed images go
# here.  See 'kernel-parameters.txt' in the Linux kernel 'Documentation'
# directory. I.g. for start into 'init 5' write:  append="5"
#append = ""
 
# If you used a serial console to install Debian, this option should be
# enabled by default.
#serial = 0,9600

# Set the image which should be started after delay or timeout.
# If not set, the first defined image will be started.
#default = Linux


# ################### LILO per-image section ####################

# Each image is configured with the linux kernel (=image) and
# usually with the initrd file. Configure all GNU/Linux systems
# on other partitions, too.

image = /boot/vmlinuz-3.5.0-17-generic
    label = "Linux"
    #root = /dev/sdb1
    root = "UUID=11d0c7d7-5e6d-48cc-80b3-709e5b8e80c5"
    read-only
#    restricted
#    alias = 1
#    optional
    initrd = /boot/initrd.img-3.5.0-17-generic

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.5.0-17-generic               1
               =                boot/vmlinuz-3.5.0-17-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by oldfred on 2013-01-26
Grub does not properly install to gpt drives without a small 1MB unformatted bios_grub partition. It can be anywhere on the gpt drive.

       In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on
    
Then grub will correctly install. You can boot live installer and reinstall grub, use Boot-Repair or Supergrub to boot into system and reinstall grub.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

            How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

    
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
    
When you have very large hard drives I suggest smaller root partitions and large data or /home partitions. Some BIOS (or maybe grub) have issues with booting when grub's boot files may be anywhere on a very large / (root) partition. I normally use 25GB for / and have all my data in other data partitions.

---

