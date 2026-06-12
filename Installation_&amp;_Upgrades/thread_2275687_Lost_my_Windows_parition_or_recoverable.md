---
title: "Lost my Windows parition? or recoverable?"
date: 2015-04-27
forum: Installation &amp; Upgrades
---

### Post by mike_p2 on 2015-04-27
So after using Linux Mint via dual boot on my Acer laptop (Win 7) over the past year and loving it, I got the bright idea to install ubuntu (64 bit) to my Acer desktop. Everything went fairly smooth.....except.....I have a feeling I made a really bad mistake and I'm hoping someone can help me walk through what I need to to do to either: 

a) recover the data on my windows partition (at a minimum)

b) access my windows OEM recovery partition (for a refresh/re-install)

c) find a way to get this ubuntu to dual boot (which I'm not hopeful for). 

From some of my research thus far, I'm left with the bad feeling that I won't be able to accomplish option C, and of that's the case, I'm fine with that. However, at a bare minimum, I really REALLY need to recover my data on my windows partition if that the case.

The good news is that Ubuntu boots right up and works fine. However, no GRUB menu as I have on my lap. Instead, it just jumps right into ubuntu. More bad news is that I can't see any of my previous paritions (Acer OEM recovery partition, or my Windows 8.1 partition). 

Can anyone walk me through where I should start? 

Thanks.

---

### Post by yancek on 2015-04-27
The more times you boot the machine and use it, the less  likely you are to recover data.  If you have your Ubuntu (or any other Linux) Live CD or installation media, boot it instead and run the command below to check to see if you have any windows partitions:

```
sudo fdisk -l
``` 

If you see any ntfs partitions under the Filesystem column, you should be able to access the partitions.
Do you remember which option you selected during the install?  Did you install Ubuntu to the same partition as you previously had Mint on?

---

### Post by sisco311 on 2015-04-27
Please post your `boot info':  [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by mike_p2 on 2015-04-27
> **yancek said:**
> 
Do you remember which option you selected during the install?  Did you install Ubuntu to the same partition as you previously had Mint on?

I actually never had Mint installed on this machine. That was on my old Acer laptop.

Before I installed ubuntu on this desktop, I created a separate partition from Win 8.1 for my ubuntu install. I believe I had three partitions when everything was said and done. A recovery partition, my Windows 8.1 partition, and this new ubuntu partition I created before I started the infamous ubuntu install.

---

### Post by mike_p2 on 2015-04-27
> **sisco311 said:**
> Please post your `boot info':  [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

```
Boot-Info

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.2 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 4079104 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624 1,945,397,247 1,944,346,624 Data partition (Linux)
/dev/sda3   1,945,397,248 1,953,523,711     8,126,464 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8017 MB, 8017412096 bytes
186 heads, 43 sectors/track, 1957 cylinders, total 15659008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,659,007    15,658,976   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1B16-93F4                              vfat       
/dev/sda2        fb487f61-009a-4721-838d-19237a3739e3   ext4       
/dev/sda3        5a0b2a1a-7bdd-4de0-8079-a7b4156b9b20   swap       
/dev/sdb1        B61F-97B5                              vfat       Lexar

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr 28 00:09 ata-MATSHITADVD-RAM_UJ8E2Q_H088_031439 -> ../../sr0
lrwxrwxrwx 1 root root  9 Apr 28 00:26 ata-WDC_WD10JPVX-22JC3T0_WD-WXD1A34K4050 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 28 00:09 ata-WDC_WD10JPVX-22JC3T0_WD-WXD1A34K4050-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 28 00:09 ata-WDC_WD10JPVX-22JC3T0_WD-WXD1A34K4050-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 28 00:09 ata-WDC_WD10JPVX-22JC3T0_WD-WXD1A34K4050-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Apr 28 00:26 usb-Lexar_USB_Flash_Drive_AAZHP37D2M3JG5WW-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr 28 00:09 usb-Lexar_USB_Flash_Drive_AAZHP37D2M3JG5WW-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Apr 28 00:26 wwn-0x50014ee659f76845 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 28 00:09 wwn-0x50014ee659f76845-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 28 00:09 wwn-0x50014ee659f76845-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 28 00:09 wwn-0x50014ee659f76845-part3 -> ../../sda3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/ubuntu/fb487f61-009a-4721-838d-19237a3739e3 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb1         /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
   search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2  --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   fb487f61-009a-4721-838d-19237a3739e3
else
  search --no-floppy --fs-uuid --set=root fb487f61-009a-4721-838d-19237a3739e3
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
menuentry  'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os  $menuentry_id_option  'gnulinux-simple-fb487f61-009a-4721-838d-19237a3739e3' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
       search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2  --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   fb487f61-009a-4721-838d-19237a3739e3
    else
      search --no-floppy --fs-uuid --set=root fb487f61-009a-4721-838d-19237a3739e3
    fi
     linux    /boot/vmlinuz-3.13.0-49-generic.efi.signed  root=UUID=fb487f61-009a-4721-838d-19237a3739e3 ro  quiet splash  $vt_handoff
    initrd    /boot/initrd.img-3.13.0-49-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-fb487f61-009a-4721-838d-19237a3739e3' {
     menuentry 'Ubuntu, with Linux 3.13.0-49-generic' --class ubuntu  --class gnu-linux --class gnu --class os $menuentry_id_option  'gnulinux-3.13.0-49-generic-advanced-fb487f61-009a-4721-838d-19237a3739e3'  {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2  --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   fb487f61-009a-4721-838d-19237a3739e3
        else
          search --no-floppy --fs-uuid --set=root fb487f61-009a-4721-838d-19237a3739e3
        fi
        echo    'Loading Linux 3.13.0-49-generic ...'
         linux    /boot/vmlinuz-3.13.0-49-generic.efi.signed  root=UUID=fb487f61-009a-4721-838d-19237a3739e3 ro  quiet splash  $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-49-generic
    }
     menuentry 'Ubuntu, with Linux 3.13.0-49-generic (recovery mode)'  --class ubuntu --class gnu-linux --class gnu --class os  $menuentry_id_option  'gnulinux-3.13.0-49-generic-recovery-fb487f61-009a-4721-838d-19237a3739e3'  {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2  --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   fb487f61-009a-4721-838d-19237a3739e3
        else
          search --no-floppy --fs-uuid --set=root fb487f61-009a-4721-838d-19237a3739e3
        fi
        echo    'Loading Linux 3.13.0-49-generic ...'
         linux    /boot/vmlinuz-3.13.0-49-generic.efi.signed  root=UUID=fb487f61-009a-4721-838d-19237a3739e3 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-49-generic
    }
     menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu  --class gnu-linux --class gnu --class os $menuentry_id_option  'gnulinux-3.13.0-32-generic-advanced-fb487f61-009a-4721-838d-19237a3739e3'  {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2  --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   fb487f61-009a-4721-838d-19237a3739e3
        else
          search --no-floppy --fs-uuid --set=root fb487f61-009a-4721-838d-19237a3739e3
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=fb487f61-009a-4721-838d-19237a3739e3 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
     menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)'  --class ubuntu --class gnu-linux --class gnu --class os  $menuentry_id_option  'gnulinux-3.13.0-32-generic-recovery-fb487f61-009a-4721-838d-19237a3739e3'  {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2  --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   fb487f61-009a-4721-838d-19237a3739e3
        else
          search --no-floppy --fs-uuid --set=root fb487f61-009a-4721-838d-19237a3739e3
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=fb487f61-009a-4721-838d-19237a3739e3 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=fb487f61-009a-4721-838d-19237a3739e3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=1B16-93F4  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=5a0b2a1a-7bdd-4de0-8079-a7b4156b9b20 none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
     linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed  boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/4929/mounts) leaked on lvs invocation. Parent PID 10925: bash
File descriptor 63 (pipe:[47862]) leaked on lvs invocation. Parent PID 10925: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-info 2015-04-28__00h26 ===================
boot-info version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
boot-info is executed in live-session (Ubuntu 14.04.1 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
ls: cannot access /home/usr/.config: No such file or directory

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2:Ubuntu 14.04.2 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="1B16-93F4" TYPE="vfat"
/dev/sda2: UUID="fb487f61-009a-4721-838d-19237a3739e3" TYPE="ext4"
/dev/sda3: UUID="5a0b2a1a-7bdd-4de0-8079-a7b4156b9b20" TYPE="swap"
/dev/sdb1: LABEL="Lexar" UUID="B61F-97B5" TYPE="vfat"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== /media/ubuntu/fb487f61-009a-4721-838d-19237a3739e3/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Jul 22  2014 grub.d
total 76
-rwxr-xr-x 1 root root  9424 May 15  2014 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 May 15  2014 README




=================== /media/ubuntu/fb487f61-009a-4721-838d-19237a3739e3/etc/default/grub :

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



/boot/efi detected in the fstab of sda2: UUID=1B16-93F4   (sda1)

=================== efibootmgr -v
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0000,0002,0001
Boot0000* ubuntu    HD(1,800,100000,e2a63f4e-6ee4-42f8-8230-fa6ac77cb416)File(EFIubuntushimx64.efi)
Boot0001   Windows Boot Manager     Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0002* UEFI: Lexar USB Flash Drive 1100    ACPI(a0341d0,0)PCI(14,0)USB(1,0)USB(1,0)HD(1,20,eeefe0,0005a38e)..BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1     : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,     not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,     update-grub,    64,    with-boot,    is-os,    not--efi--part,     fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,     grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,     standard,    farbios,     /media/ubuntu/fb487f61-009a-4721-838d-19237a3739e3.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD10JPVX-22J (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      1049kB  538MB   537MB   fat32                 boot
2      538MB   996GB   996GB   ext4
3      996GB   1000GB  4161MB  linux-swap(v1)


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdb: 8017MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  8017MB  8017MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA WDC WD10JPVX-22J;
1:1049kB:538MB:537MB:fat32::boot;
2:538MB:996GB:996GB:ext4::;
3:996GB:1000GB:4161MB:linux-swap(v1)::;

BYT;
/dev/sdb:8017MB:scsi:512:512:msdos:Lexar USB Flash Drive;
1:16.4kB:8017MB:8017MB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL MODEL      UUID
sda   disk          931.5G       WDC WD10JP
sda1  part vfat       512M                  1B16-93F4
sda2  part ext4     927.1G                  fb487f61-009a-4721-838d-19237a3739e3
sda3  part swap       3.9G                  5a0b2a1a-7bdd-4de0-8079-a7b4156b9b20
sdb   disk            7.5G       USB Flash
sdb1  part vfat       7.5G Lexar            B61F-97B5
sr0   rom            1024M       DVD-RAM UJ
loop0 loop squashfs 938.7M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /media/ubuntu/fb487f61-009a-4721-838d-19237a3739e3
sda3     1  0  0         [SWAP]
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1  on /cdrom type vfat  (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/ubuntu/fb487f61-009a-4721-838d-19237a3739e3 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)


=================== ls:
/sys/block/sda  (filtered):  alignment_offset bdi capability dev device  discard_alignment events events_async events_poll_msecs ext_range  holders inflight power queue range removable ro sda1 sda2 sda3 size  slaves stat subsystem trace uevent
/sys/block/sdb (filtered):   alignment_offset bdi capability dev device discard_alignment events  events_async events_poll_msecs ext_range holders inflight power queue  range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0  (filtered):  alignment_offset bdi capability dev device  discard_alignment events events_async events_poll_msecs ext_range  holders inflight power queue range removable ro size slaves stat  subsystem trace uevent
/dev (filtered):  autofs block bsg  btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk  dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet input  kmsg kvm log mapper mcelog mem net network_latency network_throughput  null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3  sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid  uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 fe 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 f4 93 16 1b 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.9G  111M  1.8G   6% /
udev           devtmpfs   1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs      383M  1.2M  382M   1% /run
/dev/sdb1      vfat       7.5G  5.6G  2.0G  75% /cdrom
/dev/loop0     squashfs   939M  939M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.9G   52K  1.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.9G   76K  1.9G   1% /run/shm
none           tmpfs      100M   84K  100M   1% /run/user
/dev/sda2      ext4       913G  5.1G  862G   1% /media/ubuntu/fb487f61-009a-4721-838d-19237a3739e3
/dev/sda1      vfat       511M  3.4M  508M   1% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbb63fba3

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8017 MB, 8017412096 bytes
186 heads, 43 sectors/track, 1957 cylinders, total 15659008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a38e

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15659007     7829488    c  W95 FAT32 (LBA)




=================== Suggested repair
The  default repair of the Boot-Repair utility would reinstall the  grub-efi-amd64-signed of sda2, using the following options:         sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file rename-ms-efi


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by yancek on 2015-04-27
I don't know which option you selected during the install but, there isn't any sign of a windows partition in the bootinfo output you posted nor is there an entry for it in the Grub boot menu.  Not sure if you can recover but you could try using testdisk.  See the link below and be sure to read the step by step instructions before beginning.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2015-04-27
Was Windows on Acer installed in UEFI boot mode or BIOS boot mode. You have Ubuntu installed in UEFI boot mode.
Reason is that Windows in BIOS mode only boots from MBR(msdos) drives, but UEFI uses gpt partitioned drives. And first question from testdisk is whether drive is MBR or gpt(GUID).

You cannot now recover working Windows nor recovery partition not some of your data. Linux install is small but writes full files all over drive, not like Windows NTFS where everything is packed into beginning of drive and then you have to defragment as parts of files then get written later on drive.

If deeper search in testdisk shows files be sure to copy to another drive immediately. If not then you need photorec which also is part of testdisk. Both are in repository, so you can easily install into live Ubuntu system installer.

You may be able to get new set of DVDs from system vendor for a nominal charge that would be the recovery partition. Generally the first thing you do with a new system is make backup of that partition. And have regular backups of your data.

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
      
 [URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"]http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step
[/URL]
 [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

[URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"]
[/URL]

---

