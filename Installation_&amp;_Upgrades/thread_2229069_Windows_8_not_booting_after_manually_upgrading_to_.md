---
title: "Windows 8 not booting after manually upgrading to 14.04"
date: 2014-06-11
forum: Installation &amp; Upgrades
---

### Post by EthioJOB on 2014-06-11
[COLOR=#333333][FONT=UbuntuRegular]I installed Ubuntu 14.04 on top of my previous 13.10 Ubuntu installation. I did it manually by formating the mount and home folders without touching the Windows partition. Apparently it didn't detect the Windows OS.

But there is a "Windows boot manager (on /dev/sda2)" entry on the grub menu (a leftover from the previous installation I think) but it doesn't do anything. I can only boot into Ubuntu. 

I also tried sudo apt-get update grub and boot-repair but no changes so far.[/FONT][/COLOR]

---

### Post by Mark Phelps on 2014-06-11
> I installed Ubuntu 14.04 on top of my previous 13.10 Ubuntu installation. 

There have been lots of reports of folks "reinstalling" Ubuntu to their dual-boot machines only to have it completely ERASE their previous Windows install.

To confirm yours still exists, when you boot into Ubuntu, access the Windows partitions and confirm that it is still there.

---

### Post by EthioJOB on 2014-06-11
> **Mark Phelps said:**
> There have been lots of reports of folks "reinstalling" Ubuntu to their dual-boot machines only to have it completely ERASE their previous Windows install.

To confirm yours still exists, when you boot into Ubuntu, access the Windows partitions and confirm that it is still there.


The Windows partition is still there. I chose 'Do something else' during installation to make sure it didn't touch the Windows installation when I suspected it didn't detect the Windows OS.

---

### Post by oldfred on 2014-06-11
Then post link to BootInfo report.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But grub really only boots working Windows. If Windows needs repair you may need a Windows repair cd or flash drive.

---

### Post by EthioJOB on 2014-06-11
```
[COLOR=#000000] Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013][/COLOR]

============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/bcd

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/toshiba/Boot/bootmgfw.efi 
                       /EFI/toshiba/Boot/bootmgr.efi 
                       /EFI/toshiba/Boot/memtest.efi

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     2,099,199     2,097,152 Windows Recovery Environment (Windows)
/dev/sda2       2,099,200     2,631,679       532,480 EFI System partition
/dev/sda3       2,631,680     2,893,823       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       2,893,824   433,889,279   430,995,456 Data partition (Windows/Linux)
/dev/sda5   1,439,543,296 1,465,147,391    25,604,096 Windows Recovery Environment (Windows)
/dev/sda6     433,889,280   629,200,895   195,311,616 Data partition (Linux)
/dev/sda7     858,275,840 1,439,543,295   581,267,456 Data partition (Windows/Linux)
/dev/sda8     629,200,896   838,744,063   209,543,168 Data partition (Linux)
/dev/sda9     838,744,064   858,275,839    19,531,776 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        CA54472B54471999                       ntfs       System
/dev/sda2        5048-B488                              vfat       
/dev/sda3        62784A4B784A1E63                       ntfs       
/dev/sda4        48160FF5160FE334                       ntfs       TI10667700C
/dev/sda5        E6E44177E4414ACF                       ntfs       Recovery
/dev/sda6        396b3d30-30c1-4917-8dcd-3fbd55533a92   ext4       
/dev/sda7        0641E1E17B7C843C                       ntfs       
/dev/sda8        a33bf4de-708e-4791-ac68-a31a98d93d39   ext4       
/dev/sr1                                                iso9660    Mobile Partner

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw)
/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /media/ethiojob/0641E1E17B7C843C fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda8        /home                    ext4       (rw)


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
insmod part_gpt
insmod ext2
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  396b3d30-30c1-4917-8dcd-3fbd55533a92
else
  search --no-floppy --fs-uuid --set=root 396b3d30-30c1-4917-8dcd-3fbd55533a92
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-396b3d30-30c1-4917-8dcd-3fbd55533a92' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  396b3d30-30c1-4917-8dcd-3fbd55533a92
    else
      search --no-floppy --fs-uuid --set=root 396b3d30-30c1-4917-8dcd-3fbd55533a92
    fi
    linux    /boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=396b3d30-30c1-4917-8dcd-3fbd55533a92 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-29-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-396b3d30-30c1-4917-8dcd-3fbd55533a92' {
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-advanced-396b3d30-30c1-4917-8dcd-3fbd55533a92' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  396b3d30-30c1-4917-8dcd-3fbd55533a92
        else
          search --no-floppy --fs-uuid --set=root 396b3d30-30c1-4917-8dcd-3fbd55533a92
        fi
        echo    'Loading Linux 3.13.0-29-generic ...'
        linux    /boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=396b3d30-30c1-4917-8dcd-3fbd55533a92 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-recovery-396b3d30-30c1-4917-8dcd-3fbd55533a92' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  396b3d30-30c1-4917-8dcd-3fbd55533a92
        else
          search --no-floppy --fs-uuid --set=root 396b3d30-30c1-4917-8dcd-3fbd55533a92
        fi
        echo    'Loading Linux 3.13.0-29-generic ...'
        linux    /boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=396b3d30-30c1-4917-8dcd-3fbd55533a92 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-396b3d30-30c1-4917-8dcd-3fbd55533a92' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  396b3d30-30c1-4917-8dcd-3fbd55533a92
        else
          search --no-floppy --fs-uuid --set=root 396b3d30-30c1-4917-8dcd-3fbd55533a92
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=396b3d30-30c1-4917-8dcd-3fbd55533a92 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-396b3d30-30c1-4917-8dcd-3fbd55533a92' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  396b3d30-30c1-4917-8dcd-3fbd55533a92
        else
          search --no-floppy --fs-uuid --set=root 396b3d30-30c1-4917-8dcd-3fbd55533a92
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=396b3d30-30c1-4917-8dcd-3fbd55533a92 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-5048-B488' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  5048-B488
    else
      search --no-floppy --fs-uuid --set=root 5048-B488
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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
UUID=396b3d30-30c1-4917-8dcd-3fbd55533a92 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=5048-B488  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda8 during installation
UUID=a33bf4de-708e-4791-ac68-a31a98d93d39 /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
#UUID=44c4bda9-1609-4d88-9112-07736098249c none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=5048-B488    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-Ckve3Zyq/Tmp_Log: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-06-10__14h22 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in installed-session (Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=396b3d30-30c1-4917-8dcd-3fbd55533a92 ro quiet splash vt.handoff=7

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda6:The OS now in use - Ubuntu 14.04 LTS CurrentSession:linux
/dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi

=================== blkid:
/dev/sda1: LABEL="System" UUID="CA54472B54471999" TYPE="ntfs"
/dev/sda2: UUID="5048-B488" TYPE="vfat"
/dev/sda3: UUID="62784A4B784A1E63" TYPE="ntfs"
/dev/sda4: LABEL="TI10667700C" UUID="48160FF5160FE334" TYPE="ntfs"
/dev/sda5: LABEL="Recovery" UUID="E6E44177E4414ACF" TYPE="ntfs"
/dev/sda6: UUID="396b3d30-30c1-4917-8dcd-3fbd55533a92" TYPE="ext4"
/dev/sda7: UUID="0641E1E17B7C843C" TYPE="ntfs"
/dev/sda8: UUID="a33bf4de-708e-4791-ac68-a31a98d93d39" TYPE="ext4"
/dev/sr1: LABEL="Mobile Partner" TYPE="iso9660"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda4.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== /etc/grub.d/ :
drwxr-xr-x  2 root root      4096 &#4772;&#4949;&#4648; 17 04:26 grub.d
total 76
-rwxr-xr-x 1 root root  9424 &#4772;&#4949;&#4648; 11 13:51 00_header
-rwxr-xr-x 1 root root  6058 &#4772;&#4949;&#4648; 10 18:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 &#4772;&#4949;&#4648; 11 13:51 10_linux
-rwxr-xr-x 1 root root 10412 &#4772;&#4949;&#4648; 11 13:51 20_linux_xen
-rwxr-xr-x 1 root root  1992 &#4635;&#4653;&#4733; 12 15:31 20_memtest86+
-rwxr-xr-x 1 root root 11692 &#4772;&#4949;&#4648; 11 13:51 30_os-prober
-rwxr-xr-x 1 root root  1416 &#4772;&#4949;&#4648; 11 13:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 &#4772;&#4949;&#4648; 11 13:51 40_custom
-rwxr-xr-x 1 root root   216 &#4772;&#4949;&#4648; 11 13:51 41_custom
-rw-r--r-- 1 root root   483 &#4772;&#4949;&#4648; 11 13:51 README




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



/boot/efi detected in the fstab of sda6: UUID=5048-B488   (sda2)
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi

efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0003,0000,0004,2003,2001,2002
Boot0000* ubuntu    HD(2,200800,82000,70ecfca5-b142-11e2-9b5f-fa1a369aa39b)File(EFIubuntushimx64.efi)
Boot0001* EFI Network 0 for IPv6 (7C-05-07-79-30-63)     ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(7c0507793063,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* EFI Network 0 for IPv4 (7C-05-07-79-30-63)     ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(7c0507793063,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0003* Windows Boot Manager    HD(2,200800,82000,70ecfca5-b142-11e2-9b5f-fa1a369aa39b)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* Ubuntu    HD(2,200800,82000,70ecfca5-b142-11e2-9b5f-fa1a369aa39b)File(EFIubuntugrubx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to boot.repair@gmail.com
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /boot/efi.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda3.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda7    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/ethiojob/0641E1E17B7C843C.
sda8    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /home.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
1      1049kB  1075MB  1074MB  ntfs         Basic data partition  hidden, diag
2      1075MB  1347MB  273MB   fat32        Basic data partition  boot
3      1347MB  1482MB  134MB   ntfs         Basic data partition  msftres
4      1482MB  222GB   221GB   ntfs         Basic data partition  msftdata
6      222GB   322GB   100GB   ext4
8      322GB   429GB   107GB   ext4
9      429GB   439GB   10.0GB
7      439GB   737GB   298GB   ntfs                               msftdata
5      737GB   750GB   13.1GB  ntfs         Basic data partition  hidden, diag



                                                                          
Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.

                                                                          
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.

=================== parted -lm:

BYT;
/dev/sda:750GB:scsi:512:512:gpt:ATA TOSHIBA MQ01ABD0;
1:1049kB:1075MB:1074MB:ntfs:Basic data partition:hidden, diag;
2:1075MB:1347MB:273MB:fat32:Basic data partition:boot;
3:1347MB:1482MB:134MB:ntfs:Basic data partition:msftres;
4:1482MB:222GB:221GB:ntfs:Basic data partition:msftdata;
6:222GB:322GB:100GB:ext4::;
8:322GB:429GB:107GB:ext4::;
9:429GB:439GB:10.0GB:::;
7:439GB:737GB:298GB:ntfs::msftdata;
5:737GB:750GB:13.1GB:ntfs:Basic data partition:hidden, diag;


                                                                          
Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.

                                                                          
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.


=================== mount:
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda8 on /home type ext4 (rw)
/dev/sda2 on /boot/efi type vfat (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/home/ethiojob/.Private on /home/ethiojob type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=07d1818800ba1899,ecryptfs_fnek_sig=c90277e1f9fc1a67)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ethiojob)
/dev/sda7 on /media/ethiojob/0641E1E17B7C843C type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
none on /tmp/guest-rxBHXO type tmpfs (rw,mode=700)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdc-wdm1 cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sdb sdc serial sg0 sg1 sg2 sg3 sg4 shm snapshot snd sr0 sr1 stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  f8 ff 1f 00 00 00 00 00  |................|
00000030  55 55 01 00 00 00 00 00  ff ff 01 00 00 00 00 00  |UU..............|
00000040  f6 00 00 00 01 00 00 00  99 19 47 54 2b 47 54 ca  |..........GT+GT.|
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
ls /boot/efi/1:

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 20 00  |........?..... .|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 61 18 00 00  |. ..........a...|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 88 b4 48 50 4e  4f 20 4e 41 4d 45 20 20  |..)..HPNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 28 00  |........?....((.|
00000020  00 00 00 00 80 00 80 00  ff ff 03 00 00 00 00 00  |................|
00000030  aa 2a 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.*..............|
00000040  f6 00 00 00 01 00 00 00  63 1e 4a 78 4b 4a 78 62  |........c.JxKJxb|
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

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 2c 00  |........?....(,.|
00000020  00 00 00 00 80 00 80 00  f0 77 b0 19 00 00 00 00  |.........w......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  34 e3 0f 16 f5 0f 16 48  |........4......H|
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

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 b0 cd 55  |........?......U|
00000020  00 00 00 00 80 00 80 00  f8 af 86 01 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  cf 4a 41 e4 77 41 e4 e6  |.........JA.wA..|
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

=================== hexdump -n512 -C /dev/sda7
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 40 28 33  |........?....@(3|
00000020  00 00 00 00 80 00 80 00  ff 6f a5 22 00 00 00 00  |.........o."....|
00000030  04 00 00 00 00 00 00 00  ff 56 2a 02 00 00 00 00  |.........V*.....|
00000040  f6 00 00 00 01 00 00 00  3c 84 7c 7b e1 e1 41 06  |........<.|{..A.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem              Type      Size  Used Avail Use% Mounted on
/dev/sda6               ext4       92G  5.4G   82G   7% /
none                    tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev                    devtmpfs  2.9G   12K  2.9G   1% /dev
tmpfs                   tmpfs     585M  1.3M  584M   1% /run
none                    tmpfs     5.0M  8.0K  5.0M   1% /run/lock
none                    tmpfs     2.9G   55M  2.9G   2% /run/shm
none                    tmpfs     100M  120K  100M   1% /run/user
/dev/sda8               ext4       99G   31G   64G  33% /home
/dev/sda2               vfat      256M   55M  202M  22% /boot/efi
/home/ethiojob/.Private ecryptfs   99G   31G   64G  33% /home/ethiojob
/dev/sda7               fuseblk   278G   53G  225G  20% /media/ethiojob/0641E1E17B7C843C
none                    tmpfs     2.9G  2.5M  2.9G   1% /tmp/guest-rxBHXO
/dev/sda1               fuseblk   1.0G  355M  670M  35% /mnt/boot-sav/sda1
/dev/sda3               fuseblk   128M   15M  114M  12% /mnt/boot-sav/sda3
/dev/sda4               fuseblk   206G   54G  152G  27% /mnt/boot-sav/sda4
/dev/sda5               fuseblk    13G   12G  861M  94% /mnt/boot-sav/sda5

=================== fdisk -l:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT


EFI detected. Please check the options.

=================== Recommended repair
Recommended-Repair
This setting will purge (in order to sign-grub upgrade version) and reinstall the grub-efi-amd64-signed of sda6, using the following options: upgrade-grub       sda2/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


/boot/efi added in sda6/fstab
Quantity of real Windows: 1
df: ‘/dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi’: No such file or directory
Could not detect USEDPERCENT of sda2@/EFI/Microsoft/Boot/bootmgfw.efi ().
df: ‘/dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi’: No such file or directory

sda6/boot/efi not empty
apt-get -y --force-yes update
Purge the GRUB of sda6
Install last GRUB version in /etc/apt/sources.list
apt-get -y --force-yes update
grub-efi-amd64-signed available


0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 4 not upgraded.
DEBCHECK debOK, grub-efi-amd64-signed
DEBCHECK debOK
shim-signed available
linux-signed-generic available
Please type: sudo dpkg --configure -ansudo apt-get install -fynsudo apt-get purge -y --force-yes grub* shim-signed linux-signed*

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root      4096 &#4865;&#4757;  10 14:54 grub.d
total 4
-rwxr-xr-x 1 root root 1992 &#4635;&#4653;&#4733; 12 15:31 20_memtest86+


/boot/efi detected in the fstab of sda6: UUID=5048-B488     (sda2)
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
shim-signed available
linux-signed-generic available
Then type: sudo apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic
/boot/efi detected in the fstab of sda6: UUID=5048-B488     (sda2)
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root      4096 &#4865;&#4757;  10 15:01 grub.d
drwxr-xr-x  2 root root      4096 &#4865;&#4757;  10 14:54 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 &#4772;&#4949;&#4648; 11 13:51 00_header
-rwxr-xr-x 1 root root  6058 &#4772;&#4949;&#4648; 10 18:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 &#4772;&#4949;&#4648; 11 13:51 10_linux
-rwxr-xr-x 1 root root 10412 &#4772;&#4949;&#4648; 11 13:51 20_linux_xen
-rwxr-xr-x 1 root root 11692 &#4772;&#4949;&#4648; 11 13:51 30_os-prober
-rwxr-xr-x 1 root root  1416 &#4772;&#4949;&#4648; 11 13:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 &#4772;&#4949;&#4648; 11 13:51 40_custom
-rwxr-xr-x 1 root root   216 &#4772;&#4949;&#4648; 11 13:51 41_custom
-rw-r--r-- 1 root root   483 &#4772;&#4949;&#4648; 11 13:51 README




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



/boot/efi detected in the fstab of sda6: UUID=5048-B488     (sda2)
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Unhide GRUB boot menu in sda6/etc/default/grub

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root      4096 &#4865;&#4757;  10 15:01 grub.d
drwxr-xr-x  2 root root      4096 &#4865;&#4757;  10 14:54 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 &#4772;&#4949;&#4648; 11 13:51 00_header
-rwxr-xr-x 1 root root  6058 &#4772;&#4949;&#4648; 10 18:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 &#4772;&#4949;&#4648; 11 13:51 10_linux
-rwxr-xr-x 1 root root 10412 &#4772;&#4949;&#4648; 11 13:51 20_linux_xen
-rwxr-xr-x 1 root root 11692 &#4772;&#4949;&#4648; 11 13:51 30_os-prober
-rwxr-xr-x 1 root root  1416 &#4772;&#4949;&#4648; 11 13:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 &#4772;&#4949;&#4648; 11 13:51 40_custom
-rwxr-xr-x 1 root root   216 &#4772;&#4949;&#4648; 11 13:51 41_custom
-rw-r--r-- 1 root root   483 &#4772;&#4949;&#4648; 11 13:51 README




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



/boot/efi detected in the fstab of sda6: UUID=5048-B488     (sda2)
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
Subsystem: Toshiba America Info Systems Device [1179:fa44]
Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
*******

grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ...found.
Installing for x86_64-efi platform.
grub-install: info: cannot open `/boot/grub/device.map': No such file or directory.
grub-install: info: /dev/sda2 is not present.
grub-install: info: Looking for /dev/sda2.
grub-install: info: /dev/sda is a parent of /dev/sda2.
grub-install: info: /dev/sda2 starts from 2099200.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 1 starts from 2099200.
grub-install: info: /dev/sda2 is present.
grub-install: info: Looking for /dev/sda2.
grub-install: info: /dev/sda is a parent of /dev/sda2.
grub-install: info: /dev/sda2 starts from 2099200.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 1 starts from 2099200.
grub-install: info: /dev/sda2 is present.
grub-install: info: Looking for /dev/sda2.
grub-install: info: /dev/sda is a parent of /dev/sda2.
grub-install: info: /dev/sda2 starts from 2099200.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 1 starts from 2099200.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/nativedisk.mod' -> `/boot/grub/x86_64-efi/nativedisk.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/backtrace.mod' -> `/boot/grub/x86_64-efi/backtrace.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/reboot.mod' -> `/boot/grub/x86_64-efi/reboot.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/bfs.mod' -> `/boot/grub/x86_64-efi/bfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/raid5rec.mod' -> `/boot/grub/x86_64-efi/raid5rec.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix_be.mod' -> `/boot/grub/x86_64-efi/minix_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/mdraid09_be.mod' -> `/boot/grub/x86_64-efi/mdraid09_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/http.mod' -> `/boot/grub/x86_64-efi/http.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_dsa.mod' -> `/boot/grub/x86_64-efi/gcry_dsa.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_gpt.mod' -> `/boot/grub/x86_64-efi/part_gpt.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/probe.mod' -> `/boot/grub/x86_64-efi/probe.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/halt.mod' -> `/boot/grub/x86_64-efi/halt.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/eval.mod' -> `/boot/grub/x86_64-efi/eval.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_des.mod' -> `/boot/grub/x86_64-efi/gcry_des.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/net.mod' -> `/boot/grub/x86_64-efi/net.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ntfscomp.mod' -> `/boot/grub/x86_64-efi/ntfscomp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ohci.mod' -> `/boot/grub/x86_64-efi/ohci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/serial.mod' -> `/boot/grub/x86_64-efi/serial.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/file.mod' -> `/boot/grub/x86_64-efi/file.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video_cirrus.mod' -> `/boot/grub/x86_64-efi/video_cirrus.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cbfs.mod' -> `/boot/grub/x86_64-efi/cbfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_rfc2268.mod' -> `/boot/grub/x86_64-efi/gcry_rfc2268.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/legacy_password_test.mod' -> `/boot/grub/x86_64-efi/legacy_password_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/setjmp.mod' -> `/boot/grub/x86_64-efi/setjmp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/tar.mod' -> `/boot/grub/x86_64-efi/tar.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_whirlpool.mod' -> `/boot/grub/x86_64-efi/gcry_whirlpool.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/read.mod' -> `/boot/grub/x86_64-efi/read.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video_colors.mod' -> `/boot/grub/x86_64-efi/video_colors.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ehci.mod' -> `/boot/grub/x86_64-efi/ehci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/search_label.mod' -> `/boot/grub/x86_64-efi/search_label.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_sha256.mod' -> `/boot/grub/x86_64-efi/gcry_sha256.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/iorw.mod' -> `/boot/grub/x86_64-efi/iorw.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/luks.mod' -> `/boot/grub/x86_64-efi/luks.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/all_video.mod' -> `/boot/grub/x86_64-efi/all_video.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/scsi.mod' -> `/boot/grub/x86_64-efi/scsi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/zfsinfo.mod' -> `/boot/grub/x86_64-efi/zfsinfo.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/bufio.mod' -> `/boot/grub/x86_64-efi/bufio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_blowfish.mod' -> `/boot/grub/x86_64-efi/gcry_blowfish.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/xnu_uuid.mod' -> `/boot/grub/x86_64-efi/xnu_uuid.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/bitmap.mod' -> `/boot/grub/x86_64-efi/bitmap.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hfspluscomp.mod' -> `/boot/grub/x86_64-efi/hfspluscomp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbserial_usbdebug.mod' -> `/boot/grub/x86_64-efi/usbserial_usbdebug.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/datehook.mod' -> `/boot/grub/x86_64-efi/datehook.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lsefimmap.mod' -> `/boot/grub/x86_64-efi/lsefimmap.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix3_be.mod' -> `/boot/grub/x86_64-efi/minix3_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/sleep.mod' -> `/boot/grub/x86_64-efi/sleep.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ata.mod' -> `/boot/grub/x86_64-efi/ata.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/syslinuxcfg.mod' -> `/boot/grub/x86_64-efi/syslinuxcfg.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cmp.mod' -> `/boot/grub/x86_64-efi/cmp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/newc.mod' -> `/boot/grub/x86_64-efi/newc.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/terminfo.mod' -> `/boot/grub/x86_64-efi/terminfo.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lspci.mod' -> `/boot/grub/x86_64-efi/lspci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/parttool.mod' -> `/boot/grub/x86_64-efi/parttool.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cryptodisk.mod' -> `/boot/grub/x86_64-efi/cryptodisk.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/msdospart.mod' -> `/boot/grub/x86_64-efi/msdospart.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/legacycfg.mod' -> `/boot/grub/x86_64-efi/legacycfg.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/disk.mod' -> `/boot/grub/x86_64-efi/disk.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_msdos.mod' -> `/boot/grub/x86_64-efi/part_msdos.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/extcmd.mod' -> `/boot/grub/x86_64-efi/extcmd.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_sha1.mod' -> `/boot/grub/x86_64-efi/gcry_sha1.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/normal.mod' -> `/boot/grub/x86_64-efi/normal.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_arcfour.mod' -> `/boot/grub/x86_64-efi/gcry_arcfour.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_dvh.mod' -> `/boot/grub/x86_64-efi/part_dvh.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/test.mod' -> `/boot/grub/x86_64-efi/test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/offsetio.mod' -> `/boot/grub/x86_64-efi/offsetio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_md5.mod' -> `/boot/grub/x86_64-efi/gcry_md5.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/crypto.mod' -> `/boot/grub/x86_64-efi/crypto.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_crc.mod' -> `/boot/grub/x86_64-efi/gcry_crc.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/iso9660.mod' -> `/boot/grub/x86_64-efi/iso9660.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cpio_be.mod' -> `/boot/grub/x86_64-efi/cpio_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/xfs.mod' -> `/boot/grub/x86_64-efi/xfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_sha512.mod' -> `/boot/grub/x86_64-efi/gcry_sha512.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/nilfs2.mod' -> `/boot/grub/x86_64-efi/nilfs2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/setpci.mod' -> `/boot/grub/x86_64-efi/setpci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lsacpi.mod' -> `/boot/grub/x86_64-efi/lsacpi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/sleep_test.mod' -> `/boot/grub/x86_64-efi/sleep_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/pbkdf2.mod' -> `/boot/grub/x86_64-efi/pbkdf2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/functional_test.mod' -> `/boot/grub/x86_64-efi/functional_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gptsync.mod' -> `/boot/grub/x86_64-efi/gptsync.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/test_blockarg.mod' -> `/boot/grub/x86_64-efi/test_blockarg.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/verify.mod' -> `/boot/grub/x86_64-efi/verify.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/dm_nv.mod' -> `/boot/grub/x86_64-efi/dm_nv.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/loadenv.mod' -> `/boot/grub/x86_64-efi/loadenv.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/password.mod' -> `/boot/grub/x86_64-efi/password.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ntfs.mod' -> `/boot/grub/x86_64-efi/ntfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cpuid.mod' -> `/boot/grub/x86_64-efi/cpuid.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hfsplus.mod' -> `/boot/grub/x86_64-efi/hfsplus.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/progress.mod' -> `/boot/grub/x86_64-efi/progress.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lssal.mod' -> `/boot/grub/x86_64-efi/lssal.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gfxterm_menu.mod' -> `/boot/grub/x86_64-efi/gfxterm_menu.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/xzio.mod' -> `/boot/grub/x86_64-efi/xzio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cbtime.mod' -> `/boot/grub/x86_64-efi/cbtime.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbms.mod' -> `/boot/grub/x86_64-efi/usbms.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/fat.mod' -> `/boot/grub/x86_64-efi/fat.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_amiga.mod' -> `/boot/grub/x86_64-efi/part_amiga.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/xnu.mod' -> `/boot/grub/x86_64-efi/xnu.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/videotest_checksum.mod' -> `/boot/grub/x86_64-efi/videotest_checksum.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/macho.mod' -> `/boot/grub/x86_64-efi/macho.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gfxterm.mod' -> `/boot/grub/x86_64-efi/gfxterm.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/boot.mod' -> `/boot/grub/x86_64-efi/boot.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video_fb.mod' -> `/boot/grub/x86_64-efi/video_fb.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/xnu_uuid_test.mod' -> `/boot/grub/x86_64-efi/xnu_uuid_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cs5536.mod' -> `/boot/grub/x86_64-efi/cs5536.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/raid6rec.mod' -> `/boot/grub/x86_64-efi/raid6rec.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbserial_common.mod' -> `/boot/grub/x86_64-efi/usbserial_common.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/elf.mod' -> `/boot/grub/x86_64-efi/elf.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/keylayouts.mod' -> `/boot/grub/x86_64-efi/keylayouts.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/afs.mod' -> `/boot/grub/x86_64-efi/afs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lvm.mod' -> `/boot/grub/x86_64-efi/lvm.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/search_fs_file.mod' -> `/boot/grub/x86_64-efi/search_fs_file.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_camellia.mod' -> `/boot/grub/x86_64-efi/gcry_camellia.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ufs1.mod' -> `/boot/grub/x86_64-efi/ufs1.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/uhci.mod' -> `/boot/grub/x86_64-efi/uhci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/appleldr.mod' -> `/boot/grub/x86_64-efi/appleldr.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/mdraid1x.mod' -> `/boot/grub/x86_64-efi/mdraid1x.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/png.mod' -> `/boot/grub/x86_64-efi/png.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hashsum.mod' -> `/boot/grub/x86_64-efi/hashsum.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/terminal.mod' -> `/boot/grub/x86_64-efi/terminal.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cbmemc.mod' -> `/boot/grub/x86_64-efi/cbmemc.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/search_fs_uuid.mod' -> `/boot/grub/x86_64-efi/search_fs_uuid.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/exfctest.mod' -> `/boot/grub/x86_64-efi/exfctest.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cbtable.mod' -> `/boot/grub/x86_64-efi/cbtable.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/fixvideo.mod' -> `/boot/grub/x86_64-efi/fixvideo.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cat.mod' -> `/boot/grub/x86_64-efi/cat.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_sunpc.mod' -> `/boot/grub/x86_64-efi/part_sunpc.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/videoinfo.mod' -> `/boot/grub/x86_64-efi/videoinfo.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_sun.mod' -> `/boot/grub/x86_64-efi/part_sun.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/priority_queue.mod' -> `/boot/grub/x86_64-efi/priority_queue.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/trig.mod' -> `/boot/grub/x86_64-efi/trig.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/pata.mod' -> `/boot/grub/x86_64-efi/pata.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/jfs.mod' -> `/boot/grub/x86_64-efi/jfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_rsa.mod' -> `/boot/grub/x86_64-efi/gcry_rsa.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbserial_ftdi.mod' -> `/boot/grub/x86_64-efi/usbserial_ftdi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/zfscrypt.mod' -> `/boot/grub/x86_64-efi/zfscrypt.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/signature_test.mod' -> `/boot/grub/x86_64-efi/signature_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix.mod' -> `/boot/grub/x86_64-efi/minix.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/memdisk.mod' -> `/boot/grub/x86_64-efi/memdisk.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/udf.mod' -> `/boot/grub/x86_64-efi/udf.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_dfly.mod' -> `/boot/grub/x86_64-efi/part_dfly.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/squash4.mod' -> `/boot/grub/x86_64-efi/squash4.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/font.mod' -> `/boot/grub/x86_64-efi/font.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/spkmodem.mod' -> `/boot/grub/x86_64-efi/spkmodem.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/time.mod' -> `/boot/grub/x86_64-efi/time.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_md4.mod' -> `/boot/grub/x86_64-efi/gcry_md4.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cmdline_cat_test.mod' -> `/boot/grub/x86_64-efi/cmdline_cat_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_seed.mod' -> `/boot/grub/x86_64-efi/gcry_seed.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usb_keyboard.mod' -> `/boot/grub/x86_64-efi/usb_keyboard.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/tr.mod' -> `/boot/grub/x86_64-efi/tr.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/mpi.mod' -> `/boot/grub/x86_64-efi/mpi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/reiserfs.mod' -> `/boot/grub/x86_64-efi/reiserfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/help.mod' -> `/boot/grub/x86_64-efi/help.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hello.mod' -> `/boot/grub/x86_64-efi/hello.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/fshelp.mod' -> `/boot/grub/x86_64-efi/fshelp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix2_be.mod' -> `/boot/grub/x86_64-efi/minix2_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/testspeed.mod' -> `/boot/grub/x86_64-efi/testspeed.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/play.mod' -> `/boot/grub/x86_64-efi/play.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/multiboot.mod' -> `/boot/grub/x86_64-efi/multiboot.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/loadbios.mod' -> `/boot/grub/x86_64-efi/loadbios.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cbls.mod' -> `/boot/grub/x86_64-efi/cbls.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hexdump.mod' -> `/boot/grub/x86_64-efi/hexdump.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efi_uga.mod' -> `/boot/grub/x86_64-efi/efi_uga.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_twofish.mod' -> `/boot/grub/x86_64-efi/gcry_twofish.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/true.mod' -> `/boot/grub/x86_64-efi/true.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/echo.mod' -> `/boot/grub/x86_64-efi/echo.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/multiboot2.mod' -> `/boot/grub/x86_64-efi/multiboot2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/mdraid09.mod' -> `/boot/grub/x86_64-efi/mdraid09.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lzopio.mod' -> `/boot/grub/x86_64-efi/lzopio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/blocklist.mod' -> `/boot/grub/x86_64-efi/blocklist.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ahci.mod' -> `/boot/grub/x86_64-efi/ahci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gzio.mod' -> `/boot/grub/x86_64-efi/gzio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minicmd.mod' -> `/boot/grub/x86_64-efi/minicmd.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/diskfilter.mod' -> `/boot/grub/x86_64-efi/diskfilter.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/macbless.mod' -> `/boot/grub/x86_64-efi/macbless.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_serpent.mod' -> `/boot/grub/x86_64-efi/gcry_serpent.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/date.mod' -> `/boot/grub/x86_64-efi/date.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/search.mod' -> `/boot/grub/x86_64-efi/search.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_rijndael.mod' -> `/boot/grub/x86_64-efi/gcry_rijndael.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/geli.mod' -> `/boot/grub/x86_64-efi/geli.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/tftp.mod' -> `/boot/grub/x86_64-efi/tftp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gfxterm_background.mod' -> `/boot/grub/x86_64-efi/gfxterm_background.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/exfat.mod' -> `/boot/grub/x86_64-efi/exfat.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cpio.mod' -> `/boot/grub/x86_64-efi/cpio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/regexp.mod' -> `/boot/grub/x86_64-efi/regexp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efi_gop.mod' -> `/boot/grub/x86_64-efi/efi_gop.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/jpeg.mod' -> `/boot/grub/x86_64-efi/jpeg.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/archelp.mod' -> `/boot/grub/x86_64-efi/archelp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lsefisystab.mod' -> `/boot/grub/x86_64-efi/lsefisystab.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usb.mod' -> `/boot/grub/x86_64-efi/usb.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/procfs.mod' -> `/boot/grub/x86_64-efi/procfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/acpi.mod' -> `/boot/grub/x86_64-efi/acpi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/linux16.mod' -> `/boot/grub/x86_64-efi/linux16.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_rmd160.mod' -> `/boot/grub/x86_64-efi/gcry_rmd160.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/videotest.mod' -> `/boot/grub/x86_64-efi/videotest.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/mmap.mod' -> `/boot/grub/x86_64-efi/mmap.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lsmmap.mod' -> `/boot/grub/x86_64-efi/lsmmap.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ext2.mod' -> `/boot/grub/x86_64-efi/ext2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/adler32.mod' -> `/boot/grub/x86_64-efi/adler32.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/configfile.mod' -> `/boot/grub/x86_64-efi/configfile.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_tiger.mod' -> `/boot/grub/x86_64-efi/gcry_tiger.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/odc.mod' -> `/boot/grub/x86_64-efi/odc.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ufs1_be.mod' -> `/boot/grub/x86_64-efi/ufs1_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbserial_pl2303.mod' -> `/boot/grub/x86_64-efi/usbserial_pl2303.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/btrfs.mod' -> `/boot/grub/x86_64-efi/btrfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbtest.mod' -> `/boot/grub/x86_64-efi/usbtest.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/chain.mod' -> `/boot/grub/x86_64-efi/chain.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/affs.mod' -> `/boot/grub/x86_64-efi/affs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/linux.mod' -> `/boot/grub/x86_64-efi/linux.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/aout.mod' -> `/boot/grub/x86_64-efi/aout.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_apple.mod' -> `/boot/grub/x86_64-efi/part_apple.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hdparm.mod' -> `/boot/grub/x86_64-efi/hdparm.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_idea.mod' -> `/boot/grub/x86_64-efi/gcry_idea.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/tga.mod' -> `/boot/grub/x86_64-efi/tga.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/loopback.mod' -> `/boot/grub/x86_64-efi/loopback.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/password_pbkdf2.mod' -> `/boot/grub/x86_64-efi/password_pbkdf2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/div_test.mod' -> `/boot/grub/x86_64-efi/div_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ldm.mod' -> `/boot/grub/x86_64-efi/ldm.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/keystatus.mod' -> `/boot/grub/x86_64-efi/keystatus.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/bitmap_scale.mod' -> `/boot/grub/x86_64-efi/bitmap_scale.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lsefi.mod' -> `/boot/grub/x86_64-efi/lsefi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/zfs.mod' -> `/boot/grub/x86_64-efi/zfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_plan.mod' -> `/boot/grub/x86_64-efi/part_plan.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/pcidump.mod' -> `/boot/grub/x86_64-efi/pcidump.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_cast5.mod' -> `/boot/grub/x86_64-efi/gcry_cast5.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efifwsetup.mod' -> `/boot/grub/x86_64-efi/efifwsetup.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/morse.mod' -> `/boot/grub/x86_64-efi/morse.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gettext.mod' -> `/boot/grub/x86_64-efi/gettext.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/relocator.mod' -> `/boot/grub/x86_64-efi/relocator.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/sfs.mod' -> `/boot/grub/x86_64-efi/sfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/pbkdf2_test.mod' -> `/boot/grub/x86_64-efi/pbkdf2_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/linuxefi.mod' -> `/boot/grub/x86_64-efi/linuxefi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/bsd.mod' -> `/boot/grub/x86_64-efi/bsd.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/memrw.mod' -> `/boot/grub/x86_64-efi/memrw.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hfs.mod' -> `/boot/grub/x86_64-efi/hfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_acorn.mod' -> `/boot/grub/x86_64-efi/part_acorn.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/at_keyboard.mod' -> `/boot/grub/x86_64-efi/at_keyboard.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_bsd.mod' -> `/boot/grub/x86_64-efi/part_bsd.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video.mod' -> `/boot/grub/x86_64-efi/video.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efinet.mod' -> `/boot/grub/x86_64-efi/efinet.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gfxmenu.mod' -> `/boot/grub/x86_64-efi/gfxmenu.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/romfs.mod' -> `/boot/grub/x86_64-efi/romfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ls.mod' -> `/boot/grub/x86_64-efi/ls.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/setjmp_test.mod' -> `/boot/grub/x86_64-efi/setjmp_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video_bochs.mod' -> `/boot/grub/x86_64-efi/video_bochs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/crc64.mod' -> `/boot/grub/x86_64-efi/crc64.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix2.mod' -> `/boot/grub/x86_64-efi/minix2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/testload.mod' -> `/boot/grub/x86_64-efi/testload.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ufs2.mod' -> `/boot/grub/x86_64-efi/ufs2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/datetime.mod' -> `/boot/grub/x86_64-efi/datetime.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix3.mod' -> `/boot/grub/x86_64-efi/minix3.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efiemu32.o' -> `/boot/grub/x86_64-efi/efiemu32.o'.
grub-install: info: cannot open `/usr/lib/grub/x86_64-efi/efiemu32.o': No such file or directory.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efiemu64.o' -> `/boot/grub/x86_64-efi/efiemu64.o'.
grub-install: info: cannot open `/usr/lib/grub/x86_64-efi/efiemu64.o': No such file or directory.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/moddep.lst' -> `/boot/grub/x86_64-efi/moddep.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/command.lst' -> `/boot/grub/x86_64-efi/command.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/fs.lst' -> `/boot/grub/x86_64-efi/fs.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/partmap.lst' -> `/boot/grub/x86_64-efi/partmap.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/parttool.lst' -> `/boot/grub/x86_64-efi/parttool.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video.lst' -> `/boot/grub/x86_64-efi/video.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/crypto.lst' -> `/boot/grub/x86_64-efi/crypto.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/terminal.lst' -> `/boot/grub/x86_64-efi/terminal.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/modinfo.sh' -> `/boot/grub/x86_64-efi/modinfo.sh'.
grub-install: info: copying `/usr/share/locale/haw/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/haw.mo'.
grub-install: info: cannot open `/usr/share/locale/haw/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/es_AR/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/es_AR.mo'.
grub-install: info: cannot open `/usr/share/locale/es_AR/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ga/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ga.mo'.
grub-install: info: cannot open `/usr/share/locale/ga/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fa/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fa.mo'.
grub-install: info: cannot open `/usr/share/locale/fa/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ach/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ach.mo'.
grub-install: info: cannot open `/usr/share/locale/ach/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sml/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sml.mo'.
grub-install: info: cannot open `/usr/share/locale/sml/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/om/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/om.mo'.
grub-install: info: cannot open `/usr/share/locale/om/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ur/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ur.mo'.
grub-install: info: cannot open `/usr/share/locale/ur/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/uk/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/uk.mo'.
grub-install: info: cannot open `/usr/share/locale/uk/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/hi/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/hi.mo'.
grub-install: info: cannot open `/usr/share/locale/hi/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/hu/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/hu.mo'.
grub-install: info: cannot open `/usr/share/locale/hu/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/az/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/az.mo'.
grub-install: info: cannot open `/usr/share/locale/az/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ace/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ace.mo'.
grub-install: info: cannot open `/usr/share/locale/ace/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/xh/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/xh.mo'.
grub-install: info: cannot open `/usr/share/locale/xh/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/lt/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/lt.mo'.
grub-install: info: cannot open `/usr/share/locale/lt/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/jv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/jv.mo'.
grub-install: info: cannot open `/usr/share/locale/jv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/id_ID/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/id_ID.mo'.
grub-install: info: cannot open `/usr/share/locale/id_ID/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/frp/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/frp.mo'.
grub-install: info: cannot open `/usr/share/locale/frp/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/or/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/or.mo'.
grub-install: info: cannot open `/usr/share/locale/or/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/vec/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/vec.mo'.
grub-install: info: cannot open `/usr/share/locale/vec/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/gez/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/gez.mo'.
grub-install: info: cannot open `/usr/share/locale/gez/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sr@latin/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sr@latin.mo'.
grub-install: info: cannot open `/usr/share/locale/sr@latin/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/cs/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/cs.mo'.
grub-install: info: cannot open `/usr/share/locale/cs/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ary/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ary.mo'.
grub-install: info: cannot open `/usr/share/locale/ary/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/kl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/kl.mo'.
grub-install: info: cannot open `/usr/share/locale/kl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ps/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ps.mo'.
grub-install: info: cannot open `/usr/share/locale/ps/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/byn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/byn.mo'.
grub-install: info: cannot open `/usr/share/locale/byn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ta/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ta.mo'.
grub-install: info: cannot open `/usr/share/locale/ta/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/szl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/szl.mo'.
grub-install: info: cannot open `/usr/share/locale/szl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/be@latin/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/be@latin.mo'.
grub-install: info: cannot open `/usr/share/locale/be@latin/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/os/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/os.mo'.
grub-install: info: cannot open `/usr/share/locale/os/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/chr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/chr.mo'.
grub-install: info: cannot open `/usr/share/locale/chr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fil/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fil.mo'.
grub-install: info: cannot open `/usr/share/locale/fil/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sv.mo'.
grub-install: info: cannot open `/usr/share/locale/sv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sc/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sc.mo'.
grub-install: info: cannot open `/usr/share/locale/sc/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tt@iqtelif/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tt@iqtelif.mo'.
grub-install: info: cannot open `/usr/share/locale/tt@iqtelif/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/trv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/trv.mo'.
grub-install: info: cannot open `/usr/share/locale/trv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/shn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/shn.mo'.
grub-install: info: cannot open `/usr/share/locale/shn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ug/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ug.mo'.
grub-install: info: cannot open `/usr/share/locale/ug/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sr.mo'.
grub-install: info: cannot open `/usr/share/locale/sr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sd/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sd.mo'.
grub-install: info: cannot open `/usr/share/locale/sd/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fy/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fy.mo'.
grub-install: info: cannot open `/usr/share/locale/fy/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/wae/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/wae.mo'.
grub-install: info: cannot open `/usr/share/locale/wae/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tr.mo'.
grub-install: info: cannot open `/usr/share/locale/tr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sco/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sco.mo'.
grub-install: info: cannot open `/usr/share/locale/sco/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fur/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fur.mo'.
grub-install: info: cannot open `/usr/share/locale/fur/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nb/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nb.mo'.
grub-install: info: cannot open `/usr/share/locale/nb/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/da/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/da.mo'.
grub-install: info: cannot open `/usr/share/locale/da/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/gu/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/gu.mo'.
grub-install: info: cannot open `/usr/share/locale/gu/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/lb/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/lb.mo'.
grub-install: info: cannot open `/usr/share/locale/lb/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tk/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tk.mo'.
grub-install: info: cannot open `/usr/share/locale/tk/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/lv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/lv.mo'.
grub-install: info: cannot open `/usr/share/locale/lv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tl.mo'.
grub-install: info: cannot open `/usr/share/locale/tl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/oc/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/oc.mo'.
grub-install: info: cannot open `/usr/share/locale/oc/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/en@quot/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en@quot.mo'.
grub-install: info: cannot open `/usr/share/locale/en@quot/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fi/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fi.mo'.
grub-install: info: cannot open `/usr/share/locale/fi/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/eo/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/eo.mo'.
grub-install: info: cannot open `/usr/share/locale/eo/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/zu/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/zu.mo'.
grub-install: info: cannot open `/usr/share/locale/zu/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mk/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mk.mo'.
grub-install: info: cannot open `/usr/share/locale/mk/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/cv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/cv.mo'.
grub-install: info: cannot open `/usr/share/locale/cv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/it/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/it.mo'.
grub-install: info: cannot open `/usr/share/locale/it/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/gd/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/gd.mo'.
grub-install: info: cannot open `/usr/share/locale/gd/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ve/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ve.mo'.
grub-install: info: cannot open `/usr/share/locale/ve/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/st/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/st.mo'.
grub-install: info: cannot open `/usr/share/locale/st/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/zh/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/zh.mo'.
grub-install: info: cannot open `/usr/share/locale/zh/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ckb/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ckb.mo'.
grub-install: info: cannot open `/usr/share/locale/ckb/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/km/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/km.mo'.
grub-install: info: cannot open `/usr/share/locale/km/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/hr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/hr.mo'.
grub-install: info: cannot open `/usr/share/locale/hr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/qu/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/qu.mo'.
grub-install: info: cannot open `/usr/share/locale/qu/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/kn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/kn.mo'.
grub-install: info: cannot open `/usr/share/locale/kn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/wo/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/wo.mo'.
grub-install: info: cannot open `/usr/share/locale/wo/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bem/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bem.mo'.
grub-install: info: cannot open `/usr/share/locale/bem/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/dv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/dv.mo'.
grub-install: info: cannot open `/usr/share/locale/dv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/br/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/br.mo'.
grub-install: info: cannot open `/usr/share/locale/br/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bn.mo'.
grub-install: info: cannot open `/usr/share/locale/bn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/gv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/gv.mo'.
grub-install: info: cannot open `/usr/share/locale/gv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/aa/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/aa.mo'.
grub-install: info: cannot open `/usr/share/locale/aa/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/gl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/gl.mo'.
grub-install: info: cannot open `/usr/share/locale/gl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/so/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/so.mo'.
grub-install: info: cannot open `/usr/share/locale/so/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/zh_HK/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/zh_HK.mo'.
grub-install: info: cannot open `/usr/share/locale/zh_HK/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/kw/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/kw.mo'.
grub-install: info: cannot open `/usr/share/locale/kw/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pa/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pa.mo'.
grub-install: info: cannot open `/usr/share/locale/pa/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nds/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nds.mo'.
grub-install: info: cannot open `/usr/share/locale/nds/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/es/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/es.mo'.
grub-install: info: cannot open `/usr/share/locale/es/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/kk/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/kk.mo'.
grub-install: info: cannot open `/usr/share/locale/kk/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mi/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mi.mo'.
grub-install: info: cannot open `/usr/share/locale/mi/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pam/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pam.mo'.
grub-install: info: cannot open `/usr/share/locale/pam/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/dz/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/dz.mo'.
grub-install: info: cannot open `/usr/share/locale/dz/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nso/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nso.mo'.
grub-install: info: cannot open `/usr/share/locale/nso/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/si/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/si.mo'.
grub-install: info: cannot open `/usr/share/locale/si/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/am/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/am.mo'.
grub-install: info: cannot open `/usr/share/locale/am/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/eu_ES/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/eu_ES.mo'.
grub-install: info: cannot open `/usr/share/locale/eu_ES/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fa_AF/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fa_AF.mo'.
grub-install: info: cannot open `/usr/share/locale/fa_AF/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pt/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pt.mo'.
grub-install: info: cannot open `/usr/share/locale/pt/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sk/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sk.mo'.
grub-install: info: cannot open `/usr/share/locale/sk/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pl.mo'.
grub-install: info: cannot open `/usr/share/locale/pl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/et/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/et.mo'.
grub-install: info: cannot open `/usr/share/locale/et/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ar/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ar.mo'.
grub-install: info: cannot open `/usr/share/locale/ar/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fr.mo'.
grub-install: info: cannot open `/usr/share/locale/fr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mr.mo'.
grub-install: info: cannot open `/usr/share/locale/mr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pt_BR/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pt_BR.mo'.
grub-install: info: cannot open `/usr/share/locale/pt_BR/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sw/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sw.mo'.
grub-install: info: cannot open `/usr/share/locale/sw/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bn_IN/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bn_IN.mo'.
grub-install: info: cannot open `/usr/share/locale/bn_IN/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/zh_TW/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/zh_TW.mo'.
grub-install: info: cannot open `/usr/share/locale/zh_TW/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/as/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/as.mo'.
grub-install: info: cannot open `/usr/share/locale/as/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/cy/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/cy.mo'.
grub-install: info: cannot open `/usr/share/locale/cy/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ti/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ti.mo'.
grub-install: info: cannot open `/usr/share/locale/ti/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ro_RO/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ro_RO.mo'.
grub-install: info: cannot open `/usr/share/locale/ro_RO/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/uz/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/uz.mo'.
grub-install: info: cannot open `/usr/share/locale/uz/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/lg/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/lg.mo'.
grub-install: info: cannot open `/usr/share/locale/lg/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ca@valencia/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ca@valencia.mo'.
grub-install: info: cannot open `/usr/share/locale/ca@valencia/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/en_CA/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_CA.mo'.
grub-install: info: cannot open `/usr/share/locale/en_CA/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ru/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ru.mo'.
grub-install: info: cannot open `/usr/share/locale/ru/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ff/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ff.mo'.
grub-install: info: cannot open `/usr/share/locale/ff/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/eu/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/eu.mo'.
grub-install: info: cannot open `/usr/share/locale/eu/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/an/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/an.mo'.
grub-install: info: cannot open `/usr/share/locale/an/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/languages/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/languages.mo'.
grub-install: info: cannot open `/usr/share/locale/languages/LC_MESSAGES/grub.mo': Not a directory.
grub-install: info: copying `/usr/share/locale/yi/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/yi.mo'.
grub-install: info: cannot open `/usr/share/locale/yi/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ml_IN/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ml_IN.mo'.
grub-install: info: cannot open `/usr/share/locale/ml_IN/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/csb/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/csb.mo'.
grub-install: info: cannot open `/usr/share/locale/csb/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fa_IR/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fa_IR.mo'.
grub-install: info: cannot open `/usr/share/locale/fa_IR/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mn.mo'.
grub-install: info: cannot open `/usr/share/locale/mn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bs/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bs.mo'.
grub-install: info: cannot open `/usr/share/locale/bs/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/vi/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/vi.mo'.
grub-install: info: cannot open `/usr/share/locale/vi/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/se/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/se.mo'.
grub-install: info: cannot open `/usr/share/locale/se/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ka/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ka.mo'.
grub-install: info: cannot open `/usr/share/locale/ka/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ca/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ca.mo'.
grub-install: info: cannot open `/usr/share/locale/ca/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/be/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/be.mo'.
grub-install: info: cannot open `/usr/share/locale/be/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/co/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/co.mo'.
grub-install: info: cannot open `/usr/share/locale/co/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nl.mo'.
grub-install: info: cannot open `/usr/share/locale/nl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tig/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tig.mo'.
grub-install: info: cannot open `/usr/share/locale/tig/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/de_DE/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/de_DE.mo'.
grub-install: info: cannot open `/usr/share/locale/de_DE/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tt/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tt.mo'.
grub-install: info: cannot open `/usr/share/locale/tt/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ia/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ia.mo'.
grub-install: info: cannot open `/usr/share/locale/ia/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mt/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mt.mo'.
grub-install: info: cannot open `/usr/share/locale/mt/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/en/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en.mo'.
grub-install: info: cannot open `/usr/share/locale/en/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fo/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fo.mo'.
grub-install: info: cannot open `/usr/share/locale/fo/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ast/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ast.mo'.
grub-install: info: cannot open `/usr/share/locale/ast/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/en@boldquot/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en@boldquot.mo'.
grub-install: info: cannot open `/usr/share/locale/en@boldquot/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pt_PT/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pt_PT.mo'.
grub-install: info: cannot open `/usr/share/locale/pt_PT/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/th/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/th.mo'.
grub-install: info: cannot open `/usr/share/locale/th/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bo/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bo.mo'.
grub-install: info: cannot open `/usr/share/locale/bo/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/id/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/id.mo'.
grub-install: info: cannot open `/usr/share/locale/id/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sr@Latn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sr@Latn.mo'.
grub-install: info: cannot open `/usr/share/locale/sr@Latn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ta_LK/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ta_LK.mo'.
grub-install: info: cannot open `/usr/share/locale/ta_LK/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/wa/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/wa.mo'.
grub-install: info: cannot open `/usr/share/locale/wa/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/lo/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/lo.mo'.
grub-install: info: cannot open `/usr/share/locale/lo/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/en_AU/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_AU.mo'.
grub-install: info: cannot open `/usr/share/locale/en_AU/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ms/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ms.mo'.
grub-install: info: cannot open `/usr/share/locale/ms/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sn.mo'.
grub-install: info: cannot open `/usr/share/locale/sn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sl.mo'.
grub-install: info: cannot open `/usr/share/locale/sl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/en_GB/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_GB.mo'.
grub-install: info: cannot open `/usr/share/locale/en_GB/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sq/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sq.mo'.
grub-install: info: cannot open `/usr/share/locale/sq/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/kok/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/kok.mo'.
grub-install: info: cannot open `/usr/share/locale/kok/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mg/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mg.mo'.
grub-install: info: cannot open `/usr/share/locale/mg/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mhr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mhr.mo'.
grub-install: info: cannot open `/usr/share/locale/mhr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ko/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ko.mo'.
grub-install: info: cannot open `/usr/share/locale/ko/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/cgg/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/cgg.mo'.
grub-install: info: cannot open `/usr/share/locale/cgg/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/es_ES/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/es_ES.mo'.
grub-install: info: cannot open `/usr/share/locale/es_ES/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/el/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/el.mo'.
grub-install: info: cannot open `/usr/share/locale/el/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/hy/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/hy.mo'.
grub-install: info: cannot open `/usr/share/locale/hy/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/crh/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/crh.mo'.
grub-install: info: cannot open `/usr/share/locale/crh/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/af/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/af.mo'.
grub-install: info: cannot open `/usr/share/locale/af/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bg/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bg.mo'.
grub-install: info: cannot open `/usr/share/locale/bg/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/zh_CN/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/zh_CN.mo'.
grub-install: info: cannot open `/usr/share/locale/zh_CN/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ky/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ky.mo'.
grub-install: info: cannot open `/usr/share/locale/ky/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ro/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ro.mo'.
grub-install: info: cannot open `/usr/share/locale/ro/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/wal/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/wal.mo'.
grub-install: info: cannot open `/usr/share/locale/wal/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nn.mo'.
grub-install: info: cannot open `/usr/share/locale/nn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ne/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ne.mo'.
grub-install: info: cannot open `/usr/share/locale/ne/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tg/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tg.mo'.
grub-install: info: cannot open `/usr/share/locale/tg/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/cmn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/cmn.mo'.
grub-install: info: cannot open `/usr/share/locale/cmn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sr_RS@latin/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sr_RS@latin.mo'.
grub-install: info: cannot open `/usr/share/locale/sr_RS@latin/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sr_RS/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sr_RS.mo'.
grub-install: info: cannot open `/usr/share/locale/sr_RS/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ja/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ja.mo'.
grub-install: info: cannot open `/usr/share/locale/ja/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/te/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/te.mo'.
grub-install: info: cannot open `/usr/share/locale/te/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ml/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ml.mo'.
grub-install: info: cannot open `/usr/share/locale/ml/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/de/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/de.mo'.
grub-install: info: cannot open `/usr/share/locale/de/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/es_MX/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/es_MX.mo'.
grub-install: info: cannot open `/usr/share/locale/es_MX/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nb_NO/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nb_NO.mo'.
grub-install: info: cannot open `/usr/share/locale/nb_NO/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/he/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/he.mo'.
grub-install: info: cannot open `/usr/share/locale/he/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/my/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/my.mo'.
grub-install: info: cannot open `/usr/share/locale/my/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fr_CA/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fr_CA.mo'.
grub-install: info: cannot open `/usr/share/locale/fr_CA/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ln/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ln.mo'.
grub-install: info: cannot open `/usr/share/locale/ln/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ht/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ht.mo'.
grub-install: info: cannot open `/usr/share/locale/ht/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/locale.alias/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/locale.alias.mo'.
grub-install: info: cannot open `/usr/share/locale/locale.alias/LC_MESSAGES/grub.mo': Not a directory.
grub-install: info: copying `/usr/share/locale/is/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/is.mo'.
grub-install: info: cannot open `/usr/share/locale/is/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/rw/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/rw.mo'.
grub-install: info: cannot open `/usr/share/locale/rw/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ku/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ku.mo'.
grub-install: info: cannot open `/usr/share/locale/ku/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tet/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tet.mo'.
grub-install: info: cannot open `/usr/share/locale/tet/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en_NZ/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_NZ.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en_NZ/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en@shaw/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en@shaw.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en@shaw/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en_US@piglatin/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_US@piglatin.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en_US@piglatin/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en@quot/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en@quot.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en@quot/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/am/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/am.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/am/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en_US/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_US.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en_US/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en_CA/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_CA.mo'.
grub-install: info: copying `/usr/share/locale-langpack/en/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en@boldquot/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en@boldquot.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en@boldquot/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en_AU/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_AU.mo'.
grub-install: info: copying `/usr/share/locale-langpack/en_GB/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_GB.mo'.
grub-install: info: copying `/usr/share/grub/unicode.pf2' -> `/boot/grub/fonts/unicode.pf2'.
grub-install: info: /dev/sda6 is present.
grub-install: info: Looking for /dev/sda6.
grub-install: info: /dev/sda is a parent of /dev/sda6.
grub-install: info: /dev/sda6 starts from 433889280.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 1 starts from 2099200.
grub-install: info: Partition 2 starts from 2631680.
grub-install: info: Partition 3 starts from 2893824.
grub-install: info: Partition 4 starts from 1439543296.
grub-install: info: Partition 5 starts from 433889280.
grub-install: info: /dev/sda6 is present.
grub-install: info: Looking for /dev/sda6.
grub-install: info: /dev/sda is a parent of /dev/sda6.
grub-install: info: /dev/sda6 starts from 433889280.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 1 starts from 2099200.
grub-install: info: Partition 2 starts from 2631680.
grub-install: info: Partition 3 starts from 2893824.
grub-install: info: Partition 4 starts from 1439543296.
grub-install: info: Partition 5 starts from 433889280.
grub-install: info: /dev/sda6 is present.
grub-install: info: Looking for /dev/sda6.
grub-install: info: /dev/sda is a parent of /dev/sda6.
grub-install: info: /dev/sda6 starts from 433889280.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 1 starts from 2099200.
grub-install: info: Partition 2 starts from 2631680.
grub-install: info: Partition 3 starts from 2893824.
grub-install: info: Partition 4 starts from 1439543296.
grub-install: info: Partition 5 starts from 433889280.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: /dev/sda2 is present.
grub-install: info: Looking for /dev/sda2.
grub-install: info: /dev/sda is a parent of /dev/sda2.
grub-install: info: /dev/sda2 starts from 2099200.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 1 starts from 2099200.
grub-install: info: /dev/sda2 is present.
grub-install: info: Looking for /dev/sda2.
grub-install: info: /dev/sda is a parent of /dev/sda2.
grub-install: info: /dev/sda2 starts from 2099200.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 1 starts from 2099200.
grub-install: info: /dev/sda2 is present.
grub-install: info: Looking for /dev/sda2.
grub-install: info: /dev/sda is a parent of /dev/sda2.
grub-install: info: /dev/sda2 starts from 2099200.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1465149168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 1 starts from 2099200.
grub-install: info: grub-mkimage --directory '/usr/lib/grub/x86_64-efi' --prefix '/boot/grub' --output '/boot/grub/x86_64-efi/core.efi' --format 'x86_64-efi' --compression 'auto'  --config '/boot/grub/x86_64-efi/load.cfg' 'ext2' 'part_gpt' 'search_fs_uuid'
.
grub-install: info: the size of config file is 0x68.
grub-install: info: the total module size is 0x51c8.
grub-install: info: reading /usr/lib/grub/x86_64-efi/kernel.img.
grub-install: info: locating the section .text at 0x0.
grub-install: info: locating the section .rodata at 0x9600.
grub-install: info: locating the section .rodata.str1.1 at 0x9798.
grub-install: info: locating the section .data at 0xb0e0.
grub-install: info: locating the section .module_license at 0xc278.
grub-install: info: locating the section .bss at 0xc290.
grub-install: info: locating  at 0x400 (0x400).
grub-install: info: locating  at 0x9a00 (0x9a00).
grub-install: info: locating  at 0x9b98 (0x9b98).
grub-install: info: locating  at 0xb4e0 (0xb4e0).
grub-install: info: locating  at 0xc690 (0xc690).
grub-install: info: locating  at 0xc678 (0xc678).
grub-install: info: locating  at 0x400 (0x400).
grub-install: info: locating grub_strlen at 0x7c25 (0x400).
grub-install: info: locating grub_net_poll_cards_idle at 0xe3d0 (0xc690).
grub-install: info: locating grub_efi_finish_boot_services at 0x2f18 (0x400).
grub-install: info: locating grub_disk_get_size at 0x55c0 (0x400).
grub-install: info: locating grub_file_progress_hook at 0x184e0 (0xc690).
grub-install: info: locating grub_efidisk_fini at 0xe51 (0x400).
grub-install: info: locating grub_puts_ at 0x79d3 (0x400).
grub-install: info: locating grub_millisleep at 0x4195 (0x400).
grub-install: info: locating grub_fs_autoload_hook at 0xe1b0 (0xc690).
grub-install: info: locating efi_wrap_10 at 0x4cc (0x400).
grub-install: info: locating grub_efi_allocate_pages_max at 0x2d32 (0x400).
grub-install: info: locating grub_fs_blocklist at 0xb640 (0xb4e0).
grub-install: info: locating grub_errmsg at 0x183d0 (0xc690).
grub-install: info: locating efi_wrap_5 at 0x463 (0x400).
grub-install: info: locating grub_strncmp at 0x7a4d (0x400).
grub-install: info: locating grub_strtoull at 0x7d3d (0x400).
grub-install: info: locating grub_dma_get_virt at 0x5a5 (0x400).
grub-install: info: locating grub_efi_system_table at 0xe3e0 (0xc690).
grub-install: info: locating memmove at 0x797a (0x400).
grub-install: info: locating efi_wrap_4 at 0x44f (0x400).
grub-install: info: locating grub_disk_open at 0x4f8a (0x400).
grub-install: info: locating grub_efi_locate_protocol at 0x1c16 (0x400).
grub-install: info: locating grub_env_update_get_sorted at 0x669c (0x400).
grub-install: info: locating grub_strcpy at 0x79c0 (0x400).
grub-install: info: locating grub_partition_probe at 0x8fd0 (0x400).
grub-install: info: locating grub_strrchr at 0x7a99 (0x400).
grub-install: info: locating grub_partition_get_name at 0x91d0 (0x400).
grub-install: info: locating grub_dl_load at 0x631d (0x400).
grub-install: info: locating grub_efi_stall at 0x1e3f (0x400).
grub-install: info: locating grub_efi_get_filename at 0x2289 (0x400).
grub-install: info: locating grub_env_export at 0x6788 (0x400).
grub-install: info: locating grub_xvasprintf at 0x89b2 (0x400).
grub-install: info: locating grub_error_push at 0x684a (0x400).
grub-install: info: locating grub_rescue_run at 0x9750 (0x400).
grub-install: info: locating grub_xasprintf at 0x8a4d (0x400).
grub-install: info: locating grub_realloc at 0x40bf (0x400).
grub-install: info: locating grub_exit at 0x1e7e (0x400).
grub-install: info: locating memcpy at 0x797a (0x400).
grub-install: info: locating grub_memmove at 0x797a (0x400).
grub-install: info: locating grub_device_open at 0x47bb (0x400).
grub-install: info: locating grub_register_exported_symbols at 0x993e (0x400).
grub-install: info: locating grub_strdup at 0x7c8f (0x400).
grub-install: info: locating grub_disk_firmware_is_tainted at 0xe420 (0xc690).
grub-install: info: locating grub_divmod64 at 0x7cd7 (0x400).
grub-install: info: locating grub_file_get_device_name at 0x69dd (0x400).
grub-install: info: locating grub_efi_print_device_path at 0x2370 (0x400).
grub-install: info: locating grub_partition_iterate at 0x9164 (0x400).
grub-install: info: locating grub_dma_free at 0x599 (0x400).
grub-install: info: locating grub_vsnprintf at 0x88fd (0x400).
grub-install: info: locating grub_partition_map_list at 0x18530 (0xc690).
grub-install: info: locating efi_wrap_1 at 0x422 (0x400).
grub-install: info: locating grub_command_list at 0xe410 (0xc690).
grub-install: info: locating grub_machine_fini at 0x534 (0x400).
grub-install: info: locating grub_tsc_rate at 0xe400 (0xc690).
grub-install: info: locating grub_rescue_parse_line at 0x94ce (0x400).
grub-install: info: locating grub_efi_get_variable at 0x1ff7 (0x400).
grub-install: info: locating grub_snprintf at 0x896d (0x400).
grub-install: info: locating grub_register_core_commands at 0x4632 (0x400).
grub-install: info: locating grub_disk_dev_register at 0x4ea0 (0x400).
grub-install: info: locating grub_console_init at 0x3927 (0x400).
grub-install: info: locating grub_disk_write_weak at 0xe428 (0xc690).
grub-install: info: locating grub_dl_add at 0x5696 (0x400).
grub-install: info: locating grub_disk_read at 0x5270 (0x400).
grub-install: info: locating grub_term_highlight_color at 0xb7e8 (0xb4e0).
grub-install: info: locating grub_parser_execute at 0x8f62 (0x400).
grub-install: info: locating grub_xputs at 0xb7e0 (0xb4e0).
grub-install: info: locating grub_console_fini at 0x3a28 (0x400).
grub-install: info: locating grub_fatal at 0x8a9c (0x400).
grub-install: info: locating grub_dl_ref at 0x5792 (0x400).
grub-install: info: locating grub_file_seek at 0x6d22 (0x400).
grub-install: info: locating grub_pci_find_capability at 0x6a2 (0x400).
grub-install: info: locating grub_efi_get_loaded_image at 0x1e63 (0x400).
grub-install: info: locating grub_errno at 0x184d0 (0xc690).
grub-install: info: locating grub_parser_cmdline_state at 0x8c1a (0x400).
grub-install: info: locating grub_memset at 0x7baf (0x400).
grub-install: info: locating grub_getkey at 0x991f (0x400).
grub-install: info: locating grub_term_outputs_disabled at 0x18538 (0xc690).
grub-install: info: locating grub_grubnet_fini at 0x184e8 (0xc690).
grub-install: info: locating grub_register_variable_hook at 0x6728 (0x400).
grub-install: info: locating grub_efi_image_handle at 0xe3e8 (0xc690).
grub-install: info: locating grub_vprintf at 0x8666 (0x400).
grub-install: info: locating grub_net_open at 0xc6e8 (0xc690).
grub-install: info: locating grub_register_command_prio at 0x41be (0x400).
grub-install: info: locating grub_efi_compare_device_paths at 0x29f5 (0x400).
grub-install: info: locating grub_file_filters_all at 0x184f0 (0xc690).
grub-install: info: locating grub_install_get_time_ms at 0x4187 (0x400).
grub-install: info: locating _start at 0x400 (0x400).
grub-install: info: locating grub_term_inputs at 0x18540 (0xc690).
grub-install: info: locating grub_parser_split_cmdline at 0x8cd3 (0x400).
grub-install: info: locating grub_disk_firmware_fini at 0xe430 (0xc690).
grub-install: info: locating grub_disk_close at 0x4ee6 (0x400).
grub-install: info: locating grub_dl_unload at 0x580c (0x400).
grub-install: info: locating grub_efi_set_variable at 0x1f1d (0x400).
grub-install: info: locating grub_printf at 0x87d3 (0x400).
grub-install: info: locating grub_efi_secure_boot at 0x2117 (0x400).
grub-install: info: locating grub_unregister_command at 0x42af (0x400).
grub-install: info: locating grub_fs_list at 0xe1b8 (0xc690).
grub-install: info: locating grub_efidisk_get_device_handle at 0x1581 (0x400).
grub-install: info: locating grub_main at 0x731f (0x400).
grub-install: info: locating grub_file_read at 0x6a68 (0x400).
grub-install: info: locating grub_dl_unload_unneeded at 0x641a (0x400).
grub-install: info: locating grub_pci_make_address at 0x5ac (0x400).
grub-install: info: locating memcmp at 0x7a0c (0x400).
grub-install: info: locating grub_term_normal_color at 0xb7e9 (0xb4e0).
grub-install: info: locating grub_disk_dev_list at 0xe438 (0xc690).
grub-install: info: locating grub_machine_init at 0x51a (0x400).
grub-install: info: locating efi_wrap_0 at 0x417 (0x400).
grub-install: info: locating grub_efi_locate_handle at 0x1c5f (0x400).
grub-install: info: locating grub_term_outputs at 0x18548 (0xc690).
grub-install: info: locating grub_modbase at 0xe3f0 (0xc690).
grub-install: info: locating grub_term_inputs_disabled at 0x18550 (0xc690).
grub-install: info: locating grub_efi_net_config at 0xe3f8 (0xc690).
grub-install: info: locating grub_efi_set_virtual_address_map at 0x1ec2 (0x400).
grub-install: info: locating grub_print_error at 0x6944 (0x400).
grub-install: info: locating grub_efi_mm_init at 0x31e7 (0x400).
grub-install: info: locating memset at 0x7baf (0x400).
grub-install: info: locating grub_zalloc at 0x3e36 (0x400).
grub-install: info: locating grub_strcmp at 0x7a2e (0x400).
grub-install: info: locating grub_tsc_init at 0x3aa7 (0x400).
grub-install: info: locating grub_efi_allocate_pages at 0x2c6e (0x400).
grub-install: info: locating grub_strchr at 0x7a83 (0x400).
grub-install: info: locating grub_refresh at 0x98f7 (0x400).
grub-install: info: locating grub_malloc at 0x3e25 (0x400).
grub-install: info: locating grub_efi_get_memory_map at 0x2de4 (0x400).
grub-install: info: locating grub_efidisk_get_device_name at 0x16cc (0x400).
grub-install: info: locating grub_get_time_ms at 0x417b (0x400).
grub-install: info: locating grub_file_close at 0x6b05 (0x400).
grub-install: info: locating grub_file_open at 0x6b50 (0x400).
grub-install: info: locating grub_isspace at 0x7aae (0x400).
grub-install: info: locating grub_efi_open_protocol at 0x1d5a (0x400).
grub-install: info: locating grub_real_dprintf at 0x8822 (0x400).
grub-install: info: locating efi_wrap_3 at 0x43e (0x400).
grub-install: info: locating grub_dl_load_core_noinit at 0x5926 (0x400).
grub-install: info: locating grub_dl_load_file at 0x621a (0x400).
grub-install: info: locating grub_env_unset at 0x6618 (0x400).
grub-install: info: locating grub_device_close at 0x4899 (0x400).
grub-install: info: locating efi_wrap_6 at 0x47c (0x400).
grub-install: info: locating grub_dl_head at 0xc700 (0xc690).
grub-install: info: locating grub_fs_probe at 0x7033 (0x400).
grub-install: info: locating grub_mm_base at 0xe408 (0xc690).
grub-install: info: locating grub_term_poll_usb at 0xe3d8 (0xc690).
grub-install: info: locating grub_file_filters_enabled at 0x18510 (0xc690).
grub-install: info: locating grub_strword at 0x7b0e (0x400).
grub-install: info: locating grub_machine_get_bootlocation at 0x2aeb (0x400).
grub-install: info: locating grub_efi_fini at 0x2b82 (0x400).
grub-install: info: locating grub_err_printed_errors at 0x184d4 (0xc690).
grub-install: info: locating grub_error at 0x67ce (0x400).
grub-install: info: locating grub_current_context at 0xb630 (0xb4e0).
grub-install: info: locating efi_codes at 0x9ae0 (0x9a00).
grub-install: info: locating grub_dl_register_symbol at 0x56d3 (0x400).
grub-install: info: locating grub_efi_is_finished at 0xc6a8 (0xc690).
grub-install: info: locating grub_list_remove at 0x7290 (0x400).
grub-install: info: locating grub_pci_iterate at 0x5d3 (0x400).
grub-install: info: locating grub_modules_get_end at 0x7303 (0x400).
grub-install: info: locating grub_free at 0x3e70 (0x400).
grub-install: info: locating grub_strndup at 0x7c36 (0x400).
grub-install: info: locating efi_wrap_7 at 0x49f (0x400).
grub-install: info: locating grub_named_list_find at 0x7242 (0x400).
grub-install: info: locating grub_dl_unref at 0x57cf (0x400).
grub-install: info: locating grub_efidisk_init at 0x134a (0x400).
grub-install: info: locating grub_disk_dev_unregister at 0x4eb5 (0x400).
grub-install: info: locating grub_efi_init at 0x2a85 (0x400).
grub-install: info: locating grub_arch_dl_check_header at 0x744 (0x400).
grub-install: info: locating grub_arch_dl_relocate_symbols at 0x773 (0x400).
grub-install: info: locating grub_efi_free_pages at 0x2c44 (0x400).
grub-install: info: locating grub_printf_ at 0x8775 (0x400).
grub-install: info: locating grub_efi_get_device_path at 0x2355 (0x400).
grub-install: info: locating start at 0x400 (0x400).
grub-install: info: locating grub_efi_modules_addr at 0x21ea (0x400).
grub-install: info: locating grub_error_pop at 0x68d6 (0x400).
grub-install: info: locating grub_device_iterate at 0x49da (0x400).
grub-install: info: locating grub_getkey_noblock at 0x98ad (0x400).
grub-install: info: locating grub_memalign_dma32 at 0x547 (0x400).
grub-install: info: locating grub_list_push at 0x7276 (0x400).
grub-install: info: locating grub_efi_set_text_mode at 0x1db8 (0x400).
grub-install: info: locating grub_err_printf at 0x87d3 (0x400).
grub-install: info: locating grub_disk_cache_invalidate_all at 0x4e56 (0x400).
grub-install: info: locating grub_env_set at 0x64bc (0x400).
grub-install: info: locating grub_dl_load_core at 0x61d4 (0x400).
grub-install: info: locating grub_gettext at 0xb690 (0xb4e0).
grub-install: info: locating grub_memcmp at 0x7a0c (0x400).
grub-install: info: locating grub_env_get at 0x65ea (0x400).
grub-install: info: locating efi_wrap_2 at 0x430 (0x400).
grub-install: info: locating grub_strtoul at 0x81c5 (0x400).
grub-install: info: locating grub_dma_get_phys at 0x5a9 (0x400).
grub-install: info: locating grub_mm_init_region at 0x3f86 (0x400).
grub-install: info: locating grub_disk_cache_table at 0xe440 (0xc690).
grub-install: info: locating grub_memalign at 0x3c27 (0x400).
grub-install: info: dealing with the relocation section .rela.text for .text.
grub-install: info: relocating an R_X86_64_PC32 entry to 0xdfe1 at the offset 0x3.
grub-install: info: relocating an R_X86_64_PC32 entry to 0xdfd2 at the offset 0xa.
grub-install: info: relocating an R_X86_64_PC32 entry to 0x6f08 at the offset 0x13.
grub-install: info: relocating an R_X86_64_64 entry to 0x2a85 at the offset 0x11d.
grub-install: info: relocating an R_X86_64_64 entry to 0x3aa7 at the offset 0x12a.
grub-install: info: relocating an R_X86_64_64 entry to 0x2b82 at the offset 0x13c.
grub-install: info: relocating an R_X86_64_64 entry to 0x3c27 at the offset 0x165.
grub-install: info: relocating an R_X86_64_64 entry to 0x9b98 at the offset 0x17a.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x18b.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x19b.
grub-install: info: relocating an R_X86_64_64 entry to 0x5ac at the offset 0x1e0.
grub-install: info: relocating an R_X86_64_64 entry to 0x5ac at the offset 0x2af.
grub-install: info: relocating an R_X86_64_64 entry to 0x9bb8 at the offset 0x355.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x366.
grub-install: info: relocating an R_X86_64_64 entry to 0x9bd9 at the offset 0x38f.
grub-install: info: relocating an R_X86_64_64 entry to 0x9bfc at the offset 0x410.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x422.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c14 at the offset 0x474.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x485.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4fd.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a0 at the offset 0x527.
grub-install: info: relocating an R_X86_64_64 entry to 0x29f5 at the offset 0x545.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x57a.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x5ac.
grub-install: info: relocating an R_X86_64_64 entry to 0x29f5 at the offset 0x5cd.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c3b at the offset 0x5fa.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0x60c.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0x638.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c9 at the offset 0x642.
grub-install: info: relocating an R_X86_64_64 entry to 0xc690 at the offset 0x66d.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0x694.
grub-install: info: relocating an R_X86_64_64 entry to 0xb520 at the offset 0x6c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x1c5f at the offset 0x6cf.
grub-install: info: relocating an R_X86_64_64 entry to 0x2355 at the offset 0x6fd.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a0 at the offset 0x722.
grub-install: info: relocating an R_X86_64_64 entry to 0xb520 at the offset 0x73b.
grub-install: info: relocating an R_X86_64_64 entry to 0x1d5a at the offset 0x749.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x767.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x780.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x7c6.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c3f at the offset 0x7eb.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0x7f5.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0x804.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x810.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c66 at the offset 0x824.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0x82e.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x838.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0x84a.
grub-install: info: relocating an R_X86_64_64 entry to 0x81c5 at the offset 0x880.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x88f.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c72 at the offset 0x8a5.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x8b6.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8c1.
grub-install: info: relocating an R_X86_64_64 entry to 0xc690 at the offset 0x8ec.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0x8fb.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0x90a.
grub-install: info: relocating an R_X86_64_64 entry to 0x8da at the offset 0x917.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c80 at the offset 0x933.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x944.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c8f at the offset 0x958.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0x965.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0x977.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x981.
grub-install: info: relocating an R_X86_64_64 entry to 0x9cbb at the offset 0x9d4.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x9e5.
grub-install: info: relocating an R_X86_64_64 entry to 0x9cd2 at the offset 0xa18.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xa22.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xa31.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xa3b.
grub-install: info: relocating an R_X86_64_64 entry to 0xc690 at the offset 0xa55.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0xa61.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0xa6c.
grub-install: info: relocating an R_X86_64_64 entry to 0x8fa at the offset 0xa77.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4e0 at the offset 0xaa4.
grub-install: info: relocating an R_X86_64_64 entry to 0x4eb5 at the offset 0xab6.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0xaea.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ce8 at the offset 0xaff.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0xb13.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ced at the offset 0xb25.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xb2f.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xb3e.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xb48.
grub-install: info: relocating an R_X86_64_64 entry to 0xc690 at the offset 0xb77.
grub-install: info: relocating an R_X86_64_64 entry to 0x9cfb at the offset 0xb8c.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0xba0.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ced at the offset 0xbb2.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xbbc.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xbcb.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xbd5.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0xc00.
grub-install: info: relocating an R_X86_64_64 entry to 0x9d00 at the offset 0xc15.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0xc29.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ced at the offset 0xc3b.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xc45.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xc54.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xc5e.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xca5.
grub-install: info: relocating an R_X86_64_64 entry to 0x9d05 at the offset 0xcb1.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xcbe.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xcdb.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0xd09.
grub-install: info: relocating an R_X86_64_64 entry to 0x9d39 at the offset 0xd24.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0xd3d.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0xd7f.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0xd9c.
grub-install: info: relocating an R_X86_64_64 entry to 0x1152 at the offset 0xdb2.
grub-install: info: relocating an R_X86_64_64 entry to 0x29f5 at the offset 0xdd8.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a0 at the offset 0xde2.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0xe20.
grub-install: info: relocating an R_X86_64_64 entry to 0x91d0 at the offset 0xe7a.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xe9d.
grub-install: info: relocating an R_X86_64_64 entry to 0x9d61 at the offset 0xea9.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xeb6.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xed3.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0xf01.
grub-install: info: relocating an R_X86_64_64 entry to 0x9d93 at the offset 0xf1c.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0xf35.
grub-install: info: relocating an R_X86_64_64 entry to 0xe51 at the offset 0xf4e.
grub-install: info: relocating an R_X86_64_64 entry to 0xe430 at the offset 0xf62.
grub-install: info: relocating an R_X86_64_64 entry to 0xaba at the offset 0xf6c.
grub-install: info: relocating an R_X86_64_64 entry to 0x11ae at the offset 0xf87.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0xfee.
grub-install: info: relocating an R_X86_64_64 entry to 0x91b at the offset 0xff8.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0x1004.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0x109d.
grub-install: info: relocating an R_X86_64_64 entry to 0x11ae at the offset 0x10b3.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0x1106.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0x1115.
grub-install: info: relocating an R_X86_64_64 entry to 0x91b at the offset 0x111f.
grub-install: info: relocating an R_X86_64_64 entry to 0x8fa at the offset 0x113b.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4e0 at the offset 0x1147.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ea0 at the offset 0x1151.
grub-install: info: relocating an R_X86_64_64 entry to 0xc690 at the offset 0x116a.
grub-install: info: relocating an R_X86_64_64 entry to 0xaba at the offset 0x11cd.
grub-install: info: relocating an R_X86_64_64 entry to 0x1152 at the offset 0x11d7.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a0 at the offset 0x1204.
grub-install: info: relocating an R_X86_64_64 entry to 0x29f5 at the offset 0x1225.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1238.
grub-install: info: relocating an R_X86_64_64 entry to 0x8fa at the offset 0x12ac.
grub-install: info: relocating an R_X86_64_64 entry to 0x2355 at the offset 0x12d0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a0 at the offset 0x12f6.
grub-install: info: relocating an R_X86_64_64 entry to 0x1152 at the offset 0x132c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa34 at the offset 0x1383.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1396.
grub-install: info: relocating an R_X86_64_64 entry to 0x4f8a at the offset 0x13ae.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x13c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x55c0 at the offset 0x13f0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x140a.
grub-install: info: relocating an R_X86_64_64 entry to 0x1239 at the offset 0x141d.
grub-install: info: relocating an R_X86_64_64 entry to 0x9164 at the offset 0x142a.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ee6 at the offset 0x1443.
grub-install: info: relocating an R_X86_64_64 entry to 0x9db9 at the offset 0x1457.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x1461.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1479.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ee6 at the offset 0x1492.
grub-install: info: relocating an R_X86_64_64 entry to 0xa34 at the offset 0x14ad.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x14c6.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x15ec.
grub-install: info: relocating an R_X86_64_64 entry to 0x9dbf at the offset 0x1645.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e00 at the offset 0x1664.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x1670.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e02 at the offset 0x1684.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x181f.
grub-install: info: relocating an R_X86_64_64 entry to 0x43e at the offset 0x1832.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x1868.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x18a5.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0x18c3.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x18ec.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x192d.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1963.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x1981.
grub-install: info: relocating an R_X86_64_64 entry to 0x47c at the offset 0x1999.
grub-install: info: relocating an R_X86_64_64 entry to 0x1c16 at the offset 0x19bf.
grub-install: info: relocating an R_X86_64_64 entry to 0xb530 at the offset 0x19c9.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x19f9.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x1a24.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1a41.
grub-install: info: relocating an R_X86_64_64 entry to 0x422 at the offset 0x1a59.
grub-install: info: relocating an R_X86_64_64 entry to 0xb540 at the offset 0x1a6a.
grub-install: info: relocating an R_X86_64_64 entry to 0x1d5a at the offset 0x1a74.
grub-install: info: relocating an R_X86_64_64 entry to 0x2b82 at the offset 0x1a81.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1a8d.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x1aa9.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x1ab6.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1ac7.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x1aec.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e08 at the offset 0x1afe.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x1b0f.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x1b24.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x1b4b.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x1b59.
grub-install: info: relocating an R_X86_64_64 entry to 0x1a98 at the offset 0x1b78.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1b8a.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0x1bad.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e27 at the offset 0x1bc9.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x1be1.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x1bfb.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x1c05.
grub-install: info: relocating an R_X86_64_64 entry to 0x1a98 at the offset 0x1c5c.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0x1c66.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1c78.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1cb7.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1ce4.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e47 at the offset 0x1d1b.
grub-install: info: relocating an R_X86_64_64 entry to 0x1ff7 at the offset 0x1d27.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e52 at the offset 0x1da0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1dcf.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x1dee.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e63 at the offset 0x1e01.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x1e1f.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e5c at the offset 0x1e3c.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x1ed3.
grub-install: info: relocating an R_X86_64_64 entry to 0x18dd at the offset 0x1eea.
grub-install: info: relocating an R_X86_64_64 entry to 0xb550 at the offset 0x1f5c.
grub-install: info: relocating an R_X86_64_64 entry to 0x1d5a at the offset 0x1f66.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x1f7b.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e61 at the offset 0x1fd4.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e6d at the offset 0x1fe2.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e77 at the offset 0x1ff5.
grub-install: info: relocating an R_X86_64_64 entry to 0x9a00 at the offset 0x200e.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e88 at the offset 0x2023.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e94 at the offset 0x2036.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ea0 at the offset 0x204d.
grub-install: info: relocating an R_X86_64_64 entry to 0x9eb4 at the offset 0x2062.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ebd at the offset 0x2074.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ec7 at the offset 0x2083.
grub-install: info: relocating an R_X86_64_64 entry to 0x9efa at the offset 0x209c.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ed6 at the offset 0x20b4.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ee3 at the offset 0x20c9.
grub-install: info: relocating an R_X86_64_64 entry to 0x9eea at the offset 0x20de.
grub-install: info: relocating an R_X86_64_64 entry to 0x9eee at the offset 0x20f2.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x2104.
grub-install: info: relocating an R_X86_64_64 entry to 0x9eea at the offset 0x211e.
grub-install: info: relocating an R_X86_64_64 entry to 0x9eee at the offset 0x2134.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x2147.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ef2 at the offset 0x2176.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ef6 at the offset 0x21a1.
grub-install: info: relocating an R_X86_64_64 entry to 0x9a28 at the offset 0x21be.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f0b at the offset 0x21d3.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f1c at the offset 0x21ee.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f29 at the offset 0x2205.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f42 at the offset 0x221c.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f4e at the offset 0x2237.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f5a at the offset 0x224e.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f74 at the offset 0x2272.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f7d at the offset 0x2289.
grub-install: info: relocating an R_X86_64_64 entry to 0x9fa8 at the offset 0x22be.
grub-install: info: relocating an R_X86_64_64 entry to 0x9fd3 at the offset 0x230c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa016 at the offset 0x2388.
grub-install: info: relocating an R_X86_64_64 entry to 0xa035 at the offset 0x23ab.
grub-install: info: relocating an R_X86_64_64 entry to 0xa04a at the offset 0x23cf.
grub-install: info: relocating an R_X86_64_64 entry to 0xa05a at the offset 0x23e9.
grub-install: info: relocating an R_X86_64_64 entry to 0xa064 at the offset 0x23f8.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ab8 at the offset 0x2415.
grub-install: info: relocating an R_X86_64_64 entry to 0xa07a at the offset 0x242b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa0b3 at the offset 0x247e.
grub-install: info: relocating an R_X86_64_64 entry to 0xa0c5 at the offset 0x2497.
grub-install: info: relocating an R_X86_64_64 entry to 0x19e8 at the offset 0x24a1.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x24b6.
grub-install: info: relocating an R_X86_64_64 entry to 0x18dd at the offset 0x24e3.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x24f5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa0cb at the offset 0x2502.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x2513.
grub-install: info: relocating an R_X86_64_64 entry to 0xa0d5 at the offset 0x252c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa111 at the offset 0x256b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa133 at the offset 0x257b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa123 at the offset 0x2593.
grub-install: info: relocating an R_X86_64_64 entry to 0xa144 at the offset 0x25b9.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x25c6.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0x260e.
grub-install: info: relocating an R_X86_64_64 entry to 0x21ea at the offset 0x2688.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x2694.
grub-install: info: relocating an R_X86_64_64 entry to 0x3927 at the offset 0x269e.
grub-install: info: relocating an R_X86_64_64 entry to 0x31e7 at the offset 0x26aa.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x26b6.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x26d4.
grub-install: info: relocating an R_X86_64_64 entry to 0x134a at the offset 0x26e1.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x26ef.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e63 at the offset 0x2704.
grub-install: info: relocating an R_X86_64_64 entry to 0x16cc at the offset 0x271c.
grub-install: info: relocating an R_X86_64_64 entry to 0x2289 at the offset 0x272c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f8 at the offset 0x2747.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a99 at the offset 0x276b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe51 at the offset 0x2785.
grub-install: info: relocating an R_X86_64_64 entry to 0x3a28 at the offset 0x2792.
grub-install: info: relocating an R_X86_64_64 entry to 0x5ac at the offset 0x27bb.
grub-install: info: relocating an R_X86_64_64 entry to 0x6a2 at the offset 0x27e5.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x2849.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x285c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x28a6.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x28c3.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c44 at the offset 0x2913.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x2957.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x2976.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c44 at the offset 0x29c5.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x29e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2a16.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2a25.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x2a32.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2a45.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x2a52.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2a63.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c0 at the offset 0x2a76.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c8 at the offset 0x2a88.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d0 at the offset 0x2a9a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x2ac0.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0x2ae2.
grub-install: info: relocating an R_X86_64_64 entry to 0x2de4 at the offset 0x2b1c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x2b46.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0x2b7c.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2b8c.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d0 at the offset 0x2b96.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c8 at the offset 0x2ba0.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c0 at the offset 0x2baa.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2bb7.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2bd2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa176 at the offset 0x2be5.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x2bf6.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2c07.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x2c14.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2c23.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x2c2e.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d0 at the offset 0x2c3d.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c8 at the offset 0x2c47.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c0 at the offset 0x2c51.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2c5e.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2c6f.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x2c79.
grub-install: info: relocating an R_X86_64_64 entry to 0xa159 at the offset 0x2c88.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x2c97.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c0 at the offset 0x2cac.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x2cb9.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x2cc6.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2ce4.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x2cee.
grub-install: info: relocating an R_X86_64_64 entry to 0xa195 at the offset 0x2cff.
grub-install: info: relocating an R_X86_64_64 entry to 0xa1b5 at the offset 0x2d10.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x2d1c.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x2d34.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2d40.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2d53.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2d63.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x2d70.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c0 at the offset 0x2d81.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c8 at the offset 0x2d93.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d0 at the offset 0x2da5.
grub-install: info: relocating an R_X86_64_64 entry to 0x2b9c at the offset 0x2dc1.
grub-install: info: relocating an R_X86_64_64 entry to 0x5d3 at the offset 0x2dcb.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c6e at the offset 0x2df9.
grub-install: info: relocating an R_X86_64_64 entry to 0xa1dd at the offset 0x2e12.
grub-install: info: relocating an R_X86_64_64 entry to 0x2de4 at the offset 0x2e3c.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c44 at the offset 0x2e54.
grub-install: info: relocating an R_X86_64_64 entry to 0xa1f4 at the offset 0x2ea5.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x2eb1.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x2f17.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c6e at the offset 0x3052.
grub-install: info: relocating an R_X86_64_64 entry to 0xa20a at the offset 0x306e.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x3078.
grub-install: info: relocating an R_X86_64_64 entry to 0x3f86 at the offset 0x308a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa23f at the offset 0x30aa.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c44 at the offset 0x30c2.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x30dd.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x30f8.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x323a.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x3252.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x3269.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x3278.
grub-install: info: relocating an R_X86_64_64 entry to 0x43e at the offset 0x3298.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x32a9.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x32b7.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x32ed.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x3311.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x3323.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x3343.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x3352.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x336a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3741 at the offset 0x337a.
grub-install: info: relocating an R_X86_64_64 entry to 0x1db8 at the offset 0x3388.
grub-install: info: relocating an R_X86_64_64 entry to 0x1db8 at the offset 0x339c.
grub-install: info: relocating an R_X86_64_64 entry to 0x3741 at the offset 0x33b0.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x33c5.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x33d6.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e9 at the offset 0x33ff.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e8 at the offset 0x340a.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x341e.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x342c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x3441.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x3454.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ae0 at the offset 0x34af.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x34c4.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x34d5.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x34e2.
grub-install: info: relocating an R_X86_64_64 entry to 0x422 at the offset 0x3509.
grub-install: info: relocating an R_X86_64_64 entry to 0x1db8 at the offset 0x352f.
grub-install: info: relocating an R_X86_64_64 entry to 0xa251 at the offset 0x3540.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x354f.
grub-install: info: relocating an R_X86_64_64 entry to 0x18540 at the offset 0x355b.
grub-install: info: relocating an R_X86_64_64 entry to 0xb560 at the offset 0x356b.
grub-install: info: relocating an R_X86_64_64 entry to 0x18550 at the offset 0x3575.
grub-install: info: relocating an R_X86_64_64 entry to 0xb578 at the offset 0x3581.
grub-install: info: relocating an R_X86_64_64 entry to 0xb560 at the offset 0x3590.
grub-install: info: relocating an R_X86_64_64 entry to 0x18540 at the offset 0x359a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7276 at the offset 0x35a4.
grub-install: info: relocating an R_X86_64_64 entry to 0xb560 at the offset 0x35b2.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x35c2.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5a0 at the offset 0x35d2.
grub-install: info: relocating an R_X86_64_64 entry to 0x18538 at the offset 0x35dc.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5b8 at the offset 0x35e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5a0 at the offset 0x35f7.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x3601.
grub-install: info: relocating an R_X86_64_64 entry to 0x7276 at the offset 0x360c.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5a0 at the offset 0x3618.
grub-install: info: relocating an R_X86_64_64 entry to 0x7290 at the offset 0x362b.
grub-install: info: relocating an R_X86_64_64 entry to 0xb560 at the offset 0x3635.
grub-install: info: relocating an R_X86_64_64 entry to 0xb560 at the offset 0x3641.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5a0 at the offset 0x364d.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5a0 at the offset 0x365c.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d8 at the offset 0x3679.
grub-install: info: relocating an R_X86_64_64 entry to 0xe400 at the offset 0x3686.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d8 at the offset 0x36ea.
grub-install: info: relocating an R_X86_64_64 entry to 0x7cd7 at the offset 0x3730.
grub-install: info: relocating an R_X86_64_64 entry to 0xe400 at the offset 0x3749.
grub-install: info: relocating an R_X86_64_64 entry to 0x3a67 at the offset 0x3753.
grub-install: info: relocating an R_X86_64_64 entry to 0x4187 at the offset 0x375d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa26e at the offset 0x3769.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x3775.
grub-install: info: relocating an R_X86_64_64 entry to 0xa27b at the offset 0x378b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x379a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa290 at the offset 0x37c9.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x37d5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa2a2 at the offset 0x37ea.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x37f6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa2c3 at the offset 0x3805.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x382b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x3870.
grub-install: info: relocating an R_X86_64_64 entry to 0xa2db at the offset 0x38b9.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x38c5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa2ec at the offset 0x38de.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x38ea.
grub-install: info: relocating an R_X86_64_64 entry to 0x4e56 at the offset 0x39e9.
grub-install: info: relocating an R_X86_64_64 entry to 0xa30d at the offset 0x3a00.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x3a11.
grub-install: info: relocating an R_X86_64_64 entry to 0x3c27 at the offset 0x3a2a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3c27 at the offset 0x3a3f.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0x3a5f.
grub-install: info: relocating an R_X86_64_64 entry to 0x3b7f at the offset 0x3a7f.
grub-install: info: relocating an R_X86_64_64 entry to 0xa2ec at the offset 0x3ace.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x3ada.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x3bb4.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x3bc1.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x3c22.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x3c8b.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x3cd7.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x3cf0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3b7f at the offset 0x3d05.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x3d30.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x3d52.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x3d65.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6e0 at the offset 0x3d7d.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6e0 at the offset 0x3d8c.
grub-install: info: relocating an R_X86_64_64 entry to 0x417b at the offset 0x3d9d.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x3dc2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa31b at the offset 0x3e0a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe410 at the offset 0x3e23.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x3e3e.
grub-install: info: relocating an R_X86_64_64 entry to 0x7290 at the offset 0x3ecd.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x3edc.
grub-install: info: relocating an R_X86_64_64 entry to 0xa31e at the offset 0x3eed.
grub-install: info: relocating an R_X86_64_64 entry to 0xa31c at the offset 0x3ef7.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x3f04.
grub-install: info: relocating an R_X86_64_64 entry to 0xa31f at the offset 0x3f0e.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x3f28.
grub-install: info: relocating an R_X86_64_64 entry to 0xa325 at the offset 0x3f32.
grub-install: info: relocating an R_X86_64_64 entry to 0x4322 at the offset 0x3f51.
grub-install: info: relocating an R_X86_64_64 entry to 0x49da at the offset 0x3f5b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa333 at the offset 0x3f67.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x3f71.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x3f7d.
grub-install: info: relocating an R_X86_64_64 entry to 0x69dd at the offset 0x3f94.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x3fa3.
grub-install: info: relocating an R_X86_64_64 entry to 0x47bb at the offset 0x3fb9.
grub-install: info: relocating an R_X86_64_64 entry to 0x7033 at the offset 0x3fd4.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x3fec.
grub-install: info: relocating an R_X86_64_64 entry to 0xa335 at the offset 0x400f.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4020.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4031.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4041.
grub-install: info: relocating an R_X86_64_64 entry to 0xa32b at the offset 0x4057.
grub-install: info: relocating an R_X86_64_64 entry to 0xa346 at the offset 0x4064.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x4070.
grub-install: info: relocating an R_X86_64_64 entry to 0x42e7 at the offset 0x4085.
grub-install: info: relocating an R_X86_64_64 entry to 0xa333 at the offset 0x4097.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x40a1.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x40ad.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x40be.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x40c9.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x40d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xa35f at the offset 0x40f2.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4103.
grub-install: info: relocating an R_X86_64_64 entry to 0x621a at the offset 0x4121.
grub-install: info: relocating an R_X86_64_64 entry to 0x631d at the offset 0x412d.
grub-install: info: relocating an R_X86_64_64 entry to 0x5792 at the offset 0x4141.
grub-install: info: relocating an R_X86_64_64 entry to 0xa35f at the offset 0x4155.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4166.
grub-install: info: relocating an R_X86_64_64 entry to 0x6618 at the offset 0x4173.
grub-install: info: relocating an R_X86_64_64 entry to 0x669c at the offset 0x418d.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x4197.
grub-install: info: relocating an R_X86_64_64 entry to 0xa375 at the offset 0x41b3.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x41bf.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x41de.
grub-install: info: relocating an R_X86_64_64 entry to 0xa37c at the offset 0x41f8.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4209.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x421f.
grub-install: info: relocating an R_X86_64_64 entry to 0xa38e at the offset 0x4238.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3ab at the offset 0x4242.
grub-install: info: relocating an R_X86_64_64 entry to 0x4584 at the offset 0x424c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3ba at the offset 0x4256.
grub-install: info: relocating an R_X86_64_64 entry to 0x41be at the offset 0x4260.
grub-install: info: relocating an R_X86_64_64 entry to 0x41be at the offset 0x4278.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3be at the offset 0x4285.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3de at the offset 0x428f.
grub-install: info: relocating an R_X86_64_64 entry to 0x454f at the offset 0x4299.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3e5 at the offset 0x42a3.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3eb at the offset 0x42b2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa402 at the offset 0x42bc.
grub-install: info: relocating an R_X86_64_64 entry to 0x4342 at the offset 0x42c6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa408 at the offset 0x42d0.
grub-install: info: relocating an R_X86_64_64 entry to 0xa40b at the offset 0x42e2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa41c at the offset 0x42ed.
grub-install: info: relocating an R_X86_64_64 entry to 0x44ec at the offset 0x42f7.
grub-install: info: relocating an R_X86_64_64 entry to 0xa423 at the offset 0x4301.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x4313.
grub-install: info: relocating an R_X86_64_64 entry to 0x91d0 at the offset 0x433a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4351.
grub-install: info: relocating an R_X86_64_64 entry to 0xa42a at the offset 0x4366.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x4372.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4385.
grub-install: info: relocating an R_X86_64_64 entry to 0xa430 at the offset 0x43c8.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x43d2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa430 at the offset 0x43eb.
grub-install: info: relocating an R_X86_64_64 entry to 0xa435 at the offset 0x43f5.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4406.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x441b.
grub-install: info: relocating an R_X86_64_64 entry to 0x4f8a at the offset 0x443a.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6e8 at the offset 0x444e.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4460.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4488.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ee6 at the offset 0x44a9.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x44c1.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x44d6.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x44e1.
grub-install: info: relocating an R_X86_64_64 entry to 0x47bb at the offset 0x4514.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x452c.
grub-install: info: relocating an R_X86_64_64 entry to 0x470c at the offset 0x4546.
grub-install: info: relocating an R_X86_64_64 entry to 0x9164 at the offset 0x4558.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4565.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x4574.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4585.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x45c4.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x45f7.
grub-install: info: relocating an R_X86_64_64 entry to 0x48ed at the offset 0x461c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe440 at the offset 0x4675.
grub-install: info: relocating an R_X86_64_64 entry to 0xe440 at the offset 0x46d3.
grub-install: info: relocating an R_X86_64_64 entry to 0xe440 at the offset 0x4704.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4744.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x4776.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x478a.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x47a1.
grub-install: info: relocating an R_X86_64_64 entry to 0x4a48 at the offset 0x47f0.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x480d.
grub-install: info: relocating an R_X86_64_64 entry to 0x4aa6 at the offset 0x4827.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x483d.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x48a9.
grub-install: info: relocating an R_X86_64_64 entry to 0x4afd at the offset 0x48c6.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x48d5.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x48e9.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4903.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x4951.
grub-install: info: relocating an R_X86_64_64 entry to 0x684a at the offset 0x499d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa462 at the offset 0x49a9.
grub-install: info: relocating an R_X86_64_64 entry to 0xa44d at the offset 0x49b6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa45d at the offset 0x49c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x49d1.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x49de.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x49ef.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x4a08.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4a5a.
grub-install: info: relocating an R_X86_64_64 entry to 0x183c8 at the offset 0x4a65.
grub-install: info: relocating an R_X86_64_64 entry to 0xe440 at the offset 0x4a70.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x4aa2.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x4ab7.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x4ac1.
grub-install: info: relocating an R_X86_64_64 entry to 0xa46e at the offset 0x4aec.
grub-install: info: relocating an R_X86_64_64 entry to 0xa45d at the offset 0x4af6.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x4b05.
grub-install: info: relocating an R_X86_64_64 entry to 0xa462 at the offset 0x4b17.
grub-install: info: relocating an R_X86_64_64 entry to 0x417b at the offset 0x4b3b.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4b45.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6f0 at the offset 0x4b51.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4b6c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa47d at the offset 0x4b93.
grub-install: info: relocating an R_X86_64_64 entry to 0xa45d at the offset 0x4b9d.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x4bae.
grub-install: info: relocating an R_X86_64_64 entry to 0xa462 at the offset 0x4bbf.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x4bd7.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x4c2d.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x4c55.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x4c6a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x4c7e.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x4c9d.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4ca7.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4cd7.
grub-install: info: relocating an R_X86_64_64 entry to 0xa48e at the offset 0x4cf0.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4d03.
grub-install: info: relocating an R_X86_64_64 entry to 0x8fd0 at the offset 0x4d24.
grub-install: info: relocating an R_X86_64_64 entry to 0xa4bc at the offset 0x4d39.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4d48.
grub-install: info: relocating an R_X86_64_64 entry to 0x417b at the offset 0x4d56.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6f0 at the offset 0x4d62.
grub-install: info: relocating an R_X86_64_64 entry to 0x4e56 at the offset 0x4d80.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6f0 at the offset 0x4d91.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4da8.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4db4.
grub-install: info: relocating an R_X86_64_64 entry to 0x684a at the offset 0x4dc7.
grub-install: info: relocating an R_X86_64_64 entry to 0xa4ce at the offset 0x4dd6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa45d at the offset 0x4de0.
grub-install: info: relocating an R_X86_64_64 entry to 0xa462 at the offset 0x4def.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x4df9.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x4e08.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ee6 at the offset 0x4e17.
grub-install: info: relocating an R_X86_64_64 entry to 0xa4e4 at the offset 0x4e2a.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4e3b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa4f8 at the offset 0x4ebc.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4ecd.
grub-install: info: relocating an R_X86_64_64 entry to 0xa526 at the offset 0x4f1b.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4f2c.
grub-install: info: relocating an R_X86_64_64 entry to 0x684a at the offset 0x4f3c.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x4f4a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa554 at the offset 0x4f57.
grub-install: info: relocating an R_X86_64_64 entry to 0xa45d at the offset 0x4f61.
grub-install: info: relocating an R_X86_64_64 entry to 0xa462 at the offset 0x4f70.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x4f7a.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x4f87.
grub-install: info: relocating an R_X86_64_64 entry to 0x4bc1 at the offset 0x4fc8.
grub-install: info: relocating an R_X86_64_64 entry to 0x4a48 at the offset 0x5008.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x505d.
grub-install: info: relocating an R_X86_64_64 entry to 0x4aa6 at the offset 0x507c.
grub-install: info: relocating an R_X86_64_64 entry to 0x4afd at the offset 0x50c4.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x5189.
grub-install: info: relocating an R_X86_64_64 entry to 0x4bc1 at the offset 0x51a3.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x51ec.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x51f6.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x522a.
grub-install: info: relocating an R_X86_64_64 entry to 0x55e8 at the offset 0x5299.
grub-install: info: relocating an R_X86_64_64 entry to 0xa57c at the offset 0x52b3.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x52c5.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x52d7.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x530c.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x5324.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x532f.
grub-install: info: relocating an R_X86_64_64 entry to 0xc710 at the offset 0x5372.
grub-install: info: relocating an R_X86_64_64 entry to 0x5792 at the offset 0x53a4.
grub-install: info: relocating an R_X86_64_64 entry to 0x57cf at the offset 0x53e1.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x5436.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x5440.
grub-install: info: relocating an R_X86_64_64 entry to 0xc710 at the offset 0x546a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x547b.
grub-install: info: relocating an R_X86_64_64 entry to 0x580c at the offset 0x54cc.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x54e6.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x54fa.
grub-install: info: relocating an R_X86_64_64 entry to 0xa593 at the offset 0x5532.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5ad at the offset 0x553c.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x5548.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5b5 at the offset 0x5563.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5bf at the offset 0x5578.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5e0 at the offset 0x55a6.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x55b7.
grub-install: info: relocating an R_X86_64_64 entry to 0x744 at the offset 0x55c8.
grub-install: info: relocating an R_X86_64_64 entry to 0xa603 at the offset 0x55e1.
grub-install: info: relocating an R_X86_64_64 entry to 0xa62a at the offset 0x5608.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x5619.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x562f.
grub-install: info: relocating an R_X86_64_64 entry to 0xa644 at the offset 0x5651.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5ad at the offset 0x565d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5b5 at the offset 0x566c.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x5676.
grub-install: info: relocating an R_X86_64_64 entry to 0xa656 at the offset 0x5683.
grub-install: info: relocating an R_X86_64_64 entry to 0x5626 at the offset 0x5690.
grub-install: info: relocating an R_X86_64_64 entry to 0xa666 at the offset 0x56a6.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x56b5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa67b at the offset 0x56d1.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x56db.
grub-install: info: relocating an R_X86_64_64 entry to 0xa689 at the offset 0x56f4.
grub-install: info: relocating an R_X86_64_64 entry to 0xa698 at the offset 0x570d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6a7 at the offset 0x571e.
grub-install: info: relocating an R_X86_64_64 entry to 0x5626 at the offset 0x572b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6b0 at the offset 0x573c.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x574b.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x5760.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6c5 at the offset 0x5775.
grub-install: info: relocating an R_X86_64_64 entry to 0x5626 at the offset 0x5782.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x579b.
grub-install: info: relocating an R_X86_64_64 entry to 0x631d at the offset 0x57ba.
grub-install: info: relocating an R_X86_64_64 entry to 0x5792 at the offset 0x57e1.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x57f2.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x5802.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x5820.
grub-install: info: relocating an R_X86_64_64 entry to 0x3c27 at the offset 0x588d.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x58d0.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x58e3.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x592d.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0x5940.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6ce at the offset 0x59c4.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x59d5.
grub-install: info: relocating an R_X86_64_64 entry to 0x9b40 at the offset 0x5a4b.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x5a8f.
grub-install: info: relocating an R_X86_64_64 entry to 0xc710 at the offset 0x5aa2.
grub-install: info: relocating an R_X86_64_64 entry to 0x56d3 at the offset 0x5b37.
grub-install: info: relocating an R_X86_64_64 entry to 0x56d3 at the offset 0x5b85.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x5b94.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x5ba3.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6de at the offset 0x5bad.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6ec at the offset 0x5bd4.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6fa at the offset 0x5c22.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x5c33.
grub-install: info: relocating an R_X86_64_64 entry to 0x773 at the offset 0x5c5f.
grub-install: info: relocating an R_X86_64_64 entry to 0x580c at the offset 0x5cbc.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x5ce7.
grub-install: info: relocating an R_X86_64_64 entry to 0xa713 at the offset 0x5cf5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5ad at the offset 0x5cff.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5b5 at the offset 0x5d0e.
grub-install: info: relocating an R_X86_64_64 entry to 0xa72f at the offset 0x5d20.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5ad at the offset 0x5d2a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5b5 at the offset 0x5d39.
grub-install: info: relocating an R_X86_64_64 entry to 0xa740 at the offset 0x5d4b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5ad at the offset 0x5d55.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5b5 at the offset 0x5d64.
grub-install: info: relocating an R_X86_64_64 entry to 0x5696 at the offset 0x5d73.
grub-install: info: relocating an R_X86_64_64 entry to 0xa753 at the offset 0x5d8b.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x5d9c.
grub-install: info: relocating an R_X86_64_64 entry to 0x5926 at the offset 0x5dda.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x5e03.
grub-install: info: relocating an R_X86_64_64 entry to 0x2117 at the offset 0x5e1e.
grub-install: info: relocating an R_X86_64_64 entry to 0xa769 at the offset 0x5e41.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x5e52.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b50 at the offset 0x5e60.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x5e7a.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b05 at the offset 0x5e94.
grub-install: info: relocating an R_X86_64_64 entry to 0x6a68 at the offset 0x5eab.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b05 at the offset 0x5ec0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x5ed1.
grub-install: info: relocating an R_X86_64_64 entry to 0x61d4 at the offset 0x5ee9.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x5efd.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x5f21.
grub-install: info: relocating an R_X86_64_64 entry to 0xa794 at the offset 0x5f30.
grub-install: info: relocating an R_X86_64_64 entry to 0x55e8 at the offset 0x5f45.
grub-install: info: relocating an R_X86_64_64 entry to 0xa794 at the offset 0x5f62.
grub-install: info: relocating an R_X86_64_64 entry to 0xa79b at the offset 0x5f6c.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x5f7d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7b3 at the offset 0x5f96.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x5fa0.
grub-install: info: relocating an R_X86_64_64 entry to 0x621a at the offset 0x5fb7.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x5fc9.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x5fe1.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7c8 at the offset 0x5ff4.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x6005.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x601d.
grub-install: info: relocating an R_X86_64_64 entry to 0x580c at the offset 0x6027.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x6041.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x6081.
grub-install: info: relocating an R_X86_64_64 entry to 0xb630 at the offset 0x608d.
grub-install: info: relocating an R_X86_64_64 entry to 0x645b at the offset 0x60c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x60f6.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x6119.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x612f.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x614b.
grub-install: info: relocating an R_X86_64_64 entry to 0xb630 at the offset 0x616f.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x61c7.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x61dd.
grub-install: info: relocating an R_X86_64_64 entry to 0x645b at the offset 0x61ec.
grub-install: info: relocating an R_X86_64_64 entry to 0x645b at the offset 0x621e.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7d9 at the offset 0x6247.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x6251.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x627a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x62a0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb630 at the offset 0x62bd.
grub-install: info: relocating an R_X86_64_64 entry to 0x645b at the offset 0x6335.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7d9 at the offset 0x634b.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x6358.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6367.
grub-install: info: relocating an R_X86_64_64 entry to 0x645b at the offset 0x638b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7d9 at the offset 0x63a1.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x63ae.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x63db.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0x6415.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x642e.
grub-install: info: relocating an R_X86_64_64 entry to 0x88fd at the offset 0x6438.
grub-install: info: relocating an R_X86_64_64 entry to 0xd770 at the offset 0x644b.
grub-install: info: relocating an R_X86_64_64 entry to 0xd780 at the offset 0x645c.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x6473.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x647f.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x648f.
grub-install: info: relocating an R_X86_64_64 entry to 0xd770 at the offset 0x649a.
grub-install: info: relocating an R_X86_64_64 entry to 0xd770 at the offset 0x64a5.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1a8 at the offset 0x64b5.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x64c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x64cc.
grub-install: info: relocating an R_X86_64_64 entry to 0xd770 at the offset 0x64d7.
grub-install: info: relocating an R_X86_64_64 entry to 0xd780 at the offset 0x64e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xd770 at the offset 0x64f1.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x6509.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x651b.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x6525.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6539.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6547.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7da at the offset 0x6556.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0x6560.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x656c.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x6579.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d4 at the offset 0x6586.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d4 at the offset 0x6591.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x659b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1a8 at the offset 0x65ab.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7e6 at the offset 0x65ba.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x65c6.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1a8 at the offset 0x65d3.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x65f2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa80e at the offset 0x6608.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x6617.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x662a.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x6650.
grub-install: info: relocating an R_X86_64_64 entry to 0xa822 at the offset 0x667e.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x668f.
grub-install: info: relocating an R_X86_64_64 entry to 0x184e0 at the offset 0x66d1.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x6725.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x6734.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6744.
grub-install: info: relocating an R_X86_64_64 entry to 0x69dd at the offset 0x6754.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x676b.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x6791.
grub-install: info: relocating an R_X86_64_64 entry to 0x47bb at the offset 0x67a9.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x67bb.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x67d5.
grub-install: info: relocating an R_X86_64_64 entry to 0xb640 at the offset 0x67ff.
grub-install: info: relocating an R_X86_64_64 entry to 0x7033 at the offset 0x6812.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x6843.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6858.
grub-install: info: relocating an R_X86_64_64 entry to 0x18510 at the offset 0x6862.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b05 at the offset 0x6899.
grub-install: info: relocating an R_X86_64_64 entry to 0x184f0 at the offset 0x68aa.
grub-install: info: relocating an R_X86_64_64 entry to 0x18510 at the offset 0x68b4.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x68be.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x68cf.
grub-install: info: relocating an R_X86_64_64 entry to 0x184f0 at the offset 0x68e2.
grub-install: info: relocating an R_X86_64_64 entry to 0x18510 at the offset 0x68ec.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x68f6.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x6907.
grub-install: info: relocating an R_X86_64_64 entry to 0xa847 at the offset 0x692a.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x693c.
grub-install: info: relocating an R_X86_64_64 entry to 0x5270 at the offset 0x6964.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x6a5c.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x6aba.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0x6aff.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6b0e.
grub-install: info: relocating an R_X86_64_64 entry to 0xa86b at the offset 0x6b20.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x6b31.
grub-install: info: relocating an R_X86_64_64 entry to 0x81c5 at the offset 0x6b58.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6b6c.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0x6b9a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa882 at the offset 0x6bca.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x6bdb.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x6c0a.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6c18.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b8 at the offset 0x6c46.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x6c50.
grub-install: info: relocating an R_X86_64_64 entry to 0xa89b at the offset 0x6c68.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8ac at the offset 0x6c72.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8af at the offset 0x6c81.
grub-install: info: relocating an R_X86_64_64 entry to 0x6d57 at the offset 0x6c90.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8b9 at the offset 0x6c9a.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6caa.
grub-install: info: relocating an R_X86_64_64 entry to 0x684a at the offset 0x6cbd.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8bb at the offset 0x6ccf.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8ac at the offset 0x6cd9.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8af at the offset 0x6ce8.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x6cf5.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6d00.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6d1a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b0 at the offset 0x6d2d.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6d41.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6d58.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b8 at the offset 0x6d64.
grub-install: info: relocating an R_X86_64_64 entry to 0x6d57 at the offset 0x6d73.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8b9 at the offset 0x6d7d.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6d8e.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6d9b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6da9.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6dbf.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6dca.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6dd7.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b0 at the offset 0x6de1.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6df4.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6dff.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8d1 at the offset 0x6e1d.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x6e2e.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x6e46.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x6ec8.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c36 at the offset 0x6ee8.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x6ef8.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x6f05.
grub-install: info: relocating an R_X86_64_64 entry to 0x51a at the offset 0x6f23.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x6f37.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x6f5e.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x6f9f.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c8 at the offset 0x6fb2.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0x6fbe.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x6fd6.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c8 at the offset 0x6fe9.
grub-install: info: relocating an R_X86_64_64 entry to 0x993e at the offset 0x7012.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x7020.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x7057.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8ef at the offset 0x7061.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x706b.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x7077.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0x7086.
grub-install: info: relocating an R_X86_64_64 entry to 0x61d4 at the offset 0x70a3.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x70b2.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x70c9.
grub-install: info: relocating an R_X86_64_64 entry to 0x72bf at the offset 0x7122.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8f2 at the offset 0x712c.
grub-install: info: relocating an R_X86_64_64 entry to 0x6728 at the offset 0x7136.
grub-install: info: relocating an R_X86_64_64 entry to 0x2aeb at the offset 0x714a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8ee at the offset 0x7177.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8f7 at the offset 0x7181.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x718b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8fe at the offset 0x71ab.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x71b5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8fe at the offset 0x71c1.
grub-install: info: relocating an R_X86_64_64 entry to 0x6788 at the offset 0x71cb.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x71da.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a99 at the offset 0x71fd.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c36 at the offset 0x721c.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x7244.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x72aa.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x72c2.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x72dd.
grub-install: info: relocating an R_X86_64_64 entry to 0xa906 at the offset 0x7317.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0x7321.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x7342.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8ee at the offset 0x7356.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8f7 at the offset 0x7367.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x7373.
grub-install: info: relocating an R_X86_64_64 entry to 0xa911 at the offset 0x738a.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x7394.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x73a3.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8f2 at the offset 0x73b2.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x73bc.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x73cb.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0x73dc.
grub-install: info: relocating an R_X86_64_64 entry to 0x6788 at the offset 0x73e6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8f2 at the offset 0x73f2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa911 at the offset 0x73fe.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x740a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x741c.
grub-install: info: relocating an R_X86_64_64 entry to 0x4632 at the offset 0x7426.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c8 at the offset 0x7432.
grub-install: info: relocating an R_X86_64_64 entry to 0x8f62 at the offset 0x7444.
grub-install: info: relocating an R_X86_64_64 entry to 0xa918 at the offset 0x7450.
grub-install: info: relocating an R_X86_64_64 entry to 0x631d at the offset 0x745a.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0x7466.
grub-install: info: relocating an R_X86_64_64 entry to 0xe410 at the offset 0x7474.
grub-install: info: relocating an R_X86_64_64 entry to 0xa918 at the offset 0x747e.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x7487.
grub-install: info: relocating an R_X86_64_64 entry to 0x7242 at the offset 0x7494.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x74af.
grub-install: info: relocating an R_X86_64_64 entry to 0x9750 at the offset 0x74d9.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c36 at the offset 0x74ef.
grub-install: info: relocating an R_X86_64_64 entry to 0xa91f at the offset 0x7507.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x7513.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x7525.
grub-install: info: relocating an R_X86_64_64 entry to 0xa91f at the offset 0x753c.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x7548.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x756f.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x75d6.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0x75e4.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0x76d3.
grub-install: info: relocating an R_X86_64_64 entry to 0x7ad0 at the offset 0x771a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7ad0 at the offset 0x778b.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x783a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x7858.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x7879.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x7895.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x78a7.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x78c7.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0x7946.
grub-install: info: relocating an R_X86_64_64 entry to 0x7cd7 at the offset 0x79f2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa924 at the offset 0x7a03.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x7a14.
grub-install: info: relocating an R_X86_64_64 entry to 0xa939 at the offset 0x7a45.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x7a56.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x7b84.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x7b9c.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0x7bcc.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0x7bd6.
grub-install: info: relocating an R_X86_64_64 entry to 0x9b68 at the offset 0x7d20.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0x7dc7.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0x7e6d.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0x7eb7.
grub-install: info: relocating an R_X86_64_64 entry to 0x7cd7 at the offset 0x8010.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x804d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa94d at the offset 0x8190.
grub-install: info: relocating an R_X86_64_64 entry to 0x7e79 at the offset 0x826d.
grub-install: info: relocating an R_X86_64_64 entry to 0x81d1 at the offset 0x8277.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1d0 at the offset 0x8288.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1d0 at the offset 0x82a9.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x82c6.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1d0 at the offset 0x82dc.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x82e5.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2cc at the offset 0x82f0.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2cd at the offset 0x82f9.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2ce at the offset 0x8302.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2cf at the offset 0x830d.
grub-install: info: relocating an R_X86_64_64 entry to 0x795e at the offset 0x832e.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x833a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1d0 at the offset 0x8349.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x835b.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0x83b0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8666 at the offset 0x83c4.
grub-install: info: relocating an R_X86_64_64 entry to 0x8666 at the offset 0x8413.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x8426.
grub-install: info: relocating an R_X86_64_64 entry to 0xa954 at the offset 0x843d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa95a at the offset 0x846a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7b0e at the offset 0x8477.
grub-install: info: relocating an R_X86_64_64 entry to 0xa95e at the offset 0x8499.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x84a3.
grub-install: info: relocating an R_X86_64_64 entry to 0x8666 at the offset 0x84d8.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x84e4.
grub-install: info: relocating an R_X86_64_64 entry to 0x7e79 at the offset 0x850b.
grub-install: info: relocating an R_X86_64_64 entry to 0x81d1 at the offset 0x853c.
grub-install: info: relocating an R_X86_64_64 entry to 0x795e at the offset 0x854d.
grub-install: info: relocating an R_X86_64_64 entry to 0x88fd at the offset 0x85a3.
grub-install: info: relocating an R_X86_64_64 entry to 0x7e79 at the offset 0x85b9.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x85e1.
grub-install: info: relocating an R_X86_64_64 entry to 0x81d1 at the offset 0x8603.
grub-install: info: relocating an R_X86_64_64 entry to 0x795e at the offset 0x861a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x862b.
grub-install: info: relocating an R_X86_64_64 entry to 0x89b2 at the offset 0x868d.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x869f.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0x86e2.
grub-install: info: relocating an R_X86_64_64 entry to 0x8666 at the offset 0x86f6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa966 at the offset 0x8704.
grub-install: info: relocating an R_X86_64_64 entry to 0x18540 at the offset 0x8710.
grub-install: info: relocating an R_X86_64_64 entry to 0xa970 at the offset 0x8720.
grub-install: info: relocating an R_X86_64_64 entry to 0x991f at the offset 0x872e.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e7e at the offset 0x873a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x8783.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c36 at the offset 0x87a0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x87b5.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x87eb.
grub-install: info: relocating an R_X86_64_64 entry to 0xb6a0 at the offset 0x8841.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0x8876.
grub-install: info: relocating an R_X86_64_64 entry to 0x8c1a at the offset 0x895d.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b44 at the offset 0x8967.
grub-install: info: relocating an R_X86_64_64 entry to 0x8bd0 at the offset 0x8998.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b44 at the offset 0x89a7.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0x89e0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b44 at the offset 0x8a4e.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b44 at the offset 0x8a64.
grub-install: info: relocating an R_X86_64_64 entry to 0x8bd0 at the offset 0x8a83.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x8ab9.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x8ade.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x8b07.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8b12.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b60 at the offset 0x8b65.
grub-install: info: relocating an R_X86_64_64 entry to 0x94ce at the offset 0x8b70.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b60 at the offset 0x8b9d.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x8bae.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8bc1.
grub-install: info: relocating an R_X86_64_64 entry to 0x81c5 at the offset 0x8c12.
grub-install: info: relocating an R_X86_64_64 entry to 0x18530 at the offset 0x8c24.
grub-install: info: relocating an R_X86_64_64 entry to 0x9471 at the offset 0x8c65.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8c75.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a4d at the offset 0x8c98.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x8cc0.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8cd8.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8ce8.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x8d48.
grub-install: info: relocating an R_X86_64_64 entry to 0x18530 at the offset 0x8d67.
grub-install: info: relocating an R_X86_64_64 entry to 0x939d at the offset 0x8d95.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8daa.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x8dd8.
grub-install: info: relocating an R_X86_64_64 entry to 0xa988 at the offset 0x8df8.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x8e02.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x8e34.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0x8e59.
grub-install: info: relocating an R_X86_64_64 entry to 0xa989 at the offset 0x8e63.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x8e72.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x8e83.
grub-install: info: relocating an R_X86_64_64 entry to 0x91d0 at the offset 0x8f2c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa98c at the offset 0x8f41.
grub-install: info: relocating an R_X86_64_64 entry to 0xa9c8 at the offset 0x8f55.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x8f5f.
grub-install: info: relocating an R_X86_64_64 entry to 0xa9be at the offset 0x8f71.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x8f80.
grub-install: info: relocating an R_X86_64_64 entry to 0x9304 at the offset 0x8fc0.
grub-install: info: relocating an R_X86_64_64 entry to 0x18530 at the offset 0x9024.
grub-install: info: relocating an R_X86_64_64 entry to 0x939d at the offset 0x9036.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x904d.
grub-install: info: relocating an R_X86_64_64 entry to 0x9304 at the offset 0x9086.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x909b.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x90bb.
grub-install: info: relocating an R_X86_64_64 entry to 0x8cd3 at the offset 0x90d1.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x911c.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x914e.
grub-install: info: relocating an R_X86_64_64 entry to 0xe410 at the offset 0x9173.
grub-install: info: relocating an R_X86_64_64 entry to 0x7242 at the offset 0x9183.
grub-install: info: relocating an R_X86_64_64 entry to 0xa9d9 at the offset 0x91ae.
grub-install: info: relocating an R_X86_64_64 entry to 0x8775 at the offset 0x91ba.
grub-install: info: relocating an R_X86_64_64 entry to 0xe410 at the offset 0x91c6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa9f0 at the offset 0x91d0.
grub-install: info: relocating an R_X86_64_64 entry to 0xa9f5 at the offset 0x91e4.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x91f0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x9201.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x9216.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa0e at the offset 0x9228.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa0b at the offset 0x9235.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x924a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2d0 at the offset 0x9261.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0x926b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2d0 at the offset 0x928c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2d0 at the offset 0x92b1.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x92db.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x92e7.
grub-install: info: relocating an R_X86_64_64 entry to 0x991f at the offset 0x92f3.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa1c at the offset 0x930d.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x9317.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x9323.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2d0 at the offset 0x932f.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x9339.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa1e at the offset 0x9353.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x935f.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0x936f.
grub-install: info: relocating an R_X86_64_64 entry to 0x9625 at the offset 0x9379.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x938f.
grub-install: info: relocating an R_X86_64_64 entry to 0x94ce at the offset 0x93af.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x93c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x97cc at the offset 0x940a.
grub-install: info: relocating an R_X86_64_64 entry to 0x97cc at the offset 0x9442.
grub-install: info: relocating an R_X86_64_64 entry to 0x97cc at the offset 0x9459.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x947b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3d8 at the offset 0x94af.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3d0 at the offset 0x94c3.
grub-install: info: relocating an R_X86_64_64 entry to 0x18540 at the offset 0x94d4.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x94fa.
grub-install: info: relocating an R_X86_64_64 entry to 0x98ad at the offset 0x9522.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x952c.
grub-install: info: relocating an R_X86_64_64 entry to 0x56d3 at the offset 0x9541.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7f0 at the offset 0x954c.
grub-install: info: dealing with the relocation section .rela.rodata for .rodata.
grub-install: info: relocating an R_X86_64_64 entry to 0x2419 at the offset 0x0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2430 at the offset 0x8.
grub-install: info: relocating an R_X86_64_64 entry to 0x2443 at the offset 0x10.
grub-install: info: relocating an R_X86_64_64 entry to 0x245d at the offset 0x18.
grub-install: info: relocating an R_X86_64_64 entry to 0x246f at the offset 0x20.
grub-install: info: relocating an R_X86_64_64 entry to 0x25c9 at the offset 0x28.
grub-install: info: relocating an R_X86_64_64 entry to 0x25e4 at the offset 0x30.
grub-install: info: relocating an R_X86_64_64 entry to 0x25fb at the offset 0x38.
grub-install: info: relocating an R_X86_64_64 entry to 0x2616 at the offset 0x40.
grub-install: info: relocating an R_X86_64_64 entry to 0x262d at the offset 0x48.
grub-install: info: relocating an R_X86_64_64 entry to 0x266d at the offset 0x50.
grub-install: info: relocating an R_X86_64_64 entry to 0x27f6 at the offset 0x58.
grub-install: info: relocating an R_X86_64_64 entry to 0x27f6 at the offset 0x60.
grub-install: info: relocating an R_X86_64_64 entry to 0x277e at the offset 0x68.
grub-install: info: relocating an R_X86_64_64 entry to 0x27e4 at the offset 0x70.
grub-install: info: relocating an R_X86_64_64 entry to 0x267f at the offset 0x78.
grub-install: info: relocating an R_X86_64_64 entry to 0x26b6 at the offset 0x80.
grub-install: info: relocating an R_X86_64_64 entry to 0x2704 at the offset 0x88.
grub-install: info: relocating an R_X86_64_64 entry to 0x27a1 at the offset 0x90.
grub-install: info: relocating an R_X86_64_64 entry to 0x2644 at the offset 0x98.
grub-install: info: relocating an R_X86_64_64 entry to 0x27f6 at the offset 0xa0.
grub-install: info: relocating an R_X86_64_64 entry to 0x27f6 at the offset 0xa8.
grub-install: info: relocating an R_X86_64_64 entry to 0x27c5 at the offset 0xb0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2820 at the offset 0xb8.
grub-install: info: relocating an R_X86_64_64 entry to 0x2874 at the offset 0xc0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2892 at the offset 0xc8.
grub-install: info: relocating an R_X86_64_64 entry to 0x28b0 at the offset 0xd0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2922 at the offset 0xd8.
grub-install: info: relocating an R_X86_64_64 entry to 0x5e56 at the offset 0x140.
grub-install: info: relocating an R_X86_64_64 entry to 0x5e56 at the offset 0x148.
grub-install: info: relocating an R_X86_64_64 entry to 0x5f4b at the offset 0x150.
grub-install: info: relocating an R_X86_64_64 entry to 0x5fef at the offset 0x158.
grub-install: info: relocating an R_X86_64_64 entry to 0x6013 at the offset 0x160.
grub-install: info: relocating an R_X86_64_64 entry to 0x8148 at the offset 0x168.
grub-install: info: relocating an R_X86_64_64 entry to 0x818a at the offset 0x170.
grub-install: info: relocating an R_X86_64_64 entry to 0x818a at the offset 0x178.
grub-install: info: relocating an R_X86_64_64 entry to 0x8168 at the offset 0x180.
grub-install: info: relocating an R_X86_64_64 entry to 0x818a at the offset 0x188.
grub-install: info: relocating an R_X86_64_64 entry to 0x818a at the offset 0x190.
grub-install: info: dealing with the relocation section .rela.data for .data.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0x0.
grub-install: info: relocating an R_X86_64_64 entry to 0xec7 at the offset 0x10.
grub-install: info: relocating an R_X86_64_64 entry to 0xc1b at the offset 0x18.
grub-install: info: relocating an R_X86_64_64 entry to 0xbe6 at the offset 0x20.
grub-install: info: relocating an R_X86_64_64 entry to 0x1096 at the offset 0x28.
grub-install: info: relocating an R_X86_64_64 entry to 0x128e at the offset 0x30.
grub-install: info: relocating an R_X86_64_64 entry to 0xa266 at the offset 0x90.
grub-install: info: relocating an R_X86_64_64 entry to 0x3829 at the offset 0xa8.
grub-install: info: relocating an R_X86_64_64 entry to 0xa266 at the offset 0xd0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3796 at the offset 0xd8.
grub-install: info: relocating an R_X86_64_64 entry to 0x3775 at the offset 0xe0.
grub-install: info: relocating an R_X86_64_64 entry to 0x34db at the offset 0xe8.
grub-install: info: relocating an R_X86_64_64 entry to 0x36a3 at the offset 0xf8.
grub-install: info: relocating an R_X86_64_64 entry to 0x370f at the offset 0x100.
grub-install: info: relocating an R_X86_64_64 entry to 0x3667 at the offset 0x108.
grub-install: info: relocating an R_X86_64_64 entry to 0x38c2 at the offset 0x110.
grub-install: info: relocating an R_X86_64_64 entry to 0x37c3 at the offset 0x118.
grub-install: info: relocating an R_X86_64_64 entry to 0x3741 at the offset 0x120.
grub-install: info: relocating an R_X86_64_64 entry to 0xd700 at the offset 0x150.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8e4 at the offset 0x170.
grub-install: info: relocating an R_X86_64_64 entry to 0x6e4f at the offset 0x180.
grub-install: info: relocating an R_X86_64_64 entry to 0x6d5d at the offset 0x188.
grub-install: info: relocating an R_X86_64_64 entry to 0x795a at the offset 0x1b0.
grub-install: info: relocating an R_X86_64_64 entry to 0x9855 at the offset 0x300.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa37 at the offset 0x310.
grub-install: info: relocating an R_X86_64_64 entry to 0x417 at the offset 0x318.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa42 at the offset 0x328.
grub-install: info: relocating an R_X86_64_64 entry to 0x422 at the offset 0x330.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa4d at the offset 0x340.
grub-install: info: relocating an R_X86_64_64 entry to 0x4cc at the offset 0x348.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa59 at the offset 0x358.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x360.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa64 at the offset 0x370.
grub-install: info: relocating an R_X86_64_64 entry to 0x43e at the offset 0x378.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa6f at the offset 0x388.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x390.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa7a at the offset 0x3a0.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0x3a8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa85 at the offset 0x3b8.
grub-install: info: relocating an R_X86_64_64 entry to 0x47c at the offset 0x3c0.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa90 at the offset 0x3d0.
grub-install: info: relocating an R_X86_64_64 entry to 0x49f at the offset 0x3d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa9b at the offset 0x3e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xe410 at the offset 0x3f0.
grub-install: info: relocating an R_X86_64_64 entry to 0xaaad at the offset 0x400.
grub-install: info: relocating an R_X86_64_64 entry to 0xb630 at the offset 0x408.
grub-install: info: relocating an R_X86_64_64 entry to 0xaac2 at the offset 0x418.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x420.
grub-install: info: relocating an R_X86_64_64 entry to 0xaad4 at the offset 0x430.
grub-install: info: relocating an R_X86_64_64 entry to 0x49da at the offset 0x438.
grub-install: info: relocating an R_X86_64_64 entry to 0xaae8 at the offset 0x448.
grub-install: info: relocating an R_X86_64_64 entry to 0x47bb at the offset 0x450.
grub-install: info: relocating an R_X86_64_64 entry to 0xaaf9 at the offset 0x460.
grub-install: info: relocating an R_X86_64_64 entry to 0xe440 at the offset 0x468.
grub-install: info: relocating an R_X86_64_64 entry to 0xab0f at the offset 0x478.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ee6 at the offset 0x480.
grub-install: info: relocating an R_X86_64_64 entry to 0xab1f at the offset 0x490.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x498.
grub-install: info: relocating an R_X86_64_64 entry to 0xab32 at the offset 0x4a8.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ea0 at the offset 0x4b0.
grub-install: info: relocating an R_X86_64_64 entry to 0xab49 at the offset 0x4c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x4eb5 at the offset 0x4c8.
grub-install: info: relocating an R_X86_64_64 entry to 0xab62 at the offset 0x4d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xe430 at the offset 0x4e0.
grub-install: info: relocating an R_X86_64_64 entry to 0xab7a at the offset 0x4f0.
grub-install: info: relocating an R_X86_64_64 entry to 0xe420 at the offset 0x4f8.
grub-install: info: relocating an R_X86_64_64 entry to 0xab98 at the offset 0x508.
grub-install: info: relocating an R_X86_64_64 entry to 0x55c0 at the offset 0x510.
grub-install: info: relocating an R_X86_64_64 entry to 0xabab at the offset 0x520.
grub-install: info: relocating an R_X86_64_64 entry to 0x4f8a at the offset 0x528.
grub-install: info: relocating an R_X86_64_64 entry to 0xabba at the offset 0x538.
grub-install: info: relocating an R_X86_64_64 entry to 0x5270 at the offset 0x540.
grub-install: info: relocating an R_X86_64_64 entry to 0xabc9 at the offset 0x550.
grub-install: info: relocating an R_X86_64_64 entry to 0xe428 at the offset 0x558.
grub-install: info: relocating an R_X86_64_64 entry to 0xabde at the offset 0x568.
grub-install: info: relocating an R_X86_64_64 entry to 0x7cd7 at the offset 0x570.
grub-install: info: relocating an R_X86_64_64 entry to 0xabec at the offset 0x580.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x588.
grub-install: info: relocating an R_X86_64_64 entry to 0xabf9 at the offset 0x598.
grub-install: info: relocating an R_X86_64_64 entry to 0x631d at the offset 0x5a0.
grub-install: info: relocating an R_X86_64_64 entry to 0xac06 at the offset 0x5b0.
grub-install: info: relocating an R_X86_64_64 entry to 0x5926 at the offset 0x5b8.
grub-install: info: relocating an R_X86_64_64 entry to 0xac1f at the offset 0x5c8.
grub-install: info: relocating an R_X86_64_64 entry to 0x5792 at the offset 0x5d0.
grub-install: info: relocating an R_X86_64_64 entry to 0xac2b at the offset 0x5e0.
grub-install: info: relocating an R_X86_64_64 entry to 0x580c at the offset 0x5e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xac3a at the offset 0x5f8.
grub-install: info: relocating an R_X86_64_64 entry to 0x57cf at the offset 0x600.
grub-install: info: relocating an R_X86_64_64 entry to 0xac48 at the offset 0x610.
grub-install: info: relocating an R_X86_64_64 entry to 0x599 at the offset 0x618.
grub-install: info: relocating an R_X86_64_64 entry to 0xac56 at the offset 0x628.
grub-install: info: relocating an R_X86_64_64 entry to 0x5a9 at the offset 0x630.
grub-install: info: relocating an R_X86_64_64 entry to 0xac68 at the offset 0x640.
grub-install: info: relocating an R_X86_64_64 entry to 0x5a5 at the offset 0x648.
grub-install: info: relocating an R_X86_64_64 entry to 0xac7a at the offset 0x658.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c6e at the offset 0x660.
grub-install: info: relocating an R_X86_64_64 entry to 0xac92 at the offset 0x670.
grub-install: info: relocating an R_X86_64_64 entry to 0x2d32 at the offset 0x678.
grub-install: info: relocating an R_X86_64_64 entry to 0xacae at the offset 0x688.
grub-install: info: relocating an R_X86_64_64 entry to 0x29f5 at the offset 0x690.
grub-install: info: relocating an R_X86_64_64 entry to 0xaccc at the offset 0x6a0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2f18 at the offset 0x6a8.
grub-install: info: relocating an R_X86_64_64 entry to 0xacea at the offset 0x6b8.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c44 at the offset 0x6c0.
grub-install: info: relocating an R_X86_64_64 entry to 0xacfe at the offset 0x6d0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2355 at the offset 0x6d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xad17 at the offset 0x6e8.
grub-install: info: relocating an R_X86_64_64 entry to 0x2289 at the offset 0x6f0.
grub-install: info: relocating an R_X86_64_64 entry to 0xad2d at the offset 0x700.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e63 at the offset 0x708.
grub-install: info: relocating an R_X86_64_64 entry to 0xad47 at the offset 0x718.
grub-install: info: relocating an R_X86_64_64 entry to 0x2de4 at the offset 0x720.
grub-install: info: relocating an R_X86_64_64 entry to 0xad5f at the offset 0x730.
grub-install: info: relocating an R_X86_64_64 entry to 0x1ff7 at the offset 0x738.
grub-install: info: relocating an R_X86_64_64 entry to 0xad75 at the offset 0x748.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x750.
grub-install: info: relocating an R_X86_64_64 entry to 0xad8b at the offset 0x760.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x768.
grub-install: info: relocating an R_X86_64_64 entry to 0xada0 at the offset 0x778.
grub-install: info: relocating an R_X86_64_64 entry to 0x1c5f at the offset 0x780.
grub-install: info: relocating an R_X86_64_64 entry to 0xadb7 at the offset 0x790.
grub-install: info: relocating an R_X86_64_64 entry to 0x1c16 at the offset 0x798.
grub-install: info: relocating an R_X86_64_64 entry to 0xadd0 at the offset 0x7a8.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f8 at the offset 0x7b0.
grub-install: info: relocating an R_X86_64_64 entry to 0xade4 at the offset 0x7c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x1d5a at the offset 0x7c8.
grub-install: info: relocating an R_X86_64_64 entry to 0xadfb at the offset 0x7d8.
grub-install: info: relocating an R_X86_64_64 entry to 0x2370 at the offset 0x7e0.
grub-install: info: relocating an R_X86_64_64 entry to 0xae16 at the offset 0x7f0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2117 at the offset 0x7f8.
grub-install: info: relocating an R_X86_64_64 entry to 0xae2b at the offset 0x808.
grub-install: info: relocating an R_X86_64_64 entry to 0x1db8 at the offset 0x810.
grub-install: info: relocating an R_X86_64_64 entry to 0xae42 at the offset 0x820.
grub-install: info: relocating an R_X86_64_64 entry to 0x1f1d at the offset 0x828.
grub-install: info: relocating an R_X86_64_64 entry to 0xae58 at the offset 0x838.
grub-install: info: relocating an R_X86_64_64 entry to 0x1ec2 at the offset 0x840.
grub-install: info: relocating an R_X86_64_64 entry to 0xae79 at the offset 0x850.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e3f at the offset 0x858.
grub-install: info: relocating an R_X86_64_64 entry to 0xae88 at the offset 0x868.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x870.
grub-install: info: relocating an R_X86_64_64 entry to 0xae9e at the offset 0x880.
grub-install: info: relocating an R_X86_64_64 entry to 0x1581 at the offset 0x888.
grub-install: info: relocating an R_X86_64_64 entry to 0xaebd at the offset 0x898.
grub-install: info: relocating an R_X86_64_64 entry to 0x16cc at the offset 0x8a0.
grub-install: info: relocating an R_X86_64_64 entry to 0xaeda at the offset 0x8b0.
grub-install: info: relocating an R_X86_64_64 entry to 0x6788 at the offset 0x8b8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaeea at the offset 0x8c8.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x8d0.
grub-install: info: relocating an R_X86_64_64 entry to 0xaef7 at the offset 0x8e0.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x8e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf04 at the offset 0x8f8.
grub-install: info: relocating an R_X86_64_64 entry to 0x6618 at the offset 0x900.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf13 at the offset 0x910.
grub-install: info: relocating an R_X86_64_64 entry to 0x669c at the offset 0x918.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf2e at the offset 0x928.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d4 at the offset 0x930.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf46 at the offset 0x940.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x948.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf52 at the offset 0x958.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x960.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf5d at the offset 0x970.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x978.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf68 at the offset 0x988.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x990.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf77 at the offset 0x9a0.
grub-install: info: relocating an R_X86_64_64 entry to 0x684a at the offset 0x9a8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf87 at the offset 0x9b8.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e7e at the offset 0x9c0.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf91 at the offset 0x9d0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x9d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf9c at the offset 0x9e8.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b05 at the offset 0x9f0.
grub-install: info: relocating an R_X86_64_64 entry to 0xafac at the offset 0xa00.
grub-install: info: relocating an R_X86_64_64 entry to 0x184f0 at the offset 0xa08.
grub-install: info: relocating an R_X86_64_64 entry to 0xafc2 at the offset 0xa18.
grub-install: info: relocating an R_X86_64_64 entry to 0x18510 at the offset 0xa20.
grub-install: info: relocating an R_X86_64_64 entry to 0xafdc at the offset 0xa30.
grub-install: info: relocating an R_X86_64_64 entry to 0x69dd at the offset 0xa38.
grub-install: info: relocating an R_X86_64_64 entry to 0xaff6 at the offset 0xa48.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b50 at the offset 0xa50.
grub-install: info: relocating an R_X86_64_64 entry to 0xb005 at the offset 0xa60.
grub-install: info: relocating an R_X86_64_64 entry to 0x184e0 at the offset 0xa68.
grub-install: info: relocating an R_X86_64_64 entry to 0xb01d at the offset 0xa78.
grub-install: info: relocating an R_X86_64_64 entry to 0x6a68 at the offset 0xa80.
grub-install: info: relocating an R_X86_64_64 entry to 0xb02c at the offset 0xa90.
grub-install: info: relocating an R_X86_64_64 entry to 0x6d22 at the offset 0xa98.
grub-install: info: relocating an R_X86_64_64 entry to 0xb03b at the offset 0xaa8.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0xab0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb045 at the offset 0xac0.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b0 at the offset 0xac8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb05b at the offset 0xad8.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b8 at the offset 0xae0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb068 at the offset 0xaf0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7033 at the offset 0xaf8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb076 at the offset 0xb08.
grub-install: info: relocating an R_X86_64_64 entry to 0x417b at the offset 0xb10.
grub-install: info: relocating an R_X86_64_64 entry to 0xb087 at the offset 0xb20.
grub-install: info: relocating an R_X86_64_64 entry to 0x991f at the offset 0xb28.
grub-install: info: relocating an R_X86_64_64 entry to 0xb093 at the offset 0xb38.
grub-install: info: relocating an R_X86_64_64 entry to 0x98ad at the offset 0xb40.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0a7 at the offset 0xb50.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0xb58.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0b4 at the offset 0xb68.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0xb70.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0c1 at the offset 0xb80.
grub-install: info: relocating an R_X86_64_64 entry to 0x7276 at the offset 0xb88.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0d0 at the offset 0xb98.
grub-install: info: relocating an R_X86_64_64 entry to 0x7290 at the offset 0xba0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0e1 at the offset 0xbb0.
grub-install: info: relocating an R_X86_64_64 entry to 0x534 at the offset 0xbb8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0f3 at the offset 0xbc8.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0xbd0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0ff at the offset 0xbe0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3c27 at the offset 0xbe8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb10d at the offset 0xbf8.
grub-install: info: relocating an R_X86_64_64 entry to 0x547 at the offset 0xc00.
grub-install: info: relocating an R_X86_64_64 entry to 0xb121 at the offset 0xc10.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0xc18.
grub-install: info: relocating an R_X86_64_64 entry to 0xb12d at the offset 0xc28.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0xc30.
grub-install: info: relocating an R_X86_64_64 entry to 0xb13a at the offset 0xc40.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0xc48.
grub-install: info: relocating an R_X86_64_64 entry to 0xb146 at the offset 0xc58.
grub-install: info: relocating an R_X86_64_64 entry to 0x4195 at the offset 0xc60.
grub-install: info: relocating an R_X86_64_64 entry to 0xb156 at the offset 0xc70.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0xc78.
grub-install: info: relocating an R_X86_64_64 entry to 0xb163 at the offset 0xc88.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0xc90.
grub-install: info: relocating an R_X86_64_64 entry to 0xb170 at the offset 0xca0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7242 at the offset 0xca8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb185 at the offset 0xcb8.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6e8 at the offset 0xcc0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb193 at the offset 0xcd0.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3d0 at the offset 0xcd8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb1ac at the offset 0xce8.
grub-install: info: relocating an R_X86_64_64 entry to 0x8c1a at the offset 0xcf0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb1c6 at the offset 0xd00.
grub-install: info: relocating an R_X86_64_64 entry to 0x8cd3 at the offset 0xd08.
grub-install: info: relocating an R_X86_64_64 entry to 0xb1e0 at the offset 0xd18.
grub-install: info: relocating an R_X86_64_64 entry to 0x91d0 at the offset 0xd20.
grub-install: info: relocating an R_X86_64_64 entry to 0xb1f8 at the offset 0xd30.
grub-install: info: relocating an R_X86_64_64 entry to 0x9164 at the offset 0xd38.
grub-install: info: relocating an R_X86_64_64 entry to 0xb20f at the offset 0xd48.
grub-install: info: relocating an R_X86_64_64 entry to 0x18530 at the offset 0xd50.
grub-install: info: relocating an R_X86_64_64 entry to 0xb227 at the offset 0xd60.
grub-install: info: relocating an R_X86_64_64 entry to 0x8fd0 at the offset 0xd68.
grub-install: info: relocating an R_X86_64_64 entry to 0xb23c at the offset 0xd78.
grub-install: info: relocating an R_X86_64_64 entry to 0x6a2 at the offset 0xd80.
grub-install: info: relocating an R_X86_64_64 entry to 0xb255 at the offset 0xd90.
grub-install: info: relocating an R_X86_64_64 entry to 0x5d3 at the offset 0xd98.
grub-install: info: relocating an R_X86_64_64 entry to 0xb266 at the offset 0xda8.
grub-install: info: relocating an R_X86_64_64 entry to 0x5ac at the offset 0xdb0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb27c at the offset 0xdc0.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0xdc8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb28d at the offset 0xdd8.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0xde0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb299 at the offset 0xdf0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8775 at the offset 0xdf8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2a6 at the offset 0xe08.
grub-install: info: relocating an R_X86_64_64 entry to 0x79d3 at the offset 0xe10.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2b1 at the offset 0xe20.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xe28.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2c3 at the offset 0xe38.
grub-install: info: relocating an R_X86_64_64 entry to 0x40bf at the offset 0xe40.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2d0 at the offset 0xe50.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0xe58.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2dd at the offset 0xe68.
grub-install: info: relocating an R_X86_64_64 entry to 0x41be at the offset 0xe70.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2f8 at the offset 0xe80.
grub-install: info: relocating an R_X86_64_64 entry to 0x6728 at the offset 0xe88.
grub-install: info: relocating an R_X86_64_64 entry to 0xb314 at the offset 0xe98.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0xea0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb322 at the offset 0xeb0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0xeb8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb32e at the offset 0xec8.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0xed0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb33a at the offset 0xee0.
grub-install: info: relocating an R_X86_64_64 entry to 0x79c0 at the offset 0xee8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb346 at the offset 0xef8.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0xf00.
grub-install: info: relocating an R_X86_64_64 entry to 0xb352 at the offset 0xf10.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0xf18.
grub-install: info: relocating an R_X86_64_64 entry to 0xb35e at the offset 0xf28.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a4d at the offset 0xf30.
grub-install: info: relocating an R_X86_64_64 entry to 0xb36b at the offset 0xf40.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c36 at the offset 0xf48.
grub-install: info: relocating an R_X86_64_64 entry to 0xb378 at the offset 0xf58.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a99 at the offset 0xf60.
grub-install: info: relocating an R_X86_64_64 entry to 0xb385 at the offset 0xf70.
grub-install: info: relocating an R_X86_64_64 entry to 0x81c5 at the offset 0xf78.
grub-install: info: relocating an R_X86_64_64 entry to 0xb392 at the offset 0xf88.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0xf90.
grub-install: info: relocating an R_X86_64_64 entry to 0xb3a0 at the offset 0xfa0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7b0e at the offset 0xfa8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb3ad at the offset 0xfb8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e8 at the offset 0xfc0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb3c7 at the offset 0xfd0.
grub-install: info: relocating an R_X86_64_64 entry to 0x18540 at the offset 0xfd8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb3d8 at the offset 0xfe8.
grub-install: info: relocating an R_X86_64_64 entry to 0x18550 at the offset 0xff0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb3f2 at the offset 0x1000.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e9 at the offset 0x1008.
grub-install: info: relocating an R_X86_64_64 entry to 0xb409 at the offset 0x1018.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x1020.
grub-install: info: relocating an R_X86_64_64 entry to 0xb41b at the offset 0x1030.
grub-install: info: relocating an R_X86_64_64 entry to 0x18538 at the offset 0x1038.
grub-install: info: relocating an R_X86_64_64 entry to 0xb436 at the offset 0x1048.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3d8 at the offset 0x1050.
grub-install: info: relocating an R_X86_64_64 entry to 0xb449 at the offset 0x1060.
grub-install: info: relocating an R_X86_64_64 entry to 0xe400 at the offset 0x1068.
grub-install: info: relocating an R_X86_64_64 entry to 0xb457 at the offset 0x1078.
grub-install: info: relocating an R_X86_64_64 entry to 0x42af at the offset 0x1080.
grub-install: info: relocating an R_X86_64_64 entry to 0xb46f at the offset 0x1090.
grub-install: info: relocating an R_X86_64_64 entry to 0x8666 at the offset 0x1098.
grub-install: info: relocating an R_X86_64_64 entry to 0xb47c at the offset 0x10a8.
grub-install: info: relocating an R_X86_64_64 entry to 0x88fd at the offset 0x10b0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb48b at the offset 0x10c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x10c8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb49a at the offset 0x10d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x10e0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4a5 at the offset 0x10f0.
grub-install: info: relocating an R_X86_64_64 entry to 0x89b2 at the offset 0x10f8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4b5 at the offset 0x1108.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x1110.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4c1 at the offset 0x1120.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0x1128.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4c8 at the offset 0x1138.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x1140.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4cf at the offset 0x1150.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x1158.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4d7 at the offset 0x1168.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0x1170.
grub-install: info: translating the relocation section .rela.text.
grub-install: info: adding a relocation entry for 0x51d.
grub-install: info: adding a relocation entry for 0x52a.
grub-install: info: adding a relocation entry for 0x53c.
grub-install: info: adding a relocation entry for 0x565.
grub-install: info: adding a relocation entry for 0x57a.
grub-install: info: adding a relocation entry for 0x58b.
grub-install: info: adding a relocation entry for 0x59b.
grub-install: info: adding a relocation entry for 0x5e0.
grub-install: info: adding a relocation entry for 0x6af.
grub-install: info: adding a relocation entry for 0x755.
grub-install: info: adding a relocation entry for 0x766.
grub-install: info: adding a relocation entry for 0x78f.
grub-install: info: adding a relocation entry for 0x810.
grub-install: info: adding a relocation entry for 0x822.
grub-install: info: adding a relocation entry for 0x874.
grub-install: info: adding a relocation entry for 0x885.
grub-install: info: adding a relocation entry for 0x8fd.
grub-install: info: adding a relocation entry for 0x927.
grub-install: info: adding a relocation entry for 0x945.
grub-install: info: adding a relocation entry for 0x97a.
grub-install: info: adding a relocation entry for 0x9ac.
grub-install: info: adding a relocation entry for 0x9cd.
grub-install: info: adding a relocation entry for 0x9fa.
grub-install: info: adding a relocation entry for 0xa0c.
grub-install: info: adding a relocation entry for 0xa38.
grub-install: info: adding a relocation entry for 0xa42.
grub-install: info: adding a relocation entry for 0xa6d.
grub-install: info: adding a relocation entry for 0xa94.
grub-install: info: adding a relocation entry for 0xac0.
grub-install: info: adding a relocation entry for 0xacf.
grub-install: info: adding a relocation entry for 0xafd.
grub-install: info: adding a relocation entry for 0xb22.
grub-install: info: adding a relocation entry for 0xb3b.
grub-install: info: adding a relocation entry for 0xb49.
grub-install: info: adding a relocation entry for 0xb67.
grub-install: info: adding a relocation entry for 0xb80.
grub-install: info: adding a relocation entry for 0xbc6.
grub-install: info: adding a relocation entry for 0xbeb.
grub-install: info: adding a relocation entry for 0xbf5.
grub-install: info: adding a relocation entry for 0xc04.
grub-install: info: adding a relocation entry for 0xc10.
grub-install: info: adding a relocation entry for 0xc24.
grub-install: info: adding a relocation entry for 0xc2e.
grub-install: info: adding a relocation entry for 0xc38.
grub-install: info: adding a relocation entry for 0xc4a.
grub-install: info: adding a relocation entry for 0xc80.
grub-install: info: adding a relocation entry for 0xc8f.
grub-install: info: adding a relocation entry for 0xca5.
grub-install: info: adding a relocation entry for 0xcb6.
grub-install: info: adding a relocation entry for 0xcc1.
grub-install: info: adding a relocation entry for 0xcec.
grub-install: info: adding a relocation entry for 0xcfb.
grub-install: info: adding a relocation entry for 0xd0a.
grub-install: info: adding a relocation entry for 0xd17.
grub-install: info: adding a relocation entry for 0xd33.
grub-install: info: adding a relocation entry for 0xd44.
grub-install: info: adding a relocation entry for 0xd58.
grub-install: info: adding a relocation entry for 0xd65.
grub-install: info: adding a relocation entry for 0xd77.
grub-install: info: adding a relocation entry for 0xd81.
grub-install: info: adding a relocation entry for 0xdd4.
grub-install: info: adding a relocation entry for 0xde5.
grub-install: info: adding a relocation entry for 0xe18.
grub-install: info: adding a relocation entry for 0xe22.
grub-install: info: adding a relocation entry for 0xe31.
grub-install: info: adding a relocation entry for 0xe3b.
grub-install: info: adding a relocation entry for 0xe55.
grub-install: info: adding a relocation entry for 0xe61.
grub-install: info: adding a relocation entry for 0xe6c.
grub-install: info: adding a relocation entry for 0xe77.
grub-install: info: adding a relocation entry for 0xea4.
grub-install: info: adding a relocation entry for 0xeb6.
grub-install: info: adding a relocation entry for 0xeea.
grub-install: info: adding a relocation entry for 0xeff.
grub-install: info: adding a relocation entry for 0xf13.
grub-install: info: adding a relocation entry for 0xf25.
grub-install: info: adding a relocation entry for 0xf2f.
grub-install: info: adding a relocation entry for 0xf3e.
grub-install: info: adding a relocation entry for 0xf48.
grub-install: info: adding a relocation entry for 0xf77.
grub-install: info: adding a relocation entry for 0xf8c.
grub-install: info: adding a relocation entry for 0xfa0.
grub-install: info: adding a relocation entry for 0xfb2.
grub-install: info: adding a relocation entry for 0xfbc.
grub-install: info: adding a relocation entry for 0xfcb.
grub-install: info: adding a relocation entry for 0xfd5.
grub-install: info: adding a relocation entry for 0x1000.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 184 bytes of a fixup block starting at 0x0.
grub-install: info: adding a relocation entry for 0x1015.
grub-install: info: adding a relocation entry for 0x1029.
grub-install: info: adding a relocation entry for 0x103b.
grub-install: info: adding a relocation entry for 0x1045.
grub-install: info: adding a relocation entry for 0x1054.
grub-install: info: adding a relocation entry for 0x105e.
grub-install: info: adding a relocation entry for 0x10a5.
grub-install: info: adding a relocation entry for 0x10b1.
grub-install: info: adding a relocation entry for 0x10be.
grub-install: info: adding a relocation entry for 0x10db.
grub-install: info: adding a relocation entry for 0x1109.
grub-install: info: adding a relocation entry for 0x1124.
grub-install: info: adding a relocation entry for 0x113d.
grub-install: info: adding a relocation entry for 0x117f.
grub-install: info: adding a relocation entry for 0x119c.
grub-install: info: adding a relocation entry for 0x11b2.
grub-install: info: adding a relocation entry for 0x11d8.
grub-install: info: adding a relocation entry for 0x11e2.
grub-install: info: adding a relocation entry for 0x1220.
grub-install: info: adding a relocation entry for 0x127a.
grub-install: info: adding a relocation entry for 0x129d.
grub-install: info: adding a relocation entry for 0x12a9.
grub-install: info: adding a relocation entry for 0x12b6.
grub-install: info: adding a relocation entry for 0x12d3.
grub-install: info: adding a relocation entry for 0x1301.
grub-install: info: adding a relocation entry for 0x131c.
grub-install: info: adding a relocation entry for 0x1335.
grub-install: info: adding a relocation entry for 0x134e.
grub-install: info: adding a relocation entry for 0x1362.
grub-install: info: adding a relocation entry for 0x136c.
grub-install: info: adding a relocation entry for 0x1387.
grub-install: info: adding a relocation entry for 0x13ee.
grub-install: info: adding a relocation entry for 0x13f8.
grub-install: info: adding a relocation entry for 0x1404.
grub-install: info: adding a relocation entry for 0x149d.
grub-install: info: adding a relocation entry for 0x14b3.
grub-install: info: adding a relocation entry for 0x1506.
grub-install: info: adding a relocation entry for 0x1515.
grub-install: info: adding a relocation entry for 0x151f.
grub-install: info: adding a relocation entry for 0x153b.
grub-install: info: adding a relocation entry for 0x1547.
grub-install: info: adding a relocation entry for 0x1551.
grub-install: info: adding a relocation entry for 0x156a.
grub-install: info: adding a relocation entry for 0x15cd.
grub-install: info: adding a relocation entry for 0x15d7.
grub-install: info: adding a relocation entry for 0x1604.
grub-install: info: adding a relocation entry for 0x1625.
grub-install: info: adding a relocation entry for 0x1638.
grub-install: info: adding a relocation entry for 0x16ac.
grub-install: info: adding a relocation entry for 0x16d0.
grub-install: info: adding a relocation entry for 0x16f6.
grub-install: info: adding a relocation entry for 0x172c.
grub-install: info: adding a relocation entry for 0x1783.
grub-install: info: adding a relocation entry for 0x1796.
grub-install: info: adding a relocation entry for 0x17ae.
grub-install: info: adding a relocation entry for 0x17c0.
grub-install: info: adding a relocation entry for 0x17f0.
grub-install: info: adding a relocation entry for 0x180a.
grub-install: info: adding a relocation entry for 0x181d.
grub-install: info: adding a relocation entry for 0x182a.
grub-install: info: adding a relocation entry for 0x1843.
grub-install: info: adding a relocation entry for 0x1857.
grub-install: info: adding a relocation entry for 0x1861.
grub-install: info: adding a relocation entry for 0x1879.
grub-install: info: adding a relocation entry for 0x1892.
grub-install: info: adding a relocation entry for 0x18ad.
grub-install: info: adding a relocation entry for 0x18c6.
grub-install: info: adding a relocation entry for 0x19ec.
grub-install: info: adding a relocation entry for 0x1a45.
grub-install: info: adding a relocation entry for 0x1a64.
grub-install: info: adding a relocation entry for 0x1a70.
grub-install: info: adding a relocation entry for 0x1a84.
grub-install: info: adding a relocation entry for 0x1c1f.
grub-install: info: adding a relocation entry for 0x1c32.
grub-install: info: adding a relocation entry for 0x1c68.
grub-install: info: adding a relocation entry for 0x1ca5.
grub-install: info: adding a relocation entry for 0x1cc3.
grub-install: info: adding a relocation entry for 0x1cec.
grub-install: info: adding a relocation entry for 0x1d2d.
grub-install: info: adding a relocation entry for 0x1d63.
grub-install: info: adding a relocation entry for 0x1d81.
grub-install: info: adding a relocation entry for 0x1d99.
grub-install: info: adding a relocation entry for 0x1dbf.
grub-install: info: adding a relocation entry for 0x1dc9.
grub-install: info: adding a relocation entry for 0x1df9.
grub-install: info: adding a relocation entry for 0x1e24.
grub-install: info: adding a relocation entry for 0x1e41.
grub-install: info: adding a relocation entry for 0x1e59.
grub-install: info: adding a relocation entry for 0x1e6a.
grub-install: info: adding a relocation entry for 0x1e74.
grub-install: info: adding a relocation entry for 0x1e81.
grub-install: info: adding a relocation entry for 0x1e8d.
grub-install: info: adding a relocation entry for 0x1ea9.
grub-install: info: adding a relocation entry for 0x1eb6.
grub-install: info: adding a relocation entry for 0x1ec7.
grub-install: info: adding a relocation entry for 0x1eec.
grub-install: info: adding a relocation entry for 0x1efe.
grub-install: info: adding a relocation entry for 0x1f0f.
grub-install: info: adding a relocation entry for 0x1f24.
grub-install: info: adding a relocation entry for 0x1f4b.
grub-install: info: adding a relocation entry for 0x1f59.
grub-install: info: adding a relocation entry for 0x1f78.
grub-install: info: adding a relocation entry for 0x1f8a.
grub-install: info: adding a relocation entry for 0x1fad.
grub-install: info: adding a relocation entry for 0x1fc9.
grub-install: info: adding a relocation entry for 0x1fe1.
grub-install: info: adding a relocation entry for 0x1ffb.
grub-install: info: adding a relocation entry for 0x2005.
grub-install: info: writing 224 bytes of a fixup block starting at 0x1000.
grub-install: info: adding a relocation entry for 0x205c.
grub-install: info: adding a relocation entry for 0x2066.
grub-install: info: adding a relocation entry for 0x2078.
grub-install: info: adding a relocation entry for 0x20b7.
grub-install: info: adding a relocation entry for 0x20e4.
grub-install: info: adding a relocation entry for 0x211b.
grub-install: info: adding a relocation entry for 0x2127.
grub-install: info: adding a relocation entry for 0x21a0.
grub-install: info: adding a relocation entry for 0x21cf.
grub-install: info: adding a relocation entry for 0x21ee.
grub-install: info: adding a relocation entry for 0x2201.
grub-install: info: adding a relocation entry for 0x221f.
grub-install: info: adding a relocation entry for 0x223c.
grub-install: info: adding a relocation entry for 0x22d3.
grub-install: info: adding a relocation entry for 0x22ea.
grub-install: info: adding a relocation entry for 0x235c.
grub-install: info: adding a relocation entry for 0x2366.
grub-install: info: adding a relocation entry for 0x237b.
grub-install: info: adding a relocation entry for 0x23d4.
grub-install: info: adding a relocation entry for 0x23e2.
grub-install: info: adding a relocation entry for 0x23f5.
grub-install: info: adding a relocation entry for 0x240e.
grub-install: info: adding a relocation entry for 0x2423.
grub-install: info: adding a relocation entry for 0x2436.
grub-install: info: adding a relocation entry for 0x244d.
grub-install: info: adding a relocation entry for 0x2462.
grub-install: info: adding a relocation entry for 0x2474.
grub-install: info: adding a relocation entry for 0x2483.
grub-install: info: adding a relocation entry for 0x249c.
grub-install: info: adding a relocation entry for 0x24b4.
grub-install: info: adding a relocation entry for 0x24c9.
grub-install: info: adding a relocation entry for 0x24de.
grub-install: info: adding a relocation entry for 0x24f2.
grub-install: info: adding a relocation entry for 0x2504.
grub-install: info: adding a relocation entry for 0x251e.
grub-install: info: adding a relocation entry for 0x2534.
grub-install: info: adding a relocation entry for 0x2547.
grub-install: info: adding a relocation entry for 0x2576.
grub-install: info: adding a relocation entry for 0x25a1.
grub-install: info: adding a relocation entry for 0x25be.
grub-install: info: adding a relocation entry for 0x25d3.
grub-install: info: adding a relocation entry for 0x25ee.
grub-install: info: adding a relocation entry for 0x2605.
grub-install: info: adding a relocation entry for 0x261c.
grub-install: info: adding a relocation entry for 0x2637.
grub-install: info: adding a relocation entry for 0x264e.
grub-install: info: adding a relocation entry for 0x2672.
grub-install: info: adding a relocation entry for 0x2689.
grub-install: info: adding a relocation entry for 0x26be.
grub-install: info: adding a relocation entry for 0x270c.
grub-install: info: adding a relocation entry for 0x2788.
grub-install: info: adding a relocation entry for 0x27ab.
grub-install: info: adding a relocation entry for 0x27cf.
grub-install: info: adding a relocation entry for 0x27e9.
grub-install: info: adding a relocation entry for 0x27f8.
grub-install: info: adding a relocation entry for 0x2815.
grub-install: info: adding a relocation entry for 0x282b.
grub-install: info: adding a relocation entry for 0x287e.
grub-install: info: adding a relocation entry for 0x2897.
grub-install: info: adding a relocation entry for 0x28a1.
grub-install: info: adding a relocation entry for 0x28b6.
grub-install: info: adding a relocation entry for 0x28e3.
grub-install: info: adding a relocation entry for 0x28f5.
grub-install: info: adding a relocation entry for 0x2902.
grub-install: info: adding a relocation entry for 0x2913.
grub-install: info: adding a relocation entry for 0x292c.
grub-install: info: adding a relocation entry for 0x296b.
grub-install: info: adding a relocation entry for 0x297b.
grub-install: info: adding a relocation entry for 0x2993.
grub-install: info: adding a relocation entry for 0x29b9.
grub-install: info: adding a relocation entry for 0x29c6.
grub-install: info: adding a relocation entry for 0x2a0e.
grub-install: info: adding a relocation entry for 0x2a88.
grub-install: info: adding a relocation entry for 0x2a94.
grub-install: info: adding a relocation entry for 0x2a9e.
grub-install: info: adding a relocation entry for 0x2aaa.
grub-install: info: adding a relocation entry for 0x2ab6.
grub-install: info: adding a relocation entry for 0x2ad4.
grub-install: info: adding a relocation entry for 0x2ae1.
grub-install: info: adding a relocation entry for 0x2aef.
grub-install: info: adding a relocation entry for 0x2b04.
grub-install: info: adding a relocation entry for 0x2b1c.
grub-install: info: adding a relocation entry for 0x2b2c.
grub-install: info: adding a relocation entry for 0x2b47.
grub-install: info: adding a relocation entry for 0x2b6b.
grub-install: info: adding a relocation entry for 0x2b85.
grub-install: info: adding a relocation entry for 0x2b92.
grub-install: info: adding a relocation entry for 0x2bbb.
grub-install: info: adding a relocation entry for 0x2be5.
grub-install: info: adding a relocation entry for 0x2c49.
grub-install: info: adding a relocation entry for 0x2c5c.
grub-install: info: adding a relocation entry for 0x2ca6.
grub-install: info: adding a relocation entry for 0x2cc3.
grub-install: info: adding a relocation entry for 0x2d13.
grub-install: info: adding a relocation entry for 0x2d57.
grub-install: info: adding a relocation entry for 0x2d76.
grub-install: info: adding a relocation entry for 0x2dc5.
grub-install: info: adding a relocation entry for 0x2de8.
grub-install: info: adding a relocation entry for 0x2e16.
grub-install: info: adding a relocation entry for 0x2e25.
grub-install: info: adding a relocation entry for 0x2e32.
grub-install: info: adding a relocation entry for 0x2e45.
grub-install: info: adding a relocation entry for 0x2e52.
grub-install: info: adding a relocation entry for 0x2e63.
grub-install: info: adding a relocation entry for 0x2e76.
grub-install: info: adding a relocation entry for 0x2e88.
grub-install: info: adding a relocation entry for 0x2e9a.
grub-install: info: adding a relocation entry for 0x2ec0.
grub-install: info: adding a relocation entry for 0x2ee2.
grub-install: info: adding a relocation entry for 0x2f1c.
grub-install: info: adding a relocation entry for 0x2f46.
grub-install: info: adding a relocation entry for 0x2f7c.
grub-install: info: adding a relocation entry for 0x2f8c.
grub-install: info: adding a relocation entry for 0x2f96.
grub-install: info: adding a relocation entry for 0x2fa0.
grub-install: info: adding a relocation entry for 0x2faa.
grub-install: info: adding a relocation entry for 0x2fb7.
grub-install: info: adding a relocation entry for 0x2fd2.
grub-install: info: adding a relocation entry for 0x2fe5.
grub-install: info: adding a relocation entry for 0x2ff6.
grub-install: info: adding a relocation entry for 0x3007.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 256 bytes of a fixup block starting at 0x2000.
grub-install: info: adding a relocation entry for 0x3014.
grub-install: info: adding a relocation entry for 0x3023.
grub-install: info: adding a relocation entry for 0x302e.
grub-install: info: adding a relocation entry for 0x303d.
grub-install: info: adding a relocation entry for 0x3047.
grub-install: info: adding a relocation entry for 0x3051.
grub-install: info: adding a relocation entry for 0x305e.
grub-install: info: adding a relocation entry for 0x306f.
grub-install: info: adding a relocation entry for 0x3079.
grub-install: info: adding a relocation entry for 0x3088.
grub-install: info: adding a relocation entry for 0x3097.
grub-install: info: adding a relocation entry for 0x30ac.
grub-install: info: adding a relocation entry for 0x30b9.
grub-install: info: adding a relocation entry for 0x30c6.
grub-install: info: adding a relocation entry for 0x30e4.
grub-install: info: adding a relocation entry for 0x30ee.
grub-install: info: adding a relocation entry for 0x30ff.
grub-install: info: adding a relocation entry for 0x3110.
grub-install: info: adding a relocation entry for 0x311c.
grub-install: info: adding a relocation entry for 0x3134.
grub-install: info: adding a relocation entry for 0x3140.
grub-install: info: adding a relocation entry for 0x3153.
grub-install: info: adding a relocation entry for 0x3163.
grub-install: info: adding a relocation entry for 0x3170.
grub-install: info: adding a relocation entry for 0x3181.
grub-install: info: adding a relocation entry for 0x3193.
grub-install: info: adding a relocation entry for 0x31a5.
grub-install: info: adding a relocation entry for 0x31c1.
grub-install: info: adding a relocation entry for 0x31cb.
grub-install: info: adding a relocation entry for 0x31f9.
grub-install: info: adding a relocation entry for 0x3212.
grub-install: info: adding a relocation entry for 0x323c.
grub-install: info: adding a relocation entry for 0x3254.
grub-install: info: adding a relocation entry for 0x32a5.
grub-install: info: adding a relocation entry for 0x32b1.
grub-install: info: adding a relocation entry for 0x3317.
grub-install: info: adding a relocation entry for 0x3452.
grub-install: info: adding a relocation entry for 0x346e.
grub-install: info: adding a relocation entry for 0x3478.
grub-install: info: adding a relocation entry for 0x348a.
grub-install: info: adding a relocation entry for 0x34aa.
grub-install: info: adding a relocation entry for 0x34c2.
grub-install: info: adding a relocation entry for 0x34dd.
grub-install: info: adding a relocation entry for 0x34f8.
grub-install: info: adding a relocation entry for 0x363a.
grub-install: info: adding a relocation entry for 0x3652.
grub-install: info: adding a relocation entry for 0x3669.
grub-install: info: adding a relocation entry for 0x3678.
grub-install: info: adding a relocation entry for 0x3698.
grub-install: info: adding a relocation entry for 0x36a9.
grub-install: info: adding a relocation entry for 0x36b7.
grub-install: info: adding a relocation entry for 0x36ed.
grub-install: info: adding a relocation entry for 0x3711.
grub-install: info: adding a relocation entry for 0x3723.
grub-install: info: adding a relocation entry for 0x3743.
grub-install: info: adding a relocation entry for 0x3752.
grub-install: info: adding a relocation entry for 0x376a.
grub-install: info: adding a relocation entry for 0x377a.
grub-install: info: adding a relocation entry for 0x3788.
grub-install: info: adding a relocation entry for 0x379c.
grub-install: info: adding a relocation entry for 0x37b0.
grub-install: info: adding a relocation entry for 0x37c5.
grub-install: info: adding a relocation entry for 0x37d6.
grub-install: info: adding a relocation entry for 0x37ff.
grub-install: info: adding a relocation entry for 0x380a.
grub-install: info: adding a relocation entry for 0x381e.
grub-install: info: adding a relocation entry for 0x382c.
grub-install: info: adding a relocation entry for 0x3841.
grub-install: info: adding a relocation entry for 0x3854.
grub-install: info: adding a relocation entry for 0x38af.
grub-install: info: adding a relocation entry for 0x38c4.
grub-install: info: adding a relocation entry for 0x38d5.
grub-install: info: adding a relocation entry for 0x38e2.
grub-install: info: adding a relocation entry for 0x3909.
grub-install: info: adding a relocation entry for 0x392f.
grub-install: info: adding a relocation entry for 0x3940.
grub-install: info: adding a relocation entry for 0x394f.
grub-install: info: adding a relocation entry for 0x395b.
grub-install: info: adding a relocation entry for 0x396b.
grub-install: info: adding a relocation entry for 0x3975.
grub-install: info: adding a relocation entry for 0x3981.
grub-install: info: adding a relocation entry for 0x3990.
grub-install: info: adding a relocation entry for 0x399a.
grub-install: info: adding a relocation entry for 0x39a4.
grub-install: info: adding a relocation entry for 0x39b2.
grub-install: info: adding a relocation entry for 0x39c2.
grub-install: info: adding a relocation entry for 0x39d2.
grub-install: info: adding a relocation entry for 0x39dc.
grub-install: info: adding a relocation entry for 0x39e8.
grub-install: info: adding a relocation entry for 0x39f7.
grub-install: info: adding a relocation entry for 0x3a01.
grub-install: info: adding a relocation entry for 0x3a0c.
grub-install: info: adding a relocation entry for 0x3a18.
grub-install: info: adding a relocation entry for 0x3a2b.
grub-install: info: adding a relocation entry for 0x3a35.
grub-install: info: adding a relocation entry for 0x3a41.
grub-install: info: adding a relocation entry for 0x3a4d.
grub-install: info: adding a relocation entry for 0x3a5c.
grub-install: info: adding a relocation entry for 0x3a79.
grub-install: info: adding a relocation entry for 0x3a86.
grub-install: info: adding a relocation entry for 0x3aea.
grub-install: info: adding a relocation entry for 0x3b30.
grub-install: info: adding a relocation entry for 0x3b49.
grub-install: info: adding a relocation entry for 0x3b53.
grub-install: info: adding a relocation entry for 0x3b5d.
grub-install: info: adding a relocation entry for 0x3b69.
grub-install: info: adding a relocation entry for 0x3b75.
grub-install: info: adding a relocation entry for 0x3b8b.
grub-install: info: adding a relocation entry for 0x3b9a.
grub-install: info: adding a relocation entry for 0x3bc9.
grub-install: info: adding a relocation entry for 0x3bd5.
grub-install: info: adding a relocation entry for 0x3bea.
grub-install: info: adding a relocation entry for 0x3bf6.
grub-install: info: adding a relocation entry for 0x3c05.
grub-install: info: adding a relocation entry for 0x3c2b.
grub-install: info: adding a relocation entry for 0x3c70.
grub-install: info: adding a relocation entry for 0x3cb9.
grub-install: info: adding a relocation entry for 0x3cc5.
grub-install: info: adding a relocation entry for 0x3cde.
grub-install: info: adding a relocation entry for 0x3cea.
grub-install: info: adding a relocation entry for 0x3de9.
grub-install: info: adding a relocation entry for 0x3e00.
grub-install: info: adding a relocation entry for 0x3e11.
grub-install: info: adding a relocation entry for 0x3e2a.
grub-install: info: adding a relocation entry for 0x3e3f.
grub-install: info: adding a relocation entry for 0x3e5f.
grub-install: info: adding a relocation entry for 0x3e7f.
grub-install: info: adding a relocation entry for 0x3ece.
grub-install: info: adding a relocation entry for 0x3eda.
grub-install: info: adding a relocation entry for 0x3fb4.
grub-install: info: adding a relocation entry for 0x3fc1.
grub-install: info: adding a relocation entry for 0x4022.
grub-install: info: writing 272 bytes of a fixup block starting at 0x3000.
grub-install: info: adding a relocation entry for 0x408b.
grub-install: info: adding a relocation entry for 0x40d7.
grub-install: info: adding a relocation entry for 0x40f0.
grub-install: info: adding a relocation entry for 0x4105.
grub-install: info: adding a relocation entry for 0x4130.
grub-install: info: adding a relocation entry for 0x4152.
grub-install: info: adding a relocation entry for 0x4165.
grub-install: info: adding a relocation entry for 0x417d.
grub-install: info: adding a relocation entry for 0x418c.
grub-install: info: adding a relocation entry for 0x419d.
grub-install: info: adding a relocation entry for 0x41c2.
grub-install: info: adding a relocation entry for 0x420a.
grub-install: info: adding a relocation entry for 0x4223.
grub-install: info: adding a relocation entry for 0x423e.
grub-install: info: adding a relocation entry for 0x42cd.
grub-install: info: adding a relocation entry for 0x42dc.
grub-install: info: adding a relocation entry for 0x42ed.
grub-install: info: adding a relocation entry for 0x42f7.
grub-install: info: adding a relocation entry for 0x4304.
grub-install: info: adding a relocation entry for 0x430e.
grub-install: info: adding a relocation entry for 0x4328.
grub-install: info: adding a relocation entry for 0x4332.
grub-install: info: adding a relocation entry for 0x4351.
grub-install: info: adding a relocation entry for 0x435b.
grub-install: info: adding a relocation entry for 0x4367.
grub-install: info: adding a relocation entry for 0x4371.
grub-install: info: adding a relocation entry for 0x437d.
grub-install: info: adding a relocation entry for 0x4394.
grub-install: info: adding a relocation entry for 0x43a3.
grub-install: info: adding a relocation entry for 0x43b9.
grub-install: info: adding a relocation entry for 0x43d4.
grub-install: info: adding a relocation entry for 0x43ec.
grub-install: info: adding a relocation entry for 0x440f.
grub-install: info: adding a relocation entry for 0x4420.
grub-install: info: adding a relocation entry for 0x4431.
grub-install: info: adding a relocation entry for 0x4441.
grub-install: info: adding a relocation entry for 0x4457.
grub-install: info: adding a relocation entry for 0x4464.
grub-install: info: adding a relocation entry for 0x4470.
grub-install: info: adding a relocation entry for 0x4485.
grub-install: info: adding a relocation entry for 0x4497.
grub-install: info: adding a relocation entry for 0x44a1.
grub-install: info: adding a relocation entry for 0x44ad.
grub-install: info: adding a relocation entry for 0x44be.
grub-install: info: adding a relocation entry for 0x44c9.
grub-install: info: adding a relocation entry for 0x44d8.
grub-install: info: adding a relocation entry for 0x44f2.
grub-install: info: adding a relocation entry for 0x4503.
grub-install: info: adding a relocation entry for 0x4521.
grub-install: info: adding a relocation entry for 0x452d.
grub-install: info: adding a relocation entry for 0x4541.
grub-install: info: adding a relocation entry for 0x4555.
grub-install: info: adding a relocation entry for 0x4566.
grub-install: info: adding a relocation entry for 0x4573.
grub-install: info: adding a relocation entry for 0x458d.
grub-install: info: adding a relocation entry for 0x4597.
grub-install: info: adding a relocation entry for 0x45b3.
grub-install: info: adding a relocation entry for 0x45bf.
grub-install: info: adding a relocation entry for 0x45de.
grub-install: info: adding a relocation entry for 0x45f8.
grub-install: info: adding a relocation entry for 0x4609.
grub-install: info: adding a relocation entry for 0x461f.
grub-install: info: adding a relocation entry for 0x4638.
grub-install: info: adding a relocation entry for 0x4642.
grub-install: info: adding a relocation entry for 0x464c.
grub-install: info: adding a relocation entry for 0x4656.
grub-install: info: adding a relocation entry for 0x4660.
grub-install: info: adding a relocation entry for 0x4678.
grub-install: info: adding a relocation entry for 0x4685.
grub-install: info: adding a relocation entry for 0x468f.
grub-install: info: adding a relocation entry for 0x4699.
grub-install: info: adding a relocation entry for 0x46a3.
grub-install: info: adding a relocation entry for 0x46b2.
grub-install: info: adding a relocation entry for 0x46bc.
grub-install: info: adding a relocation entry for 0x46c6.
grub-install: info: adding a relocation entry for 0x46d0.
grub-install: info: adding a relocation entry for 0x46e2.
grub-install: info: adding a relocation entry for 0x46ed.
grub-install: info: adding a relocation entry for 0x46f7.
grub-install: info: adding a relocation entry for 0x4701.
grub-install: info: adding a relocation entry for 0x4713.
grub-install: info: adding a relocation entry for 0x473a.
grub-install: info: adding a relocation entry for 0x4751.
grub-install: info: adding a relocation entry for 0x4766.
grub-install: info: adding a relocation entry for 0x4772.
grub-install: info: adding a relocation entry for 0x4785.
grub-install: info: adding a relocation entry for 0x47c8.
grub-install: info: adding a relocation entry for 0x47d2.
grub-install: info: adding a relocation entry for 0x47eb.
grub-install: info: adding a relocation entry for 0x47f5.
grub-install: info: adding a relocation entry for 0x4806.
grub-install: info: adding a relocation entry for 0x481b.
grub-install: info: adding a relocation entry for 0x483a.
grub-install: info: adding a relocation entry for 0x484e.
grub-install: info: adding a relocation entry for 0x4860.
grub-install: info: adding a relocation entry for 0x4888.
grub-install: info: adding a relocation entry for 0x48a9.
grub-install: info: adding a relocation entry for 0x48c1.
grub-install: info: adding a relocation entry for 0x48d6.
grub-install: info: adding a relocation entry for 0x48e1.
grub-install: info: adding a relocation entry for 0x4914.
grub-install: info: adding a relocation entry for 0x492c.
grub-install: info: adding a relocation entry for 0x4946.
grub-install: info: adding a relocation entry for 0x4958.
grub-install: info: adding a relocation entry for 0x4965.
grub-install: info: adding a relocation entry for 0x4974.
grub-install: info: adding a relocation entry for 0x4985.
grub-install: info: adding a relocation entry for 0x49c4.
grub-install: info: adding a relocation entry for 0x49f7.
grub-install: info: adding a relocation entry for 0x4a1c.
grub-install: info: adding a relocation entry for 0x4a75.
grub-install: info: adding a relocation entry for 0x4ad3.
grub-install: info: adding a relocation entry for 0x4b04.
grub-install: info: adding a relocation entry for 0x4b44.
grub-install: info: adding a relocation entry for 0x4b76.
grub-install: info: adding a relocation entry for 0x4b8a.
grub-install: info: adding a relocation entry for 0x4ba1.
grub-install: info: adding a relocation entry for 0x4bf0.
grub-install: info: adding a relocation entry for 0x4c0d.
grub-install: info: adding a relocation entry for 0x4c27.
grub-install: info: adding a relocation entry for 0x4c3d.
grub-install: info: adding a relocation entry for 0x4ca9.
grub-install: info: adding a relocation entry for 0x4cc6.
grub-install: info: adding a relocation entry for 0x4cd5.
grub-install: info: adding a relocation entry for 0x4ce9.
grub-install: info: adding a relocation entry for 0x4d03.
grub-install: info: adding a relocation entry for 0x4d51.
grub-install: info: adding a relocation entry for 0x4d9d.
grub-install: info: adding a relocation entry for 0x4da9.
grub-install: info: adding a relocation entry for 0x4db6.
grub-install: info: adding a relocation entry for 0x4dc0.
grub-install: info: adding a relocation entry for 0x4dd1.
grub-install: info: adding a relocation entry for 0x4dde.
grub-install: info: adding a relocation entry for 0x4def.
grub-install: info: adding a relocation entry for 0x4e08.
grub-install: info: adding a relocation entry for 0x4e5a.
grub-install: info: adding a relocation entry for 0x4e65.
grub-install: info: adding a relocation entry for 0x4e70.
grub-install: info: adding a relocation entry for 0x4ea2.
grub-install: info: adding a relocation entry for 0x4eb7.
grub-install: info: adding a relocation entry for 0x4ec1.
grub-install: info: adding a relocation entry for 0x4eec.
grub-install: info: adding a relocation entry for 0x4ef6.
grub-install: info: adding a relocation entry for 0x4f05.
grub-install: info: adding a relocation entry for 0x4f17.
grub-install: info: adding a relocation entry for 0x4f3b.
grub-install: info: adding a relocation entry for 0x4f45.
grub-install: info: adding a relocation entry for 0x4f51.
grub-install: info: adding a relocation entry for 0x4f6c.
grub-install: info: adding a relocation entry for 0x4f93.
grub-install: info: adding a relocation entry for 0x4f9d.
grub-install: info: adding a relocation entry for 0x4fae.
grub-install: info: adding a relocation entry for 0x4fbf.
grub-install: info: adding a relocation entry for 0x4fd7.
grub-install: info: adding a relocation entry for 0x502d.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 320 bytes of a fixup block starting at 0x4000.
grub-install: info: adding a relocation entry for 0x5055.
grub-install: info: adding a relocation entry for 0x506a.
grub-install: info: adding a relocation entry for 0x507e.
grub-install: info: adding a relocation entry for 0x509d.
grub-install: info: adding a relocation entry for 0x50a7.
grub-install: info: adding a relocation entry for 0x50d7.
grub-install: info: adding a relocation entry for 0x50f0.
grub-install: info: adding a relocation entry for 0x5103.
grub-install: info: adding a relocation entry for 0x5124.
grub-install: info: adding a relocation entry for 0x5139.
grub-install: info: adding a relocation entry for 0x5148.
grub-install: info: adding a relocation entry for 0x5156.
grub-install: info: adding a relocation entry for 0x5162.
grub-install: info: adding a relocation entry for 0x5180.
grub-install: info: adding a relocation entry for 0x5191.
grub-install: info: adding a relocation entry for 0x51a8.
grub-install: info: adding a relocation entry for 0x51b4.
grub-install: info: adding a relocation entry for 0x51c7.
grub-install: info: adding a relocation entry for 0x51d6.
grub-install: info: adding a relocation entry for 0x51e0.
grub-install: info: adding a relocation entry for 0x51ef.
grub-install: info: adding a relocation entry for 0x51f9.
grub-install: info: adding a relocation entry for 0x5208.
grub-install: info: adding a relocation entry for 0x5217.
grub-install: info: adding a relocation entry for 0x522a.
grub-install: info: adding a relocation entry for 0x523b.
grub-install: info: adding a relocation entry for 0x52bc.
grub-install: info: adding a relocation entry for 0x52cd.
grub-install: info: adding a relocation entry for 0x531b.
grub-install: info: adding a relocation entry for 0x532c.
grub-install: info: adding a relocation entry for 0x533c.
grub-install: info: adding a relocation entry for 0x534a.
grub-install: info: adding a relocation entry for 0x5357.
grub-install: info: adding a relocation entry for 0x5361.
grub-install: info: adding a relocation entry for 0x5370.
grub-install: info: adding a relocation entry for 0x537a.
grub-install: info: adding a relocation entry for 0x5387.
grub-install: info: adding a relocation entry for 0x53c8.
grub-install: info: adding a relocation entry for 0x5408.
grub-install: info: adding a relocation entry for 0x545d.
grub-install: info: adding a relocation entry for 0x547c.
grub-install: info: adding a relocation entry for 0x54c4.
grub-install: info: adding a relocation entry for 0x5589.
grub-install: info: adding a relocation entry for 0x55a3.
grub-install: info: adding a relocation entry for 0x55ec.
grub-install: info: adding a relocation entry for 0x55f6.
grub-install: info: adding a relocation entry for 0x562a.
grub-install: info: adding a relocation entry for 0x5699.
grub-install: info: adding a relocation entry for 0x56b3.
grub-install: info: adding a relocation entry for 0x56c5.
grub-install: info: adding a relocation entry for 0x56d7.
grub-install: info: adding a relocation entry for 0x570c.
grub-install: info: adding a relocation entry for 0x5724.
grub-install: info: adding a relocation entry for 0x572f.
grub-install: info: adding a relocation entry for 0x5772.
grub-install: info: adding a relocation entry for 0x57a4.
grub-install: info: adding a relocation entry for 0x57e1.
grub-install: info: adding a relocation entry for 0x5836.
grub-install: info: adding a relocation entry for 0x5840.
grub-install: info: adding a relocation entry for 0x586a.
grub-install: info: adding a relocation entry for 0x587b.
grub-install: info: adding a relocation entry for 0x58cc.
grub-install: info: adding a relocation entry for 0x58e6.
grub-install: info: adding a relocation entry for 0x58fa.
grub-install: info: adding a relocation entry for 0x5932.
grub-install: info: adding a relocation entry for 0x593c.
grub-install: info: adding a relocation entry for 0x5948.
grub-install: info: adding a relocation entry for 0x5963.
grub-install: info: adding a relocation entry for 0x5978.
grub-install: info: adding a relocation entry for 0x59a6.
grub-install: info: adding a relocation entry for 0x59b7.
grub-install: info: adding a relocation entry for 0x59c8.
grub-install: info: adding a relocation entry for 0x59e1.
grub-install: info: adding a relocation entry for 0x5a08.
grub-install: info: adding a relocation entry for 0x5a19.
grub-install: info: adding a relocation entry for 0x5a2f.
grub-install: info: adding a relocation entry for 0x5a51.
grub-install: info: adding a relocation entry for 0x5a5d.
grub-install: info: adding a relocation entry for 0x5a6c.
grub-install: info: adding a relocation entry for 0x5a76.
grub-install: info: adding a relocation entry for 0x5a83.
grub-install: info: adding a relocation entry for 0x5a90.
grub-install: info: adding a relocation entry for 0x5aa6.
grub-install: info: adding a relocation entry for 0x5ab5.
grub-install: info: adding a relocation entry for 0x5ad1.
grub-install: info: adding a relocation entry for 0x5adb.
grub-install: info: adding a relocation entry for 0x5af4.
grub-install: info: adding a relocation entry for 0x5b0d.
grub-install: info: adding a relocation entry for 0x5b1e.
grub-install: info: adding a relocation entry for 0x5b2b.
grub-install: info: adding a relocation entry for 0x5b3c.
grub-install: info: adding a relocation entry for 0x5b4b.
grub-install: info: adding a relocation entry for 0x5b60.
grub-install: info: adding a relocation entry for 0x5b75.
grub-install: info: adding a relocation entry for 0x5b82.
grub-install: info: adding a relocation entry for 0x5b9b.
grub-install: info: adding a relocation entry for 0x5bba.
grub-install: info: adding a relocation entry for 0x5be1.
grub-install: info: adding a relocation entry for 0x5bf2.
grub-install: info: adding a relocation entry for 0x5c02.
grub-install: info: adding a relocation entry for 0x5c20.
grub-install: info: adding a relocation entry for 0x5c8d.
grub-install: info: adding a relocation entry for 0x5cd0.
grub-install: info: adding a relocation entry for 0x5ce3.
grub-install: info: adding a relocation entry for 0x5d2d.
grub-install: info: adding a relocation entry for 0x5d40.
grub-install: info: adding a relocation entry for 0x5dc4.
grub-install: info: adding a relocation entry for 0x5dd5.
grub-install: info: adding a relocation entry for 0x5e4b.
grub-install: info: adding a relocation entry for 0x5e8f.
grub-install: info: adding a relocation entry for 0x5ea2.
grub-install: info: adding a relocation entry for 0x5f37.
grub-install: info: adding a relocation entry for 0x5f85.
grub-install: info: adding a relocation entry for 0x5f94.
grub-install: info: adding a relocation entry for 0x5fa3.
grub-install: info: adding a relocation entry for 0x5fad.
grub-install: info: adding a relocation entry for 0x5fd4.
grub-install: info: adding a relocation entry for 0x6022.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 248 bytes of a fixup block starting at 0x5000.
grub-install: info: adding a relocation entry for 0x6033.
grub-install: info: adding a relocation entry for 0x605f.
grub-install: info: adding a relocation entry for 0x60bc.
grub-install: info: adding a relocation entry for 0x60e7.
grub-install: info: adding a relocation entry for 0x60f5.
grub-install: info: adding a relocation entry for 0x60ff.
grub-install: info: adding a relocation entry for 0x610e.
grub-install: info: adding a relocation entry for 0x6120.
grub-install: info: adding a relocation entry for 0x612a.
grub-install: info: adding a relocation entry for 0x6139.
grub-install: info: adding a relocation entry for 0x614b.
grub-install: info: adding a relocation entry for 0x6155.
grub-install: info: adding a relocation entry for 0x6164.
grub-install: info: adding a relocation entry for 0x6173.
grub-install: info: adding a relocation entry for 0x618b.
grub-install: info: adding a relocation entry for 0x619c.
grub-install: info: adding a relocation entry for 0x61da.
grub-install: info: adding a relocation entry for 0x6203.
grub-install: info: adding a relocation entry for 0x621e.
grub-install: info: adding a relocation entry for 0x6241.
grub-install: info: adding a relocation entry for 0x6252.
grub-install: info: adding a relocation entry for 0x6260.
grub-install: info: adding a relocation entry for 0x627a.
grub-install: info: adding a relocation entry for 0x6294.
grub-install: info: adding a relocation entry for 0x62ab.
grub-install: info: adding a relocation entry for 0x62c0.
grub-install: info: adding a relocation entry for 0x62d1.
grub-install: info: adding a relocation entry for 0x62e9.
grub-install: info: adding a relocation entry for 0x62fd.
grub-install: info: adding a relocation entry for 0x6321.
grub-install: info: adding a relocation entry for 0x6330.
grub-install: info: adding a relocation entry for 0x6345.
grub-install: info: adding a relocation entry for 0x6362.
grub-install: info: adding a relocation entry for 0x636c.
grub-install: info: adding a relocation entry for 0x637d.
grub-install: info: adding a relocation entry for 0x6396.
grub-install: info: adding a relocation entry for 0x63a0.
grub-install: info: adding a relocation entry for 0x63b7.
grub-install: info: adding a relocation entry for 0x63c9.
grub-install: info: adding a relocation entry for 0x63e1.
grub-install: info: adding a relocation entry for 0x63f4.
grub-install: info: adding a relocation entry for 0x6405.
grub-install: info: adding a relocation entry for 0x641d.
grub-install: info: adding a relocation entry for 0x6427.
grub-install: info: adding a relocation entry for 0x6441.
grub-install: info: adding a relocation entry for 0x6481.
grub-install: info: adding a relocation entry for 0x648d.
grub-install: info: adding a relocation entry for 0x64c0.
grub-install: info: adding a relocation entry for 0x64f6.
grub-install: info: adding a relocation entry for 0x6519.
grub-install: info: adding a relocation entry for 0x652f.
grub-install: info: adding a relocation entry for 0x654b.
grub-install: info: adding a relocation entry for 0x656f.
grub-install: info: adding a relocation entry for 0x65c7.
grub-install: info: adding a relocation entry for 0x65dd.
grub-install: info: adding a relocation entry for 0x65ec.
grub-install: info: adding a relocation entry for 0x661e.
grub-install: info: adding a relocation entry for 0x6647.
grub-install: info: adding a relocation entry for 0x6651.
grub-install: info: adding a relocation entry for 0x667a.
grub-install: info: adding a relocation entry for 0x66a0.
grub-install: info: adding a relocation entry for 0x66bd.
grub-install: info: adding a relocation entry for 0x6735.
grub-install: info: adding a relocation entry for 0x674b.
grub-install: info: adding a relocation entry for 0x6758.
grub-install: info: adding a relocation entry for 0x6767.
grub-install: info: adding a relocation entry for 0x678b.
grub-install: info: adding a relocation entry for 0x67a1.
grub-install: info: adding a relocation entry for 0x67ae.
grub-install: info: adding a relocation entry for 0x67db.
grub-install: info: adding a relocation entry for 0x6815.
grub-install: info: adding a relocation entry for 0x682e.
grub-install: info: adding a relocation entry for 0x6838.
grub-install: info: adding a relocation entry for 0x684b.
grub-install: info: adding a relocation entry for 0x685c.
grub-install: info: adding a relocation entry for 0x6873.
grub-install: info: adding a relocation entry for 0x687f.
grub-install: info: adding a relocation entry for 0x688f.
grub-install: info: adding a relocation entry for 0x689a.
grub-install: info: adding a relocation entry for 0x68a5.
grub-install: info: adding a relocation entry for 0x68b5.
grub-install: info: adding a relocation entry for 0x68c0.
grub-install: info: adding a relocation entry for 0x68cc.
grub-install: info: adding a relocation entry for 0x68d7.
grub-install: info: adding a relocation entry for 0x68e8.
grub-install: info: adding a relocation entry for 0x68f1.
grub-install: info: adding a relocation entry for 0x6909.
grub-install: info: adding a relocation entry for 0x691b.
grub-install: info: adding a relocation entry for 0x6925.
grub-install: info: adding a relocation entry for 0x6939.
grub-install: info: adding a relocation entry for 0x6947.
grub-install: info: adding a relocation entry for 0x6956.
grub-install: info: adding a relocation entry for 0x6960.
grub-install: info: adding a relocation entry for 0x696c.
grub-install: info: adding a relocation entry for 0x6979.
grub-install: info: adding a relocation entry for 0x6986.
grub-install: info: adding a relocation entry for 0x6991.
grub-install: info: adding a relocation entry for 0x699b.
grub-install: info: adding a relocation entry for 0x69ab.
grub-install: info: adding a relocation entry for 0x69ba.
grub-install: info: adding a relocation entry for 0x69c6.
grub-install: info: adding a relocation entry for 0x69d3.
grub-install: info: adding a relocation entry for 0x69f2.
grub-install: info: adding a relocation entry for 0x6a08.
grub-install: info: adding a relocation entry for 0x6a17.
grub-install: info: adding a relocation entry for 0x6a2a.
grub-install: info: adding a relocation entry for 0x6a50.
grub-install: info: adding a relocation entry for 0x6a7e.
grub-install: info: adding a relocation entry for 0x6a8f.
grub-install: info: adding a relocation entry for 0x6ad1.
grub-install: info: adding a relocation entry for 0x6b25.
grub-install: info: adding a relocation entry for 0x6b34.
grub-install: info: adding a relocation entry for 0x6b44.
grub-install: info: adding a relocation entry for 0x6b54.
grub-install: info: adding a relocation entry for 0x6b6b.
grub-install: info: adding a relocation entry for 0x6b91.
grub-install: info: adding a relocation entry for 0x6ba9.
grub-install: info: adding a relocation entry for 0x6bbb.
grub-install: info: adding a relocation entry for 0x6bd5.
grub-install: info: adding a relocation entry for 0x6bff.
grub-install: info: adding a relocation entry for 0x6c12.
grub-install: info: adding a relocation entry for 0x6c43.
grub-install: info: adding a relocation entry for 0x6c58.
grub-install: info: adding a relocation entry for 0x6c62.
grub-install: info: adding a relocation entry for 0x6c99.
grub-install: info: adding a relocation entry for 0x6caa.
grub-install: info: adding a relocation entry for 0x6cb4.
grub-install: info: adding a relocation entry for 0x6cbe.
grub-install: info: adding a relocation entry for 0x6ccf.
grub-install: info: adding a relocation entry for 0x6ce2.
grub-install: info: adding a relocation entry for 0x6cec.
grub-install: info: adding a relocation entry for 0x6cf6.
grub-install: info: adding a relocation entry for 0x6d07.
grub-install: info: adding a relocation entry for 0x6d2a.
grub-install: info: adding a relocation entry for 0x6d3c.
grub-install: info: adding a relocation entry for 0x6d64.
grub-install: info: adding a relocation entry for 0x6e5c.
grub-install: info: adding a relocation entry for 0x6eba.
grub-install: info: adding a relocation entry for 0x6eff.
grub-install: info: adding a relocation entry for 0x6f0e.
grub-install: info: adding a relocation entry for 0x6f20.
grub-install: info: adding a relocation entry for 0x6f31.
grub-install: info: adding a relocation entry for 0x6f58.
grub-install: info: adding a relocation entry for 0x6f6c.
grub-install: info: adding a relocation entry for 0x6f9a.
grub-install: info: adding a relocation entry for 0x6fca.
grub-install: info: adding a relocation entry for 0x6fdb.
grub-install: info: adding a relocation entry for 0x700a.
grub-install: info: writing 304 bytes of a fixup block starting at 0x6000.
grub-install: info: adding a relocation entry for 0x7018.
grub-install: info: adding a relocation entry for 0x7046.
grub-install: info: adding a relocation entry for 0x7050.
grub-install: info: adding a relocation entry for 0x7068.
grub-install: info: adding a relocation entry for 0x7072.
grub-install: info: adding a relocation entry for 0x7081.
grub-install: info: adding a relocation entry for 0x7090.
grub-install: info: adding a relocation entry for 0x709a.
grub-install: info: adding a relocation entry for 0x70aa.
grub-install: info: adding a relocation entry for 0x70bd.
grub-install: info: adding a relocation entry for 0x70cf.
grub-install: info: adding a relocation entry for 0x70d9.
grub-install: info: adding a relocation entry for 0x70e8.
grub-install: info: adding a relocation entry for 0x70f5.
grub-install: info: adding a relocation entry for 0x7100.
grub-install: info: adding a relocation entry for 0x711a.
grub-install: info: adding a relocation entry for 0x712d.
grub-install: info: adding a relocation entry for 0x7141.
grub-install: info: adding a relocation entry for 0x7158.
grub-install: info: adding a relocation entry for 0x7164.
grub-install: info: adding a relocation entry for 0x7173.
grub-install: info: adding a relocation entry for 0x717d.
grub-install: info: adding a relocation entry for 0x718e.
grub-install: info: adding a relocation entry for 0x719b.
grub-install: info: adding a relocation entry for 0x71a9.
grub-install: info: adding a relocation entry for 0x71bf.
grub-install: info: adding a relocation entry for 0x71ca.
grub-install: info: adding a relocation entry for 0x71d7.
grub-install: info: adding a relocation entry for 0x71e1.
grub-install: info: adding a relocation entry for 0x71f4.
grub-install: info: adding a relocation entry for 0x71ff.
grub-install: info: adding a relocation entry for 0x721d.
grub-install: info: adding a relocation entry for 0x722e.
grub-install: info: adding a relocation entry for 0x7246.
grub-install: info: adding a relocation entry for 0x72c8.
grub-install: info: adding a relocation entry for 0x72e8.
grub-install: info: adding a relocation entry for 0x72f8.
grub-install: info: adding a relocation entry for 0x7305.
grub-install: info: adding a relocation entry for 0x7323.
grub-install: info: adding a relocation entry for 0x7337.
grub-install: info: adding a relocation entry for 0x735e.
grub-install: info: adding a relocation entry for 0x739f.
grub-install: info: adding a relocation entry for 0x73b2.
grub-install: info: adding a relocation entry for 0x73be.
grub-install: info: adding a relocation entry for 0x73d6.
grub-install: info: adding a relocation entry for 0x73e9.
grub-install: info: adding a relocation entry for 0x7412.
grub-install: info: adding a relocation entry for 0x7420.
grub-install: info: adding a relocation entry for 0x7457.
grub-install: info: adding a relocation entry for 0x7461.
grub-install: info: adding a relocation entry for 0x746b.
grub-install: info: adding a relocation entry for 0x7477.
grub-install: info: adding a relocation entry for 0x7486.
grub-install: info: adding a relocation entry for 0x74a3.
grub-install: info: adding a relocation entry for 0x74b2.
grub-install: info: adding a relocation entry for 0x74c9.
grub-install: info: adding a relocation entry for 0x7522.
grub-install: info: adding a relocation entry for 0x752c.
grub-install: info: adding a relocation entry for 0x7536.
grub-install: info: adding a relocation entry for 0x754a.
grub-install: info: adding a relocation entry for 0x7577.
grub-install: info: adding a relocation entry for 0x7581.
grub-install: info: adding a relocation entry for 0x758b.
grub-install: info: adding a relocation entry for 0x75ab.
grub-install: info: adding a relocation entry for 0x75b5.
grub-install: info: adding a relocation entry for 0x75c1.
grub-install: info: adding a relocation entry for 0x75cb.
grub-install: info: adding a relocation entry for 0x75da.
grub-install: info: adding a relocation entry for 0x75fd.
grub-install: info: adding a relocation entry for 0x761c.
grub-install: info: adding a relocation entry for 0x7644.
grub-install: info: adding a relocation entry for 0x76aa.
grub-install: info: adding a relocation entry for 0x76c2.
grub-install: info: adding a relocation entry for 0x76dd.
grub-install: info: adding a relocation entry for 0x7717.
grub-install: info: adding a relocation entry for 0x7721.
grub-install: info: adding a relocation entry for 0x7742.
grub-install: info: adding a relocation entry for 0x7756.
grub-install: info: adding a relocation entry for 0x7767.
grub-install: info: adding a relocation entry for 0x7773.
grub-install: info: adding a relocation entry for 0x778a.
grub-install: info: adding a relocation entry for 0x7794.
grub-install: info: adding a relocation entry for 0x77a3.
grub-install: info: adding a relocation entry for 0x77b2.
grub-install: info: adding a relocation entry for 0x77bc.
grub-install: info: adding a relocation entry for 0x77cb.
grub-install: info: adding a relocation entry for 0x77dc.
grub-install: info: adding a relocation entry for 0x77e6.
grub-install: info: adding a relocation entry for 0x77f2.
grub-install: info: adding a relocation entry for 0x77fe.
grub-install: info: adding a relocation entry for 0x780a.
grub-install: info: adding a relocation entry for 0x781c.
grub-install: info: adding a relocation entry for 0x7826.
grub-install: info: adding a relocation entry for 0x7832.
grub-install: info: adding a relocation entry for 0x7844.
grub-install: info: adding a relocation entry for 0x7850.
grub-install: info: adding a relocation entry for 0x785a.
grub-install: info: adding a relocation entry for 0x7866.
grub-install: info: adding a relocation entry for 0x7874.
grub-install: info: adding a relocation entry for 0x787e.
grub-install: info: adding a relocation entry for 0x7887.
grub-install: info: adding a relocation entry for 0x7894.
grub-install: info: adding a relocation entry for 0x78af.
grub-install: info: adding a relocation entry for 0x78d9.
grub-install: info: adding a relocation entry for 0x78ef.
grub-install: info: adding a relocation entry for 0x7907.
grub-install: info: adding a relocation entry for 0x7913.
grub-install: info: adding a relocation entry for 0x7925.
grub-install: info: adding a relocation entry for 0x793c.
grub-install: info: adding a relocation entry for 0x7948.
grub-install: info: adding a relocation entry for 0x796f.
grub-install: info: adding a relocation entry for 0x79d6.
grub-install: info: adding a relocation entry for 0x79e4.
grub-install: info: adding a relocation entry for 0x7ad3.
grub-install: info: adding a relocation entry for 0x7b1a.
grub-install: info: adding a relocation entry for 0x7b8b.
grub-install: info: adding a relocation entry for 0x7c3a.
grub-install: info: adding a relocation entry for 0x7c58.
grub-install: info: adding a relocation entry for 0x7c79.
grub-install: info: adding a relocation entry for 0x7c95.
grub-install: info: adding a relocation entry for 0x7ca7.
grub-install: info: adding a relocation entry for 0x7cc7.
grub-install: info: adding a relocation entry for 0x7d46.
grub-install: info: adding a relocation entry for 0x7df2.
grub-install: info: adding a relocation entry for 0x7e03.
grub-install: info: adding a relocation entry for 0x7e14.
grub-install: info: adding a relocation entry for 0x7e45.
grub-install: info: adding a relocation entry for 0x7e56.
grub-install: info: adding a relocation entry for 0x7f84.
grub-install: info: adding a relocation entry for 0x7f9c.
grub-install: info: adding a relocation entry for 0x7fcc.
grub-install: info: adding a relocation entry for 0x7fd6.
grub-install: info: adding a relocation entry for 0x8120.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 280 bytes of a fixup block starting at 0x7000.
grub-install: info: adding a relocation entry for 0x81c7.
grub-install: info: adding a relocation entry for 0x826d.
grub-install: info: adding a relocation entry for 0x82b7.
grub-install: info: adding a relocation entry for 0x8410.
grub-install: info: adding a relocation entry for 0x844d.
grub-install: info: adding a relocation entry for 0x8590.
grub-install: info: adding a relocation entry for 0x866d.
grub-install: info: adding a relocation entry for 0x8677.
grub-install: info: adding a relocation entry for 0x8688.
grub-install: info: adding a relocation entry for 0x86a9.
grub-install: info: adding a relocation entry for 0x86c6.
grub-install: info: adding a relocation entry for 0x86dc.
grub-install: info: adding a relocation entry for 0x86e5.
grub-install: info: adding a relocation entry for 0x86f0.
grub-install: info: adding a relocation entry for 0x86f9.
grub-install: info: adding a relocation entry for 0x8702.
grub-install: info: adding a relocation entry for 0x870d.
grub-install: info: adding a relocation entry for 0x872e.
grub-install: info: adding a relocation entry for 0x873a.
grub-install: info: adding a relocation entry for 0x8749.
grub-install: info: adding a relocation entry for 0x875b.
grub-install: info: adding a relocation entry for 0x87b0.
grub-install: info: adding a relocation entry for 0x87c4.
grub-install: info: adding a relocation entry for 0x8813.
grub-install: info: adding a relocation entry for 0x8826.
grub-install: info: adding a relocation entry for 0x883d.
grub-install: info: adding a relocation entry for 0x886a.
grub-install: info: adding a relocation entry for 0x8877.
grub-install: info: adding a relocation entry for 0x8899.
grub-install: info: adding a relocation entry for 0x88a3.
grub-install: info: adding a relocation entry for 0x88d8.
grub-install: info: adding a relocation entry for 0x88e4.
grub-install: info: adding a relocation entry for 0x890b.
grub-install: info: adding a relocation entry for 0x893c.
grub-install: info: adding a relocation entry for 0x894d.
grub-install: info: adding a relocation entry for 0x89a3.
grub-install: info: adding a relocation entry for 0x89b9.
grub-install: info: adding a relocation entry for 0x89e1.
grub-install: info: adding a relocation entry for 0x8a03.
grub-install: info: adding a relocation entry for 0x8a1a.
grub-install: info: adding a relocation entry for 0x8a2b.
grub-install: info: adding a relocation entry for 0x8a8d.
grub-install: info: adding a relocation entry for 0x8a9f.
grub-install: info: adding a relocation entry for 0x8ae2.
grub-install: info: adding a relocation entry for 0x8af6.
grub-install: info: adding a relocation entry for 0x8b04.
grub-install: info: adding a relocation entry for 0x8b10.
grub-install: info: adding a relocation entry for 0x8b20.
grub-install: info: adding a relocation entry for 0x8b2e.
grub-install: info: adding a relocation entry for 0x8b3a.
grub-install: info: adding a relocation entry for 0x8b83.
grub-install: info: adding a relocation entry for 0x8ba0.
grub-install: info: adding a relocation entry for 0x8bb5.
grub-install: info: adding a relocation entry for 0x8beb.
grub-install: info: adding a relocation entry for 0x8c41.
grub-install: info: adding a relocation entry for 0x8c76.
grub-install: info: adding a relocation entry for 0x8d5d.
grub-install: info: adding a relocation entry for 0x8d67.
grub-install: info: adding a relocation entry for 0x8d98.
grub-install: info: adding a relocation entry for 0x8da7.
grub-install: info: adding a relocation entry for 0x8de0.
grub-install: info: adding a relocation entry for 0x8e4e.
grub-install: info: adding a relocation entry for 0x8e64.
grub-install: info: adding a relocation entry for 0x8e83.
grub-install: info: adding a relocation entry for 0x8eb9.
grub-install: info: adding a relocation entry for 0x8ede.
grub-install: info: adding a relocation entry for 0x8f07.
grub-install: info: adding a relocation entry for 0x8f12.
grub-install: info: adding a relocation entry for 0x8f65.
grub-install: info: adding a relocation entry for 0x8f70.
grub-install: info: adding a relocation entry for 0x8f9d.
grub-install: info: adding a relocation entry for 0x8fae.
grub-install: info: adding a relocation entry for 0x8fc1.
grub-install: info: adding a relocation entry for 0x9012.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 160 bytes of a fixup block starting at 0x8000.
grub-install: info: adding a relocation entry for 0x9024.
grub-install: info: adding a relocation entry for 0x9065.
grub-install: info: adding a relocation entry for 0x9075.
grub-install: info: adding a relocation entry for 0x9098.
grub-install: info: adding a relocation entry for 0x90c0.
grub-install: info: adding a relocation entry for 0x90d8.
grub-install: info: adding a relocation entry for 0x90e8.
grub-install: info: adding a relocation entry for 0x9148.
grub-install: info: adding a relocation entry for 0x9167.
grub-install: info: adding a relocation entry for 0x9195.
grub-install: info: adding a relocation entry for 0x91aa.
grub-install: info: adding a relocation entry for 0x91d8.
grub-install: info: adding a relocation entry for 0x91f8.
grub-install: info: adding a relocation entry for 0x9202.
grub-install: info: adding a relocation entry for 0x9234.
grub-install: info: adding a relocation entry for 0x9259.
grub-install: info: adding a relocation entry for 0x9263.
grub-install: info: adding a relocation entry for 0x9272.
grub-install: info: adding a relocation entry for 0x9283.
grub-install: info: adding a relocation entry for 0x932c.
grub-install: info: adding a relocation entry for 0x9341.
grub-install: info: adding a relocation entry for 0x9355.
grub-install: info: adding a relocation entry for 0x935f.
grub-install: info: adding a relocation entry for 0x9371.
grub-install: info: adding a relocation entry for 0x9380.
grub-install: info: adding a relocation entry for 0x93c0.
grub-install: info: adding a relocation entry for 0x9424.
grub-install: info: adding a relocation entry for 0x9436.
grub-install: info: adding a relocation entry for 0x944d.
grub-install: info: adding a relocation entry for 0x9486.
grub-install: info: adding a relocation entry for 0x949b.
grub-install: info: adding a relocation entry for 0x94bb.
grub-install: info: adding a relocation entry for 0x94d1.
grub-install: info: adding a relocation entry for 0x951c.
grub-install: info: adding a relocation entry for 0x954e.
grub-install: info: adding a relocation entry for 0x9573.
grub-install: info: adding a relocation entry for 0x9583.
grub-install: info: adding a relocation entry for 0x95ae.
grub-install: info: adding a relocation entry for 0x95ba.
grub-install: info: adding a relocation entry for 0x95c6.
grub-install: info: adding a relocation entry for 0x95d0.
grub-install: info: adding a relocation entry for 0x95e4.
grub-install: info: adding a relocation entry for 0x95f0.
grub-install: info: adding a relocation entry for 0x9601.
grub-install: info: adding a relocation entry for 0x9616.
grub-install: info: adding a relocation entry for 0x9628.
grub-install: info: adding a relocation entry for 0x9635.
grub-install: info: adding a relocation entry for 0x964a.
grub-install: info: adding a relocation entry for 0x9661.
grub-install: info: adding a relocation entry for 0x966b.
grub-install: info: adding a relocation entry for 0x968c.
grub-install: info: adding a relocation entry for 0x96b1.
grub-install: info: adding a relocation entry for 0x96db.
grub-install: info: adding a relocation entry for 0x96e7.
grub-install: info: adding a relocation entry for 0x96f3.
grub-install: info: adding a relocation entry for 0x970d.
grub-install: info: adding a relocation entry for 0x9717.
grub-install: info: adding a relocation entry for 0x9723.
grub-install: info: adding a relocation entry for 0x972f.
grub-install: info: adding a relocation entry for 0x9739.
grub-install: info: adding a relocation entry for 0x9753.
grub-install: info: adding a relocation entry for 0x975f.
grub-install: info: adding a relocation entry for 0x976f.
grub-install: info: adding a relocation entry for 0x9779.
grub-install: info: adding a relocation entry for 0x978f.
grub-install: info: adding a relocation entry for 0x97af.
grub-install: info: adding a relocation entry for 0x97c0.
grub-install: info: adding a relocation entry for 0x980a.
grub-install: info: adding a relocation entry for 0x9842.
grub-install: info: adding a relocation entry for 0x9859.
grub-install: info: adding a relocation entry for 0x987b.
grub-install: info: adding a relocation entry for 0x98af.
grub-install: info: adding a relocation entry for 0x98c3.
grub-install: info: adding a relocation entry for 0x98d4.
grub-install: info: adding a relocation entry for 0x98fa.
grub-install: info: adding a relocation entry for 0x9922.
grub-install: info: adding a relocation entry for 0x992c.
grub-install: info: adding a relocation entry for 0x9941.
grub-install: info: adding a relocation entry for 0x994c.
grub-install: info: translating the relocation section .rela.rodata.
grub-install: info: adding a relocation entry for 0x9a00.
grub-install: info: adding a relocation entry for 0x9a08.
grub-install: info: adding a relocation entry for 0x9a10.
grub-install: info: adding a relocation entry for 0x9a18.
grub-install: info: adding a relocation entry for 0x9a20.
grub-install: info: adding a relocation entry for 0x9a28.
grub-install: info: adding a relocation entry for 0x9a30.
grub-install: info: adding a relocation entry for 0x9a38.
grub-install: info: adding a relocation entry for 0x9a40.
grub-install: info: adding a relocation entry for 0x9a48.
grub-install: info: adding a relocation entry for 0x9a50.
grub-install: info: adding a relocation entry for 0x9a58.
grub-install: info: adding a relocation entry for 0x9a60.
grub-install: info: adding a relocation entry for 0x9a68.
grub-install: info: adding a relocation entry for 0x9a70.
grub-install: info: adding a relocation entry for 0x9a78.
grub-install: info: adding a relocation entry for 0x9a80.
grub-install: info: adding a relocation entry for 0x9a88.
grub-install: info: adding a relocation entry for 0x9a90.
grub-install: info: adding a relocation entry for 0x9a98.
grub-install: info: adding a relocation entry for 0x9aa0.
grub-install: info: adding a relocation entry for 0x9aa8.
grub-install: info: adding a relocation entry for 0x9ab0.
grub-install: info: adding a relocation entry for 0x9ab8.
grub-install: info: adding a relocation entry for 0x9ac0.
grub-install: info: adding a relocation entry for 0x9ac8.
grub-install: info: adding a relocation entry for 0x9ad0.
grub-install: info: adding a relocation entry for 0x9ad8.
grub-install: info: adding a relocation entry for 0x9b40.
grub-install: info: adding a relocation entry for 0x9b48.
grub-install: info: adding a relocation entry for 0x9b50.
grub-install: info: adding a relocation entry for 0x9b58.
grub-install: info: adding a relocation entry for 0x9b60.
grub-install: info: adding a relocation entry for 0x9b68.
grub-install: info: adding a relocation entry for 0x9b70.
grub-install: info: adding a relocation entry for 0x9b78.
grub-install: info: adding a relocation entry for 0x9b80.
grub-install: info: adding a relocation entry for 0x9b88.
grub-install: info: adding a relocation entry for 0x9b90.
grub-install: info: translating the relocation section .rela.data.
grub-install: info: adding a relocation entry for 0xb4e0.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 248 bytes of a fixup block starting at 0x9000.
grub-install: info: adding a relocation entry for 0xb4f0.
grub-install: info: adding a relocation entry for 0xb4f8.
grub-install: info: adding a relocation entry for 0xb500.
grub-install: info: adding a relocation entry for 0xb508.
grub-install: info: adding a relocation entry for 0xb510.
grub-install: info: adding a relocation entry for 0xb570.
grub-install: info: adding a relocation entry for 0xb588.
grub-install: info: adding a relocation entry for 0xb5b0.
grub-install: info: adding a relocation entry for 0xb5b8.
grub-install: info: adding a relocation entry for 0xb5c0.
grub-install: info: adding a relocation entry for 0xb5c8.
grub-install: info: adding a relocation entry for 0xb5d8.
grub-install: info: adding a relocation entry for 0xb5e0.
grub-install: info: adding a relocation entry for 0xb5e8.
grub-install: info: adding a relocation entry for 0xb5f0.
grub-install: info: adding a relocation entry for 0xb5f8.
grub-install: info: adding a relocation entry for 0xb600.
grub-install: info: adding a relocation entry for 0xb630.
grub-install: info: adding a relocation entry for 0xb650.
grub-install: info: adding a relocation entry for 0xb660.
grub-install: info: adding a relocation entry for 0xb668.
grub-install: info: adding a relocation entry for 0xb690.
grub-install: info: adding a relocation entry for 0xb7e0.
grub-install: info: adding a relocation entry for 0xb7f0.
grub-install: info: adding a relocation entry for 0xb7f8.
grub-install: info: adding a relocation entry for 0xb808.
grub-install: info: adding a relocation entry for 0xb810.
grub-install: info: adding a relocation entry for 0xb820.
grub-install: info: adding a relocation entry for 0xb828.
grub-install: info: adding a relocation entry for 0xb838.
grub-install: info: adding a relocation entry for 0xb840.
grub-install: info: adding a relocation entry for 0xb850.
grub-install: info: adding a relocation entry for 0xb858.
grub-install: info: adding a relocation entry for 0xb868.
grub-install: info: adding a relocation entry for 0xb870.
grub-install: info: adding a relocation entry for 0xb880.
grub-install: info: adding a relocation entry for 0xb888.
grub-install: info: adding a relocation entry for 0xb898.
grub-install: info: adding a relocation entry for 0xb8a0.
grub-install: info: adding a relocation entry for 0xb8b0.
grub-install: info: adding a relocation entry for 0xb8b8.
grub-install: info: adding a relocation entry for 0xb8c8.
grub-install: info: adding a relocation entry for 0xb8d0.
grub-install: info: adding a relocation entry for 0xb8e0.
grub-install: info: adding a relocation entry for 0xb8e8.
grub-install: info: adding a relocation entry for 0xb8f8.
grub-install: info: adding a relocation entry for 0xb900.
grub-install: info: adding a relocation entry for 0xb910.
grub-install: info: adding a relocation entry for 0xb918.
grub-install: info: adding a relocation entry for 0xb928.
grub-install: info: adding a relocation entry for 0xb930.
grub-install: info: adding a relocation entry for 0xb940.
grub-install: info: adding a relocation entry for 0xb948.
grub-install: info: adding a relocation entry for 0xb958.
grub-install: info: adding a relocation entry for 0xb960.
grub-install: info: adding a relocation entry for 0xb970.
grub-install: info: adding a relocation entry for 0xb978.
grub-install: info: adding a relocation entry for 0xb988.
grub-install: info: adding a relocation entry for 0xb990.
grub-install: info: adding a relocation entry for 0xb9a0.
grub-install: info: adding a relocation entry for 0xb9a8.
grub-install: info: adding a relocation entry for 0xb9b8.
grub-install: info: adding a relocation entry for 0xb9c0.
grub-install: info: adding a relocation entry for 0xb9d0.
grub-install: info: adding a relocation entry for 0xb9d8.
grub-install: info: adding a relocation entry for 0xb9e8.
grub-install: info: adding a relocation entry for 0xb9f0.
grub-install: info: adding a relocation entry for 0xba00.
grub-install: info: adding a relocation entry for 0xba08.
grub-install: info: adding a relocation entry for 0xba18.
grub-install: info: adding a relocation entry for 0xba20.
grub-install: info: adding a relocation entry for 0xba30.
grub-install: info: adding a relocation entry for 0xba38.
grub-install: info: adding a relocation entry for 0xba48.
grub-install: info: adding a relocation entry for 0xba50.
grub-install: info: adding a relocation entry for 0xba60.
grub-install: info: adding a relocation entry for 0xba68.
grub-install: info: adding a relocation entry for 0xba78.
grub-install: info: adding a relocation entry for 0xba80.
grub-install: info: adding a relocation entry for 0xba90.
grub-install: info: adding a relocation entry for 0xba98.
grub-install: info: adding a relocation entry for 0xbaa8.
grub-install: info: adding a relocation entry for 0xbab0.
grub-install: info: adding a relocation entry for 0xbac0.
grub-install: info: adding a relocation entry for 0xbac8.
grub-install: info: adding a relocation entry for 0xbad8.
grub-install: info: adding a relocation entry for 0xbae0.
grub-install: info: adding a relocation entry for 0xbaf0.
grub-install: info: adding a relocation entry for 0xbaf8.
grub-install: info: adding a relocation entry for 0xbb08.
grub-install: info: adding a relocation entry for 0xbb10.
grub-install: info: adding a relocation entry for 0xbb20.
grub-install: info: adding a relocation entry for 0xbb28.
grub-install: info: adding a relocation entry for 0xbb38.
grub-install: info: adding a relocation entry for 0xbb40.
grub-install: info: adding a relocation entry for 0xbb50.
grub-install: info: adding a relocation entry for 0xbb58.
grub-install: info: adding a relocation entry for 0xbb68.
grub-install: info: adding a relocation entry for 0xbb70.
grub-install: info: adding a relocation entry for 0xbb80.
grub-install: info: adding a relocation entry for 0xbb88.
grub-install: info: adding a relocation entry for 0xbb98.
grub-install: info: adding a relocation entry for 0xbba0.
grub-install: info: adding a relocation entry for 0xbbb0.
grub-install: info: adding a relocation entry for 0xbbb8.
grub-install: info: adding a relocation entry for 0xbbc8.
grub-install: info: adding a relocation entry for 0xbbd0.
grub-install: info: adding a relocation entry for 0xbbe0.
grub-install: info: adding a relocation entry for 0xbbe8.
grub-install: info: adding a relocation entry for 0xbbf8.
grub-install: info: adding a relocation entry for 0xbc00.
grub-install: info: adding a relocation entry for 0xbc10.
grub-install: info: adding a relocation entry for 0xbc18.
grub-install: info: adding a relocation entry for 0xbc28.
grub-install: info: adding a relocation entry for 0xbc30.
grub-install: info: adding a relocation entry for 0xbc40.
grub-install: info: adding a relocation entry for 0xbc48.
grub-install: info: adding a relocation entry for 0xbc58.
grub-install: info: adding a relocation entry for 0xbc60.
grub-install: info: adding a relocation entry for 0xbc70.
grub-install: info: adding a relocation entry for 0xbc78.
grub-install: info: adding a relocation entry for 0xbc88.
grub-install: info: adding a relocation entry for 0xbc90.
grub-install: info: adding a relocation entry for 0xbca0.
grub-install: info: adding a relocation entry for 0xbca8.
grub-install: info: adding a relocation entry for 0xbcb8.
grub-install: info: adding a relocation entry for 0xbcc0.
grub-install: info: adding a relocation entry for 0xbcd0.
grub-install: info: adding a relocation entry for 0xbcd8.
grub-install: info: adding a relocation entry for 0xbce8.
grub-install: info: adding a relocation entry for 0xbcf0.
grub-install: info: adding a relocation entry for 0xbd00.
grub-install: info: adding a relocation entry for 0xbd08.
grub-install: info: adding a relocation entry for 0xbd18.
grub-install: info: adding a relocation entry for 0xbd20.
grub-install: info: adding a relocation entry for 0xbd30.
grub-install: info: adding a relocation entry for 0xbd38.
grub-install: info: adding a relocation entry for 0xbd48.
grub-install: info: adding a relocation entry for 0xbd50.
grub-install: info: adding a relocation entry for 0xbd60.
grub-install: info: adding a relocation entry for 0xbd68.
grub-install: info: adding a relocation entry for 0xbd78.
grub-install: info: adding a relocation entry for 0xbd80.
grub-install: info: adding a relocation entry for 0xbd90.
grub-install: info: adding a relocation entry for 0xbd98.
grub-install: info: adding a relocation entry for 0xbda8.
grub-install: info: adding a relocation entry for 0xbdb0.
grub-install: info: adding a relocation entry for 0xbdc0.
grub-install: info: adding a relocation entry for 0xbdc8.
grub-install: info: adding a relocation entry for 0xbdd8.
grub-install: info: adding a relocation entry for 0xbde0.
grub-install: info: adding a relocation entry for 0xbdf0.
grub-install: info: adding a relocation entry for 0xbdf8.
grub-install: info: adding a relocation entry for 0xbe08.
grub-install: info: adding a relocation entry for 0xbe10.
grub-install: info: adding a relocation entry for 0xbe20.
grub-install: info: adding a relocation entry for 0xbe28.
grub-install: info: adding a relocation entry for 0xbe38.
grub-install: info: adding a relocation entry for 0xbe40.
grub-install: info: adding a relocation entry for 0xbe50.
grub-install: info: adding a relocation entry for 0xbe58.
grub-install: info: adding a relocation entry for 0xbe68.
grub-install: info: adding a relocation entry for 0xbe70.
grub-install: info: adding a relocation entry for 0xbe80.
grub-install: info: adding a relocation entry for 0xbe88.
grub-install: info: adding a relocation entry for 0xbe98.
grub-install: info: adding a relocation entry for 0xbea0.
grub-install: info: adding a relocation entry for 0xbeb0.
grub-install: info: adding a relocation entry for 0xbeb8.
grub-install: info: adding a relocation entry for 0xbec8.
grub-install: info: adding a relocation entry for 0xbed0.
grub-install: info: adding a relocation entry for 0xbee0.
grub-install: info: adding a relocation entry for 0xbee8.
grub-install: info: adding a relocation entry for 0xbef8.
grub-install: info: adding a relocation entry for 0xbf00.
grub-install: info: adding a relocation entry for 0xbf10.
grub-install: info: adding a relocation entry for 0xbf18.
grub-install: info: adding a relocation entry for 0xbf28.
grub-install: info: adding a relocation entry for 0xbf30.
grub-install: info: adding a relocation entry for 0xbf40.
grub-install: info: adding a relocation entry for 0xbf48.
grub-install: info: adding a relocation entry for 0xbf58.
grub-install: info: adding a relocation entry for 0xbf60.
grub-install: info: adding a relocation entry for 0xbf70.
grub-install: info: adding a relocation entry for 0xbf78.
grub-install: info: adding a relocation entry for 0xbf88.
grub-install: info: adding a relocation entry for 0xbf90.
grub-install: info: adding a relocation entry for 0xbfa0.
grub-install: info: adding a relocation entry for 0xbfa8.
grub-install: info: adding a relocation entry for 0xbfb8.
grub-install: info: adding a relocation entry for 0xbfc0.
grub-install: info: adding a relocation entry for 0xbfd0.
grub-install: info: adding a relocation entry for 0xbfd8.
grub-install: info: adding a relocation entry for 0xbfe8.
grub-install: info: adding a relocation entry for 0xbff0.
grub-install: info: adding a relocation entry for 0xc000.
grub-install: info: writing 400 bytes of a fixup block starting at 0xb000.
grub-install: info: adding a relocation entry for 0xc008.
grub-install: info: adding a relocation entry for 0xc018.
grub-install: info: adding a relocation entry for 0xc020.
grub-install: info: adding a relocation entry for 0xc030.
grub-install: info: adding a relocation entry for 0xc038.
grub-install: info: adding a relocation entry for 0xc048.
grub-install: info: adding a relocation entry for 0xc050.
grub-install: info: adding a relocation entry for 0xc060.
grub-install: info: adding a relocation entry for 0xc068.
grub-install: info: adding a relocation entry for 0xc078.
grub-install: info: adding a relocation entry for 0xc080.
grub-install: info: adding a relocation entry for 0xc090.
grub-install: info: adding a relocation entry for 0xc098.
grub-install: info: adding a relocation entry for 0xc0a8.
grub-install: info: adding a relocation entry for 0xc0b0.
grub-install: info: adding a relocation entry for 0xc0c0.
grub-install: info: adding a relocation entry for 0xc0c8.
grub-install: info: adding a relocation entry for 0xc0d8.
grub-install: info: adding a relocation entry for 0xc0e0.
grub-install: info: adding a relocation entry for 0xc0f0.
grub-install: info: adding a relocation entry for 0xc0f8.
grub-install: info: adding a relocation entry for 0xc108.
grub-install: info: adding a relocation entry for 0xc110.
grub-install: info: adding a relocation entry for 0xc120.
grub-install: info: adding a relocation entry for 0xc128.
grub-install: info: adding a relocation entry for 0xc138.
grub-install: info: adding a relocation entry for 0xc140.
grub-install: info: adding a relocation entry for 0xc150.
grub-install: info: adding a relocation entry for 0xc158.
grub-install: info: adding a relocation entry for 0xc168.
grub-install: info: adding a relocation entry for 0xc170.
grub-install: info: adding a relocation entry for 0xc180.
grub-install: info: adding a relocation entry for 0xc188.
grub-install: info: adding a relocation entry for 0xc198.
grub-install: info: adding a relocation entry for 0xc1a0.
grub-install: info: adding a relocation entry for 0xc1b0.
grub-install: info: adding a relocation entry for 0xc1b8.
grub-install: info: adding a relocation entry for 0xc1c8.
grub-install: info: adding a relocation entry for 0xc1d0.
grub-install: info: adding a relocation entry for 0xc1e0.
grub-install: info: adding a relocation entry for 0xc1e8.
grub-install: info: adding a relocation entry for 0xc1f8.
grub-install: info: adding a relocation entry for 0xc200.
grub-install: info: adding a relocation entry for 0xc210.
grub-install: info: adding a relocation entry for 0xc218.
grub-install: info: adding a relocation entry for 0xc228.
grub-install: info: adding a relocation entry for 0xc230.
grub-install: info: adding a relocation entry for 0xc240.
grub-install: info: adding a relocation entry for 0xc248.
grub-install: info: adding a relocation entry for 0xc258.
grub-install: info: adding a relocation entry for 0xc260.
grub-install: info: adding a relocation entry for 0xc270.
grub-install: info: adding a relocation entry for 0xc278.
grub-install: info: adding a relocation entry for 0xc288.
grub-install: info: adding a relocation entry for 0xc290.
grub-install: info: adding a relocation entry for 0xc2a0.
grub-install: info: adding a relocation entry for 0xc2a8.
grub-install: info: adding a relocation entry for 0xc2b8.
grub-install: info: adding a relocation entry for 0xc2c0.
grub-install: info: adding a relocation entry for 0xc2d0.
grub-install: info: adding a relocation entry for 0xc2d8.
grub-install: info: adding a relocation entry for 0xc2e8.
grub-install: info: adding a relocation entry for 0xc2f0.
grub-install: info: adding a relocation entry for 0xc300.
grub-install: info: adding a relocation entry for 0xc308.
grub-install: info: adding a relocation entry for 0xc318.
grub-install: info: adding a relocation entry for 0xc320.
grub-install: info: adding a relocation entry for 0xc330.
grub-install: info: adding a relocation entry for 0xc338.
grub-install: info: adding a relocation entry for 0xc348.
grub-install: info: adding a relocation entry for 0xc350.
grub-install: info: adding a relocation entry for 0xc360.
grub-install: info: adding a relocation entry for 0xc368.
grub-install: info: adding a relocation entry for 0xc378.
grub-install: info: adding a relocation entry for 0xc380.
grub-install: info: adding a relocation entry for 0xc390.
grub-install: info: adding a relocation entry for 0xc398.
grub-install: info: adding a relocation entry for 0xc3a8.
grub-install: info: adding a relocation entry for 0xc3b0.
grub-install: info: adding a relocation entry for 0xc3c0.
grub-install: info: adding a relocation entry for 0xc3c8.
grub-install: info: adding a relocation entry for 0xc3d8.
grub-install: info: adding a relocation entry for 0xc3e0.
grub-install: info: adding a relocation entry for 0xc3f0.
grub-install: info: adding a relocation entry for 0xc3f8.
grub-install: info: adding a relocation entry for 0xc408.
grub-install: info: adding a relocation entry for 0xc410.
grub-install: info: adding a relocation entry for 0xc420.
grub-install: info: adding a relocation entry for 0xc428.
grub-install: info: adding a relocation entry for 0xc438.
grub-install: info: adding a relocation entry for 0xc440.
grub-install: info: adding a relocation entry for 0xc450.
grub-install: info: adding a relocation entry for 0xc458.
grub-install: info: adding a relocation entry for 0xc468.
grub-install: info: adding a relocation entry for 0xc470.
grub-install: info: adding a relocation entry for 0xc480.
grub-install: info: adding a relocation entry for 0xc488.
grub-install: info: adding a relocation entry for 0xc498.
grub-install: info: adding a relocation entry for 0xc4a0.
grub-install: info: adding a relocation entry for 0xc4b0.
grub-install: info: adding a relocation entry for 0xc4b8.
grub-install: info: adding a relocation entry for 0xc4c8.
grub-install: info: adding a relocation entry for 0xc4d0.
grub-install: info: adding a relocation entry for 0xc4e0.
grub-install: info: adding a relocation entry for 0xc4e8.
grub-install: info: adding a relocation entry for 0xc4f8.
grub-install: info: adding a relocation entry for 0xc500.
grub-install: info: adding a relocation entry for 0xc510.
grub-install: info: adding a relocation entry for 0xc518.
grub-install: info: adding a relocation entry for 0xc528.
grub-install: info: adding a relocation entry for 0xc530.
grub-install: info: adding a relocation entry for 0xc540.
grub-install: info: adding a relocation entry for 0xc548.
grub-install: info: adding a relocation entry for 0xc558.
grub-install: info: adding a relocation entry for 0xc560.
grub-install: info: adding a relocation entry for 0xc570.
grub-install: info: adding a relocation entry for 0xc578.
grub-install: info: adding a relocation entry for 0xc588.
grub-install: info: adding a relocation entry for 0xc590.
grub-install: info: adding a relocation entry for 0xc5a0.
grub-install: info: adding a relocation entry for 0xc5a8.
grub-install: info: adding a relocation entry for 0xc5b8.
grub-install: info: adding a relocation entry for 0xc5c0.
grub-install: info: adding a relocation entry for 0xc5d0.
grub-install: info: adding a relocation entry for 0xc5d8.
grub-install: info: adding a relocation entry for 0xc5e8.
grub-install: info: adding a relocation entry for 0xc5f0.
grub-install: info: adding a relocation entry for 0xc600.
grub-install: info: adding a relocation entry for 0xc608.
grub-install: info: adding a relocation entry for 0xc618.
grub-install: info: adding a relocation entry for 0xc620.
grub-install: info: adding a relocation entry for 0xc630.
grub-install: info: adding a relocation entry for 0xc638.
grub-install: info: adding a relocation entry for 0xc648.
grub-install: info: adding a relocation entry for 0xc650.
grub-install: info: adding 204 padding fixup entries.
grub-install: info: writing 688 bytes of a fixup block starting at 0xc000.
grub-install: info: reading /usr/lib/grub/x86_64-efi/fshelp.mod.
grub-install: info: reading /usr/lib/grub/x86_64-efi/ext2.mod.
grub-install: info: reading /usr/lib/grub/x86_64-efi/part_gpt.mod.
grub-install: info: reading /usr/lib/grub/x86_64-efi/search_fs_uuid.mod.
grub-install: info: reading /boot/grub/x86_64-efi/load.cfg.
grub-install: info: kernel_img=0xae8210, kernel_size=0x18200.
grub-install: info: the core size is 0x1d3c8.
grub-install: info: writing 0x1e600 bytes.
grub-install: info: grub-mkimage --directory '/usr/lib/grub/x86_64-efi' --prefix '' --output '/boot/grub/x86_64-efi/grub.efi' --format 'x86_64-efi' --compression 'auto'  --config '/boot/grub/x86_64-efi/load.cfg' 'ext2' 'part_gpt' 'search_fs_uuid'
.
grub-install: info: the size of config file is 0x68.
grub-install: info: the total module size is 0x51c0.
grub-install: info: reading /usr/lib/grub/x86_64-efi/kernel.img.
grub-install: info: locating the section .text at 0x0.
grub-install: info: locating the section .rodata at 0x9600.
grub-install: info: locating the section .rodata.str1.1 at 0x9798.
grub-install: info: locating the section .data at 0xb0e0.
grub-install: info: locating the section .module_license at 0xc278.
grub-install: info: locating the section .bss at 0xc290.
grub-install: info: locating  at 0x400 (0x400).
grub-install: info: locating  at 0x9a00 (0x9a00).
grub-install: info: locating  at 0x9b98 (0x9b98).
grub-install: info: locating  at 0xb4e0 (0xb4e0).
grub-install: info: locating  at 0xc690 (0xc690).
grub-install: info: locating  at 0xc678 (0xc678).
grub-install: info: locating  at 0x400 (0x400).
grub-install: info: locating grub_strlen at 0x7c25 (0x400).
grub-install: info: locating grub_net_poll_cards_idle at 0xe3d0 (0xc690).
grub-install: info: locating grub_efi_finish_boot_services at 0x2f18 (0x400).
grub-install: info: locating grub_disk_get_size at 0x55c0 (0x400).
grub-install: info: locating grub_file_progress_hook at 0x184e0 (0xc690).
grub-install: info: locating grub_efidisk_fini at 0xe51 (0x400).
grub-install: info: locating grub_puts_ at 0x79d3 (0x400).
grub-install: info: locating grub_millisleep at 0x4195 (0x400).
grub-install: info: locating grub_fs_autoload_hook at 0xe1b0 (0xc690).
grub-install: info: locating efi_wrap_10 at 0x4cc (0x400).
grub-install: info: locating grub_efi_allocate_pages_max at 0x2d32 (0x400).
grub-install: info: locating grub_fs_blocklist at 0xb640 (0xb4e0).
grub-install: info: locating grub_errmsg at 0x183d0 (0xc690).
grub-install: info: locating efi_wrap_5 at 0x463 (0x400).
grub-install: info: locating grub_strncmp at 0x7a4d (0x400).
grub-install: info: locating grub_strtoull at 0x7d3d (0x400).
grub-install: info: locating grub_dma_get_virt at 0x5a5 (0x400).
grub-install: info: locating grub_efi_system_table at 0xe3e0 (0xc690).
grub-install: info: locating memmove at 0x797a (0x400).
grub-install: info: locating efi_wrap_4 at 0x44f (0x400).
grub-install: info: locating grub_disk_open at 0x4f8a (0x400).
grub-install: info: locating grub_efi_locate_protocol at 0x1c16 (0x400).
grub-install: info: locating grub_env_update_get_sorted at 0x669c (0x400).
grub-install: info: locating grub_strcpy at 0x79c0 (0x400).
grub-install: info: locating grub_partition_probe at 0x8fd0 (0x400).
grub-install: info: locating grub_strrchr at 0x7a99 (0x400).
grub-install: info: locating grub_partition_get_name at 0x91d0 (0x400).
grub-install: info: locating grub_dl_load at 0x631d (0x400).
grub-install: info: locating grub_efi_stall at 0x1e3f (0x400).
grub-install: info: locating grub_efi_get_filename at 0x2289 (0x400).
grub-install: info: locating grub_env_export at 0x6788 (0x400).
grub-install: info: locating grub_xvasprintf at 0x89b2 (0x400).
grub-install: info: locating grub_error_push at 0x684a (0x400).
grub-install: info: locating grub_rescue_run at 0x9750 (0x400).
grub-install: info: locating grub_xasprintf at 0x8a4d (0x400).
grub-install: info: locating grub_realloc at 0x40bf (0x400).
grub-install: info: locating grub_exit at 0x1e7e (0x400).
grub-install: info: locating memcpy at 0x797a (0x400).
grub-install: info: locating grub_memmove at 0x797a (0x400).
grub-install: info: locating grub_device_open at 0x47bb (0x400).
grub-install: info: locating grub_register_exported_symbols at 0x993e (0x400).
grub-install: info: locating grub_strdup at 0x7c8f (0x400).
grub-install: info: locating grub_disk_firmware_is_tainted at 0xe420 (0xc690).
grub-install: info: locating grub_divmod64 at 0x7cd7 (0x400).
grub-install: info: locating grub_file_get_device_name at 0x69dd (0x400).
grub-install: info: locating grub_efi_print_device_path at 0x2370 (0x400).
grub-install: info: locating grub_partition_iterate at 0x9164 (0x400).
grub-install: info: locating grub_dma_free at 0x599 (0x400).
grub-install: info: locating grub_vsnprintf at 0x88fd (0x400).
grub-install: info: locating grub_partition_map_list at 0x18530 (0xc690).
grub-install: info: locating efi_wrap_1 at 0x422 (0x400).
grub-install: info: locating grub_command_list at 0xe410 (0xc690).
grub-install: info: locating grub_machine_fini at 0x534 (0x400).
grub-install: info: locating grub_tsc_rate at 0xe400 (0xc690).
grub-install: info: locating grub_rescue_parse_line at 0x94ce (0x400).
grub-install: info: locating grub_efi_get_variable at 0x1ff7 (0x400).
grub-install: info: locating grub_snprintf at 0x896d (0x400).
grub-install: info: locating grub_register_core_commands at 0x4632 (0x400).
grub-install: info: locating grub_disk_dev_register at 0x4ea0 (0x400).
grub-install: info: locating grub_console_init at 0x3927 (0x400).
grub-install: info: locating grub_disk_write_weak at 0xe428 (0xc690).
grub-install: info: locating grub_dl_add at 0x5696 (0x400).
grub-install: info: locating grub_disk_read at 0x5270 (0x400).
grub-install: info: locating grub_term_highlight_color at 0xb7e8 (0xb4e0).
grub-install: info: locating grub_parser_execute at 0x8f62 (0x400).
grub-install: info: locating grub_xputs at 0xb7e0 (0xb4e0).
grub-install: info: locating grub_console_fini at 0x3a28 (0x400).
grub-install: info: locating grub_fatal at 0x8a9c (0x400).
grub-install: info: locating grub_dl_ref at 0x5792 (0x400).
grub-install: info: locating grub_file_seek at 0x6d22 (0x400).
grub-install: info: locating grub_pci_find_capability at 0x6a2 (0x400).
grub-install: info: locating grub_efi_get_loaded_image at 0x1e63 (0x400).
grub-install: info: locating grub_errno at 0x184d0 (0xc690).
grub-install: info: locating grub_parser_cmdline_state at 0x8c1a (0x400).
grub-install: info: locating grub_memset at 0x7baf (0x400).
grub-install: info: locating grub_getkey at 0x991f (0x400).
grub-install: info: locating grub_term_outputs_disabled at 0x18538 (0xc690).
grub-install: info: locating grub_grubnet_fini at 0x184e8 (0xc690).
grub-install: info: locating grub_register_variable_hook at 0x6728 (0x400).
grub-install: info: locating grub_efi_image_handle at 0xe3e8 (0xc690).
grub-install: info: locating grub_vprintf at 0x8666 (0x400).
grub-install: info: locating grub_net_open at 0xc6e8 (0xc690).
grub-install: info: locating grub_register_command_prio at 0x41be (0x400).
grub-install: info: locating grub_efi_compare_device_paths at 0x29f5 (0x400).
grub-install: info: locating grub_file_filters_all at 0x184f0 (0xc690).
grub-install: info: locating grub_install_get_time_ms at 0x4187 (0x400).
grub-install: info: locating _start at 0x400 (0x400).
grub-install: info: locating grub_term_inputs at 0x18540 (0xc690).
grub-install: info: locating grub_parser_split_cmdline at 0x8cd3 (0x400).
grub-install: info: locating grub_disk_firmware_fini at 0xe430 (0xc690).
grub-install: info: locating grub_disk_close at 0x4ee6 (0x400).
grub-install: info: locating grub_dl_unload at 0x580c (0x400).
grub-install: info: locating grub_efi_set_variable at 0x1f1d (0x400).
grub-install: info: locating grub_printf at 0x87d3 (0x400).
grub-install: info: locating grub_efi_secure_boot at 0x2117 (0x400).
grub-install: info: locating grub_unregister_command at 0x42af (0x400).
grub-install: info: locating grub_fs_list at 0xe1b8 (0xc690).
grub-install: info: locating grub_efidisk_get_device_handle at 0x1581 (0x400).
grub-install: info: locating grub_main at 0x731f (0x400).
grub-install: info: locating grub_file_read at 0x6a68 (0x400).
grub-install: info: locating grub_dl_unload_unneeded at 0x641a (0x400).
grub-install: info: locating grub_pci_make_address at 0x5ac (0x400).
grub-install: info: locating memcmp at 0x7a0c (0x400).
grub-install: info: locating grub_term_normal_color at 0xb7e9 (0xb4e0).
grub-install: info: locating grub_disk_dev_list at 0xe438 (0xc690).
grub-install: info: locating grub_machine_init at 0x51a (0x400).
grub-install: info: locating efi_wrap_0 at 0x417 (0x400).
grub-install: info: locating grub_efi_locate_handle at 0x1c5f (0x400).
grub-install: info: locating grub_term_outputs at 0x18548 (0xc690).
grub-install: info: locating grub_modbase at 0xe3f0 (0xc690).
grub-install: info: locating grub_term_inputs_disabled at 0x18550 (0xc690).
grub-install: info: locating grub_efi_net_config at 0xe3f8 (0xc690).
grub-install: info: locating grub_efi_set_virtual_address_map at 0x1ec2 (0x400).
grub-install: info: locating grub_print_error at 0x6944 (0x400).
grub-install: info: locating grub_efi_mm_init at 0x31e7 (0x400).
grub-install: info: locating memset at 0x7baf (0x400).
grub-install: info: locating grub_zalloc at 0x3e36 (0x400).
grub-install: info: locating grub_strcmp at 0x7a2e (0x400).
grub-install: info: locating grub_tsc_init at 0x3aa7 (0x400).
grub-install: info: locating grub_efi_allocate_pages at 0x2c6e (0x400).
grub-install: info: locating grub_strchr at 0x7a83 (0x400).
grub-install: info: locating grub_refresh at 0x98f7 (0x400).
grub-install: info: locating grub_malloc at 0x3e25 (0x400).
grub-install: info: locating grub_efi_get_memory_map at 0x2de4 (0x400).
grub-install: info: locating grub_efidisk_get_device_name at 0x16cc (0x400).
grub-install: info: locating grub_get_time_ms at 0x417b (0x400).
grub-install: info: locating grub_file_close at 0x6b05 (0x400).
grub-install: info: locating grub_file_open at 0x6b50 (0x400).
grub-install: info: locating grub_isspace at 0x7aae (0x400).
grub-install: info: locating grub_efi_open_protocol at 0x1d5a (0x400).
grub-install: info: locating grub_real_dprintf at 0x8822 (0x400).
grub-install: info: locating efi_wrap_3 at 0x43e (0x400).
grub-install: info: locating grub_dl_load_core_noinit at 0x5926 (0x400).
grub-install: info: locating grub_dl_load_file at 0x621a (0x400).
grub-install: info: locating grub_env_unset at 0x6618 (0x400).
grub-install: info: locating grub_device_close at 0x4899 (0x400).
grub-install: info: locating efi_wrap_6 at 0x47c (0x400).
grub-install: info: locating grub_dl_head at 0xc700 (0xc690).
grub-install: info: locating grub_fs_probe at 0x7033 (0x400).
grub-install: info: locating grub_mm_base at 0xe408 (0xc690).
grub-install: info: locating grub_term_poll_usb at 0xe3d8 (0xc690).
grub-install: info: locating grub_file_filters_enabled at 0x18510 (0xc690).
grub-install: info: locating grub_strword at 0x7b0e (0x400).
grub-install: info: locating grub_machine_get_bootlocation at 0x2aeb (0x400).
grub-install: info: locating grub_efi_fini at 0x2b82 (0x400).
grub-install: info: locating grub_err_printed_errors at 0x184d4 (0xc690).
grub-install: info: locating grub_error at 0x67ce (0x400).
grub-install: info: locating grub_current_context at 0xb630 (0xb4e0).
grub-install: info: locating efi_codes at 0x9ae0 (0x9a00).
grub-install: info: locating grub_dl_register_symbol at 0x56d3 (0x400).
grub-install: info: locating grub_efi_is_finished at 0xc6a8 (0xc690).
grub-install: info: locating grub_list_remove at 0x7290 (0x400).
grub-install: info: locating grub_pci_iterate at 0x5d3 (0x400).
grub-install: info: locating grub_modules_get_end at 0x7303 (0x400).
grub-install: info: locating grub_free at 0x3e70 (0x400).
grub-install: info: locating grub_strndup at 0x7c36 (0x400).
grub-install: info: locating efi_wrap_7 at 0x49f (0x400).
grub-install: info: locating grub_named_list_find at 0x7242 (0x400).
grub-install: info: locating grub_dl_unref at 0x57cf (0x400).
grub-install: info: locating grub_efidisk_init at 0x134a (0x400).
grub-install: info: locating grub_disk_dev_unregister at 0x4eb5 (0x400).
grub-install: info: locating grub_efi_init at 0x2a85 (0x400).
grub-install: info: locating grub_arch_dl_check_header at 0x744 (0x400).
grub-install: info: locating grub_arch_dl_relocate_symbols at 0x773 (0x400).
grub-install: info: locating grub_efi_free_pages at 0x2c44 (0x400).
grub-install: info: locating grub_printf_ at 0x8775 (0x400).
grub-install: info: locating grub_efi_get_device_path at 0x2355 (0x400).
grub-install: info: locating start at 0x400 (0x400).
grub-install: info: locating grub_efi_modules_addr at 0x21ea (0x400).
grub-install: info: locating grub_error_pop at 0x68d6 (0x400).
grub-install: info: locating grub_device_iterate at 0x49da (0x400).
grub-install: info: locating grub_getkey_noblock at 0x98ad (0x400).
grub-install: info: locating grub_memalign_dma32 at 0x547 (0x400).
grub-install: info: locating grub_list_push at 0x7276 (0x400).
grub-install: info: locating grub_efi_set_text_mode at 0x1db8 (0x400).
grub-install: info: locating grub_err_printf at 0x87d3 (0x400).
grub-install: info: locating grub_disk_cache_invalidate_all at 0x4e56 (0x400).
grub-install: info: locating grub_env_set at 0x64bc (0x400).
grub-install: info: locating grub_dl_load_core at 0x61d4 (0x400).
grub-install: info: locating grub_gettext at 0xb690 (0xb4e0).
grub-install: info: locating grub_memcmp at 0x7a0c (0x400).
grub-install: info: locating grub_env_get at 0x65ea (0x400).
grub-install: info: locating efi_wrap_2 at 0x430 (0x400).
grub-install: info: locating grub_strtoul at 0x81c5 (0x400).
grub-install: info: locating grub_dma_get_phys at 0x5a9 (0x400).
grub-install: info: locating grub_mm_init_region at 0x3f86 (0x400).
grub-install: info: locating grub_disk_cache_table at 0xe440 (0xc690).
grub-install: info: locating grub_memalign at 0x3c27 (0x400).
grub-install: info: dealing with the relocation section .rela.text for .text.
grub-install: info: relocating an R_X86_64_PC32 entry to 0xdfe1 at the offset 0x3.
grub-install: info: relocating an R_X86_64_PC32 entry to 0xdfd2 at the offset 0xa.
grub-install: info: relocating an R_X86_64_PC32 entry to 0x6f08 at the offset 0x13.
grub-install: info: relocating an R_X86_64_64 entry to 0x2a85 at the offset 0x11d.
grub-install: info: relocating an R_X86_64_64 entry to 0x3aa7 at the offset 0x12a.
grub-install: info: relocating an R_X86_64_64 entry to 0x2b82 at the offset 0x13c.
grub-install: info: relocating an R_X86_64_64 entry to 0x3c27 at the offset 0x165.
grub-install: info: relocating an R_X86_64_64 entry to 0x9b98 at the offset 0x17a.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x18b.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x19b.
grub-install: info: relocating an R_X86_64_64 entry to 0x5ac at the offset 0x1e0.
grub-install: info: relocating an R_X86_64_64 entry to 0x5ac at the offset 0x2af.
grub-install: info: relocating an R_X86_64_64 entry to 0x9bb8 at the offset 0x355.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x366.
grub-install: info: relocating an R_X86_64_64 entry to 0x9bd9 at the offset 0x38f.
grub-install: info: relocating an R_X86_64_64 entry to 0x9bfc at the offset 0x410.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x422.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c14 at the offset 0x474.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x485.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4fd.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a0 at the offset 0x527.
grub-install: info: relocating an R_X86_64_64 entry to 0x29f5 at the offset 0x545.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x57a.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x5ac.
grub-install: info: relocating an R_X86_64_64 entry to 0x29f5 at the offset 0x5cd.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c3b at the offset 0x5fa.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0x60c.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0x638.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c9 at the offset 0x642.
grub-install: info: relocating an R_X86_64_64 entry to 0xc690 at the offset 0x66d.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0x694.
grub-install: info: relocating an R_X86_64_64 entry to 0xb520 at the offset 0x6c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x1c5f at the offset 0x6cf.
grub-install: info: relocating an R_X86_64_64 entry to 0x2355 at the offset 0x6fd.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a0 at the offset 0x722.
grub-install: info: relocating an R_X86_64_64 entry to 0xb520 at the offset 0x73b.
grub-install: info: relocating an R_X86_64_64 entry to 0x1d5a at the offset 0x749.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x767.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x780.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x7c6.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c3f at the offset 0x7eb.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0x7f5.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0x804.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x810.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c66 at the offset 0x824.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0x82e.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x838.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0x84a.
grub-install: info: relocating an R_X86_64_64 entry to 0x81c5 at the offset 0x880.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x88f.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c72 at the offset 0x8a5.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x8b6.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8c1.
grub-install: info: relocating an R_X86_64_64 entry to 0xc690 at the offset 0x8ec.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0x8fb.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0x90a.
grub-install: info: relocating an R_X86_64_64 entry to 0x8da at the offset 0x917.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c80 at the offset 0x933.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x944.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c8f at the offset 0x958.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0x965.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0x977.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x981.
grub-install: info: relocating an R_X86_64_64 entry to 0x9cbb at the offset 0x9d4.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x9e5.
grub-install: info: relocating an R_X86_64_64 entry to 0x9cd2 at the offset 0xa18.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xa22.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xa31.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xa3b.
grub-install: info: relocating an R_X86_64_64 entry to 0xc690 at the offset 0xa55.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0xa61.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0xa6c.
grub-install: info: relocating an R_X86_64_64 entry to 0x8fa at the offset 0xa77.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4e0 at the offset 0xaa4.
grub-install: info: relocating an R_X86_64_64 entry to 0x4eb5 at the offset 0xab6.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0xaea.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ce8 at the offset 0xaff.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0xb13.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ced at the offset 0xb25.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xb2f.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xb3e.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xb48.
grub-install: info: relocating an R_X86_64_64 entry to 0xc690 at the offset 0xb77.
grub-install: info: relocating an R_X86_64_64 entry to 0x9cfb at the offset 0xb8c.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0xba0.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ced at the offset 0xbb2.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xbbc.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xbcb.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xbd5.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0xc00.
grub-install: info: relocating an R_X86_64_64 entry to 0x9d00 at the offset 0xc15.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0xc29.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ced at the offset 0xc3b.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xc45.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xc54.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xc5e.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xca5.
grub-install: info: relocating an R_X86_64_64 entry to 0x9d05 at the offset 0xcb1.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xcbe.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xcdb.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0xd09.
grub-install: info: relocating an R_X86_64_64 entry to 0x9d39 at the offset 0xd24.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0xd3d.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0xd7f.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0xd9c.
grub-install: info: relocating an R_X86_64_64 entry to 0x1152 at the offset 0xdb2.
grub-install: info: relocating an R_X86_64_64 entry to 0x29f5 at the offset 0xdd8.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a0 at the offset 0xde2.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0xe20.
grub-install: info: relocating an R_X86_64_64 entry to 0x91d0 at the offset 0xe7a.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xe9d.
grub-install: info: relocating an R_X86_64_64 entry to 0x9d61 at the offset 0xea9.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0xeb6.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c53 at the offset 0xed3.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0xf01.
grub-install: info: relocating an R_X86_64_64 entry to 0x9d93 at the offset 0xf1c.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0xf35.
grub-install: info: relocating an R_X86_64_64 entry to 0xe51 at the offset 0xf4e.
grub-install: info: relocating an R_X86_64_64 entry to 0xe430 at the offset 0xf62.
grub-install: info: relocating an R_X86_64_64 entry to 0xaba at the offset 0xf6c.
grub-install: info: relocating an R_X86_64_64 entry to 0x11ae at the offset 0xf87.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0xfee.
grub-install: info: relocating an R_X86_64_64 entry to 0x91b at the offset 0xff8.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0x1004.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0x109d.
grub-install: info: relocating an R_X86_64_64 entry to 0x11ae at the offset 0x10b3.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a0 at the offset 0x1106.
grub-install: info: relocating an R_X86_64_64 entry to 0xc698 at the offset 0x1115.
grub-install: info: relocating an R_X86_64_64 entry to 0x91b at the offset 0x111f.
grub-install: info: relocating an R_X86_64_64 entry to 0x8fa at the offset 0x113b.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4e0 at the offset 0x1147.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ea0 at the offset 0x1151.
grub-install: info: relocating an R_X86_64_64 entry to 0xc690 at the offset 0x116a.
grub-install: info: relocating an R_X86_64_64 entry to 0xaba at the offset 0x11cd.
grub-install: info: relocating an R_X86_64_64 entry to 0x1152 at the offset 0x11d7.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a0 at the offset 0x1204.
grub-install: info: relocating an R_X86_64_64 entry to 0x29f5 at the offset 0x1225.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1238.
grub-install: info: relocating an R_X86_64_64 entry to 0x8fa at the offset 0x12ac.
grub-install: info: relocating an R_X86_64_64 entry to 0x2355 at the offset 0x12d0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a0 at the offset 0x12f6.
grub-install: info: relocating an R_X86_64_64 entry to 0x1152 at the offset 0x132c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa34 at the offset 0x1383.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1396.
grub-install: info: relocating an R_X86_64_64 entry to 0x4f8a at the offset 0x13ae.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x13c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x55c0 at the offset 0x13f0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x140a.
grub-install: info: relocating an R_X86_64_64 entry to 0x1239 at the offset 0x141d.
grub-install: info: relocating an R_X86_64_64 entry to 0x9164 at the offset 0x142a.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ee6 at the offset 0x1443.
grub-install: info: relocating an R_X86_64_64 entry to 0x9db9 at the offset 0x1457.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x1461.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1479.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ee6 at the offset 0x1492.
grub-install: info: relocating an R_X86_64_64 entry to 0xa34 at the offset 0x14ad.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x14c6.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x15ec.
grub-install: info: relocating an R_X86_64_64 entry to 0x9dbf at the offset 0x1645.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e00 at the offset 0x1664.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x1670.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e02 at the offset 0x1684.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x181f.
grub-install: info: relocating an R_X86_64_64 entry to 0x43e at the offset 0x1832.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x1868.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x18a5.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0x18c3.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x18ec.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x192d.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1963.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x1981.
grub-install: info: relocating an R_X86_64_64 entry to 0x47c at the offset 0x1999.
grub-install: info: relocating an R_X86_64_64 entry to 0x1c16 at the offset 0x19bf.
grub-install: info: relocating an R_X86_64_64 entry to 0xb530 at the offset 0x19c9.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x19f9.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x1a24.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1a41.
grub-install: info: relocating an R_X86_64_64 entry to 0x422 at the offset 0x1a59.
grub-install: info: relocating an R_X86_64_64 entry to 0xb540 at the offset 0x1a6a.
grub-install: info: relocating an R_X86_64_64 entry to 0x1d5a at the offset 0x1a74.
grub-install: info: relocating an R_X86_64_64 entry to 0x2b82 at the offset 0x1a81.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1a8d.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x1aa9.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x1ab6.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1ac7.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x1aec.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e08 at the offset 0x1afe.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x1b0f.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x1b24.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x1b4b.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x1b59.
grub-install: info: relocating an R_X86_64_64 entry to 0x1a98 at the offset 0x1b78.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1b8a.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0x1bad.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e27 at the offset 0x1bc9.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x1be1.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x1bfb.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x1c05.
grub-install: info: relocating an R_X86_64_64 entry to 0x1a98 at the offset 0x1c5c.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0x1c66.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x1c78.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1cb7.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1ce4.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e47 at the offset 0x1d1b.
grub-install: info: relocating an R_X86_64_64 entry to 0x1ff7 at the offset 0x1d27.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e52 at the offset 0x1da0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x1dcf.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x1dee.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e63 at the offset 0x1e01.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x1e1f.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e5c at the offset 0x1e3c.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x1ed3.
grub-install: info: relocating an R_X86_64_64 entry to 0x18dd at the offset 0x1eea.
grub-install: info: relocating an R_X86_64_64 entry to 0xb550 at the offset 0x1f5c.
grub-install: info: relocating an R_X86_64_64 entry to 0x1d5a at the offset 0x1f66.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x1f7b.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e61 at the offset 0x1fd4.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e6d at the offset 0x1fe2.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e77 at the offset 0x1ff5.
grub-install: info: relocating an R_X86_64_64 entry to 0x9a00 at the offset 0x200e.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e88 at the offset 0x2023.
grub-install: info: relocating an R_X86_64_64 entry to 0x9e94 at the offset 0x2036.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ea0 at the offset 0x204d.
grub-install: info: relocating an R_X86_64_64 entry to 0x9eb4 at the offset 0x2062.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ebd at the offset 0x2074.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ec7 at the offset 0x2083.
grub-install: info: relocating an R_X86_64_64 entry to 0x9efa at the offset 0x209c.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ed6 at the offset 0x20b4.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ee3 at the offset 0x20c9.
grub-install: info: relocating an R_X86_64_64 entry to 0x9eea at the offset 0x20de.
grub-install: info: relocating an R_X86_64_64 entry to 0x9eee at the offset 0x20f2.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x2104.
grub-install: info: relocating an R_X86_64_64 entry to 0x9eea at the offset 0x211e.
grub-install: info: relocating an R_X86_64_64 entry to 0x9eee at the offset 0x2134.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x2147.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ef2 at the offset 0x2176.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ef6 at the offset 0x21a1.
grub-install: info: relocating an R_X86_64_64 entry to 0x9a28 at the offset 0x21be.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f0b at the offset 0x21d3.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f1c at the offset 0x21ee.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f29 at the offset 0x2205.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f42 at the offset 0x221c.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f4e at the offset 0x2237.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f5a at the offset 0x224e.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f74 at the offset 0x2272.
grub-install: info: relocating an R_X86_64_64 entry to 0x9f7d at the offset 0x2289.
grub-install: info: relocating an R_X86_64_64 entry to 0x9fa8 at the offset 0x22be.
grub-install: info: relocating an R_X86_64_64 entry to 0x9fd3 at the offset 0x230c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa016 at the offset 0x2388.
grub-install: info: relocating an R_X86_64_64 entry to 0xa035 at the offset 0x23ab.
grub-install: info: relocating an R_X86_64_64 entry to 0xa04a at the offset 0x23cf.
grub-install: info: relocating an R_X86_64_64 entry to 0xa05a at the offset 0x23e9.
grub-install: info: relocating an R_X86_64_64 entry to 0xa064 at the offset 0x23f8.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ab8 at the offset 0x2415.
grub-install: info: relocating an R_X86_64_64 entry to 0xa07a at the offset 0x242b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa0b3 at the offset 0x247e.
grub-install: info: relocating an R_X86_64_64 entry to 0xa0c5 at the offset 0x2497.
grub-install: info: relocating an R_X86_64_64 entry to 0x19e8 at the offset 0x24a1.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x24b6.
grub-install: info: relocating an R_X86_64_64 entry to 0x18dd at the offset 0x24e3.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x24f5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa0cb at the offset 0x2502.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x2513.
grub-install: info: relocating an R_X86_64_64 entry to 0xa0d5 at the offset 0x252c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa111 at the offset 0x256b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa133 at the offset 0x257b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa123 at the offset 0x2593.
grub-install: info: relocating an R_X86_64_64 entry to 0xa144 at the offset 0x25b9.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x25c6.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0x260e.
grub-install: info: relocating an R_X86_64_64 entry to 0x21ea at the offset 0x2688.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x2694.
grub-install: info: relocating an R_X86_64_64 entry to 0x3927 at the offset 0x269e.
grub-install: info: relocating an R_X86_64_64 entry to 0x31e7 at the offset 0x26aa.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x26b6.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x26d4.
grub-install: info: relocating an R_X86_64_64 entry to 0x134a at the offset 0x26e1.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x26ef.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e63 at the offset 0x2704.
grub-install: info: relocating an R_X86_64_64 entry to 0x16cc at the offset 0x271c.
grub-install: info: relocating an R_X86_64_64 entry to 0x2289 at the offset 0x272c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f8 at the offset 0x2747.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a99 at the offset 0x276b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe51 at the offset 0x2785.
grub-install: info: relocating an R_X86_64_64 entry to 0x3a28 at the offset 0x2792.
grub-install: info: relocating an R_X86_64_64 entry to 0x5ac at the offset 0x27bb.
grub-install: info: relocating an R_X86_64_64 entry to 0x6a2 at the offset 0x27e5.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x2849.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x285c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x28a6.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x28c3.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c44 at the offset 0x2913.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x2957.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x2976.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c44 at the offset 0x29c5.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x29e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2a16.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2a25.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x2a32.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2a45.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x2a52.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2a63.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c0 at the offset 0x2a76.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c8 at the offset 0x2a88.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d0 at the offset 0x2a9a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x2ac0.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0x2ae2.
grub-install: info: relocating an R_X86_64_64 entry to 0x2de4 at the offset 0x2b1c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x2b46.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0x2b7c.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2b8c.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d0 at the offset 0x2b96.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c8 at the offset 0x2ba0.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c0 at the offset 0x2baa.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2bb7.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2bd2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa176 at the offset 0x2be5.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x2bf6.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2c07.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x2c14.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2c23.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x2c2e.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d0 at the offset 0x2c3d.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c8 at the offset 0x2c47.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c0 at the offset 0x2c51.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2c5e.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2c6f.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x2c79.
grub-install: info: relocating an R_X86_64_64 entry to 0xa159 at the offset 0x2c88.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x2c97.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c0 at the offset 0x2cac.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x2cb9.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x2cc6.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2ce4.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x2cee.
grub-install: info: relocating an R_X86_64_64 entry to 0xa195 at the offset 0x2cff.
grub-install: info: relocating an R_X86_64_64 entry to 0xa1b5 at the offset 0x2d10.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x2d1c.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x2d34.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2d40.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b8 at the offset 0x2d53.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6b0 at the offset 0x2d63.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x2d70.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c0 at the offset 0x2d81.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6c8 at the offset 0x2d93.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d0 at the offset 0x2da5.
grub-install: info: relocating an R_X86_64_64 entry to 0x2b9c at the offset 0x2dc1.
grub-install: info: relocating an R_X86_64_64 entry to 0x5d3 at the offset 0x2dcb.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c6e at the offset 0x2df9.
grub-install: info: relocating an R_X86_64_64 entry to 0xa1dd at the offset 0x2e12.
grub-install: info: relocating an R_X86_64_64 entry to 0x2de4 at the offset 0x2e3c.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c44 at the offset 0x2e54.
grub-install: info: relocating an R_X86_64_64 entry to 0xa1f4 at the offset 0x2ea5.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x2eb1.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x2f17.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c6e at the offset 0x3052.
grub-install: info: relocating an R_X86_64_64 entry to 0xa20a at the offset 0x306e.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x3078.
grub-install: info: relocating an R_X86_64_64 entry to 0x3f86 at the offset 0x308a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa23f at the offset 0x30aa.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c44 at the offset 0x30c2.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x30dd.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x30f8.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x323a.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x3252.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x3269.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x3278.
grub-install: info: relocating an R_X86_64_64 entry to 0x43e at the offset 0x3298.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x32a9.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x32b7.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x32ed.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x3311.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x3323.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x3343.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x3352.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x336a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3741 at the offset 0x337a.
grub-install: info: relocating an R_X86_64_64 entry to 0x1db8 at the offset 0x3388.
grub-install: info: relocating an R_X86_64_64 entry to 0x1db8 at the offset 0x339c.
grub-install: info: relocating an R_X86_64_64 entry to 0x3741 at the offset 0x33b0.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x33c5.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x33d6.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e9 at the offset 0x33ff.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e8 at the offset 0x340a.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x341e.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x342c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x3441.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x3454.
grub-install: info: relocating an R_X86_64_64 entry to 0x9ae0 at the offset 0x34af.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x34c4.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x34d5.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x34e2.
grub-install: info: relocating an R_X86_64_64 entry to 0x422 at the offset 0x3509.
grub-install: info: relocating an R_X86_64_64 entry to 0x1db8 at the offset 0x352f.
grub-install: info: relocating an R_X86_64_64 entry to 0xa251 at the offset 0x3540.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x354f.
grub-install: info: relocating an R_X86_64_64 entry to 0x18540 at the offset 0x355b.
grub-install: info: relocating an R_X86_64_64 entry to 0xb560 at the offset 0x356b.
grub-install: info: relocating an R_X86_64_64 entry to 0x18550 at the offset 0x3575.
grub-install: info: relocating an R_X86_64_64 entry to 0xb578 at the offset 0x3581.
grub-install: info: relocating an R_X86_64_64 entry to 0xb560 at the offset 0x3590.
grub-install: info: relocating an R_X86_64_64 entry to 0x18540 at the offset 0x359a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7276 at the offset 0x35a4.
grub-install: info: relocating an R_X86_64_64 entry to 0xb560 at the offset 0x35b2.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x35c2.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5a0 at the offset 0x35d2.
grub-install: info: relocating an R_X86_64_64 entry to 0x18538 at the offset 0x35dc.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5b8 at the offset 0x35e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5a0 at the offset 0x35f7.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x3601.
grub-install: info: relocating an R_X86_64_64 entry to 0x7276 at the offset 0x360c.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5a0 at the offset 0x3618.
grub-install: info: relocating an R_X86_64_64 entry to 0x7290 at the offset 0x362b.
grub-install: info: relocating an R_X86_64_64 entry to 0xb560 at the offset 0x3635.
grub-install: info: relocating an R_X86_64_64 entry to 0xb560 at the offset 0x3641.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5a0 at the offset 0x364d.
grub-install: info: relocating an R_X86_64_64 entry to 0xb5a0 at the offset 0x365c.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d8 at the offset 0x3679.
grub-install: info: relocating an R_X86_64_64 entry to 0xe400 at the offset 0x3686.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6d8 at the offset 0x36ea.
grub-install: info: relocating an R_X86_64_64 entry to 0x7cd7 at the offset 0x3730.
grub-install: info: relocating an R_X86_64_64 entry to 0xe400 at the offset 0x3749.
grub-install: info: relocating an R_X86_64_64 entry to 0x3a67 at the offset 0x3753.
grub-install: info: relocating an R_X86_64_64 entry to 0x4187 at the offset 0x375d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa26e at the offset 0x3769.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x3775.
grub-install: info: relocating an R_X86_64_64 entry to 0xa27b at the offset 0x378b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x379a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa290 at the offset 0x37c9.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x37d5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa2a2 at the offset 0x37ea.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x37f6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa2c3 at the offset 0x3805.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x382b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x3870.
grub-install: info: relocating an R_X86_64_64 entry to 0xa2db at the offset 0x38b9.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x38c5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa2ec at the offset 0x38de.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x38ea.
grub-install: info: relocating an R_X86_64_64 entry to 0x4e56 at the offset 0x39e9.
grub-install: info: relocating an R_X86_64_64 entry to 0xa30d at the offset 0x3a00.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x3a11.
grub-install: info: relocating an R_X86_64_64 entry to 0x3c27 at the offset 0x3a2a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3c27 at the offset 0x3a3f.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0x3a5f.
grub-install: info: relocating an R_X86_64_64 entry to 0x3b7f at the offset 0x3a7f.
grub-install: info: relocating an R_X86_64_64 entry to 0xa2ec at the offset 0x3ace.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x3ada.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x3bb4.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x3bc1.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x3c22.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0x3c8b.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x3cd7.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x3cf0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3b7f at the offset 0x3d05.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x3d30.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x3d52.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x3d65.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6e0 at the offset 0x3d7d.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6e0 at the offset 0x3d8c.
grub-install: info: relocating an R_X86_64_64 entry to 0x417b at the offset 0x3d9d.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x3dc2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa31b at the offset 0x3e0a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe410 at the offset 0x3e23.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x3e3e.
grub-install: info: relocating an R_X86_64_64 entry to 0x7290 at the offset 0x3ecd.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x3edc.
grub-install: info: relocating an R_X86_64_64 entry to 0xa31e at the offset 0x3eed.
grub-install: info: relocating an R_X86_64_64 entry to 0xa31c at the offset 0x3ef7.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x3f04.
grub-install: info: relocating an R_X86_64_64 entry to 0xa31f at the offset 0x3f0e.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x3f28.
grub-install: info: relocating an R_X86_64_64 entry to 0xa325 at the offset 0x3f32.
grub-install: info: relocating an R_X86_64_64 entry to 0x4322 at the offset 0x3f51.
grub-install: info: relocating an R_X86_64_64 entry to 0x49da at the offset 0x3f5b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa333 at the offset 0x3f67.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x3f71.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x3f7d.
grub-install: info: relocating an R_X86_64_64 entry to 0x69dd at the offset 0x3f94.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x3fa3.
grub-install: info: relocating an R_X86_64_64 entry to 0x47bb at the offset 0x3fb9.
grub-install: info: relocating an R_X86_64_64 entry to 0x7033 at the offset 0x3fd4.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x3fec.
grub-install: info: relocating an R_X86_64_64 entry to 0xa335 at the offset 0x400f.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4020.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4031.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4041.
grub-install: info: relocating an R_X86_64_64 entry to 0xa32b at the offset 0x4057.
grub-install: info: relocating an R_X86_64_64 entry to 0xa346 at the offset 0x4064.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x4070.
grub-install: info: relocating an R_X86_64_64 entry to 0x42e7 at the offset 0x4085.
grub-install: info: relocating an R_X86_64_64 entry to 0xa333 at the offset 0x4097.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x40a1.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x40ad.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x40be.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x40c9.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x40d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xa35f at the offset 0x40f2.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4103.
grub-install: info: relocating an R_X86_64_64 entry to 0x621a at the offset 0x4121.
grub-install: info: relocating an R_X86_64_64 entry to 0x631d at the offset 0x412d.
grub-install: info: relocating an R_X86_64_64 entry to 0x5792 at the offset 0x4141.
grub-install: info: relocating an R_X86_64_64 entry to 0xa35f at the offset 0x4155.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4166.
grub-install: info: relocating an R_X86_64_64 entry to 0x6618 at the offset 0x4173.
grub-install: info: relocating an R_X86_64_64 entry to 0x669c at the offset 0x418d.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x4197.
grub-install: info: relocating an R_X86_64_64 entry to 0xa375 at the offset 0x41b3.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x41bf.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x41de.
grub-install: info: relocating an R_X86_64_64 entry to 0xa37c at the offset 0x41f8.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4209.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x421f.
grub-install: info: relocating an R_X86_64_64 entry to 0xa38e at the offset 0x4238.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3ab at the offset 0x4242.
grub-install: info: relocating an R_X86_64_64 entry to 0x4584 at the offset 0x424c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3ba at the offset 0x4256.
grub-install: info: relocating an R_X86_64_64 entry to 0x41be at the offset 0x4260.
grub-install: info: relocating an R_X86_64_64 entry to 0x41be at the offset 0x4278.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3be at the offset 0x4285.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3de at the offset 0x428f.
grub-install: info: relocating an R_X86_64_64 entry to 0x454f at the offset 0x4299.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3e5 at the offset 0x42a3.
grub-install: info: relocating an R_X86_64_64 entry to 0xa3eb at the offset 0x42b2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa402 at the offset 0x42bc.
grub-install: info: relocating an R_X86_64_64 entry to 0x4342 at the offset 0x42c6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa408 at the offset 0x42d0.
grub-install: info: relocating an R_X86_64_64 entry to 0xa40b at the offset 0x42e2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa41c at the offset 0x42ed.
grub-install: info: relocating an R_X86_64_64 entry to 0x44ec at the offset 0x42f7.
grub-install: info: relocating an R_X86_64_64 entry to 0xa423 at the offset 0x4301.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x4313.
grub-install: info: relocating an R_X86_64_64 entry to 0x91d0 at the offset 0x433a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4351.
grub-install: info: relocating an R_X86_64_64 entry to 0xa42a at the offset 0x4366.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x4372.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4385.
grub-install: info: relocating an R_X86_64_64 entry to 0xa430 at the offset 0x43c8.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x43d2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa430 at the offset 0x43eb.
grub-install: info: relocating an R_X86_64_64 entry to 0xa435 at the offset 0x43f5.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4406.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x441b.
grub-install: info: relocating an R_X86_64_64 entry to 0x4f8a at the offset 0x443a.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6e8 at the offset 0x444e.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4460.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4488.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ee6 at the offset 0x44a9.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x44c1.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x44d6.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x44e1.
grub-install: info: relocating an R_X86_64_64 entry to 0x47bb at the offset 0x4514.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x452c.
grub-install: info: relocating an R_X86_64_64 entry to 0x470c at the offset 0x4546.
grub-install: info: relocating an R_X86_64_64 entry to 0x9164 at the offset 0x4558.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4565.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x4574.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4585.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x45c4.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x45f7.
grub-install: info: relocating an R_X86_64_64 entry to 0x48ed at the offset 0x461c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe440 at the offset 0x4675.
grub-install: info: relocating an R_X86_64_64 entry to 0xe440 at the offset 0x46d3.
grub-install: info: relocating an R_X86_64_64 entry to 0xe440 at the offset 0x4704.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4744.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x4776.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x478a.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x47a1.
grub-install: info: relocating an R_X86_64_64 entry to 0x4a48 at the offset 0x47f0.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x480d.
grub-install: info: relocating an R_X86_64_64 entry to 0x4aa6 at the offset 0x4827.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x483d.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x48a9.
grub-install: info: relocating an R_X86_64_64 entry to 0x4afd at the offset 0x48c6.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x48d5.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x48e9.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4903.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x4951.
grub-install: info: relocating an R_X86_64_64 entry to 0x684a at the offset 0x499d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa462 at the offset 0x49a9.
grub-install: info: relocating an R_X86_64_64 entry to 0xa44d at the offset 0x49b6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa45d at the offset 0x49c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x49d1.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x49de.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x49ef.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x4a08.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4a5a.
grub-install: info: relocating an R_X86_64_64 entry to 0x183c8 at the offset 0x4a65.
grub-install: info: relocating an R_X86_64_64 entry to 0xe440 at the offset 0x4a70.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x4aa2.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x4ab7.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x4ac1.
grub-install: info: relocating an R_X86_64_64 entry to 0xa46e at the offset 0x4aec.
grub-install: info: relocating an R_X86_64_64 entry to 0xa45d at the offset 0x4af6.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x4b05.
grub-install: info: relocating an R_X86_64_64 entry to 0xa462 at the offset 0x4b17.
grub-install: info: relocating an R_X86_64_64 entry to 0x417b at the offset 0x4b3b.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4b45.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6f0 at the offset 0x4b51.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4b6c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa47d at the offset 0x4b93.
grub-install: info: relocating an R_X86_64_64 entry to 0xa45d at the offset 0x4b9d.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x4bae.
grub-install: info: relocating an R_X86_64_64 entry to 0xa462 at the offset 0x4bbf.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x4bd7.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x4c2d.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x4c55.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x4c6a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x4c7e.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x4c9d.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4ca7.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4cd7.
grub-install: info: relocating an R_X86_64_64 entry to 0xa48e at the offset 0x4cf0.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4d03.
grub-install: info: relocating an R_X86_64_64 entry to 0x8fd0 at the offset 0x4d24.
grub-install: info: relocating an R_X86_64_64 entry to 0xa4bc at the offset 0x4d39.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4d48.
grub-install: info: relocating an R_X86_64_64 entry to 0x417b at the offset 0x4d56.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6f0 at the offset 0x4d62.
grub-install: info: relocating an R_X86_64_64 entry to 0x4e56 at the offset 0x4d80.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6f0 at the offset 0x4d91.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x4da8.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x4db4.
grub-install: info: relocating an R_X86_64_64 entry to 0x684a at the offset 0x4dc7.
grub-install: info: relocating an R_X86_64_64 entry to 0xa4ce at the offset 0x4dd6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa45d at the offset 0x4de0.
grub-install: info: relocating an R_X86_64_64 entry to 0xa462 at the offset 0x4def.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x4df9.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x4e08.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ee6 at the offset 0x4e17.
grub-install: info: relocating an R_X86_64_64 entry to 0xa4e4 at the offset 0x4e2a.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4e3b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa4f8 at the offset 0x4ebc.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4ecd.
grub-install: info: relocating an R_X86_64_64 entry to 0xa526 at the offset 0x4f1b.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x4f2c.
grub-install: info: relocating an R_X86_64_64 entry to 0x684a at the offset 0x4f3c.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x4f4a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa554 at the offset 0x4f57.
grub-install: info: relocating an R_X86_64_64 entry to 0xa45d at the offset 0x4f61.
grub-install: info: relocating an R_X86_64_64 entry to 0xa462 at the offset 0x4f70.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x4f7a.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x4f87.
grub-install: info: relocating an R_X86_64_64 entry to 0x4bc1 at the offset 0x4fc8.
grub-install: info: relocating an R_X86_64_64 entry to 0x4a48 at the offset 0x5008.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x505d.
grub-install: info: relocating an R_X86_64_64 entry to 0x4aa6 at the offset 0x507c.
grub-install: info: relocating an R_X86_64_64 entry to 0x4afd at the offset 0x50c4.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x5189.
grub-install: info: relocating an R_X86_64_64 entry to 0x4bc1 at the offset 0x51a3.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x51ec.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x51f6.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x522a.
grub-install: info: relocating an R_X86_64_64 entry to 0x55e8 at the offset 0x5299.
grub-install: info: relocating an R_X86_64_64 entry to 0xa57c at the offset 0x52b3.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x52c5.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x52d7.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x530c.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x5324.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x532f.
grub-install: info: relocating an R_X86_64_64 entry to 0xc710 at the offset 0x5372.
grub-install: info: relocating an R_X86_64_64 entry to 0x5792 at the offset 0x53a4.
grub-install: info: relocating an R_X86_64_64 entry to 0x57cf at the offset 0x53e1.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x5436.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x5440.
grub-install: info: relocating an R_X86_64_64 entry to 0xc710 at the offset 0x546a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x547b.
grub-install: info: relocating an R_X86_64_64 entry to 0x580c at the offset 0x54cc.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x54e6.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x54fa.
grub-install: info: relocating an R_X86_64_64 entry to 0xa593 at the offset 0x5532.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5ad at the offset 0x553c.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x5548.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5b5 at the offset 0x5563.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5bf at the offset 0x5578.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5e0 at the offset 0x55a6.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x55b7.
grub-install: info: relocating an R_X86_64_64 entry to 0x744 at the offset 0x55c8.
grub-install: info: relocating an R_X86_64_64 entry to 0xa603 at the offset 0x55e1.
grub-install: info: relocating an R_X86_64_64 entry to 0xa62a at the offset 0x5608.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x5619.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x562f.
grub-install: info: relocating an R_X86_64_64 entry to 0xa644 at the offset 0x5651.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5ad at the offset 0x565d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5b5 at the offset 0x566c.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x5676.
grub-install: info: relocating an R_X86_64_64 entry to 0xa656 at the offset 0x5683.
grub-install: info: relocating an R_X86_64_64 entry to 0x5626 at the offset 0x5690.
grub-install: info: relocating an R_X86_64_64 entry to 0xa666 at the offset 0x56a6.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x56b5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa67b at the offset 0x56d1.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x56db.
grub-install: info: relocating an R_X86_64_64 entry to 0xa689 at the offset 0x56f4.
grub-install: info: relocating an R_X86_64_64 entry to 0xa698 at the offset 0x570d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6a7 at the offset 0x571e.
grub-install: info: relocating an R_X86_64_64 entry to 0x5626 at the offset 0x572b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6b0 at the offset 0x573c.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x574b.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x5760.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6c5 at the offset 0x5775.
grub-install: info: relocating an R_X86_64_64 entry to 0x5626 at the offset 0x5782.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x579b.
grub-install: info: relocating an R_X86_64_64 entry to 0x631d at the offset 0x57ba.
grub-install: info: relocating an R_X86_64_64 entry to 0x5792 at the offset 0x57e1.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x57f2.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x5802.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x5820.
grub-install: info: relocating an R_X86_64_64 entry to 0x3c27 at the offset 0x588d.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x58d0.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x58e3.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x592d.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0x5940.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6ce at the offset 0x59c4.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x59d5.
grub-install: info: relocating an R_X86_64_64 entry to 0x9b40 at the offset 0x5a4b.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x5a8f.
grub-install: info: relocating an R_X86_64_64 entry to 0xc710 at the offset 0x5aa2.
grub-install: info: relocating an R_X86_64_64 entry to 0x56d3 at the offset 0x5b37.
grub-install: info: relocating an R_X86_64_64 entry to 0x56d3 at the offset 0x5b85.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x5b94.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x5ba3.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6de at the offset 0x5bad.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6ec at the offset 0x5bd4.
grub-install: info: relocating an R_X86_64_64 entry to 0xa6fa at the offset 0x5c22.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x5c33.
grub-install: info: relocating an R_X86_64_64 entry to 0x773 at the offset 0x5c5f.
grub-install: info: relocating an R_X86_64_64 entry to 0x580c at the offset 0x5cbc.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x5ce7.
grub-install: info: relocating an R_X86_64_64 entry to 0xa713 at the offset 0x5cf5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5ad at the offset 0x5cff.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5b5 at the offset 0x5d0e.
grub-install: info: relocating an R_X86_64_64 entry to 0xa72f at the offset 0x5d20.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5ad at the offset 0x5d2a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5b5 at the offset 0x5d39.
grub-install: info: relocating an R_X86_64_64 entry to 0xa740 at the offset 0x5d4b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5ad at the offset 0x5d55.
grub-install: info: relocating an R_X86_64_64 entry to 0xa5b5 at the offset 0x5d64.
grub-install: info: relocating an R_X86_64_64 entry to 0x5696 at the offset 0x5d73.
grub-install: info: relocating an R_X86_64_64 entry to 0xa753 at the offset 0x5d8b.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x5d9c.
grub-install: info: relocating an R_X86_64_64 entry to 0x5926 at the offset 0x5dda.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x5e03.
grub-install: info: relocating an R_X86_64_64 entry to 0x2117 at the offset 0x5e1e.
grub-install: info: relocating an R_X86_64_64 entry to 0xa769 at the offset 0x5e41.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x5e52.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b50 at the offset 0x5e60.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x5e7a.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b05 at the offset 0x5e94.
grub-install: info: relocating an R_X86_64_64 entry to 0x6a68 at the offset 0x5eab.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b05 at the offset 0x5ec0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x5ed1.
grub-install: info: relocating an R_X86_64_64 entry to 0x61d4 at the offset 0x5ee9.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x5efd.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x5f21.
grub-install: info: relocating an R_X86_64_64 entry to 0xa794 at the offset 0x5f30.
grub-install: info: relocating an R_X86_64_64 entry to 0x55e8 at the offset 0x5f45.
grub-install: info: relocating an R_X86_64_64 entry to 0xa794 at the offset 0x5f62.
grub-install: info: relocating an R_X86_64_64 entry to 0xa79b at the offset 0x5f6c.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x5f7d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7b3 at the offset 0x5f96.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x5fa0.
grub-install: info: relocating an R_X86_64_64 entry to 0x621a at the offset 0x5fb7.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x5fc9.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x5fe1.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7c8 at the offset 0x5ff4.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x6005.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x601d.
grub-install: info: relocating an R_X86_64_64 entry to 0x580c at the offset 0x6027.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x6041.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x6081.
grub-install: info: relocating an R_X86_64_64 entry to 0xb630 at the offset 0x608d.
grub-install: info: relocating an R_X86_64_64 entry to 0x645b at the offset 0x60c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x60f6.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x6119.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x612f.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x614b.
grub-install: info: relocating an R_X86_64_64 entry to 0xb630 at the offset 0x616f.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x61c7.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x61dd.
grub-install: info: relocating an R_X86_64_64 entry to 0x645b at the offset 0x61ec.
grub-install: info: relocating an R_X86_64_64 entry to 0x645b at the offset 0x621e.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7d9 at the offset 0x6247.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x6251.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x627a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x62a0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb630 at the offset 0x62bd.
grub-install: info: relocating an R_X86_64_64 entry to 0x645b at the offset 0x6335.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7d9 at the offset 0x634b.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x6358.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6367.
grub-install: info: relocating an R_X86_64_64 entry to 0x645b at the offset 0x638b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7d9 at the offset 0x63a1.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x63ae.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x63db.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0x6415.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x642e.
grub-install: info: relocating an R_X86_64_64 entry to 0x88fd at the offset 0x6438.
grub-install: info: relocating an R_X86_64_64 entry to 0xd770 at the offset 0x644b.
grub-install: info: relocating an R_X86_64_64 entry to 0xd780 at the offset 0x645c.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x6473.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x647f.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x648f.
grub-install: info: relocating an R_X86_64_64 entry to 0xd770 at the offset 0x649a.
grub-install: info: relocating an R_X86_64_64 entry to 0xd770 at the offset 0x64a5.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1a8 at the offset 0x64b5.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x64c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x64cc.
grub-install: info: relocating an R_X86_64_64 entry to 0xd770 at the offset 0x64d7.
grub-install: info: relocating an R_X86_64_64 entry to 0xd780 at the offset 0x64e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xd770 at the offset 0x64f1.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x6509.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x651b.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x6525.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6539.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6547.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7da at the offset 0x6556.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0x6560.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x656c.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x6579.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d4 at the offset 0x6586.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d4 at the offset 0x6591.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x659b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1a8 at the offset 0x65ab.
grub-install: info: relocating an R_X86_64_64 entry to 0xa7e6 at the offset 0x65ba.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x65c6.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1a8 at the offset 0x65d3.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x65f2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa80e at the offset 0x6608.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x6617.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x662a.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x6650.
grub-install: info: relocating an R_X86_64_64 entry to 0xa822 at the offset 0x667e.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x668f.
grub-install: info: relocating an R_X86_64_64 entry to 0x184e0 at the offset 0x66d1.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x6725.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x6734.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6744.
grub-install: info: relocating an R_X86_64_64 entry to 0x69dd at the offset 0x6754.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x676b.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x6791.
grub-install: info: relocating an R_X86_64_64 entry to 0x47bb at the offset 0x67a9.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x67bb.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x67d5.
grub-install: info: relocating an R_X86_64_64 entry to 0xb640 at the offset 0x67ff.
grub-install: info: relocating an R_X86_64_64 entry to 0x7033 at the offset 0x6812.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x6843.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6858.
grub-install: info: relocating an R_X86_64_64 entry to 0x18510 at the offset 0x6862.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b05 at the offset 0x6899.
grub-install: info: relocating an R_X86_64_64 entry to 0x184f0 at the offset 0x68aa.
grub-install: info: relocating an R_X86_64_64 entry to 0x18510 at the offset 0x68b4.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x68be.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x68cf.
grub-install: info: relocating an R_X86_64_64 entry to 0x184f0 at the offset 0x68e2.
grub-install: info: relocating an R_X86_64_64 entry to 0x18510 at the offset 0x68ec.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x68f6.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x6907.
grub-install: info: relocating an R_X86_64_64 entry to 0xa847 at the offset 0x692a.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x693c.
grub-install: info: relocating an R_X86_64_64 entry to 0x5270 at the offset 0x6964.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x6a5c.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x6aba.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0x6aff.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6b0e.
grub-install: info: relocating an R_X86_64_64 entry to 0xa86b at the offset 0x6b20.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x6b31.
grub-install: info: relocating an R_X86_64_64 entry to 0x81c5 at the offset 0x6b58.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6b6c.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0x6b9a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa882 at the offset 0x6bca.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x6bdb.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x6c0a.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6c18.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b8 at the offset 0x6c46.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x6c50.
grub-install: info: relocating an R_X86_64_64 entry to 0xa89b at the offset 0x6c68.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8ac at the offset 0x6c72.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8af at the offset 0x6c81.
grub-install: info: relocating an R_X86_64_64 entry to 0x6d57 at the offset 0x6c90.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8b9 at the offset 0x6c9a.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6caa.
grub-install: info: relocating an R_X86_64_64 entry to 0x684a at the offset 0x6cbd.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8bb at the offset 0x6ccf.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8ac at the offset 0x6cd9.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8af at the offset 0x6ce8.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x6cf5.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6d00.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6d1a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b0 at the offset 0x6d2d.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6d41.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6d58.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b8 at the offset 0x6d64.
grub-install: info: relocating an R_X86_64_64 entry to 0x6d57 at the offset 0x6d73.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8b9 at the offset 0x6d7d.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6d8e.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6d9b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6da9.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6dbf.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6dca.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x6dd7.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b0 at the offset 0x6de1.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6df4.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c0 at the offset 0x6dff.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8d1 at the offset 0x6e1d.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x6e2e.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0x6e46.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x6ec8.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c36 at the offset 0x6ee8.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x6ef8.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x6f05.
grub-install: info: relocating an R_X86_64_64 entry to 0x51a at the offset 0x6f23.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x6f37.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x6f5e.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x6f9f.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c8 at the offset 0x6fb2.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0x6fbe.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x6fd6.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c8 at the offset 0x6fe9.
grub-install: info: relocating an R_X86_64_64 entry to 0x993e at the offset 0x7012.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x7020.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x7057.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8ef at the offset 0x7061.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x706b.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x7077.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0x7086.
grub-install: info: relocating an R_X86_64_64 entry to 0x61d4 at the offset 0x70a3.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x70b2.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x70c9.
grub-install: info: relocating an R_X86_64_64 entry to 0x72bf at the offset 0x7122.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8f2 at the offset 0x712c.
grub-install: info: relocating an R_X86_64_64 entry to 0x6728 at the offset 0x7136.
grub-install: info: relocating an R_X86_64_64 entry to 0x2aeb at the offset 0x714a.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8ee at the offset 0x7177.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8f7 at the offset 0x7181.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x718b.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8fe at the offset 0x71ab.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x71b5.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8fe at the offset 0x71c1.
grub-install: info: relocating an R_X86_64_64 entry to 0x6788 at the offset 0x71cb.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x71da.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a99 at the offset 0x71fd.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c36 at the offset 0x721c.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x7244.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x72aa.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x72c2.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x72dd.
grub-install: info: relocating an R_X86_64_64 entry to 0xa906 at the offset 0x7317.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0x7321.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x7342.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8ee at the offset 0x7356.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8f7 at the offset 0x7367.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x7373.
grub-install: info: relocating an R_X86_64_64 entry to 0xa911 at the offset 0x738a.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x7394.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x73a3.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8f2 at the offset 0x73b2.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x73bc.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x73cb.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0x73dc.
grub-install: info: relocating an R_X86_64_64 entry to 0x6788 at the offset 0x73e6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8f2 at the offset 0x73f2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa911 at the offset 0x73fe.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x740a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0x741c.
grub-install: info: relocating an R_X86_64_64 entry to 0x4632 at the offset 0x7426.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1c8 at the offset 0x7432.
grub-install: info: relocating an R_X86_64_64 entry to 0x8f62 at the offset 0x7444.
grub-install: info: relocating an R_X86_64_64 entry to 0xa918 at the offset 0x7450.
grub-install: info: relocating an R_X86_64_64 entry to 0x631d at the offset 0x745a.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0x7466.
grub-install: info: relocating an R_X86_64_64 entry to 0xe410 at the offset 0x7474.
grub-install: info: relocating an R_X86_64_64 entry to 0xa918 at the offset 0x747e.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x7487.
grub-install: info: relocating an R_X86_64_64 entry to 0x7242 at the offset 0x7494.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x74af.
grub-install: info: relocating an R_X86_64_64 entry to 0x9750 at the offset 0x74d9.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c36 at the offset 0x74ef.
grub-install: info: relocating an R_X86_64_64 entry to 0xa91f at the offset 0x7507.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x7513.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x7525.
grub-install: info: relocating an R_X86_64_64 entry to 0xa91f at the offset 0x753c.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x7548.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x756f.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x75d6.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0x75e4.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0x76d3.
grub-install: info: relocating an R_X86_64_64 entry to 0x7ad0 at the offset 0x771a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7ad0 at the offset 0x778b.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x783a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x7858.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x7879.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x7895.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x78a7.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x78c7.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0x7946.
grub-install: info: relocating an R_X86_64_64 entry to 0x7cd7 at the offset 0x79f2.
grub-install: info: relocating an R_X86_64_64 entry to 0xa924 at the offset 0x7a03.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x7a14.
grub-install: info: relocating an R_X86_64_64 entry to 0xa939 at the offset 0x7a45.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x7a56.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x7b84.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x7b9c.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0x7bcc.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0x7bd6.
grub-install: info: relocating an R_X86_64_64 entry to 0x9b68 at the offset 0x7d20.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0x7dc7.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0x7e6d.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0x7eb7.
grub-install: info: relocating an R_X86_64_64 entry to 0x7cd7 at the offset 0x8010.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x804d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa94d at the offset 0x8190.
grub-install: info: relocating an R_X86_64_64 entry to 0x7e79 at the offset 0x826d.
grub-install: info: relocating an R_X86_64_64 entry to 0x81d1 at the offset 0x8277.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1d0 at the offset 0x8288.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1d0 at the offset 0x82a9.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x82c6.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1d0 at the offset 0x82dc.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x82e5.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2cc at the offset 0x82f0.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2cd at the offset 0x82f9.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2ce at the offset 0x8302.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2cf at the offset 0x830d.
grub-install: info: relocating an R_X86_64_64 entry to 0x795e at the offset 0x832e.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x833a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1d0 at the offset 0x8349.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x835b.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0x83b0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8666 at the offset 0x83c4.
grub-install: info: relocating an R_X86_64_64 entry to 0x8666 at the offset 0x8413.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x8426.
grub-install: info: relocating an R_X86_64_64 entry to 0xa954 at the offset 0x843d.
grub-install: info: relocating an R_X86_64_64 entry to 0xa95a at the offset 0x846a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7b0e at the offset 0x8477.
grub-install: info: relocating an R_X86_64_64 entry to 0xa95e at the offset 0x8499.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x84a3.
grub-install: info: relocating an R_X86_64_64 entry to 0x8666 at the offset 0x84d8.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x84e4.
grub-install: info: relocating an R_X86_64_64 entry to 0x7e79 at the offset 0x850b.
grub-install: info: relocating an R_X86_64_64 entry to 0x81d1 at the offset 0x853c.
grub-install: info: relocating an R_X86_64_64 entry to 0x795e at the offset 0x854d.
grub-install: info: relocating an R_X86_64_64 entry to 0x88fd at the offset 0x85a3.
grub-install: info: relocating an R_X86_64_64 entry to 0x7e79 at the offset 0x85b9.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x85e1.
grub-install: info: relocating an R_X86_64_64 entry to 0x81d1 at the offset 0x8603.
grub-install: info: relocating an R_X86_64_64 entry to 0x795e at the offset 0x861a.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x862b.
grub-install: info: relocating an R_X86_64_64 entry to 0x89b2 at the offset 0x868d.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x869f.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0x86e2.
grub-install: info: relocating an R_X86_64_64 entry to 0x8666 at the offset 0x86f6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa966 at the offset 0x8704.
grub-install: info: relocating an R_X86_64_64 entry to 0x18540 at the offset 0x8710.
grub-install: info: relocating an R_X86_64_64 entry to 0xa970 at the offset 0x8720.
grub-install: info: relocating an R_X86_64_64 entry to 0x991f at the offset 0x872e.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e7e at the offset 0x873a.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x8783.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c36 at the offset 0x87a0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x87b5.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x87eb.
grub-install: info: relocating an R_X86_64_64 entry to 0xb6a0 at the offset 0x8841.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0x8876.
grub-install: info: relocating an R_X86_64_64 entry to 0x8c1a at the offset 0x895d.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b44 at the offset 0x8967.
grub-install: info: relocating an R_X86_64_64 entry to 0x8bd0 at the offset 0x8998.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b44 at the offset 0x89a7.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0x89e0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b44 at the offset 0x8a4e.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b44 at the offset 0x8a64.
grub-install: info: relocating an R_X86_64_64 entry to 0x8bd0 at the offset 0x8a83.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x8ab9.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x8ade.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x8b07.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8b12.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b60 at the offset 0x8b65.
grub-install: info: relocating an R_X86_64_64 entry to 0x94ce at the offset 0x8b70.
grub-install: info: relocating an R_X86_64_64 entry to 0x8b60 at the offset 0x8b9d.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x8bae.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8bc1.
grub-install: info: relocating an R_X86_64_64 entry to 0x81c5 at the offset 0x8c12.
grub-install: info: relocating an R_X86_64_64 entry to 0x18530 at the offset 0x8c24.
grub-install: info: relocating an R_X86_64_64 entry to 0x9471 at the offset 0x8c65.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8c75.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a4d at the offset 0x8c98.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x8cc0.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8cd8.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8ce8.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x8d48.
grub-install: info: relocating an R_X86_64_64 entry to 0x18530 at the offset 0x8d67.
grub-install: info: relocating an R_X86_64_64 entry to 0x939d at the offset 0x8d95.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x8daa.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x8dd8.
grub-install: info: relocating an R_X86_64_64 entry to 0xa988 at the offset 0x8df8.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x8e02.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x8e34.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0x8e59.
grub-install: info: relocating an R_X86_64_64 entry to 0xa989 at the offset 0x8e63.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0x8e72.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x8e83.
grub-install: info: relocating an R_X86_64_64 entry to 0x91d0 at the offset 0x8f2c.
grub-install: info: relocating an R_X86_64_64 entry to 0xa98c at the offset 0x8f41.
grub-install: info: relocating an R_X86_64_64 entry to 0xa9c8 at the offset 0x8f55.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0x8f5f.
grub-install: info: relocating an R_X86_64_64 entry to 0xa9be at the offset 0x8f71.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x8f80.
grub-install: info: relocating an R_X86_64_64 entry to 0x9304 at the offset 0x8fc0.
grub-install: info: relocating an R_X86_64_64 entry to 0x18530 at the offset 0x9024.
grub-install: info: relocating an R_X86_64_64 entry to 0x939d at the offset 0x9036.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x904d.
grub-install: info: relocating an R_X86_64_64 entry to 0x9304 at the offset 0x9086.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0x909b.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x90bb.
grub-install: info: relocating an R_X86_64_64 entry to 0x8cd3 at the offset 0x90d1.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0x911c.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x914e.
grub-install: info: relocating an R_X86_64_64 entry to 0xe410 at the offset 0x9173.
grub-install: info: relocating an R_X86_64_64 entry to 0x7242 at the offset 0x9183.
grub-install: info: relocating an R_X86_64_64 entry to 0xa9d9 at the offset 0x91ae.
grub-install: info: relocating an R_X86_64_64 entry to 0x8775 at the offset 0x91ba.
grub-install: info: relocating an R_X86_64_64 entry to 0xe410 at the offset 0x91c6.
grub-install: info: relocating an R_X86_64_64 entry to 0xa9f0 at the offset 0x91d0.
grub-install: info: relocating an R_X86_64_64 entry to 0xa9f5 at the offset 0x91e4.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x91f0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x9201.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x9216.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa0e at the offset 0x9228.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa0b at the offset 0x9235.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x924a.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2d0 at the offset 0x9261.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0x926b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2d0 at the offset 0x928c.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2d0 at the offset 0x92b1.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x92db.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x92e7.
grub-install: info: relocating an R_X86_64_64 entry to 0x991f at the offset 0x92f3.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa1c at the offset 0x930d.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x9317.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x9323.
grub-install: info: relocating an R_X86_64_64 entry to 0xe2d0 at the offset 0x932f.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0x9339.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa1e at the offset 0x9353.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0x935f.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0x936f.
grub-install: info: relocating an R_X86_64_64 entry to 0x9625 at the offset 0x9379.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x938f.
grub-install: info: relocating an R_X86_64_64 entry to 0x94ce at the offset 0x93af.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0x93c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x97cc at the offset 0x940a.
grub-install: info: relocating an R_X86_64_64 entry to 0x97cc at the offset 0x9442.
grub-install: info: relocating an R_X86_64_64 entry to 0x97cc at the offset 0x9459.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x947b.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3d8 at the offset 0x94af.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3d0 at the offset 0x94c3.
grub-install: info: relocating an R_X86_64_64 entry to 0x18540 at the offset 0x94d4.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x94fa.
grub-install: info: relocating an R_X86_64_64 entry to 0x98ad at the offset 0x9522.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0x952c.
grub-install: info: relocating an R_X86_64_64 entry to 0x56d3 at the offset 0x9541.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7f0 at the offset 0x954c.
grub-install: info: dealing with the relocation section .rela.rodata for .rodata.
grub-install: info: relocating an R_X86_64_64 entry to 0x2419 at the offset 0x0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2430 at the offset 0x8.
grub-install: info: relocating an R_X86_64_64 entry to 0x2443 at the offset 0x10.
grub-install: info: relocating an R_X86_64_64 entry to 0x245d at the offset 0x18.
grub-install: info: relocating an R_X86_64_64 entry to 0x246f at the offset 0x20.
grub-install: info: relocating an R_X86_64_64 entry to 0x25c9 at the offset 0x28.
grub-install: info: relocating an R_X86_64_64 entry to 0x25e4 at the offset 0x30.
grub-install: info: relocating an R_X86_64_64 entry to 0x25fb at the offset 0x38.
grub-install: info: relocating an R_X86_64_64 entry to 0x2616 at the offset 0x40.
grub-install: info: relocating an R_X86_64_64 entry to 0x262d at the offset 0x48.
grub-install: info: relocating an R_X86_64_64 entry to 0x266d at the offset 0x50.
grub-install: info: relocating an R_X86_64_64 entry to 0x27f6 at the offset 0x58.
grub-install: info: relocating an R_X86_64_64 entry to 0x27f6 at the offset 0x60.
grub-install: info: relocating an R_X86_64_64 entry to 0x277e at the offset 0x68.
grub-install: info: relocating an R_X86_64_64 entry to 0x27e4 at the offset 0x70.
grub-install: info: relocating an R_X86_64_64 entry to 0x267f at the offset 0x78.
grub-install: info: relocating an R_X86_64_64 entry to 0x26b6 at the offset 0x80.
grub-install: info: relocating an R_X86_64_64 entry to 0x2704 at the offset 0x88.
grub-install: info: relocating an R_X86_64_64 entry to 0x27a1 at the offset 0x90.
grub-install: info: relocating an R_X86_64_64 entry to 0x2644 at the offset 0x98.
grub-install: info: relocating an R_X86_64_64 entry to 0x27f6 at the offset 0xa0.
grub-install: info: relocating an R_X86_64_64 entry to 0x27f6 at the offset 0xa8.
grub-install: info: relocating an R_X86_64_64 entry to 0x27c5 at the offset 0xb0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2820 at the offset 0xb8.
grub-install: info: relocating an R_X86_64_64 entry to 0x2874 at the offset 0xc0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2892 at the offset 0xc8.
grub-install: info: relocating an R_X86_64_64 entry to 0x28b0 at the offset 0xd0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2922 at the offset 0xd8.
grub-install: info: relocating an R_X86_64_64 entry to 0x5e56 at the offset 0x140.
grub-install: info: relocating an R_X86_64_64 entry to 0x5e56 at the offset 0x148.
grub-install: info: relocating an R_X86_64_64 entry to 0x5f4b at the offset 0x150.
grub-install: info: relocating an R_X86_64_64 entry to 0x5fef at the offset 0x158.
grub-install: info: relocating an R_X86_64_64 entry to 0x6013 at the offset 0x160.
grub-install: info: relocating an R_X86_64_64 entry to 0x8148 at the offset 0x168.
grub-install: info: relocating an R_X86_64_64 entry to 0x818a at the offset 0x170.
grub-install: info: relocating an R_X86_64_64 entry to 0x818a at the offset 0x178.
grub-install: info: relocating an R_X86_64_64 entry to 0x8168 at the offset 0x180.
grub-install: info: relocating an R_X86_64_64 entry to 0x818a at the offset 0x188.
grub-install: info: relocating an R_X86_64_64 entry to 0x818a at the offset 0x190.
grub-install: info: dealing with the relocation section .rela.data for .data.
grub-install: info: relocating an R_X86_64_64 entry to 0x9c4b at the offset 0x0.
grub-install: info: relocating an R_X86_64_64 entry to 0xec7 at the offset 0x10.
grub-install: info: relocating an R_X86_64_64 entry to 0xc1b at the offset 0x18.
grub-install: info: relocating an R_X86_64_64 entry to 0xbe6 at the offset 0x20.
grub-install: info: relocating an R_X86_64_64 entry to 0x1096 at the offset 0x28.
grub-install: info: relocating an R_X86_64_64 entry to 0x128e at the offset 0x30.
grub-install: info: relocating an R_X86_64_64 entry to 0xa266 at the offset 0x90.
grub-install: info: relocating an R_X86_64_64 entry to 0x3829 at the offset 0xa8.
grub-install: info: relocating an R_X86_64_64 entry to 0xa266 at the offset 0xd0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3796 at the offset 0xd8.
grub-install: info: relocating an R_X86_64_64 entry to 0x3775 at the offset 0xe0.
grub-install: info: relocating an R_X86_64_64 entry to 0x34db at the offset 0xe8.
grub-install: info: relocating an R_X86_64_64 entry to 0x36a3 at the offset 0xf8.
grub-install: info: relocating an R_X86_64_64 entry to 0x370f at the offset 0x100.
grub-install: info: relocating an R_X86_64_64 entry to 0x3667 at the offset 0x108.
grub-install: info: relocating an R_X86_64_64 entry to 0x38c2 at the offset 0x110.
grub-install: info: relocating an R_X86_64_64 entry to 0x37c3 at the offset 0x118.
grub-install: info: relocating an R_X86_64_64 entry to 0x3741 at the offset 0x120.
grub-install: info: relocating an R_X86_64_64 entry to 0xd700 at the offset 0x150.
grub-install: info: relocating an R_X86_64_64 entry to 0xa8e4 at the offset 0x170.
grub-install: info: relocating an R_X86_64_64 entry to 0x6e4f at the offset 0x180.
grub-install: info: relocating an R_X86_64_64 entry to 0x6d5d at the offset 0x188.
grub-install: info: relocating an R_X86_64_64 entry to 0x795a at the offset 0x1b0.
grub-install: info: relocating an R_X86_64_64 entry to 0x9855 at the offset 0x300.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa37 at the offset 0x310.
grub-install: info: relocating an R_X86_64_64 entry to 0x417 at the offset 0x318.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa42 at the offset 0x328.
grub-install: info: relocating an R_X86_64_64 entry to 0x422 at the offset 0x330.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa4d at the offset 0x340.
grub-install: info: relocating an R_X86_64_64 entry to 0x4cc at the offset 0x348.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa59 at the offset 0x358.
grub-install: info: relocating an R_X86_64_64 entry to 0x430 at the offset 0x360.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa64 at the offset 0x370.
grub-install: info: relocating an R_X86_64_64 entry to 0x43e at the offset 0x378.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa6f at the offset 0x388.
grub-install: info: relocating an R_X86_64_64 entry to 0x44f at the offset 0x390.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa7a at the offset 0x3a0.
grub-install: info: relocating an R_X86_64_64 entry to 0x463 at the offset 0x3a8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa85 at the offset 0x3b8.
grub-install: info: relocating an R_X86_64_64 entry to 0x47c at the offset 0x3c0.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa90 at the offset 0x3d0.
grub-install: info: relocating an R_X86_64_64 entry to 0x49f at the offset 0x3d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaa9b at the offset 0x3e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xe410 at the offset 0x3f0.
grub-install: info: relocating an R_X86_64_64 entry to 0xaaad at the offset 0x400.
grub-install: info: relocating an R_X86_64_64 entry to 0xb630 at the offset 0x408.
grub-install: info: relocating an R_X86_64_64 entry to 0xaac2 at the offset 0x418.
grub-install: info: relocating an R_X86_64_64 entry to 0x4899 at the offset 0x420.
grub-install: info: relocating an R_X86_64_64 entry to 0xaad4 at the offset 0x430.
grub-install: info: relocating an R_X86_64_64 entry to 0x49da at the offset 0x438.
grub-install: info: relocating an R_X86_64_64 entry to 0xaae8 at the offset 0x448.
grub-install: info: relocating an R_X86_64_64 entry to 0x47bb at the offset 0x450.
grub-install: info: relocating an R_X86_64_64 entry to 0xaaf9 at the offset 0x460.
grub-install: info: relocating an R_X86_64_64 entry to 0xe440 at the offset 0x468.
grub-install: info: relocating an R_X86_64_64 entry to 0xab0f at the offset 0x478.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ee6 at the offset 0x480.
grub-install: info: relocating an R_X86_64_64 entry to 0xab1f at the offset 0x490.
grub-install: info: relocating an R_X86_64_64 entry to 0xe438 at the offset 0x498.
grub-install: info: relocating an R_X86_64_64 entry to 0xab32 at the offset 0x4a8.
grub-install: info: relocating an R_X86_64_64 entry to 0x4ea0 at the offset 0x4b0.
grub-install: info: relocating an R_X86_64_64 entry to 0xab49 at the offset 0x4c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x4eb5 at the offset 0x4c8.
grub-install: info: relocating an R_X86_64_64 entry to 0xab62 at the offset 0x4d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xe430 at the offset 0x4e0.
grub-install: info: relocating an R_X86_64_64 entry to 0xab7a at the offset 0x4f0.
grub-install: info: relocating an R_X86_64_64 entry to 0xe420 at the offset 0x4f8.
grub-install: info: relocating an R_X86_64_64 entry to 0xab98 at the offset 0x508.
grub-install: info: relocating an R_X86_64_64 entry to 0x55c0 at the offset 0x510.
grub-install: info: relocating an R_X86_64_64 entry to 0xabab at the offset 0x520.
grub-install: info: relocating an R_X86_64_64 entry to 0x4f8a at the offset 0x528.
grub-install: info: relocating an R_X86_64_64 entry to 0xabba at the offset 0x538.
grub-install: info: relocating an R_X86_64_64 entry to 0x5270 at the offset 0x540.
grub-install: info: relocating an R_X86_64_64 entry to 0xabc9 at the offset 0x550.
grub-install: info: relocating an R_X86_64_64 entry to 0xe428 at the offset 0x558.
grub-install: info: relocating an R_X86_64_64 entry to 0xabde at the offset 0x568.
grub-install: info: relocating an R_X86_64_64 entry to 0x7cd7 at the offset 0x570.
grub-install: info: relocating an R_X86_64_64 entry to 0xabec at the offset 0x580.
grub-install: info: relocating an R_X86_64_64 entry to 0xc700 at the offset 0x588.
grub-install: info: relocating an R_X86_64_64 entry to 0xabf9 at the offset 0x598.
grub-install: info: relocating an R_X86_64_64 entry to 0x631d at the offset 0x5a0.
grub-install: info: relocating an R_X86_64_64 entry to 0xac06 at the offset 0x5b0.
grub-install: info: relocating an R_X86_64_64 entry to 0x5926 at the offset 0x5b8.
grub-install: info: relocating an R_X86_64_64 entry to 0xac1f at the offset 0x5c8.
grub-install: info: relocating an R_X86_64_64 entry to 0x5792 at the offset 0x5d0.
grub-install: info: relocating an R_X86_64_64 entry to 0xac2b at the offset 0x5e0.
grub-install: info: relocating an R_X86_64_64 entry to 0x580c at the offset 0x5e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xac3a at the offset 0x5f8.
grub-install: info: relocating an R_X86_64_64 entry to 0x57cf at the offset 0x600.
grub-install: info: relocating an R_X86_64_64 entry to 0xac48 at the offset 0x610.
grub-install: info: relocating an R_X86_64_64 entry to 0x599 at the offset 0x618.
grub-install: info: relocating an R_X86_64_64 entry to 0xac56 at the offset 0x628.
grub-install: info: relocating an R_X86_64_64 entry to 0x5a9 at the offset 0x630.
grub-install: info: relocating an R_X86_64_64 entry to 0xac68 at the offset 0x640.
grub-install: info: relocating an R_X86_64_64 entry to 0x5a5 at the offset 0x648.
grub-install: info: relocating an R_X86_64_64 entry to 0xac7a at the offset 0x658.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c6e at the offset 0x660.
grub-install: info: relocating an R_X86_64_64 entry to 0xac92 at the offset 0x670.
grub-install: info: relocating an R_X86_64_64 entry to 0x2d32 at the offset 0x678.
grub-install: info: relocating an R_X86_64_64 entry to 0xacae at the offset 0x688.
grub-install: info: relocating an R_X86_64_64 entry to 0x29f5 at the offset 0x690.
grub-install: info: relocating an R_X86_64_64 entry to 0xaccc at the offset 0x6a0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2f18 at the offset 0x6a8.
grub-install: info: relocating an R_X86_64_64 entry to 0xacea at the offset 0x6b8.
grub-install: info: relocating an R_X86_64_64 entry to 0x2c44 at the offset 0x6c0.
grub-install: info: relocating an R_X86_64_64 entry to 0xacfe at the offset 0x6d0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2355 at the offset 0x6d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xad17 at the offset 0x6e8.
grub-install: info: relocating an R_X86_64_64 entry to 0x2289 at the offset 0x6f0.
grub-install: info: relocating an R_X86_64_64 entry to 0xad2d at the offset 0x700.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e63 at the offset 0x708.
grub-install: info: relocating an R_X86_64_64 entry to 0xad47 at the offset 0x718.
grub-install: info: relocating an R_X86_64_64 entry to 0x2de4 at the offset 0x720.
grub-install: info: relocating an R_X86_64_64 entry to 0xad5f at the offset 0x730.
grub-install: info: relocating an R_X86_64_64 entry to 0x1ff7 at the offset 0x738.
grub-install: info: relocating an R_X86_64_64 entry to 0xad75 at the offset 0x748.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e8 at the offset 0x750.
grub-install: info: relocating an R_X86_64_64 entry to 0xad8b at the offset 0x760.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6a8 at the offset 0x768.
grub-install: info: relocating an R_X86_64_64 entry to 0xada0 at the offset 0x778.
grub-install: info: relocating an R_X86_64_64 entry to 0x1c5f at the offset 0x780.
grub-install: info: relocating an R_X86_64_64 entry to 0xadb7 at the offset 0x790.
grub-install: info: relocating an R_X86_64_64 entry to 0x1c16 at the offset 0x798.
grub-install: info: relocating an R_X86_64_64 entry to 0xadd0 at the offset 0x7a8.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f8 at the offset 0x7b0.
grub-install: info: relocating an R_X86_64_64 entry to 0xade4 at the offset 0x7c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x1d5a at the offset 0x7c8.
grub-install: info: relocating an R_X86_64_64 entry to 0xadfb at the offset 0x7d8.
grub-install: info: relocating an R_X86_64_64 entry to 0x2370 at the offset 0x7e0.
grub-install: info: relocating an R_X86_64_64 entry to 0xae16 at the offset 0x7f0.
grub-install: info: relocating an R_X86_64_64 entry to 0x2117 at the offset 0x7f8.
grub-install: info: relocating an R_X86_64_64 entry to 0xae2b at the offset 0x808.
grub-install: info: relocating an R_X86_64_64 entry to 0x1db8 at the offset 0x810.
grub-install: info: relocating an R_X86_64_64 entry to 0xae42 at the offset 0x820.
grub-install: info: relocating an R_X86_64_64 entry to 0x1f1d at the offset 0x828.
grub-install: info: relocating an R_X86_64_64 entry to 0xae58 at the offset 0x838.
grub-install: info: relocating an R_X86_64_64 entry to 0x1ec2 at the offset 0x840.
grub-install: info: relocating an R_X86_64_64 entry to 0xae79 at the offset 0x850.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e3f at the offset 0x858.
grub-install: info: relocating an R_X86_64_64 entry to 0xae88 at the offset 0x868.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3e0 at the offset 0x870.
grub-install: info: relocating an R_X86_64_64 entry to 0xae9e at the offset 0x880.
grub-install: info: relocating an R_X86_64_64 entry to 0x1581 at the offset 0x888.
grub-install: info: relocating an R_X86_64_64 entry to 0xaebd at the offset 0x898.
grub-install: info: relocating an R_X86_64_64 entry to 0x16cc at the offset 0x8a0.
grub-install: info: relocating an R_X86_64_64 entry to 0xaeda at the offset 0x8b0.
grub-install: info: relocating an R_X86_64_64 entry to 0x6788 at the offset 0x8b8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaeea at the offset 0x8c8.
grub-install: info: relocating an R_X86_64_64 entry to 0x65ea at the offset 0x8d0.
grub-install: info: relocating an R_X86_64_64 entry to 0xaef7 at the offset 0x8e0.
grub-install: info: relocating an R_X86_64_64 entry to 0x64bc at the offset 0x8e8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf04 at the offset 0x8f8.
grub-install: info: relocating an R_X86_64_64 entry to 0x6618 at the offset 0x900.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf13 at the offset 0x910.
grub-install: info: relocating an R_X86_64_64 entry to 0x669c at the offset 0x918.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf2e at the offset 0x928.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d4 at the offset 0x930.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf46 at the offset 0x940.
grub-install: info: relocating an R_X86_64_64 entry to 0x183d0 at the offset 0x948.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf52 at the offset 0x958.
grub-install: info: relocating an R_X86_64_64 entry to 0x184d0 at the offset 0x960.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf5d at the offset 0x970.
grub-install: info: relocating an R_X86_64_64 entry to 0x67ce at the offset 0x978.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf68 at the offset 0x988.
grub-install: info: relocating an R_X86_64_64 entry to 0x68d6 at the offset 0x990.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf77 at the offset 0x9a0.
grub-install: info: relocating an R_X86_64_64 entry to 0x684a at the offset 0x9a8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf87 at the offset 0x9b8.
grub-install: info: relocating an R_X86_64_64 entry to 0x1e7e at the offset 0x9c0.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf91 at the offset 0x9d0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a9c at the offset 0x9d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xaf9c at the offset 0x9e8.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b05 at the offset 0x9f0.
grub-install: info: relocating an R_X86_64_64 entry to 0xafac at the offset 0xa00.
grub-install: info: relocating an R_X86_64_64 entry to 0x184f0 at the offset 0xa08.
grub-install: info: relocating an R_X86_64_64 entry to 0xafc2 at the offset 0xa18.
grub-install: info: relocating an R_X86_64_64 entry to 0x18510 at the offset 0xa20.
grub-install: info: relocating an R_X86_64_64 entry to 0xafdc at the offset 0xa30.
grub-install: info: relocating an R_X86_64_64 entry to 0x69dd at the offset 0xa38.
grub-install: info: relocating an R_X86_64_64 entry to 0xaff6 at the offset 0xa48.
grub-install: info: relocating an R_X86_64_64 entry to 0x6b50 at the offset 0xa50.
grub-install: info: relocating an R_X86_64_64 entry to 0xb005 at the offset 0xa60.
grub-install: info: relocating an R_X86_64_64 entry to 0x184e0 at the offset 0xa68.
grub-install: info: relocating an R_X86_64_64 entry to 0xb01d at the offset 0xa78.
grub-install: info: relocating an R_X86_64_64 entry to 0x6a68 at the offset 0xa80.
grub-install: info: relocating an R_X86_64_64 entry to 0xb02c at the offset 0xa90.
grub-install: info: relocating an R_X86_64_64 entry to 0x6d22 at the offset 0xa98.
grub-install: info: relocating an R_X86_64_64 entry to 0xb03b at the offset 0xaa8.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e70 at the offset 0xab0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb045 at the offset 0xac0.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b0 at the offset 0xac8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb05b at the offset 0xad8.
grub-install: info: relocating an R_X86_64_64 entry to 0xe1b8 at the offset 0xae0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb068 at the offset 0xaf0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7033 at the offset 0xaf8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb076 at the offset 0xb08.
grub-install: info: relocating an R_X86_64_64 entry to 0x417b at the offset 0xb10.
grub-install: info: relocating an R_X86_64_64 entry to 0xb087 at the offset 0xb20.
grub-install: info: relocating an R_X86_64_64 entry to 0x991f at the offset 0xb28.
grub-install: info: relocating an R_X86_64_64 entry to 0xb093 at the offset 0xb38.
grub-install: info: relocating an R_X86_64_64 entry to 0x98ad at the offset 0xb40.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0a7 at the offset 0xb50.
grub-install: info: relocating an R_X86_64_64 entry to 0xb690 at the offset 0xb58.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0b4 at the offset 0xb68.
grub-install: info: relocating an R_X86_64_64 entry to 0x7aae at the offset 0xb70.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0c1 at the offset 0xb80.
grub-install: info: relocating an R_X86_64_64 entry to 0x7276 at the offset 0xb88.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0d0 at the offset 0xb98.
grub-install: info: relocating an R_X86_64_64 entry to 0x7290 at the offset 0xba0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0e1 at the offset 0xbb0.
grub-install: info: relocating an R_X86_64_64 entry to 0x534 at the offset 0xbb8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0f3 at the offset 0xbc8.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e25 at the offset 0xbd0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb0ff at the offset 0xbe0.
grub-install: info: relocating an R_X86_64_64 entry to 0x3c27 at the offset 0xbe8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb10d at the offset 0xbf8.
grub-install: info: relocating an R_X86_64_64 entry to 0x547 at the offset 0xc00.
grub-install: info: relocating an R_X86_64_64 entry to 0xb121 at the offset 0xc10.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0xc18.
grub-install: info: relocating an R_X86_64_64 entry to 0xb12d at the offset 0xc28.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0xc30.
grub-install: info: relocating an R_X86_64_64 entry to 0xb13a at the offset 0xc40.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0xc48.
grub-install: info: relocating an R_X86_64_64 entry to 0xb146 at the offset 0xc58.
grub-install: info: relocating an R_X86_64_64 entry to 0x4195 at the offset 0xc60.
grub-install: info: relocating an R_X86_64_64 entry to 0xb156 at the offset 0xc70.
grub-install: info: relocating an R_X86_64_64 entry to 0xe408 at the offset 0xc78.
grub-install: info: relocating an R_X86_64_64 entry to 0xb163 at the offset 0xc88.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3f0 at the offset 0xc90.
grub-install: info: relocating an R_X86_64_64 entry to 0xb170 at the offset 0xca0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7242 at the offset 0xca8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb185 at the offset 0xcb8.
grub-install: info: relocating an R_X86_64_64 entry to 0xc6e8 at the offset 0xcc0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb193 at the offset 0xcd0.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3d0 at the offset 0xcd8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb1ac at the offset 0xce8.
grub-install: info: relocating an R_X86_64_64 entry to 0x8c1a at the offset 0xcf0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb1c6 at the offset 0xd00.
grub-install: info: relocating an R_X86_64_64 entry to 0x8cd3 at the offset 0xd08.
grub-install: info: relocating an R_X86_64_64 entry to 0xb1e0 at the offset 0xd18.
grub-install: info: relocating an R_X86_64_64 entry to 0x91d0 at the offset 0xd20.
grub-install: info: relocating an R_X86_64_64 entry to 0xb1f8 at the offset 0xd30.
grub-install: info: relocating an R_X86_64_64 entry to 0x9164 at the offset 0xd38.
grub-install: info: relocating an R_X86_64_64 entry to 0xb20f at the offset 0xd48.
grub-install: info: relocating an R_X86_64_64 entry to 0x18530 at the offset 0xd50.
grub-install: info: relocating an R_X86_64_64 entry to 0xb227 at the offset 0xd60.
grub-install: info: relocating an R_X86_64_64 entry to 0x8fd0 at the offset 0xd68.
grub-install: info: relocating an R_X86_64_64 entry to 0xb23c at the offset 0xd78.
grub-install: info: relocating an R_X86_64_64 entry to 0x6a2 at the offset 0xd80.
grub-install: info: relocating an R_X86_64_64 entry to 0xb255 at the offset 0xd90.
grub-install: info: relocating an R_X86_64_64 entry to 0x5d3 at the offset 0xd98.
grub-install: info: relocating an R_X86_64_64 entry to 0xb266 at the offset 0xda8.
grub-install: info: relocating an R_X86_64_64 entry to 0x5ac at the offset 0xdb0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb27c at the offset 0xdc0.
grub-install: info: relocating an R_X86_64_64 entry to 0x6944 at the offset 0xdc8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb28d at the offset 0xdd8.
grub-install: info: relocating an R_X86_64_64 entry to 0x87d3 at the offset 0xde0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb299 at the offset 0xdf0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8775 at the offset 0xdf8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2a6 at the offset 0xe08.
grub-install: info: relocating an R_X86_64_64 entry to 0x79d3 at the offset 0xe10.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2b1 at the offset 0xe20.
grub-install: info: relocating an R_X86_64_64 entry to 0x8822 at the offset 0xe28.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2c3 at the offset 0xe38.
grub-install: info: relocating an R_X86_64_64 entry to 0x40bf at the offset 0xe40.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2d0 at the offset 0xe50.
grub-install: info: relocating an R_X86_64_64 entry to 0x98f7 at the offset 0xe58.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2dd at the offset 0xe68.
grub-install: info: relocating an R_X86_64_64 entry to 0x41be at the offset 0xe70.
grub-install: info: relocating an R_X86_64_64 entry to 0xb2f8 at the offset 0xe80.
grub-install: info: relocating an R_X86_64_64 entry to 0x6728 at the offset 0xe88.
grub-install: info: relocating an R_X86_64_64 entry to 0xb314 at the offset 0xe98.
grub-install: info: relocating an R_X86_64_64 entry to 0x896d at the offset 0xea0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb322 at the offset 0xeb0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a83 at the offset 0xeb8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb32e at the offset 0xec8.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a2e at the offset 0xed0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb33a at the offset 0xee0.
grub-install: info: relocating an R_X86_64_64 entry to 0x79c0 at the offset 0xee8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb346 at the offset 0xef8.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c8f at the offset 0xf00.
grub-install: info: relocating an R_X86_64_64 entry to 0xb352 at the offset 0xf10.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c25 at the offset 0xf18.
grub-install: info: relocating an R_X86_64_64 entry to 0xb35e at the offset 0xf28.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a4d at the offset 0xf30.
grub-install: info: relocating an R_X86_64_64 entry to 0xb36b at the offset 0xf40.
grub-install: info: relocating an R_X86_64_64 entry to 0x7c36 at the offset 0xf48.
grub-install: info: relocating an R_X86_64_64 entry to 0xb378 at the offset 0xf58.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a99 at the offset 0xf60.
grub-install: info: relocating an R_X86_64_64 entry to 0xb385 at the offset 0xf70.
grub-install: info: relocating an R_X86_64_64 entry to 0x81c5 at the offset 0xf78.
grub-install: info: relocating an R_X86_64_64 entry to 0xb392 at the offset 0xf88.
grub-install: info: relocating an R_X86_64_64 entry to 0x7d3d at the offset 0xf90.
grub-install: info: relocating an R_X86_64_64 entry to 0xb3a0 at the offset 0xfa0.
grub-install: info: relocating an R_X86_64_64 entry to 0x7b0e at the offset 0xfa8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb3ad at the offset 0xfb8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e8 at the offset 0xfc0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb3c7 at the offset 0xfd0.
grub-install: info: relocating an R_X86_64_64 entry to 0x18540 at the offset 0xfd8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb3d8 at the offset 0xfe8.
grub-install: info: relocating an R_X86_64_64 entry to 0x18550 at the offset 0xff0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb3f2 at the offset 0x1000.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e9 at the offset 0x1008.
grub-install: info: relocating an R_X86_64_64 entry to 0xb409 at the offset 0x1018.
grub-install: info: relocating an R_X86_64_64 entry to 0x18548 at the offset 0x1020.
grub-install: info: relocating an R_X86_64_64 entry to 0xb41b at the offset 0x1030.
grub-install: info: relocating an R_X86_64_64 entry to 0x18538 at the offset 0x1038.
grub-install: info: relocating an R_X86_64_64 entry to 0xb436 at the offset 0x1048.
grub-install: info: relocating an R_X86_64_64 entry to 0xe3d8 at the offset 0x1050.
grub-install: info: relocating an R_X86_64_64 entry to 0xb449 at the offset 0x1060.
grub-install: info: relocating an R_X86_64_64 entry to 0xe400 at the offset 0x1068.
grub-install: info: relocating an R_X86_64_64 entry to 0xb457 at the offset 0x1078.
grub-install: info: relocating an R_X86_64_64 entry to 0x42af at the offset 0x1080.
grub-install: info: relocating an R_X86_64_64 entry to 0xb46f at the offset 0x1090.
grub-install: info: relocating an R_X86_64_64 entry to 0x8666 at the offset 0x1098.
grub-install: info: relocating an R_X86_64_64 entry to 0xb47c at the offset 0x10a8.
grub-install: info: relocating an R_X86_64_64 entry to 0x88fd at the offset 0x10b0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb48b at the offset 0x10c0.
grub-install: info: relocating an R_X86_64_64 entry to 0x8a4d at the offset 0x10c8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb49a at the offset 0x10d8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb7e0 at the offset 0x10e0.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4a5 at the offset 0x10f0.
grub-install: info: relocating an R_X86_64_64 entry to 0x89b2 at the offset 0x10f8.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4b5 at the offset 0x1108.
grub-install: info: relocating an R_X86_64_64 entry to 0x3e36 at the offset 0x1110.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4c1 at the offset 0x1120.
grub-install: info: relocating an R_X86_64_64 entry to 0x7a0c at the offset 0x1128.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4c8 at the offset 0x1138.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x1140.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4cf at the offset 0x1150.
grub-install: info: relocating an R_X86_64_64 entry to 0x797a at the offset 0x1158.
grub-install: info: relocating an R_X86_64_64 entry to 0xb4d7 at the offset 0x1168.
grub-install: info: relocating an R_X86_64_64 entry to 0x7baf at the offset 0x1170.
grub-install: info: translating the relocation section .rela.text.
grub-install: info: adding a relocation entry for 0x51d.
grub-install: info: adding a relocation entry for 0x52a.
grub-install: info: adding a relocation entry for 0x53c.
grub-install: info: adding a relocation entry for 0x565.
grub-install: info: adding a relocation entry for 0x57a.
grub-install: info: adding a relocation entry for 0x58b.
grub-install: info: adding a relocation entry for 0x59b.
grub-install: info: adding a relocation entry for 0x5e0.
grub-install: info: adding a relocation entry for 0x6af.
grub-install: info: adding a relocation entry for 0x755.
grub-install: info: adding a relocation entry for 0x766.
grub-install: info: adding a relocation entry for 0x78f.
grub-install: info: adding a relocation entry for 0x810.
grub-install: info: adding a relocation entry for 0x822.
grub-install: info: adding a relocation entry for 0x874.
grub-install: info: adding a relocation entry for 0x885.
grub-install: info: adding a relocation entry for 0x8fd.
grub-install: info: adding a relocation entry for 0x927.
grub-install: info: adding a relocation entry for 0x945.
grub-install: info: adding a relocation entry for 0x97a.
grub-install: info: adding a relocation entry for 0x9ac.
grub-install: info: adding a relocation entry for 0x9cd.
grub-install: info: adding a relocation entry for 0x9fa.
grub-install: info: adding a relocation entry for 0xa0c.
grub-install: info: adding a relocation entry for 0xa38.
grub-install: info: adding a relocation entry for 0xa42.
grub-install: info: adding a relocation entry for 0xa6d.
grub-install: info: adding a relocation entry for 0xa94.
grub-install: info: adding a relocation entry for 0xac0.
grub-install: info: adding a relocation entry for 0xacf.
grub-install: info: adding a relocation entry for 0xafd.
grub-install: info: adding a relocation entry for 0xb22.
grub-install: info: adding a relocation entry for 0xb3b.
grub-install: info: adding a relocation entry for 0xb49.
grub-install: info: adding a relocation entry for 0xb67.
grub-install: info: adding a relocation entry for 0xb80.
grub-install: info: adding a relocation entry for 0xbc6.
grub-install: info: adding a relocation entry for 0xbeb.
grub-install: info: adding a relocation entry for 0xbf5.
grub-install: info: adding a relocation entry for 0xc04.
grub-install: info: adding a relocation entry for 0xc10.
grub-install: info: adding a relocation entry for 0xc24.
grub-install: info: adding a relocation entry for 0xc2e.
grub-install: info: adding a relocation entry for 0xc38.
grub-install: info: adding a relocation entry for 0xc4a.
grub-install: info: adding a relocation entry for 0xc80.
grub-install: info: adding a relocation entry for 0xc8f.
grub-install: info: adding a relocation entry for 0xca5.
grub-install: info: adding a relocation entry for 0xcb6.
grub-install: info: adding a relocation entry for 0xcc1.
grub-install: info: adding a relocation entry for 0xcec.
grub-install: info: adding a relocation entry for 0xcfb.
grub-install: info: adding a relocation entry for 0xd0a.
grub-install: info: adding a relocation entry for 0xd17.
grub-install: info: adding a relocation entry for 0xd33.
grub-install: info: adding a relocation entry for 0xd44.
grub-install: info: adding a relocation entry for 0xd58.
grub-install: info: adding a relocation entry for 0xd65.
grub-install: info: adding a relocation entry for 0xd77.
grub-install: info: adding a relocation entry for 0xd81.
grub-install: info: adding a relocation entry for 0xdd4.
grub-install: info: adding a relocation entry for 0xde5.
grub-install: info: adding a relocation entry for 0xe18.
grub-install: info: adding a relocation entry for 0xe22.
grub-install: info: adding a relocation entry for 0xe31.
grub-install: info: adding a relocation entry for 0xe3b.
grub-install: info: adding a relocation entry for 0xe55.
grub-install: info: adding a relocation entry for 0xe61.
grub-install: info: adding a relocation entry for 0xe6c.
grub-install: info: adding a relocation entry for 0xe77.
grub-install: info: adding a relocation entry for 0xea4.
grub-install: info: adding a relocation entry for 0xeb6.
grub-install: info: adding a relocation entry for 0xeea.
grub-install: info: adding a relocation entry for 0xeff.
grub-install: info: adding a relocation entry for 0xf13.
grub-install: info: adding a relocation entry for 0xf25.
grub-install: info: adding a relocation entry for 0xf2f.
grub-install: info: adding a relocation entry for 0xf3e.
grub-install: info: adding a relocation entry for 0xf48.
grub-install: info: adding a relocation entry for 0xf77.
grub-install: info: adding a relocation entry for 0xf8c.
grub-install: info: adding a relocation entry for 0xfa0.
grub-install: info: adding a relocation entry for 0xfb2.
grub-install: info: adding a relocation entry for 0xfbc.
grub-install: info: adding a relocation entry for 0xfcb.
grub-install: info: adding a relocation entry for 0xfd5.
grub-install: info: adding a relocation entry for 0x1000.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 184 bytes of a fixup block starting at 0x0.
grub-install: info: adding a relocation entry for 0x1015.
grub-install: info: adding a relocation entry for 0x1029.
grub-install: info: adding a relocation entry for 0x103b.
grub-install: info: adding a relocation entry for 0x1045.
grub-install: info: adding a relocation entry for 0x1054.
grub-install: info: adding a relocation entry for 0x105e.
grub-install: info: adding a relocation entry for 0x10a5.
grub-install: info: adding a relocation entry for 0x10b1.
grub-install: info: adding a relocation entry for 0x10be.
grub-install: info: adding a relocation entry for 0x10db.
grub-install: info: adding a relocation entry for 0x1109.
grub-install: info: adding a relocation entry for 0x1124.
grub-install: info: adding a relocation entry for 0x113d.
grub-install: info: adding a relocation entry for 0x117f.
grub-install: info: adding a relocation entry for 0x119c.
grub-install: info: adding a relocation entry for 0x11b2.
grub-install: info: adding a relocation entry for 0x11d8.
grub-install: info: adding a relocation entry for 0x11e2.
grub-install: info: adding a relocation entry for 0x1220.
grub-install: info: adding a relocation entry for 0x127a.
grub-install: info: adding a relocation entry for 0x129d.
grub-install: info: adding a relocation entry for 0x12a9.
grub-install: info: adding a relocation entry for 0x12b6.
grub-install: info: adding a relocation entry for 0x12d3.
grub-install: info: adding a relocation entry for 0x1301.
grub-install: info: adding a relocation entry for 0x131c.
grub-install: info: adding a relocation entry for 0x1335.
grub-install: info: adding a relocation entry for 0x134e.
grub-install: info: adding a relocation entry for 0x1362.
grub-install: info: adding a relocation entry for 0x136c.
grub-install: info: adding a relocation entry for 0x1387.
grub-install: info: adding a relocation entry for 0x13ee.
grub-install: info: adding a relocation entry for 0x13f8.
grub-install: info: adding a relocation entry for 0x1404.
grub-install: info: adding a relocation entry for 0x149d.
grub-install: info: adding a relocation entry for 0x14b3.
grub-install: info: adding a relocation entry for 0x1506.
grub-install: info: adding a relocation entry for 0x1515.
grub-install: info: adding a relocation entry for 0x151f.
grub-install: info: adding a relocation entry for 0x153b.
grub-install: info: adding a relocation entry for 0x1547.
grub-install: info: adding a relocation entry for 0x1551.
grub-install: info: adding a relocation entry for 0x156a.
grub-install: info: adding a relocation entry for 0x15cd.
grub-install: info: adding a relocation entry for 0x15d7.
grub-install: info: adding a relocation entry for 0x1604.
grub-install: info: adding a relocation entry for 0x1625.
grub-install: info: adding a relocation entry for 0x1638.
grub-install: info: adding a relocation entry for 0x16ac.
grub-install: info: adding a relocation entry for 0x16d0.
grub-install: info: adding a relocation entry for 0x16f6.
grub-install: info: adding a relocation entry for 0x172c.
grub-install: info: adding a relocation entry for 0x1783.
grub-install: info: adding a relocation entry for 0x1796.
grub-install: info: adding a relocation entry for 0x17ae.
grub-install: info: adding a relocation entry for 0x17c0.
grub-install: info: adding a relocation entry for 0x17f0.
grub-install: info: adding a relocation entry for 0x180a.
grub-install: info: adding a relocation entry for 0x181d.
grub-install: info: adding a relocation entry for 0x182a.
grub-install: info: adding a relocation entry for 0x1843.
grub-install: info: adding a relocation entry for 0x1857.
grub-install: info: adding a relocation entry for 0x1861.
grub-install: info: adding a relocation entry for 0x1879.
grub-install: info: adding a relocation entry for 0x1892.
grub-install: info: adding a relocation entry for 0x18ad.
grub-install: info: adding a relocation entry for 0x18c6.
grub-install: info: adding a relocation entry for 0x19ec.
grub-install: info: adding a relocation entry for 0x1a45.
grub-install: info: adding a relocation entry for 0x1a64.
grub-install: info: adding a relocation entry for 0x1a70.
grub-install: info: adding a relocation entry for 0x1a84.
grub-install: info: adding a relocation entry for 0x1c1f.
grub-install: info: adding a relocation entry for 0x1c32.
grub-install: info: adding a relocation entry for 0x1c68.
grub-install: info: adding a relocation entry for 0x1ca5.
grub-install: info: adding a relocation entry for 0x1cc3.
grub-install: info: adding a relocation entry for 0x1cec.
grub-install: info: adding a relocation entry for 0x1d2d.
grub-install: info: adding a relocation entry for 0x1d63.
grub-install: info: adding a relocation entry for 0x1d81.
grub-install: info: adding a relocation entry for 0x1d99.
grub-install: info: adding a relocation entry for 0x1dbf.
grub-install: info: adding a relocation entry for 0x1dc9.
grub-install: info: adding a relocation entry for 0x1df9.
grub-install: info: adding a relocation entry for 0x1e24.
grub-install: info: adding a relocation entry for 0x1e41.
grub-install: info: adding a relocation entry for 0x1e59.
grub-install: info: adding a relocation entry for 0x1e6a.
grub-install: info: adding a relocation entry for 0x1e74.
grub-install: info: adding a relocation entry for 0x1e81.
grub-install: info: adding a relocation entry for 0x1e8d.
grub-install: info: adding a relocation entry for 0x1ea9.
grub-install: info: adding a relocation entry for 0x1eb6.
grub-install: info: adding a relocation entry for 0x1ec7.
grub-install: info: adding a relocation entry for 0x1eec.
grub-install: info: adding a relocation entry for 0x1efe.
grub-install: info: adding a relocation entry for 0x1f0f.
grub-install: info: adding a relocation entry for 0x1f24.
grub-install: info: adding a relocation entry for 0x1f4b.
grub-install: info: adding a relocation entry for 0x1f59.
grub-install: info: adding a relocation entry for 0x1f78.
grub-install: info: adding a relocation entry for 0x1f8a.
grub-install: info: adding a relocation entry for 0x1fad.
grub-install: info: adding a relocation entry for 0x1fc9.
grub-install: info: adding a relocation entry for 0x1fe1.
grub-install: info: adding a relocation entry for 0x1ffb.
grub-install: info: adding a relocation entry for 0x2005.
grub-install: info: writing 224 bytes of a fixup block starting at 0x1000.
grub-install: info: adding a relocation entry for 0x205c.
grub-install: info: adding a relocation entry for 0x2066.
grub-install: info: adding a relocation entry for 0x2078.
grub-install: info: adding a relocation entry for 0x20b7.
grub-install: info: adding a relocation entry for 0x20e4.
grub-install: info: adding a relocation entry for 0x211b.
grub-install: info: adding a relocation entry for 0x2127.
grub-install: info: adding a relocation entry for 0x21a0.
grub-install: info: adding a relocation entry for 0x21cf.
grub-install: info: adding a relocation entry for 0x21ee.
grub-install: info: adding a relocation entry for 0x2201.
grub-install: info: adding a relocation entry for 0x221f.
grub-install: info: adding a relocation entry for 0x223c.
grub-install: info: adding a relocation entry for 0x22d3.
grub-install: info: adding a relocation entry for 0x22ea.
grub-install: info: adding a relocation entry for 0x235c.
grub-install: info: adding a relocation entry for 0x2366SET@_progressbar1.pulse()
.
grub-install: info: adding a relocation entry for 0x237b.
grub-install: info: adding a relocation entry for 0x23d4.
grub-install: info: adding a relocation entry for 0x23e2.
grub-install: info: adding a relocation entry for 0x23f5.
grub-install: info: adding a relocation entry for 0x240e.
grub-install: info: adding a relocation entry for 0x2423.
grub-install: info: adding a relocation entry for 0x2436.
grub-install: info: adding a relocation entry for 0x244d.
grub-install: info: adding a relocation entry for 0x2462.
grub-install: info: adding a relocation entry for 0x2474.
grub-install: info: adding a relocation entry for 0x2483.
grub-install: info: adding a relocation entry for 0x249c.
grub-install: info: adding a relocation entry for 0x24b4.
grub-install: info: adding a relocation entry for 0x24c9.
grub-install: info: adding a relocation entry for 0x24de.
grub-install: info: adding a relocation entry for 0x24f2.
grub-install: info: adding a relocation entry for 0x2504.
grub-install: info: adding a relocation entry for 0x251e.
grub-install: info: adding a relocation entry for 0x2534.
grub-install: info: adding a relocation entry for 0x2547.
grub-install: info: adding a relocation entry for 0x2576.
grub-install: info: adding a relocation entry for 0x25a1.
grub-install: info: adding a relocation entry for 0x25be.
grub-install: info: adding a relocation entry for 0x25d3.
grub-install: info: adding a relocation entry for 0x25ee.
grub-install: info: adding a relocation entry for 0x2605.
grub-install: info: adding a relocation entry for 0x261c.
grub-install: info: adding a relocation entry for 0x2637.
grub-install: info: adding a relocation entry for 0x264e.
grub-install: info: adding a relocation entry for 0x2672.
grub-install: info: adding a relocation entry for 0x2689.
grub-install: info: adding a relocation entry for 0x26be.
grub-install: info: adding a relocation entry for 0x270c.
grub-install: info: adding a relocation entry for 0x2788.
grub-install: info: adding a relocation entry for 0x27ab.
grub-install: info: adding a relocation entry for 0x27cf.
grub-install: info: adding a relocation entry for 0x27e9.
grub-install: info: adding a relocation entry for 0x27f8.
grub-install: info: adding a relocation entry for 0x2815.
grub-install: info: adding a relocation entry for 0x282b.
grub-install: info: adding a relocation entry for 0x287e.
grub-install: info: adding a relocation entry for 0x2897.
grub-install: info: adding a relocation entry for 0x28a1.
grub-install: info: adding a relocation entry for 0x28b6.
grub-install: info: adding a relocation entry for 0x28e3.
grub-install: info: adding a relocation entry for 0x28f5.
grub-install: info: adding a relocation entry for 0x2902.
grub-install: info: adding a relocation entry for 0x2913.
grub-install: info: adding a relocation entry for 0x292c.
grub-install: info: adding a relocation entry for 0x296b.
grub-install: info: adding a relocation entry for 0x297b.
grub-install: info: adding a relocation entry for 0x2993.
grub-install: info: adding a relocation entry for 0x29b9.
grub-install: info: adding a relocation entry for 0x29c6.
grub-install: info: adding a relocation entry for 0x2a0e.
grub-install: info: adding a relocation entry for 0x2a88.
grub-install: info: adding a relocation entry for 0x2a94.
grub-install: info: adding a relocation entry for 0x2a9e.
grub-install: info: adding a relocation entry for 0x2aaa.
grub-install: info: adding a relocation entry for 0x2ab6.
grub-install: info: adding a relocation entry for 0x2ad4.
grub-install: info: adding a relocation entry for 0x2ae1.
grub-install: info: adding a relocation entry for 0x2aef.
grub-install: info: adding a relocation entry for 0x2b04.
grub-install: info: adding a relocation entry for 0x2b1c.
grub-install: info: adding a relocation entry for 0x2b2c.
grub-install: info: adding a relocation entry for 0x2b47.
grub-install: info: adding a relocation entry for 0x2b6b.
grub-install: info: adding a relocation entry for 0x2b85.
grub-install: info: adding a relocation entry for 0x2b92.
grub-install: info: adding a relocation entry for 0x2bbb.
grub-install: info: adding a relocation entry for 0x2be5.
grub-install: info: adding a relocation entry for 0x2c49.
grub-install: info: adding a relocation entry for 0x2c5c.
grub-install: info: adding a relocation entry for 0x2ca6.
grub-install: info: adding a relocation entry for 0x2cc3.
grub-install: info: adding a relocation entry for 0x2d13.
grub-install: info: adding a relocation entry for 0x2d57.
grub-install: info: adding a relocation entry for 0x2d76.
grub-install: info: adding a relocation entry for 0x2dc5.
grub-install: info: adding a relocation entry for 0x2de8.
grub-install: info: adding a relocation entry for 0x2e16.
grub-install: info: adding a relocation entry for 0x2e25.
grub-install: info: adding a relocation entry for 0x2e32.
grub-install: info: adding a relocation entry for 0x2e45.
grub-install: info: adding a relocation entry for 0x2e52.
grub-install: info: adding a relocation entry for 0x2e63.
grub-install: info: adding a relocation entry for 0x2e76.
grub-install: info: adding a relocation entry for 0x2e88.
grub-install: info: adding a relocation entry for 0x2e9a.
grub-install: info: adding a relocation entry for 0x2ec0.
grub-install: info: adding a relocation entry for 0x2ee2.
grub-install: info: adding a relocation entry for 0x2f1c.
grub-install: info: adding a relocation entry for 0x2f46.
grub-install: info: adding a relocation entry for 0x2f7c.
grub-install: info: adding a relocation entry for 0x2f8c.
grub-install: info: adding a relocation entry for 0x2f96.
grub-install: info: adding a relocation entry for 0x2fa0.
grub-install: info: adding a relocation entry for 0x2faa.
grub-install: info: adding a relocation entry for 0x2fb7.
grub-install: info: adding a relocation entry for 0x2fd2.
grub-install: info: adding a relocation entry for 0x2fe5.
grub-install: info: adding a relocation entry for 0x2ff6.
grub-install: info: adding a relocation entry for 0x3007.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 256 bytes of a fixup block starting at 0x2000.
grub-install: info: adding a relocation entry for 0x3014.
grub-install: info: adding a relocation entry for 0x3023.
grub-install: info: adding a relocation entry for 0x302e.
grub-install: info: adding a relocation entry for 0x303d.
grub-install: info: adding a relocation entry for 0x3047.
grub-install: info: adding a relocation entry for 0x3051.
grub-install: info: adding a relocation entry for 0x305e.
grub-install: info: adding a relocation entry for 0x306f.
grub-install: info: adding a relocation entry for 0x3079.
grub-install: info: adding a relocation entry for 0x3088.
grub-install: info: adding a relocation entry for 0x3097.
grub-install: info: adding a relocation entry for 0x30ac.
grub-install: info: adding a relocation entry for 0x30b9.
grub-install: info: adding a relocation entry for 0x30c6.
grub-install: info: adding a relocation entry for 0x30e4.
grub-install: info: adding a relocation entry for 0x30ee.
grub-install: info: adding a relocation entry for 0x30ff.
grub-install: info: adding a relocation entry for 0x3110.
grub-install: info: adding a relocation entry for 0x311c.
grub-install: info: adding a relocation entry for 0x3134.
grub-install: info: adding a relocation entry for 0x3140.
grub-install: info: adding a relocation entry for 0x3153.
grub-install: info: adding a relocation entry for 0x3163.
grub-install: info: adding a relocation entry for 0x3170.
grub-install: info: adding a relocation entry for 0x3181.
grub-install: info: adding a relocation entry for 0x3193.
grub-install: info: adding a relocation entry for 0x31a5.
grub-install: info: adding a relocation entry for 0x31c1.
grub-install: info: adding a relocation entry for 0x31cb.
grub-install: info: adding a relocation entry for 0x31f9.
grub-install: info: adding a relocation entry for 0x3212.
grub-install: info: adding a relocation entry for 0x323c.
grub-install: info: adding a relocation entry for 0x3254.
grub-install: info: adding a relocation entry for 0x32a5.
grub-install: info: adding a relocation entry for 0x32b1.
grub-install: info: adding a relocation entry for 0x3317.
grub-install: info: adding a relocation entry for 0x3452.
grub-install: info: adding a relocation entry for 0x346e.
grub-install: info: adding a relocation entry for 0x3478.
grub-install: info: adding a relocation entry for 0x348a.
grub-install: info: adding a relocation entry for 0x34aa.
grub-install: info: adding a relocation entry for 0x34c2.
grub-install: info: adding a relocation entry for 0x34dd.
grub-install: info: adding a relocation entry for 0x34f8.
grub-install: info: adding a relocation entry for 0x363a.
grub-install: info: adding a relocation entry for 0x3652.
grub-install: info: adding a relocation entry for 0x3669.
grub-install: info: adding a relocation entry for 0x3678.
grub-install: info: adding a relocation entry for 0x3698.
grub-install: info: adding a relocation entry for 0x36a9.
grub-install: info: adding a relocation entry for 0x36b7.
grub-install: info: adding a relocation entry for 0x36ed.
grub-install: info: adding a relocation entry for 0x3711.
grub-install: info: adding a relocation entry for 0x3723.
grub-install: info: adding a relocation entry for 0x3743.
grub-install: info: adding a relocation entry for 0x3752.
grub-install: info: adding a relocation entry for 0x376a.
grub-install: info: adding a relocation entry for 0x377a.
grub-install: info: adding a relocation entry for 0x3788.
grub-install: info: adding a relocation entry for 0x379c.
grub-install: info: adding a relocation entry for 0x37b0.
grub-install: info: adding a relocation entry for 0x37c5.
grub-install: info: adding a relocation entry for 0x37d6.
grub-install: info: adding a relocation entry for 0x37ff.
grub-install: info: adding a relocation entry for 0x380a.
grub-install: info: adding a relocation entry for 0x381e.
grub-install: info: adding a relocation entry for 0x382c.
grub-install: info: adding a relocation entry for 0x3841.
grub-install: info: adding a relocation entry for 0x3854.
grub-install: info: adding a relocation entry for 0x38af.
grub-install: info: adding a relocation entry for 0x38c4.
grub-install: info: adding a relocation entry for 0x38d5.
grub-install: info: adding a relocation entry for 0x38e2.
grub-install: info: adding a relocation entry for 0x3909.
grub-install: info: adding a relocation entry for 0x392f.
grub-install: info: adding a relocation entry for 0x3940.
grub-install: info: adding a relocation entry for 0x394f.
grub-install: info: adding a relocation entry for 0x395b.
grub-install: info: adding a relocation entry for 0x396b.
grub-install: info: adding a relocation entry for 0x3975.
grub-install: info: adding a relocation entry for 0x3981.
grub-install: info: adding a relocation entry for 0x3990.
grub-install: info: adding a relocation entry for 0x399a.
grub-install: info: adding a relocation entry for 0x39a4.
grub-install: info: adding a relocation entry for 0x39b2.
grub-install: info: adding a relocation entry for 0x39c2.
grub-install: info: adding a relocation entry for 0x39d2.
grub-install: info: adding a relocation entry for 0x39dc.
grub-install: info: adding a relocation entry for 0x39e8.
grub-install: info: adding a relocation entry for 0x39f7.
grub-install: info: adding a relocation entry for 0x3a01.
grub-install: info: adding a relocation entry for 0x3a0c.
grub-install: info: adding a relocation entry for 0x3a18.
grub-install: info: adding a relocation entry for 0x3a2b.
grub-install: info: adding a relocation entry for 0x3a35.
grub-install: info: adding a relocation entry for 0x3a41.
grub-install: info: adding a relocation entry for 0x3a4d.
grub-install: info: adding a relocation entry for 0x3a5c.
grub-install: info: adding a relocation entry for 0x3a79.
grub-install: info: adding a relocation entry for 0x3a86.
grub-install: info: adding a relocation entry for 0x3aea.
grub-install: info: adding a relocation entry for 0x3b30.
grub-install: info: adding a relocation entry for 0x3b49.
grub-install: info: adding a relocation entry for 0x3b53.
grub-install: info: adding a relocation entry for 0x3b5d.
grub-install: info: adding a relocation entry for 0x3b69.
grub-install: info: adding a relocation entry for 0x3b75.
grub-install: info: adding a relocation entry for 0x3b8b.
grub-install: info: adding a relocation entry for 0x3b9a.
grub-install: info: adding a relocation entry for 0x3bc9.
grub-install: info: adding a relocation entry for 0x3bd5.
grub-install: info: adding a relocation entry for 0x3bea.
grub-install: info: adding a relocation entry for 0x3bf6.
grub-install: info: adding a relocation entry for 0x3c05.
grub-install: info: adding a relocation entry for 0x3c2b.
grub-install: info: adding a relocation entry for 0x3c70.
grub-install: info: adding a relocation entry for 0x3cb9.
grub-install: info: adding a relocation entry for 0x3cc5.
grub-install: info: adding a relocation entry for 0x3cde.
grub-install: info: adding a relocation entry for 0x3cea.
grub-install: info: adding a relocation entry for 0x3de9.
grub-install: info: adding a relocation entry for 0x3e00.
grub-install: info: adding a relocation entry for 0x3e11.
grub-install: info: adding a relocation entry for 0x3e2a.
grub-install: info: adding a relocation entry for 0x3e3f.
grub-install: info: adding a relocation entry for 0x3e5f.
grub-install: info: adding a relocation entry for 0x3e7f.
grub-install: info: adding a relocation entry for 0x3ece.
grub-install: info: adding a relocation entry for 0x3eda.
grub-install: info: adding a relocation entry for 0x3fb4.
grub-install: info: adding a relocation entry for 0x3fc1.
grub-install: info: adding a relocation entry for 0x4022.
grub-install: info: writing 272 bytes of a fixup block starting at 0x3000.
grub-install: info: adding a relocation entry for 0x408b.
grub-install: info: adding a relocation entry for 0x40d7.
grub-install: info: adding a relocation entry for 0x40f0.
grub-install: info: adding a relocation entry for 0x4105.
grub-install: info: adding a relocation entry for 0x4130.
grub-install: info: adding a relocation entry for 0x4152.
grub-install: info: adding a relocation entry for 0x4165.
grub-install: info: adding a relocation entry for 0x417d.
grub-install: info: adding a relocation entry for 0x418c.
grub-install: info: adding a relocation entry for 0x419d.
grub-install: info: adding a relocation entry for 0x41c2.
grub-install: info: adding a relocation entry for 0x420a.
grub-install: info: adding a relocation entry for 0x4223.
grub-install: info: adding a relocation entry for 0x423e.
grub-install: info: adding a relocation entry for 0x42cd.
grub-install: info: adding a relocation entry for 0x42dc.
grub-install: info: adding a relocation entry for 0x42ed.
grub-install: info: adding a relocation entry for 0x42f7.
grub-install: info: adding a relocation entry for 0x4304.
grub-install: info: adding a relocation entry for 0x430e.
grub-install: info: adding a relocation entry for 0x4328.
grub-install: info: adding a relocation entry for 0x4332.
grub-install: info: adding a relocation entry for 0x4351.
grub-install: info: adding a relocation entry for 0x435b.
grub-install: info: adding a relocation entry for 0x4367.
grub-install: info: adding a relocation entry for 0x4371.
grub-install: info: adding a relocation entry for 0x437d.
grub-install: info: adding a relocation entry for 0x4394.
grub-install: info: adding a relocation entry for 0x43a3.
grub-install: info: adding a relocation entry for 0x43b9.
grub-install: info: adding a relocation entry for 0x43d4.
grub-install: info: adding a relocation entry for 0x43ec.
grub-install: info: adding a relocation entry for 0x440f.
grub-install: info: adding a relocation entry for 0x4420.
grub-install: info: adding a relocation entry for 0x4431.
grub-install: info: adding a relocation entry for 0x4441.
grub-install: info: adding a relocation entry for 0x4457.
grub-install: info: adding a relocation entry for 0x4464.
grub-install: info: adding a relocation entry for 0x4470.
grub-install: info: adding a relocation entry for 0x4485.
grub-install: info: adding a relocation entry for 0x4497.
grub-install: info: adding a relocation entry for 0x44a1.
grub-install: info: adding a relocation entry for 0x44ad.
grub-install: info: adding a relocation entry for 0x44be.
grub-install: info: adding a relocation entry for 0x44c9.
grub-install: info: adding a relocation entry for 0x44d8.
grub-install: info: adding a relocation entry for 0x44f2.
grub-install: info: adding a relocation entry for 0x4503.
grub-install: info: adding a relocation entry for 0x4521.
grub-install: info: adding a relocation entry for 0x452d.
grub-install: info: adding a relocation entry for 0x4541.
grub-install: info: adding a relocation entry for 0x4555.
grub-install: info: adding a relocation entry for 0x4566.
grub-install: info: adding a relocation entry for 0x4573.
grub-install: info: adding a relocation entry for 0x458d.
grub-install: info: adding a relocation entry for 0x4597.
grub-install: info: adding a relocation entry for 0x45b3.
grub-install: info: adding a relocation entry for 0x45bf.
grub-install: info: adding a relocation entry for 0x45de.
grub-install: info: adding a relocation entry for 0x45f8.
grub-install: info: adding a relocation entry for 0x4609.
grub-install: info: adding a relocation entry for 0x461f.
grub-install: info: adding a relocation entry for 0x4638.
grub-install: info: adding a relocation entry for 0x4642.
grub-install: info: adding a relocation entry for 0x464c.
grub-install: info: adding a relocation entry for 0x4656.
grub-install: info: adding a relocation entry for 0x4660.
grub-install: info: adding a relocation entry for 0x4678.
grub-install: info: adding a relocation entry for 0x4685.
grub-install: info: adding a relocation entry for 0x468f.
grub-install: info: adding a relocation entry for 0x4699.
grub-install: info: adding a relocation entry for 0x46a3.
grub-install: info: adding a relocation entry for 0x46b2.
grub-install: info: adding a relocation entry for 0x46bc.
grub-install: info: adding a relocation entry for 0x46c6.
grub-install: info: adding a relocation entry for 0x46d0.
grub-install: info: adding a relocation entry for 0x46e2.
grub-install: info: adding a relocation entry for 0x46ed.
grub-install: info: adding a relocation entry for 0x46f7.
grub-install: info: adding a relocation entry for 0x4701.
grub-install: info: adding a relocation entry for 0x4713.
grub-install: info: adding a relocation entry for 0x473a.
grub-install: info: adding a relocation entry for 0x4751.
grub-install: info: adding a relocation entry for 0x4766.
grub-install: info: adding a relocation entry for 0x4772.
grub-install: info: adding a relocation entry for 0x4785.
grub-install: info: adding a relocation entry for 0x47c8.
grub-install: info: adding a relocation entry for 0x47d2.
grub-install: info: adding a relocation entry for 0x47eb.
grub-install: info: adding a relocation entry for 0x47f5.
grub-install: info: adding a relocation entry for 0x4806.
grub-install: info: adding a relocation entry for 0x481b.
grub-install: info: adding a relocation entry for 0x483a.
grub-install: info: adding a relocation entry for 0x484e.
grub-install: info: adding a relocation entry for 0x4860.
grub-install: info: adding a relocation entry for 0x4888.
grub-install: info: adding a relocation entry for 0x48a9.
grub-install: info: adding a relocation entry for 0x48c1.
grub-install: info: adding a relocation entry for 0x48d6.
grub-install: info: adding a relocation entry for 0x48e1.
grub-install: info: adding a relocation entry for 0x4914.
grub-install: info: adding a relocation entry for 0x492c.
grub-install: info: adding a relocation entry for 0x4946.
grub-install: info: adding a relocation entry for 0x4958.
grub-install: info: adding a relocation entry for 0x4965.
grub-install: info: adding a relocation entry for 0x4974.
grub-install: info: adding a relocation entry for 0x4985.
grub-install: info: adding a relocation entry for 0x49c4.
grub-install: info: adding a relocation entry for 0x49f7.
grub-install: info: adding a relocation entry for 0x4a1c.
grub-install: info: adding a relocation entry for 0x4a75.
grub-install: info: adding a relocation entry for 0x4ad3.
grub-install: info: adding a relocation entry for 0x4b04.
grub-install: info: adding a relocation entry for 0x4b44.
grub-install: info: adding a relocation entry for 0x4b76.
grub-install: info: adding a relocation entry for 0x4b8a.
grub-install: info: adding a relocation entry for 0x4ba1.
grub-install: info: adding a relocation entry for 0x4bf0.
grub-install: info: adding a relocation entry for 0x4c0d.
grub-install: info: adding a relocation entry for 0x4c27.
grub-install: info: adding a relocation entry for 0x4c3d.
grub-install: info: adding a relocation entry for 0x4ca9.
grub-install: info: adding a relocation entry for 0x4cc6.
grub-install: info: adding a relocation entry for 0x4cd5.
grub-install: info: adding a relocation entry for 0x4ce9.
grub-install: info: adding a relocation entry for 0x4d03.
grub-install: info: adding a relocation entry for 0x4d51.
grub-install: info: adding a relocation entry for 0x4d9d.
grub-install: info: adding a relocation entry for 0x4da9.
grub-install: info: adding a relocation entry for 0x4db6.
grub-install: info: adding a relocation entry for 0x4dc0.
grub-install: info: adding a relocation entry for 0x4dd1.
grub-install: info: adding a relocation entry for 0x4dde.
grub-install: info: adding a relocation entry for 0x4def.
grub-install: info: adding a relocation entry for 0x4e08.
grub-install: info: adding a relocation entry for 0x4e5a.
grub-install: info: adding a relocation entry for 0x4e65.
grub-install: info: adding a relocation entry for 0x4e70.
grub-install: info: adding a relocation entry for 0x4ea2.
grub-install: info: adding a relocation entry for 0x4eb7.
grub-install: info: adding a relocation entry for 0x4ec1.
grub-install: info: adding a relocation entry for 0x4eec.
grub-install: info: adding a relocation entry for 0x4ef6.
grub-install: info: adding a relocation entry for 0x4f05.
grub-install: info: adding a relocation entry for 0x4f17.
grub-install: info: adding a relocation entry for 0x4f3b.
grub-install: info: adding a relocation entry for 0x4f45.
grub-install: info: adding a relocation entry for 0x4f51.
grub-install: info: adding a relocation entry for 0x4f6c.
grub-install: info: adding a relocation entry for 0x4f93.
grub-install: info: adding a relocation entry for 0x4f9d.
grub-install: info: adding a relocation entry for 0x4fae.
grub-install: info: adding a relocation entry for 0x4fbf.
grub-install: info: adding a relocation entry for 0x4fd7.
grub-install: info: adding a relocation entry for 0x502d.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 320 bytes of a fixup block starting at 0x4000.
grub-install: info: adding a relocation entry for 0x5055.
grub-install: info: adding a relocation entry for 0x506a.
grub-install: info: adding a relocation entry for 0x507e.
grub-install: info: adding a relocation entry for 0x509d.
grub-install: info: adding a relocation entry for 0x50a7.
grub-install: info: adding a relocation entry for 0x50d7.
grub-install: info: adding a relocation entry for 0x50f0.
grub-install: info: adding a relocation entry for 0x5103.
grub-install: info: adding a relocation entry for 0x5124.
grub-install: info: adding a relocation entry for 0x5139.
grub-install: info: adding a relocation entry for 0x5148.
grub-install: info: adding a relocation entry for 0x5156.
grub-install: info: adding a relocation entry for 0x5162.
grub-install: info: adding a relocation entry for 0x5180.
grub-install: info: adding a relocation entry for 0x5191.
grub-install: info: adding a relocation entry for 0x51a8.
grub-install: info: adding a relocation entry for 0x51b4.
grub-install: info: adding a relocation entry for 0x51c7.
grub-install: info: adding a relocation entry for 0x51d6.
grub-install: info: adding a relocation entry for 0x51e0.
grub-install: info: adding a relocation entry for 0x51ef.
grub-install: info: adding a relocation entry for 0x51f9.
grub-install: info: adding a relocation entry for 0x5208.
grub-install: info: adding a relocation entry for 0x5217.
grub-install: info: adding a relocation entry for 0x522a.
grub-install: info: adding a relocation entry for 0x523b.
grub-install: info: adding a relocation entry for 0x52bc.
grub-install: info: adding a relocation entry for 0x52cd.
grub-install: info: adding a relocation entry for 0x531b.
grub-install: info: adding a relocation entry for 0x532c.
grub-install: info: adding a relocation entry for 0x533c.
grub-install: info: adding a relocation entry for 0x534a.
grub-install: info: adding a relocation entry for 0x5357.
grub-install: info: adding a relocation entry for 0x5361.
grub-install: info: adding a relocation entry for 0x5370.
grub-install: info: adding a relocation entry for 0x537a.
grub-install: info: adding a relocation entry for 0x5387.
grub-install: info: adding a relocation entry for 0x53c8.
grub-install: info: adding a relocation entry for 0x5408.
grub-install: info: adding a relocation entry for 0x545d.
grub-install: info: adding a relocation entry for 0x547c.
grub-install: info: adding a relocation entry for 0x54c4.
grub-install: info: adding a relocation entry for 0x5589.
grub-install: info: adding a relocation entry for 0x55a3.
grub-install: info: adding a relocation entry for 0x55ec.
grub-install: info: adding a relocation entry for 0x55f6.
grub-install: info: adding a relocation entry for 0x562a.
grub-install: info: adding a relocation entry for 0x5699.
grub-install: info: adding a relocation entry for 0x56b3.
grub-install: info: adding a relocation entry for 0x56c5.
grub-install: info: adding a relocation entry for 0x56d7.
grub-install: info: adding a relocation entry for 0x570c.
grub-install: info: adding a relocation entry for 0x5724.
grub-install: info: adding a relocation entry for 0x572f.
grub-install: info: adding a relocation entry for 0x5772.
grub-install: info: adding a relocation entry for 0x57a4.
grub-install: info: adding a relocation entry for 0x57e1.
grub-install: info: adding a relocation entry for 0x5836.
grub-install: info: adding a relocation entry for 0x5840.
grub-install: info: adding a relocation entry for 0x586a.
grub-install: info: adding a relocation entry for 0x587b.
grub-install: info: adding a relocation entry for 0x58cc.
grub-install: info: adding a relocation entry for 0x58e6.
grub-install: info: adding a relocation entry for 0x58fa.
grub-install: info: adding a relocation entry for 0x5932.
grub-install: info: adding a relocation entry for 0x593c.
grub-install: info: adding a relocation entry for 0x5948.
grub-install: info: adding a relocation entry for 0x5963.
grub-install: info: adding a relocation entry for 0x5978.
grub-install: info: adding a relocation entry for 0x59a6.
grub-install: info: adding a relocation entry for 0x59b7.
grub-install: info: adding a relocation entry for 0x59c8.
grub-install: info: adding a relocation entry for 0x59e1.
grub-install: info: adding a relocation entry for 0x5a08.
grub-install: info: adding a relocation entry for 0x5a19.
grub-install: info: adding a relocation entry for 0x5a2f.
grub-install: info: adding a relocation entry for 0x5a51.
grub-install: info: adding a relocation entry for 0x5a5d.
grub-install: info: adding a relocation entry for 0x5a6c.
grub-install: info: adding a relocation entry for 0x5a76.
grub-install: info: adding a relocation entry for 0x5a83.
grub-install: info: adding a relocation entry for 0x5a90.
grub-install: info: adding a relocation entry for 0x5aa6.
grub-install: info: adding a relocation entry for 0x5ab5.
grub-install: info: adding a relocation entry for 0x5ad1.
grub-install: info: adding a relocation entry for 0x5adb.
grub-install: info: adding a relocation entry for 0x5af4.
grub-install: info: adding a relocation entry for 0x5b0d.
grub-install: info: adding a relocation entry for 0x5b1e.
grub-install: info: adding a relocation entry for 0x5b2b.
grub-install: info: adding a relocation entry for 0x5b3c.
grub-install: info: adding a relocation entry for 0x5b4b.
grub-install: info: adding a relocation entry for 0x5b60.
grub-install: info: adding a relocation entry for 0x5b75.
grub-install: info: adding a relocation entry for 0x5b82.
grub-install: info: adding a relocation entry for 0x5b9b.
grub-install: info: adding a relocation entry for 0x5bba.
grub-install: info: adding a relocation entry for 0x5be1.
grub-install: info: adding a relocation entry for 0x5bf2.
grub-install: info: adding a relocation entry for 0x5c02.
grub-install: info: adding a relocation entry for 0x5c20.
grub-install: info: adding a relocation entry for 0x5c8d.
grub-install: info: adding a relocation entry for 0x5cd0.
grub-install: info: adding a relocation entry for 0x5ce3.
grub-install: info: adding a relocation entry for 0x5d2d.
grub-install: info: adding a relocation entry for 0x5d40.
grub-install: info: adding a relocation entry for 0x5dc4.
grub-install: info: adding a relocation entry for 0x5dd5.
grub-install: info: adding a relocation entry for 0x5e4b.
grub-install: info: adding a relocation entry for 0x5e8f.
grub-install: info: adding a relocation entry for 0x5ea2.
grub-install: info: adding a relocation entry for 0x5f37.
grub-install: info: adding a relocation entry for 0x5f85.
grub-install: info: adding a relocation entry for 0x5f94.
grub-install: info: adding a relocation entry for 0x5fa3.
grub-install: info: adding a relocation entry for 0x5fad.
grub-install: info: adding a relocation entry for 0x5fd4.
grub-install: info: adding a relocation entry for 0x6022.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 248 bytes of a fixup block starting at 0x5000.
grub-install: info: adding a relocation entry for 0x6033.
grub-install: info: adding a relocation entry for 0x605f.
grub-install: info: adding a relocation entry for 0x60bc.
grub-install: info: adding a relocation entry for 0x60e7.
grub-install: info: adding a relocation entry for 0x60f5.
grub-install: info: adding a relocation entry for 0x60ff.
grub-install: info: adding a relocation entry for 0x610e.
grub-install: info: adding a relocation entry for 0x6120.
grub-install: info: adding a relocation entry for 0x612a.
grub-install: info: adding a relocation entry for 0x6139.
grub-install: info: adding a relocation entry for 0x614b.
grub-install: info: adding a relocation entry for 0x6155.
grub-install: info: adding a relocation entry for 0x6164.
grub-install: info: adding a relocation entry for 0x6173.
grub-install: info: adding a relocation entry for 0x618b.
grub-install: info: adding a relocation entry for 0x619c.
grub-install: info: adding a relocation entry for 0x61da.
grub-install: info: adding a relocation entry for 0x6203.
grub-install: info: adding a relocation entry for 0x621e.
grub-install: info: adding a relocation entry for 0x6241.
grub-install: info: adding a relocation entry for 0x6252.
grub-install: info: adding a relocation entry for 0x6260.
grub-install: info: adding a relocation entry for 0x627a.
grub-install: info: adding a relocation entry for 0x6294.
grub-install: info: adding a relocation entry for 0x62ab.
grub-install: info: adding a relocation entry for 0x62c0.
grub-install: info: adding a relocation entry for 0x62d1.
grub-install: info: adding a relocation entry for 0x62e9.
grub-install: info: adding a relocation entry for 0x62fd.
grub-install: info: adding a relocation entry for 0x6321.
grub-install: info: adding a relocation entry for 0x6330.
grub-install: info: adding a relocation entry for 0x6345.
grub-install: info: adding a relocation entry for 0x6362.
grub-install: info: adding a relocation entry for 0x636c.
grub-install: info: adding a relocation entry for 0x637d.
grub-install: info: adding a relocation entry for 0x6396.
grub-install: info: adding a relocation entry for 0x63a0.
grub-install: info: adding a relocation entry for 0x63b7.
grub-install: info: adding a relocation entry for 0x63c9.
grub-install: info: adding a relocation entry for 0x63e1.
grub-install: info: adding a relocation entry for 0x63f4.
grub-install: info: adding a relocation entry for 0x6405.
grub-install: info: adding a relocation entry for 0x641d.
grub-install: info: adding a relocation entry for 0x6427.
grub-install: info: adding a relocation entry for 0x6441.
grub-install: info: adding a relocation entry for 0x6481.
grub-install: info: adding a relocation entry for 0x648d.
grub-install: info: adding a relocation entry for 0x64c0.
grub-install: info: adding a relocation entry for 0x64f6.
grub-install: info: adding a relocation entry for 0x6519.
grub-install: info: adding a relocation entry for 0x652f.
grub-install: info: adding a relocation entry for 0x654b.
grub-install: info: adding a relocation entry for 0x656f.
grub-install: info: adding a relocation entry for 0x65c7.
grub-install: info: adding a relocation entry for 0x65dd.
grub-install: info: adding a relocation entry for 0x65ec.
grub-install: info: adding a relocation entry for 0x661e.
grub-install: info: adding a relocation entry for 0x6647.
grub-install: info: adding a relocation entry for 0x6651.
grub-install: info: adding a relocation entry for 0x667a.
grub-install: info: adding a relocation entry for 0x66a0.
grub-install: info: adding a relocation entry for 0x66bd.
grub-install: info: adding a relocation entry for 0x6735.
grub-install: info: adding a relocation entry for 0x674b.
grub-install: info: adding a relocation entry for 0x6758.
grub-install: info: adding a relocation entry for 0x6767.
grub-install: info: adding a relocation entry for 0x678b.
grub-install: info: adding a relocation entry for 0x67a1.
grub-install: info: adding a relocation entry for 0x67ae.
grub-install: info: adding a relocation entry for 0x67db.
grub-install: info: adding a relocation entry for 0x6815.
grub-install: info: adding a relocation entry for 0x682e.
grub-install: info: adding a relocation entry for 0x6838.
grub-install: info: adding a relocation entry for 0x684b.
grub-install: info: adding a relocation entry for 0x685c.
grub-install: info: adding a relocation entry for 0x6873.
grub-install: info: adding a relocation entry for 0x687f.
grub-install: info: adding a relocation entry for 0x688f.
grub-install: info: adding a relocation entry for 0x689a.
grub-install: info: adding a relocation entry for 0x68a5.
grub-install: info: adding a relocation entry for 0x68b5.
grub-install: info: adding a relocation entry for 0x68c0.
grub-install: info: adding a relocation entry for 0x68cc.
grub-install: info: adding a relocation entry for 0x68d7.
grub-install: info: adding a relocation entry for 0x68e8.
grub-install: info: adding a relocation entry for 0x68f1.
grub-install: info: adding a relocation entry for 0x6909.
grub-install: info: adding a relocation entry for 0x691b.
grub-install: info: adding a relocation entry for 0x6925.
grub-install: info: adding a relocation entry for 0x6939.
grub-install: info: adding a relocation entry for 0x6947.
grub-install: info: adding a relocation entry for 0x6956.
grub-install: info: adding a relocation entry for 0x6960.
grub-install: info: adding a relocation entry for 0x696c.
grub-install: info: adding a relocation entry for 0x6979.
grub-install: info: adding a relocation entry for 0x6986.
grub-install: info: adding a relocation entry for 0x6991.
grub-install: info: adding a relocation entry for 0x699b.
grub-install: info: adding a relocation entry for 0x69ab.
grub-install: info: adding a relocation entry for 0x69ba.
grub-install: info: adding a relocation entry for 0x69c6.
grub-install: info: adding a relocation entry for 0x69d3.
grub-install: info: adding a relocation entry for 0x69f2.
grub-install: info: adding a relocation entry for 0x6a08.
grub-install: info: adding a relocation entry for 0x6a17.
grub-install: info: adding a relocation entry for 0x6a2a.
grub-install: info: adding a relocation entry for 0x6a50.
grub-install: info: adding a relocation entry for 0x6a7e.
grub-install: info: adding a relocation entry for 0x6a8f.
grub-install: info: adding a relocation entry for 0x6ad1.
grub-install: info: adding a relocation entry for 0x6b25.
grub-install: info: adding a relocation entry for 0x6b34.
grub-install: info: adding a relocation entry for 0x6b44.
grub-install: info: adding a relocation entry for 0x6b54.
grub-install: info: adding a relocation entry for 0x6b6b.
grub-install: info: adding a relocation entry for 0x6b91.
grub-install: info: adding a relocation entry for 0x6ba9.
grub-install: info: adding a relocation entry for 0x6bbb.
grub-install: info: adding a relocation entry for 0x6bd5.
grub-install: info: adding a relocation entry for 0x6bff.
grub-install: info: adding a relocation entry for 0x6c12.
grub-install: info: adding a relocation entry for 0x6c43.
grub-install: info: adding a relocation entry for 0x6c58.
grub-install: info: adding a relocation entry for 0x6c62.
grub-install: info: adding a relocation entry for 0x6c99.
grub-install: info: adding a relocation entry for 0x6caa.
grub-install: info: adding a relocation entry for 0x6cb4.
grub-install: info: adding a relocation entry for 0x6cbe.
grub-install: info: adding a relocation entry for 0x6ccf.
grub-install: info: adding a relocation entry for 0x6ce2.
grub-install: info: adding a relocation entry for 0x6cec.
grub-install: info: adding a relocation entry for 0x6cf6.
grub-install: info: adding a relocation entry for 0x6d07.
grub-install: info: adding a relocation entry for 0x6d2a.
grub-install: info: adding a relocation entry for 0x6d3c.
grub-install: info: adding a relocation entry for 0x6d64.
grub-install: info: adding a relocation entry for 0x6e5c.
grub-install: info: adding a relocation entry for 0x6eba.
grub-install: info: adding a relocation entry for 0x6eff.
grub-install: info: adding a relocation entry for 0x6f0e.
grub-install: info: adding a relocation entry for 0x6f20.
grub-install: info: adding a relocation entry for 0x6f31.
grub-install: info: adding a relocation entry for 0x6f58.
grub-install: info: adding a relocation entry for 0x6f6c.
grub-install: info: adding a relocation entry for 0x6f9a.
grub-install: info: adding a relocation entry for 0x6fca.
grub-install: info: adding a relocation entry for 0x6fdb.
grub-install: info: adding a relocation entry for 0x700a.
grub-install: info: writing 304 bytes of a fixup block starting at 0x6000.
grub-install: info: adding a relocation entry for 0x7018.
grub-install: info: adding a relocation entry for 0x7046.
grub-install: info: adding a relocation entry for 0x7050.
grub-install: info: adding a relocation entry for 0x7068.
grub-install: info: adding a relocation entry for 0x7072.
grub-install: info: adding a relocation entry for 0x7081.
grub-install: info: adding a relocation entry for 0x7090.
grub-install: info: adding a relocation entry for 0x709a.
grub-install: info: adding a relocation entry for 0x70aa.
grub-install: info: adding a relocation entry for 0x70bd.
grub-install: info: adding a relocation entry for 0x70cf.
grub-install: info: adding a relocation entry for 0x70d9.
grub-install: info: adding a relocation entry for 0x70e8.
grub-install: info: adding a relocation entry for 0x70f5.
grub-install: info: adding a relocation entry for 0x7100.
grub-install: info: adding a relocation entry for 0x711a.
grub-install: info: adding a relocation entry for 0x712d.
grub-install: info: adding a relocation entry for 0x7141.
grub-install: info: adding a relocation entry for 0x7158.
grub-install: info: adding a relocation entry for 0x7164.
grub-install: info: adding a relocation entry for 0x7173.
grub-install: info: adding a relocation entry for 0x717d.
grub-install: info: adding a relocation entry for 0x718e.
grub-install: info: adding a relocation entry for 0x719b.
grub-install: info: adding a relocation entry for 0x71a9.
grub-install: info: adding a relocation entry for 0x71bf.
grub-install: info: adding a relocation entry for 0x71ca.
grub-install: info: adding a relocation entry for 0x71d7.
grub-install: info: adding a relocation entry for 0x71e1.
grub-install: info: adding a relocation entry for 0x71f4.
grub-install: info: adding a relocation entry for 0x71ff.
grub-install: info: adding a relocation entry for 0x721d.
grub-install: info: adding a relocation entry for 0x722e.
grub-install: info: adding a relocation entry for 0x7246.
grub-install: info: adding a relocation entry for 0x72c8.
grub-install: info: adding a relocation entry for 0x72e8.
grub-install: info: adding a relocation entry for 0x72f8.
grub-install: info: adding a relocation entry for 0x7305.
grub-install: info: adding a relocation entry for 0x7323.
grub-install: info: adding a relocation entry for 0x7337.
grub-install: info: adding a relocation entry for 0x735e.
grub-install: info: adding a relocation entry for 0x739f.
grub-install: info: adding a relocation entry for 0x73b2.
grub-install: info: adding a relocation entry for 0x73be.
grub-install: info: adding a relocation entry for 0x73d6.
grub-install: info: adding a relocation entry for 0x73e9.
grub-install: info: adding a relocation entry for 0x7412.
grub-install: info: adding a relocation entry for 0x7420.
grub-install: info: adding a relocation entry for 0x7457.
grub-install: info: adding a relocation entry for 0x7461.
grub-install: info: adding a relocation entry for 0x746b.
grub-install: info: adding a relocation entry for 0x7477.
grub-install: info: adding a relocation entry for 0x7486.
grub-install: info: adding a relocation entry for 0x74a3.
grub-install: info: adding a relocation entry for 0x74b2.
grub-install: info: adding a relocation entry for 0x74c9.
grub-install: info: adding a relocation entry for 0x7522.
grub-install: info: adding a relocation entry for 0x752c.
grub-install: info: adding a relocation entry for 0x7536.
grub-install: info: adding a relocation entry for 0x754a.
grub-install: info: adding a relocation entry for 0x7577.
grub-install: info: adding a relocation entry for 0x7581.
grub-install: info: adding a relocation entry for 0x758b.
grub-install: info: adding a relocation entry for 0x75ab.
grub-install: info: adding a relocation entry for 0x75b5.
grub-install: info: adding a relocation entry for 0x75c1.
grub-install: info: adding a relocation entry for 0x75cb.
grub-install: info: adding a relocation entry for 0x75da.
grub-install: info: adding a relocation entry for 0x75fd.
grub-install: info: adding a relocation entry for 0x761c.
grub-install: info: adding a relocation entry for 0x7644.
grub-install: info: adding a relocation entry for 0x76aa.
grub-install: info: adding a relocation entry for 0x76c2.
grub-install: info: adding a relocation entry for 0x76dd.
grub-install: info: adding a relocation entry for 0x7717.
grub-install: info: adding a relocation entry for 0x7721.
grub-install: info: adding a relocation entry for 0x7742.
grub-install: info: adding a relocation entry for 0x7756.
grub-install: info: adding a relocation entry for 0x7767.
grub-install: info: adding a relocation entry for 0x7773.
grub-install: info: adding a relocation entry for 0x778a.
grub-install: info: adding a relocation entry for 0x7794.
grub-install: info: adding a relocation entry for 0x77a3.
grub-install: info: adding a relocation entry for 0x77b2.
grub-install: info: adding a relocation entry for 0x77bc.
grub-install: info: adding a relocation entry for 0x77cb.
grub-install: info: adding a relocation entry for 0x77dc.
grub-install: info: adding a relocation entry for 0x77e6.
grub-install: info: adding a relocation entry for 0x77f2.
grub-install: info: adding a relocation entry for 0x77fe.
grub-install: info: adding a relocation entry for 0x780a.
grub-install: info: adding a relocation entry for 0x781c.
grub-install: info: adding a relocation entry for 0x7826.
grub-install: info: adding a relocation entry for 0x7832.
grub-install: info: adding a relocation entry for 0x7844.
grub-install: info: adding a relocation entry for 0x7850.
grub-install: info: adding a relocation entry for 0x785a.
grub-install: info: adding a relocation entry for 0x7866.
grub-install: info: adding a relocation entry for 0x7874.
grub-install: info: adding a relocation entry for 0x787e.
grub-install: info: adding a relocation entry for 0x7887.
grub-install: info: adding a relocation entry for 0x7894.
grub-install: info: adding a relocation entry for 0x78af.
grub-install: info: adding a relocation entry for 0x78d9.
grub-install: info: adding a relocation entry for 0x78ef.
grub-install: info: adding a relocation entry for 0x7907.
grub-install: info: adding a relocation entry for 0x7913.
grub-install: info: adding a relocation entry for 0x7925.
grub-install: info: adding a relocation entry for 0x793c.
grub-install: info: adding a relocation entry for 0x7948.
grub-install: info: adding a relocation entry for 0x796f.
grub-install: info: adding a relocation entry for 0x79d6.
grub-install: info: adding a relocation entry for 0x79e4.
grub-install: info: adding a relocation entry for 0x7ad3.
grub-install: info: adding a relocation entry for 0x7b1a.
grub-install: info: adding a relocation entry for 0x7b8b.
grub-install: info: adding a relocation entry for 0x7c3a.
grub-install: info: adding a relocation entry for 0x7c58.
grub-install: info: adding a relocation entry for 0x7c79.
grub-install: info: adding a relocation entry for 0x7c95.
grub-install: info: adding a relocation entry for 0x7ca7.
grub-install: info: adding a relocation entry for 0x7cc7.
grub-install: info: adding a relocation entry for 0x7d46.
grub-install: info: adding a relocation entry for 0x7df2.
grub-install: info: adding a relocation entry for 0x7e03.
grub-install: info: adding a relocation entry for 0x7e14.
grub-install: info: adding a relocation entry for 0x7e45.
grub-install: info: adding a relocation entry for 0x7e56.
grub-install: info: adding a relocation entry for 0x7f84.
grub-install: info: adding a relocation entry for 0x7f9c.
grub-install: info: adding a relocation entry for 0x7fcc.
grub-install: info: adding a relocation entry for 0x7fd6.
grub-install: info: adding a relocation entry for 0x8120.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 280 bytes of a fixup block starting at 0x7000.
grub-install: info: adding a relocation entry for 0x81c7.
grub-install: info: adding a relocation entry for 0x826d.
grub-install: info: adding a relocation entry for 0x82b7.
grub-install: info: adding a relocation entry for 0x8410.
grub-install: info: adding a relocation entry for 0x844d.
grub-install: info: adding a relocation entry for 0x8590.
grub-install: info: adding a relocation entry for 0x866d.
grub-install: info: adding a relocation entry for 0x8677.
grub-install: info: adding a relocation entry for 0x8688.
grub-install: info: adding a relocation entry for 0x86a9.
grub-install: info: adding a relocation entry for 0x86c6.
grub-install: info: adding a relocation entry for 0x86dc.
grub-install: info: adding a relocation entry for 0x86e5.
grub-install: info: adding a relocation entry for 0x86f0.
grub-install: info: adding a relocation entry for 0x86f9.
grub-install: info: adding a relocation entry for 0x8702.
grub-install: info: adding a relocation entry for 0x870d.
grub-install: info: adding a relocation entry for 0x872e.
grub-install: info: adding a relocation entry for 0x873a.
grub-install: info: adding a relocation entry for 0x8749.
grub-install: info: adding a relocation entry for 0x875b.
grub-install: info: adding a relocation entry for 0x87b0.
grub-install: info: adding a relocation entry for 0x87c4.
grub-install: info: adding a relocation entry for 0x8813.
grub-install: info: adding a relocation entry for 0x8826.
grub-install: info: adding a relocation entry for 0x883d.
grub-install: info: adding a relocation entry for 0x886a.
grub-install: info: adding a relocation entry for 0x8877.
grub-install: info: adding a relocation entry for 0x8899.
grub-install: info: adding a relocation entry for 0x88a3.
grub-install: info: adding a relocation entry for 0x88d8.
grub-install: info: adding a relocation entry for 0x88e4.
grub-install: info: adding a relocation entry for 0x890b.
grub-install: info: adding a relocation entry for 0x893c.
grub-install: info: adding a relocation entry for 0x894d.
grub-install: info: adding a relocation entry for 0x89a3.
grub-install: info: adding a relocation entry for 0x89b9.
grub-install: info: adding a relocation entry for 0x89e1.
grub-install: info: adding a relocation entry for 0x8a03.
grub-install: info: adding a relocation entry for 0x8a1a.
grub-install: info: adding a relocation entry for 0x8a2b.
grub-install: info: adding a relocation entry for 0x8a8d.
grub-install: info: adding a relocation entry for 0x8a9f.
grub-install: info: adding a relocation entry for 0x8ae2.
grub-install: info: adding a relocation entry for 0x8af6.
grub-install: info: adding a relocation entry for 0x8b04.
grub-install: info: adding a relocation entry for 0x8b10.
grub-install: info: adding a relocation entry for 0x8b20.
grub-install: info: adding a relocation entry for 0x8b2e.
grub-install: info: adding a relocation entry for 0x8b3a.
grub-install: info: adding a relocation entry for 0x8b83.
grub-install: info: adding a relocation entry for 0x8ba0.
grub-install: info: adding a relocation entry for 0x8bb5.
grub-install: info: adding a relocation entry for 0x8beb.
grub-install: info: adding a relocation entry for 0x8c41.
grub-install: info: adding a relocation entry for 0x8c76.
grub-install: info: adding a relocation entry for 0x8d5d.
grub-install: info: adding a relocation entry for 0x8d67.
grub-install: info: adding a relocation entry for 0x8d98.
grub-install: info: adding a relocation entry for 0x8da7.
grub-install: info: adding a relocation entry for 0x8de0.
grub-install: info: adding a relocation entry for 0x8e4e.
grub-install: info: adding a relocation entry for 0x8e64.
grub-install: info: adding a relocation entry for 0x8e83.
grub-install: info: adding a relocation entry for 0x8eb9.
grub-install: info: adding a relocation entry for 0x8ede.
grub-install: info: adding a relocation entry for 0x8f07.
grub-install: info: adding a relocation entry for 0x8f12.
grub-install: info: adding a relocation entry for 0x8f65.
grub-install: info: adding a relocation entry for 0x8f70.
grub-install: info: adding a relocation entry for 0x8f9d.
grub-install: info: adding a relocation entry for 0x8fae.
grub-install: info: adding a relocation entry for 0x8fc1.
grub-install: info: adding a relocation entry for 0x9012.
grub-install: info: adding a padding fixup entry.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 160 bytes of a fixup block starting at 0x8000.
grub-install: info: adding a relocation entry for 0x9024.
grub-install: info: adding a relocation entry for 0x9065.
grub-install: info: adding a relocation entry for 0x9075.
grub-install: info: adding a relocation entry for 0x9098.
grub-install: info: adding a relocation entry for 0x90c0.
grub-install: info: adding a relocation entry for 0x90d8.
grub-install: info: adding a relocation entry for 0x90e8.
grub-install: info: adding a relocation entry for 0x9148.
grub-install: info: adding a relocation entry for 0x9167.
grub-install: info: adding a relocation entry for 0x9195.
grub-install: info: adding a relocation entry for 0x91aa.
grub-install: info: adding a relocation entry for 0x91d8.
grub-install: info: adding a relocation entry for 0x91f8.
grub-install: info: adding a relocation entry for 0x9202.
grub-install: info: adding a relocation entry for 0x9234.
grub-install: info: adding a relocation entry for 0x9259.
grub-install: info: adding a relocation entry for 0x9263.
grub-install: info: adding a relocation entry for 0x9272.
grub-install: info: adding a relocation entry for 0x9283.
grub-install: info: adding a relocation entry for 0x932c.
grub-install: info: adding a relocation entry for 0x9341.
grub-install: info: adding a relocation entry for 0x9355.
grub-install: info: adding a relocation entry for 0x935f.
grub-install: info: adding a relocation entry for 0x9371.
grub-install: info: adding a relocation entry for 0x9380.
grub-install: info: adding a relocation entry for 0x93c0.
grub-install: info: adding a relocation entry for 0x9424.
grub-install: info: adding a relocation entry for 0x9436.
grub-install: info: adding a relocation entry for 0x944d.
grub-install: info: adding a relocation entry for 0x9486.
grub-install: info: adding a relocation entry for 0x949b.
grub-install: info: adding a relocation entry for 0x94bb.
grub-install: info: adding a relocation entry for 0x94d1.
grub-install: info: adding a relocation entry for 0x951c.
grub-install: info: adding a relocation entry for 0x954e.
grub-install: info: adding a relocation entry for 0x9573.
grub-install: info: adding a relocation entry for 0x9583.
grub-install: info: adding a relocation entry for 0x95ae.
grub-install: info: adding a relocation entry for 0x95ba.
grub-install: info: adding a relocation entry for 0x95c6.
grub-install: info: adding a relocation entry for 0x95d0.
grub-install: info: adding a relocation entry for 0x95e4.
grub-install: info: adding a relocation entry for 0x95f0.
grub-install: info: adding a relocation entry for 0x9601.
grub-install: info: adding a relocation entry for 0x9616.
grub-install: info: adding a relocation entry for 0x9628.
grub-install: info: adding a relocation entry for 0x9635.
grub-install: info: adding a relocation entry for 0x964a.
grub-install: info: adding a relocation entry for 0x9661.
grub-install: info: adding a relocation entry for 0x966b.
grub-install: info: adding a relocation entry for 0x968c.
grub-install: info: adding a relocation entry for 0x96b1.
grub-install: info: adding a relocation entry for 0x96db.
grub-install: info: adding a relocation entry for 0x96e7.
grub-install: info: adding a relocation entry for 0x96f3.
grub-install: info: adding a relocation entry for 0x970d.
grub-install: info: adding a relocation entry for 0x9717.
grub-install: info: adding a relocation entry for 0x9723.
grub-install: info: adding a relocation entry for 0x972f.
grub-install: info: adding a relocation entry for 0x9739.
grub-install: info: adding a relocation entry for 0x9753.
grub-install: info: adding a relocation entry for 0x975f.
grub-install: info: adding a relocation entry for 0x976f.
grub-install: info: adding a relocation entry for 0x9779.
grub-install: info: adding a relocation entry for 0x978f.
grub-install: info: adding a relocation entry for 0x97af.
grub-install: info: adding a relocation entry for 0x97c0.
grub-install: info: adding a relocation entry for 0x980a.
grub-install: info: adding a relocation entry for 0x9842.
grub-install: info: adding a relocation entry for 0x9859.
grub-install: info: adding a relocation entry for 0x987b.
grub-install: info: adding a relocation entry for 0x98af.
grub-install: info: adding a relocation entry for 0x98c3.
grub-install: info: adding a relocation entry for 0x98d4.
grub-install: info: adding a relocation entry for 0x98fa.
grub-install: info: adding a relocation entry for 0x9922.
grub-install: info: adding a relocation entry for 0x992c.
grub-install: info: adding a relocation entry for 0x9941.
grub-install: info: adding a relocation entry for 0x994c.
grub-install: info: translating the relocation section .rela.rodata.
grub-install: info: adding a relocation entry for 0x9a00.
grub-install: info: adding a relocation entry for 0x9a08.
grub-install: info: adding a relocation entry for 0x9a10.
grub-install: info: adding a relocation entry for 0x9a18.
grub-install: info: adding a relocation entry for 0x9a20.
grub-install: info: adding a relocation entry for 0x9a28.
grub-install: info: adding a relocation entry for 0x9a30.
grub-install: info: adding a relocation entry for 0x9a38.
grub-install: info: adding a relocation entry for 0x9a40.
grub-install: info: adding a relocation entry for 0x9a48.
grub-install: info: adding a relocation entry for 0x9a50.
grub-install: info: adding a relocation entry for 0x9a58.
grub-install: info: adding a relocation entry for 0x9a60.
grub-install: info: adding a relocation entry for 0x9a68.
grub-install: info: adding a relocation entry for 0x9a70.
grub-install: info: adding a relocation entry for 0x9a78.
grub-install: info: adding a relocation entry for 0x9a80.
grub-install: info: adding a relocation entry for 0x9a88.
grub-install: info: adding a relocation entry for 0x9a90.
grub-install: info: adding a relocation entry for 0x9a98.
grub-install: info: adding a relocation entry for 0x9aa0.
grub-install: info: adding a relocation entry for 0x9aa8.
grub-install: info: adding a relocation entry for 0x9ab0.
grub-install: info: adding a relocation entry for 0x9ab8.
grub-install: info: adding a relocation entry for 0x9ac0.
grub-install: info: adding a relocation entry for 0x9ac8.
grub-install: info: adding a relocation entry for 0x9ad0.
grub-install: info: adding a relocation entry for 0x9ad8.
grub-install: info: adding a relocation entry for 0x9b40.
grub-install: info: adding a relocation entry for 0x9b48.
grub-install: info: adding a relocation entry for 0x9b50.
grub-install: info: adding a relocation entry for 0x9b58.
grub-install: info: adding a relocation entry for 0x9b60.
grub-install: info: adding a relocation entry for 0x9b68.
grub-install: info: adding a relocation entry for 0x9b70.
grub-install: info: adding a relocation entry for 0x9b78.
grub-install: info: adding a relocation entry for 0x9b80.
grub-install: info: adding a relocation entry for 0x9b88.
grub-install: info: adding a relocation entry for 0x9b90.
grub-install: info: translating the relocation section .rela.data.
grub-install: info: adding a relocation entry for 0xb4e0.
grub-install: info: adding a padding fixup entry.
grub-install: info: writing 248 bytes of a fixup block starting at 0x9000.
grub-install: info: adding a relocation entry for 0xb4f0.
grub-install: info: adding a relocation entry for 0xb4f8.
grub-install: info: adding a relocation entry for 0xb500.
grub-install: info: adding a relocation entry for 0xb508.
grub-install: info: adding a relocation entry for 0xb510.
grub-install: info: adding a relocation entry for 0xb570.
grub-install: info: adding a relocation entry for 0xb588.
grub-install: info: adding a relocation entry for 0xb5b0.
grub-install: info: adding a relocation entry for 0xb5b8.
grub-install: info: adding a relocation entry for 0xb5c0.
grub-install: info: adding a relocation entry for 0xb5c8.
grub-install: info: adding a relocation entry for 0xb5d8.
grub-install: info: adding a relocation entry for 0xb5e0.
grub-install: info: adding a relocation entry for 0xb5e8.
grub-install: info: adding a relocation entry for 0xb5f0.
grub-install: info: adding a relocation entry for 0xb5f8.
grub-install: info: adding a relocation entry for 0xb600.
grub-install: info: adding a relocation entry for 0xb630.
grub-install: info: adding a relocation entry for 0xb650.
grub-install: info: adding a relocation entry for 0xb660.
grub-install: info: adding a relocation entry for 0xb668.
grub-install: info: adding a relocation entry for 0xb690.
grub-install: info: adding a relocation entry for 0xb7e0.
grub-install: info: adding a relocation entry for 0xb7f0.
grub-install: info: adding a relocation entry for 0xb7f8.
grub-install: info: adding a relocation entry for 0xb808.
grub-install: info: adding a relocation entry for 0xb810.
grub-install: info: adding a relocation entry for 0xb820.
grub-install: info: adding a relocation entry for 0xb828.
grub-install: info: adding a relocation entry for 0xb838.
grub-install: info: adding a relocation entry for 0xb840.
grub-install: info: adding a relocation entry for 0xb850.
grub-install: info: adding a relocation entry for 0xb858.
grub-install: info: adding a relocation entry for 0xb868.
grub-install: info: adding a relocation entry for 0xb870.
grub-install: info: adding a relocation entry for 0xb880.
grub-install: info: adding a relocation entry for 0xb888.
grub-install: info: adding a relocation entry for 0xb898.
grub-install: info: adding a relocation entry for 0xb8a0.
grub-install: info: adding a relocation entry for 0xb8b0.
grub-install: info: adding a relocation entry for 0xb8b8.
grub-install: info: adding a relocation entry for 0xb8c8.
grub-install: info: adding a relocation entry for 0xb8d0.
grub-install: info: adding a relocation entry for 0xb8e0.
grub-install: info: adding a relocation entry for 0xb8e8.
grub-install: info: adding a relocation entry for 0xb8f8.
grub-install: info: adding a relocation entry for 0xb900.
grub-install: info: adding a relocation entry for 0xb910.
grub-install: info: adding a relocation entry for 0xb918.
grub-install: info: adding a relocation entry for 0xb928.
grub-install: info: adding a relocation entry for 0xb930.
grub-install: info: adding a relocation entry for 0xb940.
grub-install: info: adding a relocation entry for 0xb948.
grub-install: info: adding a relocation entry for 0xb958.
grub-install: info: adding a relocation entry for 0xb960.
grub-install: info: adding a relocation entry for 0xb970.
grub-install: info: adding a relocation entry for 0xb978.
grub-install: info: adding a relocation entry for 0xb988.
grub-install: info: adding a relocation entry for 0xb990.
grub-install: info: adding a relocation entry for 0xb9a0.
grub-install: info: adding a relocation entry for 0xb9a8.
grub-install: info: adding a relocation entry for 0xb9b8.
grub-install: info: adding a relocation entry for 0xb9c0.
grub-install: info: adding a relocation entry for 0xb9d0.
grub-install: info: adding a relocation entry for 0xb9d8.
grub-install: info: adding a relocation entry for 0xb9e8.
grub-install: info: adding a relocation entry for 0xb9f0.
grub-install: info: adding a relocation entry for 0xba00.
grub-install: info: adding a relocation entry for 0xba08.
grub-install: info: adding a relocation entry for 0xba18.
grub-install: info: adding a relocation entry for 0xba20.
grub-install: info: adding a relocation entry for 0xba30.
grub-install: info: adding a relocation entry for 0xba38.
grub-install: info: adding a relocation entry for 0xba48.
grub-install: info: adding a relocation entry for 0xba50.
grub-install: info: adding a relocation entry for 0xba60.
grub-install: info: adding a relocation entry for 0xba68.
grub-install: info: adding a relocation entry for 0xba78.
grub-install: info: adding a relocation entry for 0xba80.
grub-install: info: adding a relocation entry for 0xba90.
grub-install: info: adding a relocation entry for 0xba98.
grub-install: info: adding a relocation entry for 0xbaa8.
grub-install: info: adding a relocation entry for 0xbab0.
grub-install: info: adding a relocation entry for 0xbac0.
grub-install: info: adding a relocation entry for 0xbac8.
grub-install: info: adding a relocation entry for 0xbad8.
grub-install: info: adding a relocation entry for 0xbae0.
grub-install: info: adding a relocation entry for 0xbaf0.
grub-install: info: adding a relocation entry for 0xbaf8.
grub-install: info: adding a relocation entry for 0xbb08.
grub-install: info: adding a relocation entry for 0xbb10.
grub-install: info: adding a relocation entry for 0xbb20.
grub-install: info: adding a relocation entry for 0xbb28.
grub-install: info: adding a relocation entry for 0xbb38.
grub-install: info: adding a relocation entry for 0xbb40.
grub-install: info: adding a relocation entry for 0xbb50.
grub-install: info: adding a relocation entry for 0xbb58.
grub-install: info: adding a relocation entry for 0xbb68.
grub-install: info: adding a relocation entry for 0xbb70.
grub-install: info: adding a relocation entry for 0xbb80.
grub-install: info: adding a relocation entry for 0xbb88.
grub-install: info: adding a relocation entry for 0xbb98.
grub-install: info: adding a relocation entry for 0xbba0.
grub-install: info: adding a relocation entry for 0xbbb0.
grub-install: info: adding a relocation entry for 0xbbb8.
grub-install: info: adding a relocation entry for 0xbbc8.
grub-install: info: adding a relocation entry for 0xbbd0.
grub-install: info: adding a relocation entry for 0xbbe0.
grub-install: info: adding a relocation entry for 0xbbe8.
grub-install: info: adding a relocation entry for 0xbbf8.
grub-install: info: adding a relocation entry for 0xbc00.
grub-install: info: adding a relocation entry for 0xbc10.
grub-install: info: adding a relocation entry for 0xbc18.
grub-install: info: adding a relocation entry for 0xbc28.
grub-install: info: adding a relocation entry for 0xbc30.
grub-install: info: adding a relocation entry for 0xbc40.
grub-install: info: adding a relocation entry for 0xbc48.
grub-install: info: adding a relocation entry for 0xbc58.
grub-install: info: adding a relocation entry for 0xbc60.
grub-install: info: adding a relocation entry for 0xbc70.
grub-install: info: adding a relocation entry for 0xbc78.
grub-install: info: adding a relocation entry for 0xbc88.
grub-install: info: adding a relocation entry for 0xbc90.
grub-install: info: adding a relocation entry for 0xbca0.
grub-install: info: adding a relocation entry for 0xbca8.
grub-install: info: adding a relocation entry for 0xbcb8.
grub-install: info: adding a relocation entry for 0xbcc0.
grub-install: info: adding a relocation entry for 0xbcd0.
grub-install: info: adding a relocation entry for 0xbcd8.
grub-install: info: adding a relocation entry for 0xbce8.
grub-install: info: adding a relocation entry for 0xbcf0.
grub-install: info: adding a relocation entry for 0xbd00.
grub-install: info: adding a relocation entry for 0xbd08.
grub-install: info: adding a relocation entry for 0xbd18.
grub-install: info: adding a relocation entry for 0xbd20.
grub-install: info: adding a relocation entry for 0xbd30.
grub-install: info: adding a relocation entry for 0xbd38.
grub-install: info: adding a relocation entry for 0xbd48.
grub-install: info: adding a relocation entry for 0xbd50.
grub-install: info: adding a relocation entry for 0xbd60.
grub-install: info: adding a relocation entry for 0xbd68.
grub-install: info: adding a relocation entry for 0xbd78.
grub-install: info: adding a relocation entry for 0xbd80.
grub-install: info: adding a relocation entry for 0xbd90.
grub-install: info: adding a relocation entry for 0xbd98.
grub-install: info: adding a relocation entry for 0xbda8.
grub-install: info: adding a relocation entry for 0xbdb0.
grub-install: info: adding a relocation entry for 0xbdc0.
grub-install: info: adding a relocation entry for 0xbdc8.
grub-install: info: adding a relocation entry for 0xbdd8.
grub-install: info: adding a relocation entry for 0xbde0.
grub-install: info: adding a relocation entry for 0xbdf0.
grub-install: info: adding a relocation entry for 0xbdf8.
grub-install: info: adding a relocation entry for 0xbe08.
grub-install: info: adding a relocation entry for 0xbe10.
grub-install: info: adding a relocation entry for 0xbe20.
grub-install: info: adding a relocation entry for 0xbe28.
grub-install: info: adding a relocation entry for 0xbe38.
grub-install: info: adding a relocation entry for 0xbe40.
grub-install: info: adding a relocation entry for 0xbe50.
grub-install: info: adding a relocation entry for 0xbe58.
grub-install: info: adding a relocation entry for 0xbe68.
grub-install: info: adding a relocation entry for 0xbe70.
grub-install: info: adding a relocation entry for 0xbe80.
grub-install: info: adding a relocation entry for 0xbe88.
grub-install: info: adding a relocation entry for 0xbe98.
grub-install: info: adding a relocation entry for 0xbea0.
grub-install: info: adding a relocation entry for 0xbeb0.
grub-install: info: adding a relocation entry for 0xbeb8.
grub-install: info: adding a relocation entry for 0xbec8.
grub-install: info: adding a relocation entry for 0xbed0.
grub-install: info: adding a relocation entry for 0xbee0.
grub-install: info: adding a relocation entry for 0xbee8.
grub-install: info: adding a relocation entry for 0xbef8.
grub-install: info: adding a relocation entry for 0xbf00.
grub-install: info: adding a relocation entry for 0xbf10.
grub-install: info: adding a relocation entry for 0xbf18.
grub-install: info: adding a relocation entry for 0xbf28.
grub-install: info: adding a relocation entry for 0xbf30.
grub-install: info: adding a relocation entry for 0xbf40.
grub-install: info: adding a relocation entry for 0xbf48.
grub-install: info: adding a relocation entry for 0xbf58.
grub-install: info: adding a relocation entry for 0xbf60.
grub-install: info: adding a relocation entry for 0xbf70.
grub-install: info: adding a relocation entry for 0xbf78.
grub-install: info: adding a relocation entry for 0xbf88.
grub-install: info: adding a relocation entry for 0xbf90.
grub-install: info: adding a relocation entry for 0xbfa0.
grub-install: info: adding a relocation entry for 0xbfa8.
grub-install: info: adding a relocation entry for 0xbfb8.
grub-install: info: adding a relocation entry for 0xbfc0.
grub-install: info: adding a relocation entry for 0xbfd0.
grub-install: info: adding a relocation entry for 0xbfd8.
grub-install: info: adding a relocation entry for 0xbfe8.
grub-install: info: adding a relocation entry for 0xbff0.
grub-install: info: adding a relocation entry for 0xc000.
grub-install: info: writing 400 bytes of a fixup block starting at 0xb000.
grub-install: info: adding a relocation entry for 0xc008.
grub-install: info: adding a relocation entry for 0xc018.
grub-install: info: adding a relocation entry for 0xc020.
grub-install: info: adding a relocation entry for 0xc030.
grub-install: info: adding a relocation entry for 0xc038.
grub-install: info: adding a relocation entry for 0xc048.
grub-install: info: adding a relocation entry for 0xc050.
grub-install: info: adding a relocation entry for 0xc060.
grub-install: info: adding a relocation entry for 0xc068.
grub-install: info: adding a relocation entry for 0xc078.
grub-install: info: adding a relocation entry for 0xc080.
grub-install: info: adding a relocation entry for 0xc090.
grub-install: info: adding a relocation entry for 0xc098.
grub-install: info: adding a relocation entry for 0xc0a8.
grub-install: info: adding a relocation entry for 0xc0b0.
grub-install: info: adding a relocation entry for 0xc0c0.
grub-install: info: adding a relocation entry for 0xc0c8.
grub-install: info: adding a relocation entry for 0xc0d8.
grub-install: info: adding a relocation entry for 0xc0e0.
grub-install: info: adding a relocation entry for 0xc0f0.
grub-install: info: adding a relocation entry for 0xc0f8.
grub-install: info: adding a relocation entry for 0xc108.
grub-install: info: adding a relocation entry for 0xc110.
grub-install: info: adding a relocation entry for 0xc120.
grub-install: info: adding a relocation entry for 0xc128.
grub-install: info: adding a relocation entry for 0xc138.
grub-install: info: adding a relocation entry for 0xc140.
grub-install: info: adding a relocation entry for 0xc150.
grub-install: info: adding a relocation entry for 0xc158.
grub-install: info: adding a relocation entry for 0xc168.
grub-install: info: adding a relocation entry for 0xc170.
grub-install: info: adding a relocation entry for 0xc180.
grub-install: info: adding a relocation entry for 0xc188.
grub-install: info: adding a relocation entry for 0xc198.
grub-install: info: adding a relocation entry for 0xc1a0.
grub-install: info: adding a relocation entry for 0xc1b0.
grub-install: info: adding a relocation entry for 0xc1b8.
grub-install: info: adding a relocation entry for 0xc1c8.
grub-install: info: adding a relocation entry for 0xc1d0.
grub-install: info: adding a relocation entry for 0xc1e0.
grub-install: info: adding a relocation entry for 0xc1e8.
grub-install: info: adding a relocation entry for 0xc1f8.
grub-install: info: adding a relocation entry for 0xc200.
grub-install: info: adding a relocation entry for 0xc210.
grub-install: info: adding a relocation entry for 0xc218.
grub-install: info: adding a relocation entry for 0xc228.
grub-install: info: adding a relocation entry for 0xc230.
grub-install: info: adding a relocation entry for 0xc240.
grub-install: info: adding a relocation entry for 0xc248.
grub-install: info: adding a relocation entry for 0xc258.
grub-install: info: adding a relocation entry for 0xc260.
grub-install: info: adding a relocation entry for 0xc270.
grub-install: info: adding a relocation entry for 0xc278.
grub-install: info: adding a relocation entry for 0xc288.
grub-install: info: adding a relocation entry for 0xc290.
grub-install: info: adding a relocation entry for 0xc2a0.
grub-install: info: adding a relocation entry for 0xc2a8.
grub-install: info: adding a relocation entry for 0xc2b8.
grub-install: info: adding a relocation entry for 0xc2c0.
grub-install: info: adding a relocation entry for 0xc2d0.
grub-install: info: adding a relocation entry for 0xc2d8.
grub-install: info: adding a relocation entry for 0xc2e8.
grub-install: info: adding a relocation entry for 0xc2f0.
grub-install: info: adding a relocation entry for 0xc300.
grub-install: info: adding a relocation entry for 0xc308.
grub-install: info: adding a relocation entry for 0xc318.
grub-install: info: adding a relocation entry for 0xc320.
grub-install: info: adding a relocation entry for 0xc330.
grub-install: info: adding a relocation entry for 0xc338.
grub-install: info: adding a relocation entry for 0xc348.
grub-install: info: adding a relocation entry for 0xc350.
grub-install: info: adding a relocation entry for 0xc360.
grub-install: info: adding a relocation entry for 0xc368.
grub-install: info: adding a relocation entry for 0xc378.
grub-install: info: adding a relocation entry for 0xc380.
grub-install: info: adding a relocation entry for 0xc390.
grub-install: info: adding a relocation entry for 0xc398.
grub-install: info: adding a relocation entry for 0xc3a8.
grub-install: info: adding a relocation entry for 0xc3b0.
grub-install: info: adding a relocation entry for 0xc3c0.
grub-install: info: adding a relocation entry for 0xc3c8.
grub-install: info: adding a relocation entry for 0xc3d8.
grub-install: info: adding a relocation entry for 0xc3e0.
grub-install: info: adding a relocation entry for 0xc3f0.
grub-install: info: adding a relocation entry for 0xc3f8.
grub-install: info: adding a relocation entry for 0xc408.
grub-install: info: adding a relocation entry for 0xc410.
grub-install: info: adding a relocation entry for 0xc420.
grub-install: info: adding a relocation entry for 0xc428.
grub-install: info: adding a relocation entry for 0xc438.
grub-install: info: adding a relocation entry for 0xc440.
grub-install: info: adding a relocation entry for 0xc450.
grub-install: info: adding a relocation entry for 0xc458.
grub-install: info: adding a relocation entry for 0xc468.
grub-install: info: adding a relocation entry for 0xc470.
grub-install: info: adding a relocation entry for 0xc480.
grub-install: info: adding a relocation entry for 0xc488.
grub-install: info: adding a relocation entry for 0xc498.
grub-install: info: adding a relocation entry for 0xc4a0.
grub-install: info: adding a relocation entry for 0xc4b0.
grub-install: info: adding a relocation entry for 0xc4b8.
grub-install: info: adding a relocation entry for 0xc4c8.
grub-install: info: adding a relocation entry for 0xc4d0.
grub-install: info: adding a relocation entry for 0xc4e0.
grub-install: info: adding a relocation entry for 0xc4e8.
grub-install: info: adding a relocation entry for 0xc4f8.
grub-install: info: adding a relocation entry for 0xc500.
grub-install: info: adding a relocation entry for 0xc510.
grub-install: info: adding a relocation entry for 0xc518.
grub-install: info: adding a relocation entry for 0xc528.
grub-install: info: adding a relocation entry for 0xc530.
grub-install: info: adding a relocation entry for 0xc540.
grub-install: info: adding a relocation entry for 0xc548.
grub-install: info: adding a relocation entry for 0xc558.
grub-install: info: adding a relocation entry for 0xc560.
grub-install: info: adding a relocation entry for 0xc570.
grub-install: info: adding a relocation entry for 0xc578.
grub-install: info: adding a relocation entry for 0xc588.
grub-install: info: adding a relocation entry for 0xc590.
grub-install: info: adding a relocation entry for 0xc5a0.
grub-install: info: adding a relocation entry for 0xc5a8.
grub-install: info: adding a relocation entry for 0xc5b8.
grub-install: info: adding a relocation entry for 0xc5c0.
grub-install: info: adding a relocation entry for 0xc5d0.
grub-install: info: adding a relocation entry for 0xc5d8.
grub-install: info: adding a relocation entry for 0xc5e8.
grub-install: info: adding a relocation entry for 0xc5f0.
grub-install: info: adding a relocation entry for 0xc600.
grub-install: info: adding a relocation entry for 0xc608.
grub-install: info: adding a relocation entry for 0xc618.
grub-install: info: adding a relocation entry for 0xc620.
grub-install: info: adding a relocation entry for 0xc630.
grub-install: info: adding a relocation entry for 0xc638.
grub-install: info: adding a relocation entry for 0xc648.
grub-install: info: adding a relocation entry for 0xc650.
grub-install: info: adding 204 padding fixup entries.
grub-install: info: writing 688 bytes of a fixup block starting at 0xc000.
grub-install: info: reading /usr/lib/grub/x86_64-efi/fshelp.mod.
grub-install: info: reading /usr/lib/grub/x86_64-efi/ext2.mod.
grub-install: info: reading /usr/lib/grub/x86_64-efi/part_gpt.mod.
grub-install: info: reading /usr/lib/grub/x86_64-efi/search_fs_uuid.mod.
grub-install: info: reading /boot/grub/x86_64-efi/load.cfg.
grub-install: info: kernel_img=0xae8210, kernel_size=0x18200.
grub-install: info: the core size is 0x1d3c0.
grub-install: info: writing 0x1e600 bytes.
grub-install: info: copying `/usr/lib/shim/shim.efi.signed' -> `/boot/efi/EFI/ubuntu/shimx64.efi'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi-signed/grubx64.efi.signed' -> `/boot/efi/EFI/ubuntu/grubx64.efi'.
grub-install: info: copying `/usr/lib/shim/MokManager.efi.signed' -> `/boot/efi/EFI/ubuntu/MokManager.efi'.
grub-install: info: copying `/boot/grub/x86_64-efi/load.cfg' -> `/boot/efi/EFI/ubuntu/grub.cfg'.
grub-install: info: Registering with EFI: distributor = `ubuntu', path = `EFIubuntushimx64.efi', ESP at hostdisk//dev/sda,gpt2.
grub-install: info: executing efibootmgr --version </dev/null >/dev/null.
grub-install: info: executing modprobe -q efivars.
grub-install: info: executing efibootmgr -b 0000 -B.
grub-install: info: executing efibootmgr -c -d /dev/sda -p 2 -w -L ubuntu -l EFIubuntushimx64.efi.
Installation finished. No error reported.
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0003,2003,2001,2002
Boot0001* EFI Network 0 for IPv6 (7C-05-07-79-30-63)
Boot0002* EFI Network 0 for IPv4 (7C-05-07-79-30-63)
Boot0003* Windows Boot Manager
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0003,2003,2001,2002
Boot0001* EFI Network 0 for IPv6 (7C-05-07-79-30-63)
Boot0002* EFI Network 0 for IPv4 (7C-05-07-79-30-63)
Boot0003* Windows Boot Manager
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0000* ubuntu,BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0003,2003,2001,2002
Boot0001* EFI Network 0 for IPv6 (7C-05-07-79-30-63)
Boot0002* EFI Network 0 for IPv4 (7C-05-07-79-30-63)
Boot0003* Windows Boot Manager
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0003,2003,2001,2002
Boot0001* EFI Network 0 for IPv6 (7C-05-07-79-30-63)
Boot0002* EFI Network 0 for IPv4 (7C-05-07-79-30-63)
Boot0003* Windows Boot Manager
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0000* ubuntu.
Wrong GRUB version detected. Please report this message to boot.repair@gmail.com

Reinstall the GRUB of sda6 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

update-grub -y
Unrecognized option `-y'
Usage: grub-mkconfig [OPTION]
Generate a grub config file

-o, --output=FILE       SET@_progressbar1.pulse()
output generated config to FILE [default=stdout]
-h, --help              print this message and exit
-v, --version           print the version information and exit

Report bugs to <bug-grub@gnu.org>.

update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda6/boot/grub/grub.cfg

An error occurred during the repair.

You can now reboot your computer.

 [COLOR=#000000]The boot files of [The OS now in use - Ubuntu 14.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)[/COLOR]
```

---

### Post by oldfred on 2014-06-11
You ran Boot-Repairs' buggy UEFI "fix". That is for systems that only boot Windows as they have modified UEFI. If you can boot Ubuntu you should undo it.

This is the renamed and original bootmgfw.efi
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 

But grub only finds the bootmgfw.efi which is now actually shim because Boot-Repair renamed it.
chainloader /EFI/Microsoft/Boot/bootmgfw.efi

   
You show ubuntu as 0000 in your UEFI:
BootOrder: 0000,0003,2003,2001,2002
Boot0001* EFI Network 0 for IPv6 (7C-05-07-79-30-63)
Boot0002* EFI Network 0 for IPv4 (7C-05-07-79-30-63)
Boot0003* Windows Boot Manager
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0000* ubuntu.

Can you boot ubuntu entry, or are you just booting Windows entry which currently loads grub.
Normally Boot-Repair adds a 25_custom entry to boot the bkpbootmgfw.efi file, but it looks like it is missing.

If you can boot ubuntu undo the rename. If not we need to add a Windows entry or do other work arounds.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

That will let you boot Windows directly from UEFI menu. And if you boot grub the os-prober entry in UEFI should work if secure boot is off. There is a bug on grub not booting Windows with secure boot on.

---

### Post by EthioJOB on 2014-06-11
> **oldfred said:**
> You ran Boot-Repairs' buggy UEFI "fix". That is for systems that only boot Windows as they have modified UEFI. If you can boot Ubuntu you should undo it.

This is the renamed and original bootmgfw.efi
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 

But grub only finds the bootmgfw.efi which is now actually shim because Boot-Repair renamed it.
chainloader /EFI/Microsoft/Boot/bootmgfw.efi

   
You show ubuntu as 0000 in your UEFI:
BootOrder: 0000,0003,2003,2001,2002
Boot0001* EFI Network 0 for IPv6 (7C-05-07-79-30-63)
Boot0002* EFI Network 0 for IPv4 (7C-05-07-79-30-63)
Boot0003* Windows Boot Manager
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0000* ubuntu.

Can you boot ubuntu entry, or are you just booting Windows entry which currently loads grub.
Normally Boot-Repair adds a 25_custom entry to boot the bkpbootmgfw.efi file, but it looks like it is missing.

If you can boot ubuntu undo the rename. If not we need to add a Windows entry or do other work arounds.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

That will let you boot Windows directly from UEFI menu. And if you boot grub the os-prober entry in UEFI should work if secure boot is off. There is a bug on grub not booting Windows with secure boot on.


The thing is, I used Boot Repair because I wasn't able to boot into Windows in the first place. No change so far.

Trying the Windows entry brings no change; i.e., it'll just stay at the grub menu without any change. Here's an image of the grub menu:

[ATTACH=CONFIG]253906[/ATTACH]

If you need additional information, I did use boot-repair on my previous 13.10 installation because at some point I wasn't able to boot into Ubuntu (but was able to boot into Windows). Also, I can normally boot into and work on Ubuntu, in case you're wondering.
Also, can you please list the steps I should take a little more clearly?

Much appreciated.

---

### Post by oldfred on 2014-06-11
Did you undo the rename?
As with the rename the Windows entry just refers to grub, or it loops onto itself.

---

### Post by EthioJOB on 2014-06-12
> **oldfred said:**
> Did you undo the rename?
As with the rename the Windows entry just refers to grub, or it loops onto itself.

To be sure, all I have to do is open the 'Advanced options', and then simply click on 'Restore EFI backups' checkbox while leaving all others as they are without touching them, right?

---

### Post by oldfred on 2014-06-12
Yes after you do the undo, then the Windows entry in UEFI menu will boot Windows, not grub.
But to boot Ubuntu you have to use the ubuntu entry in UEFI menu.

---

### Post by EthioJOB on 2014-06-12
I guess I learned something new, about UEFI menu :-).

I did as you said and now I'm able to boot into Windows. Forgive my ignorance but I'm just a little confused here; to boot into Ubuntu, you said I should use the Ubuntu entry in the UEFI menu. How or where exactly do I access the UEFI menu?

---

### Post by oldfred on 2014-06-12
Each brand is a bit different and some models are different. If these do not work see your user manual.
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)



Some examples. Only two actually show an ubuntu entry, but it should be in your boot options. Some have two sets one for hardware like hard drive, DVD, etc and another for UEFI. Most seem to have one consolidated list.

---

### Post by EthioJOB on 2014-06-13
Thanks oldfred, I can finally boot into both OSes.

I'm curious though, what happened to the grub menu that appeared first when you boot? Is there a way I can restore it as the current method is a little inconvenient?

---

### Post by oldfred on 2014-06-13
You should get grub menu.
Perhaps with the updates it only has Ubuntu and with only one system it does not show menu.

This also runs os-prober and updates menu. It should find Windows.
sudo update-grub

---

### Post by Kareo on 2014-06-16
I guess you can try **[Windows Boot Genius]("http://www.windowspasswordsrecovery.com/windows-boot/")**, I have used this program to fix Windows 8 won't boot, I think this can help you. Good Luck

---

### Post by EthioJOB on 2014-06-19
> **oldfred said:**
> You should get grub menu.
Perhaps with the updates it only has Ubuntu and with only one system it does not show menu.

This also runs os-prober and updates menu. It should find Windows.
sudo update-grub

I used sudo update-grub, but it only brings the grub menu after choosing ubuntu from the boot menu (F12). Is there a way to bring the grub menu back to the default way - appearing immediately after booting the machine?

---

### Post by oldfred on 2014-06-19
What system is this? 

Sony & HP only boot Windows and Boot-Repairs work around was to rename grub/shim to have the Windows boot file name. But the rename of Windows file means you can only boot Windows from grub not from UEFI menu. And currently with Windows 8.1 grub will not boot Windows if secure boot is on.

Boot-Repair does not seem to automatically do the rename nor create the 25_custom with a Windows boot stanza of the backed up or renamed Windows boot file for Windows to boot from grub menu.

Users have posted these. I suggest manually renaming bootx64.efi or use rEFInd.

       **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming  /EFI/Boot/bootx64.efi  to be shimx64.efi or grubx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

   [http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub](http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub)

---

### Post by EthioJOB on 2014-07-13
> **oldfred said:**
> What system is this? 

Sony & HP only boot Windows and Boot-Repairs work around was to rename grub/shim to have the Windows boot file name. But the rename of Windows file means you can only boot Windows from grub not from UEFI menu. And currently with Windows 8.1 grub will not boot Windows if secure boot is on.

Boot-Repair does not seem to automatically do the rename nor create the 25_custom with a Windows boot stanza of the backed up or renamed Windows boot file for Windows to boot from grub menu.

Users have posted these. I suggest manually renaming bootx64.efi or use rEFInd.

       **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming  /EFI/Boot/bootx64.efi  to be shimx64.efi or grubx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

   [http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub](http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub)


Hi oldfred,

I've been busy so I haven't had a chance to get back to you. Before I follow your posts, my laptop is Toshiba P55.

---

### Post by oldfred on 2014-07-13
Some other threads with similar model Toshiba

  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

