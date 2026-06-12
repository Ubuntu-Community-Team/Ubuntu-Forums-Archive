---
title: "Can't boot new Ubuntu install from UEFI"
date: 2017-01-07
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2017-01-07
Hi
Have a 2 SSD drive setup. One is dedicated to Windows. The other to Ubuntu.
The only change I have made in my UEFI-BIOS is to disable fast boot.

I switch between drives via UEFI-BIOs on boot.

I was able to successfully boot into a fresh Ubunto install several times without issue.
Now for some reason my UEFI doesn't seem to recognize my Ubuntu SSD as bootable.

If you look at the Boot Priority in the attached pic the top most SSD, Samsung EVO 850 1TB has my Ubuntu install.
Shouldn't the actual drive name be preceded by [UEFI] in this menu?

Could this have something to do with either Secure Boot (enabled) or CSM(Compatibility Support Module or Legacy BIOS) enabled? If so curious why I had no issues for several reboots.

Of course, any suggestions or feedback welcome. 3rd install in the past couple months, I want to get it right this time!

---

### Post by sudodus on 2017-01-08
Sometimes Windows makes substantial updates, which also tamper with the booloader system, and after that Ubuntu might no longer boot. This can happen in UEFI mode. Maybe it works for you to repair the bootloader with [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ubuntini2 on 2017-01-08
I have a 2 internal SSD drive setup with one drive dedicated to Windows and the other Ubuntu.
I installed Ubuntu with my Windows drive fully powered and connected (and Windows previously installed). But am having boot issues (although it did boot a couple times, I can't consistently boot Ubuntu even when drive is selected thru UEFI-BIOS)

Reading this guide for installing Ubuntu and Windows on 2 separate hard drives
[http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/]](http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/])

The one paragraph that raised my eyebrows was
>   To ensure that **GRUB** is not installed on the EFI Boot Partition of the Windows 10 hard drive, you&#8217;ll have to disconnect the Windows 10 hard drive from the system. That means disconnecting the power and SATA cables from the hard drive.

To eliminate the possibility that this is my issue, 
How do I check if **GRUB** was accidentally installed on my Windows Boot partition? And if it was, 
How do I remove it? *and*
*Is it possible to properly install Ubuntu without disconnecting drives during the process?*

---

### Post by oldfred on 2017-01-08
Short answer, you cannot stop grub from installing to the Windows ESP - efi system partition.

But it should not be a problem.

Grub only installs to the ESP seen on drive sda in UEFI boot mode.
But UEFI supports multiple boot loaders in ESP, so all it does is add another folder /EFI/ubuntu to the ESP on sda.

Now I do hate that I do not have the option to specify sdb or an external drive as I only boot Ubuntu, and any other full install always overwrites my main working install's /EFI/ubuntu folder in sda. I quickly learned to backup the ESP or sda1 in my configuration.

So I always manually partition, and include an ESP on every drive. The one on my sdb internal drive, is not really used, but I do copy boot files /EFI/ubuntu to sdb, but do not use them. With external drives, I have to copy folder twice as UEFI boots external from /EFI/Boot/bootx64.efi.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ubuntini2 on 2017-01-08
duplicate post

---

### Post by ubuntini2 on 2017-01-08
Thanks! This is the result of running boot info script. sda is of course my Linux drive and sda1 is my ESP. Shouldn't I see boot files listed there? And to be quite honest, have NO idea what sdb is...

                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: /dev/sdb1 is already mounted or /tmp/BootInfo-28d6qhVm/sdb1 busy

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 3193448. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: unknown filesystem type ''
mount: /dev/sdb1 is already mounted or /tmp/BootInfo-28d6qhVm/sdb1 busy
mount: /dev/sdb2 is already mounted or /tmp/BootInfo-28d6qhVm/sdb2 busy

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,128,447     1,126,400 EFI System partition
/dev/sda2       1,128,448     1,132,543         4,096 Data partition (Linux)
/dev/sda3       1,132,544    85,018,623    83,886,080 Data partition (Linux)
/dev/sda4      85,018,624 1,427,195,903 1,342,177,280 Data partition (Linux)
/dev/sda5   1,427,195,904 1,695,631,359   268,435,456 Swap partition (Linux)

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 14.6 GiB, 15614803968 bytes, 30497664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0     3,247,999     3,248,000   0 Empty
/dev/sdb2           3,193,448     3,198,183         4,736  ef EFI (FAT-12/16/32)

/dev/sdb1 overlaps with /dev/sdb2

GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1               0     3,247,943     3,247,944 Data partition (Windows/Linux)
/dev/sdb2       3,193,448     3,198,183         4,736 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/nvme0n1                                                       
/dev/nvme0n1p1   F0C88AA6C88A6AA4                       ntfs       Recovery
/dev/nvme0n1p2   AC8A-F8FB                              vfat       
/dev/nvme0n1p3                                                     
/dev/nvme0n1p4   6C98EA5498EA1BF8                       ntfs       
/dev/nvme0n1p5   4432E41432E40D2C                       ntfs       
/dev/sda1        AE79-1124                              vfat       
/dev/sda2                                                          
/dev/sda3        30e7d85c-164c-43b9-9240-074739104dfc   ext4       /
/dev/sda4        b2f5e601-975d-4484-8e28-29e968eb8965   ext4       /home
/dev/sda5        559ac8c0-348a-470a-b627-689048d909d3   swap       
/dev/sdb1        2016-07-19-22-05-31-00                 iso9660    Ubuntu-MATE 16.04.1 LTS amd64
/dev/sdb2        0F7B-9366                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  30e7d85c-164c-43b9-9240-074739104dfc
else
  search --no-floppy --fs-uuid --set=root 30e7d85c-164c-43b9-9240-074739104dfc
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
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
if background_color 60,59,55; then
  clear
fi

color_normal=light-gray/black

if [ -e ${prefix}/themes/ubuntu-mate/theme.txt ]; then
  insmod png
  theme=${prefix}/themes/ubuntu-mate/theme.txt
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-30e7d85c-164c-43b9-9240-074739104dfc' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  30e7d85c-164c-43b9-9240-074739104dfc
    else
      search --no-floppy --fs-uuid --set=root 30e7d85c-164c-43b9-9240-074739104dfc
    fi
    linux    /boot/vmlinuz-4.4.0-57-generic.efi.signed root=UUID=30e7d85c-164c-43b9-9240-074739104dfc ro elevator=noop quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-57-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-30e7d85c-164c-43b9-9240-074739104dfc' {
    menuentry 'Ubuntu, with Linux 4.4.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-57-generic-advanced-30e7d85c-164c-43b9-9240-074739104dfc' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  30e7d85c-164c-43b9-9240-074739104dfc
        else
          search --no-floppy --fs-uuid --set=root 30e7d85c-164c-43b9-9240-074739104dfc
        fi
        echo    'Loading Linux 4.4.0-57-generic ...'
        linux    /boot/vmlinuz-4.4.0-57-generic.efi.signed root=UUID=30e7d85c-164c-43b9-9240-074739104dfc ro elevator=noop quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-57-generic-recovery-30e7d85c-164c-43b9-9240-074739104dfc' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  30e7d85c-164c-43b9-9240-074739104dfc
        else
          search --no-floppy --fs-uuid --set=root 30e7d85c-164c-43b9-9240-074739104dfc
        fi
        echo    'Loading Linux 4.4.0-57-generic ...'
        linux    /boot/vmlinuz-4.4.0-57-generic.efi.signed root=UUID=30e7d85c-164c-43b9-9240-074739104dfc ro recovery nomodeset elevator=noop
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-advanced-30e7d85c-164c-43b9-9240-074739104dfc' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  30e7d85c-164c-43b9-9240-074739104dfc
        else
          search --no-floppy --fs-uuid --set=root 30e7d85c-164c-43b9-9240-074739104dfc
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=30e7d85c-164c-43b9-9240-074739104dfc ro elevator=noop quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-recovery-30e7d85c-164c-43b9-9240-074739104dfc' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  30e7d85c-164c-43b9-9240-074739104dfc
        else
          search --no-floppy --fs-uuid --set=root 30e7d85c-164c-43b9-9240-074739104dfc
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=30e7d85c-164c-43b9-9240-074739104dfc ro recovery nomodeset elevator=noop
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/nvme0n1p2)' --class windows --class os $menuentry_id_option 'osprober-efi-AC8A-F8FB' {
    insmod part_gpt
    insmod fat
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  AC8A-F8FB
    else
      search --no-floppy --fs-uuid --set=root AC8A-F8FB
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
UUID=30e7d85c-164c-43b9-9240-074739104dfc /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p2 during installation
UUID=AC8A-F8FB  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda4 during installation
UUID=b2f5e601-975d-4484-8e28-29e968eb8965 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=559ac8c0-348a-470a-b627-689048d909d3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  04 84 30 00 00 00 00 00  bb 1a 65 15 00 00 80 00  |..0.......e.....|
000001c0  01 00 00 63 e0 f6 00 00  00 00 80 8f 31 00 00 fe  |...c........1...|
000001d0  ff ff ef fe ff ff 68 ba  30 00 80 12 00 00 00 00  |......h.0.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  04 84 30 00 00 00 00 00  bb 1a 65 15 00 00 80 00  |..0.......e.....|
000001c0  01 00 00 63 e0 f6 00 00  00 00 80 8f 31 00 00 fe  |...c........1...|
000001d0  ff ff ef fe ff ff 68 ba  30 00 80 12 00 00 00 00  |......h.0.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-28d6qhVm/Tmp_Log: No such file or directory
```

---

### Post by oldfred on 2017-01-08
Please use code tags for longer text or terminal output.

Did you run bootinfoscript, not Boot-Repair's summary report? 
Better to post link from Boot-Repair's report.

Bootinfoscript has not been maintained for years, but there is a new fork that is more up to date. And in fact Boot-Repair's report uses the fork as part of its report.
       Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

Also older tools do not show the new NVMe drives.

I would expect all the .efi boot files are in the ESP on the NVMe drive.

---

### Post by oldfred on 2017-01-08
Threads merged since duplicating effort.

---

### Post by ubuntini2 on 2017-01-08
Thanks. Your thoughtful replies are a HUGE help. If I find that all .efi boot files ARE in nvme ESP partition, what next steps would you suggest?
Also, it is my understanding that the standalone boot repair .iso for live USB is not up to date as well and better to install and run within Ubuntu

just a quick note, on my system, Asus X99 A-II mobo and Samsung 950 M.2 SSD, I cannot disable CSM without at least bricking UEFI-BIOS(can't load  UEFI screen) or worse, not even booting Windows(black screen)
I also get a warning in UEFI when trying to disable warning about requiring a special vendor signed UEFI driver or drive may not boot. I should pay attention to these:)

---

### Post by sudodus on 2017-01-08
The PPA for Boot-Repair was updated 2016-11-18 at Launchpad, so I would say that it is up to date.

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
```

The boot-repair-disk is older, modified 2014-11-30 according to the the site at Sourceforge. This is the link I found from

[help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ubuntini2 on 2017-01-08
just a note.
On my system
Asus X99AII mobo with a Samsung 950 M.2 SSD I am unable to turn off CSM without at least bricking UEFi_BIOS(can't load UEFI screen) and worse, many times bricking my Windows boot drive. I get some warning in UEFI when disabling suggesting I need a special vendor signed  UEFI driver on my Windows boot SSD, otherwise it may not work. I should pay attention to these!

---

### Post by ubuntini2 on 2017-01-08
duplicate

---

### Post by ubuntini2 on 2017-01-08
duplicate

---

### Post by ubuntini2 on 2017-01-08
duplicate

---

### Post by oldfred on 2017-01-08
I think several with Dell said system only worked with CSM on, even for UEFI booting.
Most systems seem to need to have CSM off to be able to boot in UEFI mode.

Some may get warnings on Secure boot. Not sure what you are getting.

 Asus/Samsung problem with every NVME SSD and G752! 
[https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551](https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551)
[http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04)
Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/) 
      
 ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)

---

### Post by ubfan1 on 2017-01-09
As for setting up the second EFI partition, just copy everything over from the first.  All the bootloaders and config files are just files on a FAT filesystem, so copy is all you need to do.  Now the other change might be to edit your /etc/fstab and change the UUID on the EFI partition mount from the old partition AC8A-F8FB to the new one AE79-1124.  With those files in place, you then might set up the backup bootloader /EFI/Boot/bootx64.efi.  To do that, copy grubx64.efi and shimx64.efi from /EFI/ubuntu to /EFI/Boot, and rename shimx64.efi to bootx64.efi.  Any existing bootx64.efi is probably a copy of the Windows bootloader bootmgfw.efi (tell by their sizes).  You may overwrite it or rename it, space is typically not a problem.

---

### Post by ubuntini2 on 2017-01-09
This is the error message I get when trying to disable CSM
Spent a few hours trial and error, disabling and enabling various UEFI features and reflashing my UEFI to realize I CANNOT disable CSM:(
Anyways, followed the suggestion from another thread and started again from scratch, repartitioning my Linux SSD and reinstalling Ubuntu.

I followed the instructions of user SH in the comments here EXACTLY for a 2 drive install, except for actual partition sizes and the disabling CSM part:)
[http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/](http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/)

Not sure about the pros-cons of various Live USB creation tools, but will stick with Rufus moving forward.

---

### Post by oldfred on 2017-01-09
I do not understand what Microsoft's secure boot software has to do with turning off CSM. 
You still should be able to have Secure Boot off and then boot either with UEFI or CSM.
But how you boot install media for both Windows & Ubuntu either UEFI or BIOS/CSM is then how it installs.

---

