---
title: "Installed Ubuntu, but no boot menu options, boots straight into windows 7"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by leemills on 2012-05-27
Hi there,

So kinda new to Ubuntu and been poking around the forums to try and solve this but not had much luck.

Setup: 
   I have 3 drives in my machine (brand new home build)
     - drive 1: windows 7 (sdb)
     - drive 2: Ubuntu 12.04 (sdc)
     - drive 3: Media & games (sda)

Can anyone make any suggestions?

Managed to get  a boot script readout from a live usb:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sdc2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 60982 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sda2         264,192 3,907,028,991 3,906,764,800 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   234,436,311   234,229,464   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1   250,069,679   250,069,679  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1              34       976,596       976,563 Data partition (Windows/Linux)
/dev/sdc2         976,597     8,789,097     7,812,501 Swap partition (Linux)
/dev/sdc3       8,789,098   250,068,394   241,279,297 Data partition (Windows/Linux)

Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *              2    15,663,103    15,663,102   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        94F4EE0AF4EDEE84                       ntfs       Media
/dev/sdb1        D48A09858A096578                       ntfs       System Reserved
/dev/sdb2        C4B29F99B29F8E94                       ntfs       
/dev/sdc1        2f3a623e-7c63-4b48-8770-badf03c24815   ext4       
/dev/sdc2        d2774b35-812f-4d92-a022-7f003a809bfd   swap       
/dev/sdc3        f7707c92-e2cd-42e8-9ec8-9651d0bb1d8a   ext4       
/dev/sdd1        190E-0837                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sdb1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

============================= sdc1/grub/grub.cfg: ==============================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd2,gpt3)'
search --no-floppy --fs-uuid --set=root f7707c92-e2cd-42e8-9ec8-9651d0bb1d8a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd2,gpt1)'
  search --no-floppy --fs-uuid --set=root 2f3a623e-7c63-4b48-8770-badf03c24815
  set locale_dir=($root)/grub/locale
  set lang=en_GB
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
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd2,gpt1)'
	search --no-floppy --fs-uuid --set=root 2f3a623e-7c63-4b48-8770-badf03c24815
	linux	/vmlinuz-3.2.0-23-generic root=UUID=f7707c92-e2cd-42e8-9ec8-9651d0bb1d8a ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd2,gpt1)'
	search --no-floppy --fs-uuid --set=root 2f3a623e-7c63-4b48-8770-badf03c24815
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/vmlinuz-3.2.0-23-generic root=UUID=f7707c92-e2cd-42e8-9ec8-9651d0bb1d8a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd2,gpt1)'
	search --no-floppy --fs-uuid --set=root 2f3a623e-7c63-4b48-8770-badf03c24815
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd2,gpt1)'
	search --no-floppy --fs-uuid --set=root 2f3a623e-7c63-4b48-8770-badf03c24815
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root D48A09858A096578
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

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/grub.cfg                                  1
               =                initrd.img-3.2.0-23-generic                    2
               =                vmlinuz-3.2.0-23-generic                       2

=============================== sdc3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc3 during installation
UUID=f7707c92-e2cd-42e8-9ec8-9651d0bb1d8a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=2f3a623e-7c63-4b48-8770-badf03c24815 /boot           ext4    defaults        0       2
# swap was on /dev/sdc2 during installation
UUID=d2774b35-812f-4d92-a022-7f003a809bfd none            swap    sw              0       0
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

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/leemills/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

Thanks for any help.

---

### Post by darkod on 2012-05-27
Any particular reason you are using sdc with gpt table? You usually use gpt for very large disks, above 2TB.

If you still intend to use sdc with gpt, you need to make a small 1MB partition with NO FILESYSTEM, and set the bios_grub flag on it. That way grub2 will use it for part of it.

grub2 doesn't fit on the MBR of a gpt disk, so it needs to have the bios_grub partition. You do not create any filesystem on it, not FAT, not NTFS, not EXT, nothing.

It's usually very easy to use parted to create partitions without FS because it creates only a partition with the command mkpart anyway. You can use what ever program you want, the main thing is not to have a FS and to have the bios_grub flag.

After that I suggest you reinstall ubuntu, since you will need to change the partitions now to make that small one anyway. After that set to boot from sdc and it should be fine.

---

### Post by leemills on 2012-05-28
Thanks for the response. No particular reason for using GPT on the drive, just followed a tutorial I found for the installation, can wipe the drive and start again, that's not an issue as long as I can get it working :) I'm guessing that is an option when partitioning the drive during the installation not to use GPT?

Sorry for the complete noob-ness of my posts, first time setting up Ubuntu like this.

---

### Post by darkod on 2012-05-28
If you use the manual partitioning there should be an option to write new partition table on the disk. Select this table to be msdos if you like.

If using msdos table the discussion about the small partition is finished, you don't need it for msdos table.

I found it easiest to write new tables with parted. You can do that from live mode.

First double check that the disk is still /dev/sdc, just in case. You can do that with:
```
sudo fdisk -l
```

Then, lets assume it's still /dev/sdc:
```
sudo parted /dev/sdc
mklabel msdos
quit
```

Now you have msdos table. You can start the install and install as you want.

---

### Post by leemills on 2012-05-28
Thanks dude, am giving it a try now as I type - will let you know how it goes

---

### Post by leemills on 2012-05-28
Unfortunately that didn't work - just got a blinking cursor  after the install completed... so A friend here said to install grub onto sdb - I tried that and it corrupted my windows drive... So I am now re-installing windows, and then I will give it 1 last try - surely I must be doing something wrong as I've been trying to install for well over a week now :(

---

### Post by darkod on 2012-05-28
Blinking cursor on a black screen might be video driver issue, especially with nvidia. If that's the case, often the nomodeset parameter helps. Here are details how to try it:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

Also, you might need to reinstall grub2 on /dev/sdc, not on /dev/sdb. And after that make sure you are booting from sdc. Sometimes just reinstalling grub2 to the MBR works.

---

### Post by leemills on 2012-05-28
Thanks again dude, will give that a try - though will be tomorrow as its quite late here at the moment :)

---

### Post by leemills on 2012-05-29
Hey, I got it working - it was the nVidia drivers. Basically had to run ```
sudo start lightdm
``` and then run updates and install latest nVidia drivers. 

All up a nd running now, loving 12.04!

Thanks again :)

---

