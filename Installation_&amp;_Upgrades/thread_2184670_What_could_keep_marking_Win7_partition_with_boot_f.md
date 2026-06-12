---
title: "What could keep marking Win7 partition with boot flag?"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by efflandt on 2013-10-30
I just got an MSI GE60 20E-073US gaming laptop. Since it has combo Intel and Nvidia GTX 765M graphics I installed 64-bit Ubuntu 13.10 (although, I need to figure out how to get select which grapics to use). It has 64-bit Win7 with msdos partitions, including its data partition D: where I installed Linux.

My problem is that I do not like to put grub in my main mbr because I have had issues before where some Windows programs stored things in parts of the mbr that they "thought" were unused (occupied by grub2) and a Windows Service Pack would not install unless Windows thought it was in command of boot with regular DOS mbr. So like my desktop, I put grub2 in /dev/sda4 and marked that as the boot partition with regular Windows mbr. However, everytime I clear the boot flag from /dev/sda2 (with fdisk and gparted), shut down, then cold boot, something keeps resetting /dev/sda2 as boot, so it never shows the grub menu, it just boots right into Windows..

This is after I remove the boot flag from /dev/sda2:```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda4 
                       and looks at sector 1764507960 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 94 for .
    Operating System:  Ubuntu 13.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 11022512 of /dev/sdb1 for 
                       its second stage. SYSLINUX is installed in the  
                       directory. The integrity check of the ADV area failed. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 2048.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    22,513,663    22,511,616  27 Hidden NTFS (Recovery Environment)
/dev/sda2          22,513,664    22,718,463       204,800  27 Hidden NTFS (Recovery Environment)
/dev/sda3          22,718,464 1,181,204,479 1,158,486,016   7 NTFS / exFAT / HPFS
/dev/sda4    *  1,181,204,480 1,953,523,711   772,319,232  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8100 MB, 8100249600 bytes
204 heads, 51 sectors/track, 1520 cylinders, total 15820800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    15,820,799    15,818,752   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       29c44373-96c0-433f-9295-ec09fcd137f0   ext3       
/dev/sda1        566E73656E733D35                       ntfs       BIOS_RVY
/dev/sda2        60F075B3F0759050                       ntfs       System
/dev/sda3        80B478DAB478D3DE                       ntfs       OS_Install
/dev/sda4        94402696-d979-4e19-bd11-e129e1e67f48   ext4       
/dev/sdb1        4EF0-AE52                              vfat       SONY8GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
insmod part_msdos
insmod ext2
set root='hd0,msdos4'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  94402696-d979-4e19-bd11-e129e1e67f48
else
  search --no-floppy --fs-uuid --set=root 94402696-d979-4e19-bd11-e129e1e67f48
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-94402696-d979-4e19-bd11-e129e1e67f48' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  94402696-d979-4e19-bd11-e129e1e67f48
    else
      search --no-floppy --fs-uuid --set=root 94402696-d979-4e19-bd11-e129e1e67f48
    fi
    linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=94402696-d979-4e19-bd11-e129e1e67f48 ro nomodeset  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.0-12-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-94402696-d979-4e19-bd11-e129e1e67f48' {
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-advanced-94402696-d979-4e19-bd11-e129e1e67f48' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  94402696-d979-4e19-bd11-e129e1e67f48
        else
          search --no-floppy --fs-uuid --set=root 94402696-d979-4e19-bd11-e129e1e67f48
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=94402696-d979-4e19-bd11-e129e1e67f48 ro nomodeset  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-recovery-94402696-d979-4e19-bd11-e129e1e67f48' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  94402696-d979-4e19-bd11-e129e1e67f48
        else
          search --no-floppy --fs-uuid --set=root 94402696-d979-4e19-bd11-e129e1e67f48
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=94402696-d979-4e19-bd11-e129e1e67f48 ro recovery nomodeset nomodeset
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  94402696-d979-4e19-bd11-e129e1e67f48
    else
      search --no-floppy --fs-uuid --set=root 94402696-d979-4e19-bd11-e129e1e67f48
    fi
    linux16    /boot/memtest86+.bin
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  94402696-d979-4e19-bd11-e129e1e67f48
    else
      search --no-floppy --fs-uuid --set=root 94402696-d979-4e19-bd11-e129e1e67f48
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-566E73656E733D35' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  566E73656E733D35
    else
      search --no-floppy --fs-uuid --set=root 566E73656E733D35
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-60F075B3F0759050' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  60F075B3F0759050
    else
      search --no-floppy --fs-uuid --set=root 60F075B3F0759050
    fi
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-80B478DAB478D3DE' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  80B478DAB478D3DE
    else
      search --no-floppy --fs-uuid --set=root 80B478DAB478D3DE
    fi
    chainloader +1
}
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

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=94402696-d979-4e19-bd11-e129e1e67f48 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-P2LM9u3T/Tmp_Log: No such file or directory
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-P2LM9u3T/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-P2LM9u3T/Tmp_Log: No such file or directory
  No volume groups found
```And this is after I shut down entirely and reboot:```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00db0ab6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    22513663    11255808   27  Hidden NTFS WinRE
/dev/sda2   *    22513664    22718463      102400   27  Hidden NTFS WinRE
/dev/sda3        22718464  1181204479   579243008    7  HPFS/NTFS/exFAT
/dev/sda4   *  1181204480  1953523711   386159616   83  Linux

Disk /dev/sdb: 8100 MB, 8100249600 bytes
204 heads, 51 sectors/track, 1520 cylinders, total 15820800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e729d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15820799     7909376    b  W95 FAT32
```I can boot into grub2 in /dev/sda4 using Super Grub 2 on CD, I just cannot figure out what keeps resetting /dev/sda2 with the boot flag during boot after I have cleared it, so it never boots grub in /dev/sda4.

---

### Post by fantab on 2013-10-30
Are you using EasyBCD?
If you are then I think that may be resetting the boot flag.

---

### Post by oldfred on 2013-10-30
You cannot have two boot flags. As then either one may not boot.

Another choice is use a flash drive as sdb drive and install grub2's boot loader to that drive. Then in BIOS or one time boot key boot from sdb to boot grub & Ubuntu on hard drive.

---

### Post by efflandt on 2013-10-30
As far as I know the mbr is standard Windows mbr (never used EasyBCD). I have tried removing the boot flag on sda2 numerous times with gparted and fdisk. But apparently something is resetting the ghost boot flag on sda2 during shutdown, because it is back there during any boot, even booting from USB.

To see if anything in the mbr was doing that, I backed up the 440 bytes of the mbr and dd'd /usr/lib/syslinux/mbr.bin to it instead (per [http://www.syslinux.org/wiki/index.php/Mbr](http://www.syslinux.org/wiki/index.php/Mbr) ).  But mbr.bin refused to boot with 2 boot flags when the ghost boot flag kept reappearing.

I also tried the following from that same syslinux dir thinking that it would force booting sda4, but it booted "MSI Recovery" instead, so apparently I need a different number to boot sda4:```
printf '\4' | cat altmbr.bin - | sudo dd bs=440 count=1 iflag=fullblock conv=notrunc of=/dev/sda
```

I don't see how it can be any sort of write protection on the partition table or unusual partitioning, because it happens even when booting Ubuntu live from USB stick, then removing sda2 boot flag and shutting down. And it did not prevent me from adding/removing the boot flag on sda4 or overwriting the mbr.

Anyway, I restored the original mbr and removed the boot flag  from sda4. So until I figure this out, I put Super Grub 2 on an old 256  MB USB memory stick and will consider it a security feature that someone  has to know about the memory stick to boot Linux on the hard drive (otherwise it will only boot Win7).

---

### Post by oldfred on 2013-10-30
If you can boot into install or use super grub to boot into install you can just install its grub to sdb.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb

If installing with Something else you could also specify another flash drive as install location for grub. 
Some in fact have messed up installer as some BIOS promote a flash drive to sda and then auto install installs grub to sda and system does not boot without flash drive.

I often just install grub to a flash drive so I can use it to boot some of my installs or boot ISO with loop mount on flash drive. But I have to manually create a grub on the flash drive for that.

      
 [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

### Post by efflandt on 2013-11-16
I did eventually "sudo grub-install /dev/sdb" from 13.10 on the hard drive to put grub on the USB memory stick mbr (which boots much faster than Super Grub2 from it).

But at first even after I put an msdos partition table on the memory stick and a FAT32 partition using gparted, grub refused to install to its mbr because it detected 2 different partition types, apparently remnants of the Super Grub2 iso. So I had to dd blocks of /dev/zero to /dev/sdb to zero out a bunch of it. Then I created an msdos partition table and partition and was able to install the grub boot loader to the mbr of the memory stick. That still does not resolve what kept resetting the boot flag on Window's recovery /dev/sda2, but allows me to boot 13.10 on /dev/sda4 quickly without tampering with what might be a non-standard mbr on the hard drive.

Eventually when I get the dual Intel/Nvidia graphics sorted out I may install an SSD and boot from the mbr of that (the laptop has provisions for mSATA SSD). But at least with 13.10's own grub boot loader on the USB memory stick I can boot Linux on my hard drive quickly without tampering with its mbr.

---

