---
title: "Unable to boot from hard drive after install"
date: 2014-06-02
forum: Installation &amp; Upgrades
---

### Post by astrid2 on 2014-06-02
Alright, I've read a number of threads pertaining to this and taken a few steps towards each of those solutions, but so far, none have helped. I bout a Toshiba Satellite E55-A5114 laptop about a week ago, and, as with all my devices, moved to remove windows, install ubuntu, and move on with my life. In either case, I used Windows 8 for about a week before trying to install with my boot usb. I originally set up [or tried to set up] a dual boot with Bodhi Linux, however, I messed up the partitioning and ultimately had to reset the laptop to factory settings before even having a chance to do anything [I think the issue was I set the boot partition to one that was already in use, instead of creating a new partition]. Once restored to factory settings, I made a backup image of Windows 8 onto my external hard drive and then attempted to just install Ubuntu 14.04 64bit and wipe the disk in doing so. I had to use an external keyboard to reach the bios menu at the start [apparently my F* keys don't work too well on this laptop] and finally got to booting from my usb. I tried installing Xubuntu, Mint 17, and Ubuntu 14.04 multiple times, and the install went smoothly, however, after each install, I would reboot and the computer was unable to boot from the HDD-- only able to boot from my USB livedisc. I tried Boot-Repair, and the link was [http://paste.ubuntu.com/7576549/](http://paste.ubuntu.com/7576549/) . Equally, I ran Boot Info Script, to which my output was:
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
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdb1 already mounted or sdb1 busy

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 1954316. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: /dev/sdb1 already mounted or sdb1 busy
mount: /dev/sdb2 already mounted or sdb2 busy

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
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624 1,452,738,559 1,451,687,936 Data partition (Linux)
/dev/sda3   1,452,738,560 1,465,147,391    12,408,832 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8017 MB, 8017412096 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15659008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0     1,974,271     1,974,272   0 Empty
/dev/sdb2           1,954,316     1,958,987         4,672  ef EFI (FAT-12/16/32)

/dev/sdb1 overlaps with /dev/sdb2

GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1               0     1,974,215     1,974,216 Data partition (Windows/Linux)
/dev/sdb2       1,954,316     1,958,987         4,672 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1152-44D1                              vfat       
/dev/sda2        82631270-8826-470d-bb15-a91bfc06498e   ext4       
/dev/sda3        a44648ce-a42c-4d98-9b98-45d8a1712522   swap       
/dev/sdb1                                               iso9660    Ubuntu 14.04 LTS amd64
/dev/sdb2        20E8-7ECD                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  82631270-8826-470d-bb15-a91bfc06498e
else
  search --no-floppy --fs-uuid --set=root 82631270-8826-470d-bb15-a91bfc06498e
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-82631270-8826-470d-bb15-a91bfc06498e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  82631270-8826-470d-bb15-a91bfc06498e
    else
      search --no-floppy --fs-uuid --set=root 82631270-8826-470d-bb15-a91bfc06498e
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=82631270-8826-470d-bb15-a91bfc06498e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-82631270-8826-470d-bb15-a91bfc06498e' {
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-82631270-8826-470d-bb15-a91bfc06498e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  82631270-8826-470d-bb15-a91bfc06498e
        else
          search --no-floppy --fs-uuid --set=root 82631270-8826-470d-bb15-a91bfc06498e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=82631270-8826-470d-bb15-a91bfc06498e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-82631270-8826-470d-bb15-a91bfc06498e' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  82631270-8826-470d-bb15-a91bfc06498e
        else
          search --no-floppy --fs-uuid --set=root 82631270-8826-470d-bb15-a91bfc06498e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=82631270-8826-470d-bb15-a91bfc06498e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
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
UUID=82631270-8826-470d-bb15-a91bfc06498e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=1152-44D1  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=a44648ce-a42c-4d98-9b98-45d8a1712522 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

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
000001b0  b4 35 00 00 00 00 00 00  d6 46 4a 09 00 00 80 00  |.5.......FJ.....|
000001c0  01 00 00 3f e0 c3 00 00  00 00 00 20 1e 00 00 fe  |...?....... ....|
000001d0  ff ff ef fe ff ff 0c d2  1d 00 40 12 00 00 00 00  |..........@.....|
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
000001b0  b4 35 00 00 00 00 00 00  d6 46 4a 09 00 00 80 00  |.5.......FJ.....|
000001c0  01 00 00 3f e0 c3 00 00  00 00 00 20 1e 00 00 fe  |...?....... ....|
000001d0  ff ff ef fe ff ff 0c d2  1d 00 40 12 00 00 00 00  |..........@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-PPlZ7x1C/Tmp_Log: No such file or directory
  No volume groups found


```

Other than that, I've had no luck. Anytime I try to boot from HDD or anything other than my livedisc, I get the 'Reboot and select proper boot device' screen. Please help, I'd love to actually be able to use my new computer again, preferrably without windows.

---

### Post by fantab on 2014-06-03
Welcome to the forum!

First of all, you did the right thing by backing up your Windows install.

The following code from BootInfo Summary from Boot-Repair:

```
BootCurrent: 0003
Timeout: 1 seconds
[COLOR=#b22222]BootOrder: 0004,0005,0006[/COLOR]
Boot0001* UEFI: IP4 Realtek PCIe GBE Family Controller
Boot0002* UEFI: IP6 Realtek PCIe GBE Family Controller
Boot0003* UEFI: SanDisk Cruzer Glide 1.27
[COLOR=#b22222]Boot0004* UEFI:CD/DVD Drive[/COLOR]
Boot0005* UEFI:USB Device
Boot0006* UEFI:Network Device
BootCurrent: 0003
Timeout: 1 seconds
**BootOrder: 0000,0004,0005,0006**
Boot0001* UEFI: IP4 Realtek PCIe GBE Family Controller
Boot0002* UEFI: IP6 Realtek PCIe GBE Family Controller
Boot0003* UEFI: SanDisk Cruzer Glide 1.27
Boot0004* UEFI:CD/DVD Drive
Boot0005* UEFI:USB Device
Boot0006* UEFI:Network Device
**Boot0000* ubuntu,BootCurrent: 0003**
Timeout: 1 seconds
[COLOR=#b22222]BootOrder: 0004,0005,0006[/COLOR]
Boot0001* UEFI: IP4 Realtek PCIe GBE Family Controller
Boot0002* UEFI: IP6 Realtek PCIe GBE Family Controller
Boot0003* UEFI: SanDisk Cruzer Glide 1.
```

...shows that your first 'system' to boot is "Boot0004* UEFI:CD/DVD Drive", which obviously not present.
In other words, you should set up your UEFI/BIOS to boot your HDD first. 
If you will check in UEFI settings you should be able to see "Ubuntu" or 'EFI partition location'. Set it up to boot 'Ubuntu'.

Also the 'parted' output:

```
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
1      1049kB  30.0GB  30.0GB  ext4
2      30.0GB  715GB   685GB   ext4
3      715GB   720GB   5000MB
4      720GB   720GB   34.6MB  fat32              boot
```

...shows that your Boot EFI partition (34.6MB Fat32) is located at the end of the HDD.
Some UEFI firmware needs ESP, EFI System Partition to be at the beginning of the HDD or within the first 100gb. Which is probably why you get:

> /boot/efi detected in the fstab of sda1: UUID=B113-C5A5   (sda4)
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.

Additionally your prestent ESP is only 34MB which is not enough in my view. Ideally it should be 300MB.

I'd suggest that you set up your HDD with first partition as ESP of about 300MB and REINSTALL. Disable 'Secure Boot' if you don't intend to use Windows.

---

### Post by astrid2 on 2014-06-03
Alright. However, these aren't any partitions I originally set [especially the fat32]. How can I change the partitions and reinstall?

---

### Post by astrid2 on 2014-06-03
> 
Some UEFI firmware needs ESP, EFI System Partition to be at the beginning of the HDD or within the first 100gb.

Alright, I reinstalled the system from the livedisc and chose 'something else' so I could edit the partitions. Started a new table, set up the efi boot as a 300MB partition at the beginning of the disc. However, no such luck on reboot. Still doing the same thing.

Here's my bootinfoscript output now:

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
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: /dev/sdb1 already mounted or sdb1 busy

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 1954316. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: unknown filesystem type ''
mount: /dev/sdb1 already mounted or sdb1 busy
mount: /dev/sdb2 already mounted or sdb2 busy

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
/dev/sda1           2,048       585,727       583,680 EFI System partition
/dev/sda2         585,728    59,179,007    58,593,280 Data partition (Linux)
/dev/sda3      59,179,008 1,455,384,575 1,396,205,568 Data partition (Linux)
/dev/sda4   1,455,384,576 1,465,147,391     9,762,816 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8017 MB, 8017412096 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15659008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0     1,974,271     1,974,272   0 Empty
/dev/sdb2           1,954,316     1,958,987         4,672  ef EFI (FAT-12/16/32)

/dev/sdb1 overlaps with /dev/sdb2

GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1               0     1,974,215     1,974,216 Data partition (Windows/Linux)
/dev/sdb2       1,954,316     1,958,987         4,672 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2399-DC82                              vfat       
/dev/sda2        05004bf2-b8d8-4a17-8dfc-5d62061fbf4e   ext4       
/dev/sda3        af836a90-b168-4629-a496-8b0ce1b9bc20   ext4       
/dev/sdb1                                               iso9660    Ubuntu 14.04 LTS amd64
/dev/sdb2        20E8-7ECD                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/ubuntu/05004bf2-b8d8-4a17-8dfc-5d62061fbf4e ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda3        /media/ubuntu/af836a90-b168-4629-a496-8b0ce1b9bc20 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
else
  search --no-floppy --fs-uuid --set=root 05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-05004bf2-b8d8-4a17-8dfc-5d62061fbf4e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
    else
      search --no-floppy --fs-uuid --set=root 05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
    fi
    linux    /boot/vmlinuz-3.13.0-27-generic.efi.signed root=UUID=05004bf2-b8d8-4a17-8dfc-5d62061fbf4e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-27-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-05004bf2-b8d8-4a17-8dfc-5d62061fbf4e' {
    menuentry 'Ubuntu, with Linux 3.13.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-advanced-05004bf2-b8d8-4a17-8dfc-5d62061fbf4e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
        else
          search --no-floppy --fs-uuid --set=root 05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
        fi
        echo    'Loading Linux 3.13.0-27-generic ...'
        linux    /boot/vmlinuz-3.13.0-27-generic.efi.signed root=UUID=05004bf2-b8d8-4a17-8dfc-5d62061fbf4e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-recovery-05004bf2-b8d8-4a17-8dfc-5d62061fbf4e' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
        else
          search --no-floppy --fs-uuid --set=root 05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
        fi
        echo    'Loading Linux 3.13.0-27-generic ...'
        linux    /boot/vmlinuz-3.13.0-27-generic.efi.signed root=UUID=05004bf2-b8d8-4a17-8dfc-5d62061fbf4e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-05004bf2-b8d8-4a17-8dfc-5d62061fbf4e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
        else
          search --no-floppy --fs-uuid --set=root 05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=05004bf2-b8d8-4a17-8dfc-5d62061fbf4e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-05004bf2-b8d8-4a17-8dfc-5d62061fbf4e' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
        else
          search --no-floppy --fs-uuid --set=root 05004bf2-b8d8-4a17-8dfc-5d62061fbf4e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=05004bf2-b8d8-4a17-8dfc-5d62061fbf4e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
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
UUID=05004bf2-b8d8-4a17-8dfc-5d62061fbf4e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=2399-DC82  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda3 during installation
UUID=af836a90-b168-4629-a496-8b0ce1b9bc20 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
#UUID=3b808685-252b-4d89-b04a-890e4fea349f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

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
000001b0  b4 35 00 00 00 00 00 00  d6 46 4a 09 00 00 80 00  |.5.......FJ.....|
000001c0  01 00 00 3f e0 c3 00 00  00 00 00 20 1e 00 00 fe  |...?....... ....|
000001d0  ff ff ef fe ff ff 0c d2  1d 00 40 12 00 00 00 00  |..........@.....|
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
000001b0  b4 35 00 00 00 00 00 00  d6 46 4a 09 00 00 80 00  |.5.......FJ.....|
000001c0  01 00 00 3f e0 c3 00 00  00 00 00 20 1e 00 00 fe  |...?....... ....|
000001d0  ff ff ef fe ff ff 0c d2  1d 00 40 12 00 00 00 00  |..........@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-3y6n0zGJ/Tmp_Log: No such file or directory
  No volume groups found


```

---

### Post by monkeybrain20122 on 2014-06-03
Can you choose legacy (i.e BIOS) instead of UEFI in your BIOS/UEFI settings? If yes life would be a lot simpler.

---

### Post by astrid2 on 2014-06-03
Doesn't look like it, no.

---

### Post by tom94 on 2014-06-03
you should check your bios options more carefully. Maybe there's ad "advanced" section in there, somewhere? Is it an UEFI bios, anyway? Under the boot priorities, you may have to set or choose the hd's in the right order. Maybe your computer is addressing first a wrong partition or another hard disk with boot flag, or a corrupted boot partition, so you are receiving that error message...

---

### Post by astrid2 on 2014-06-03
ok. By disabling secure boot I was able to switch my boot mode from UEFI to CSM. I'm about to reinstall and try once again.

---

### Post by astrid2 on 2014-06-04
Alright! Reinstalling through Legacy worked perfectly. All installed, working perfectly. Thanks, all!

---

