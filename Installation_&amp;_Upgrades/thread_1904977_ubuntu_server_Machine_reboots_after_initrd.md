---
title: "ubuntu server: Machine reboots after initrd"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by rented on 2012-01-05
Hi!

I am in the process of building a home multi-purpose, always-on server. It is built on the AMD Fusion APU. This being a server, but with relatively modest CPU cababilities, I figured ubuntu server edition would be a good choice. This is my first encounter with ubuntu and my comeback to Linux after more than 10 years away. I think I've forgotten everything I ever knew :)

Anyway, I started with Linux Mint 12, but it is really a desktop distro. I'm just mentioning it because it actually installed without issues and booted up just fine. I played around with it and everything seems to work properly. Mint does warn about misaligned blocks in the HDD though. I just don't want/need all the desktop stuff.

So I downloaded the latest ubuntu server (ubuntu-11.10-server-amd64.iso), loaded it onto a bootable USB stick and installed it from there. During partitioning I asked it to use the whole drive using LVM. 

The installation seems to complete without any errors, but once completed, and it reboots the server, I don't get any further than "Loading initial ramdisk" (visible when selecting the recovery mode variant in grub), after which it resets the machine and reboots. I quickly get to see a white horizontal bar accross the top of the screen before it reboots the machine.

I have tried a multitude of parameters (from the sticky atop this forum page) but nothing seems to help. I cannot even get into "text" mode. I reinstalled from scratch just in case something did go wrong after all during install, but it is still the same.

My machine specs are as follows:
-Asus E45M1-M PRO motherboard
 -UEFI, AMD E-450-processor, AMD Radeon HD 6320
-3TB SATA 6 HDD
-8GB DDR3 1600 MHz memory

I am at a loss here as to how to troubleshoot this any further. Any help much appreciated!

/Kris

Results from that boot-script thingy (run from Mint 12 LiveCD):
[http://paste.ubuntu.com/794274/](http://paste.ubuntu.com/794274/)
```

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 15528 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

treeship-root': ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

treeship-swap_1': ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       390,659       390,626 EFI System partition
/dev/sda2         390,660       890,660       500,001 Data partition (Windows/Linux)
/dev/sda3         890,661 2,639,307,646 2,638,416,986 Logical Volume Manager (LVM) partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2038 MB, 2038431744 bytes
2 heads, 63 sectors/track, 31597 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,981,311     3,981,280   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/treeship-root 6347daa6-6fad-4341-9b87-cf7818690db1   ext4       
/dev/mapper/treeship-swap_1 fd27e451-7edb-4db3-bd05-e568e74c736e   swap       
/dev/sda1        5320-9E6E                              vfat       
/dev/sda2        f9a727ec-44b7-4d8d-8178-440a13fb9027   ext2       
/dev/sda3        ycrA2W-6o3j-a4Fb-Dp0m-0rXJ-RHfb-a1RySi LVM2_member 
/dev/sdb1        1DED-310F                              vfat       PENDRIVE

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
treeship-root
treeship-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda2/grub/grub.cfg: ==============================

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

insmod lvm
insmod part_gpt
insmod ext2
set root='(treeship-root)'
search --no-floppy --fs-uuid --set=root 6347daa6-6fad-4341-9b87-cf7818690db1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root f9a727ec-44b7-4d8d-8178-440a13fb9027
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu, with Linux 3.0.0-12-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f9a727ec-44b7-4d8d-8178-440a13fb9027
	linux	/vmlinuz-3.0.0-12-server root=/dev/mapper/treeship-root ro   
	initrd	/initrd.img-3.0.0-12-server
}
menuentry 'Ubuntu, with Linux 3.0.0-12-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f9a727ec-44b7-4d8d-8178-440a13fb9027
	echo	'Loading Linux 3.0.0-12-server ...'
	linux	/vmlinuz-3.0.0-12-server root=/dev/mapper/treeship-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-12-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f9a727ec-44b7-4d8d-8178-440a13fb9027
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f9a727ec-44b7-4d8d-8178-440a13fb9027
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.236703873 = 0.254158848    grub/grub.cfg                                  1
   0.227069855 = 0.243814400    initrd.img-3.0.0-12-server                    59
   0.195573807 = 0.209995776    vmlinuz-3.0.0-12-server                       20

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
set menu_color_highlight=white/light-gray

menuentry "Start Linux Mint" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Start Linux Mint (compatibility mode)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper xforcevesa ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
	initrd	/casper/initrd.lz
}
menuentry "Check the integrity of the medium" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
default vesamenu.c32

menu background splash.jpg
menu title Welcome to Linux Mint
menu color border 0 #00eeeeee #00000000
menu color sel 7 #ffffffff #33eeeeee
menu color title 0 #ffeeeeee #00000000
menu color tabmsg 0 #ffeeeeee #00000000
menu color unsel 0 #ffeeeeee #00000000
menu color hotsel 0 #ff000000 #ffffffff
menu color hotkey 7 #ffffffff #ff000000
menu color timeout_msg 0 #ffffffff #00000000
menu color timeout 0 #ffffffff #00000000
menu color cmdline 0 #ffffffff #00000000

label live
  menu label Start Linux Mint
  kernel /casper/vmlinuz
  append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz quiet splash --
menu default
label xforcevesa
  menu label Start Linux Mint (compatibility mode)
  kernel /casper/vmlinuz
  append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/mint.seed boot=casper xforcevesa initrd=/casper/initrd.lz ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
label memtest
  menu label Memory Test
  kernel memtest
label local
  menu label Boot from local drive
  localboot 0x80 --------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on treeship-root'


Unknown BootLoader on treeship-swap_1'



=============================== StdErr Messages: ===============================

File descriptor 10 (pipe:[97272]) leaked on lvscan invocation. Parent PID 26814: bash
File descriptor 11 (pipe:[97272]) leaked on lvscan invocation. Parent PID 26814: bash
File descriptor 10 (pipe:[97272]) leaked on lvdisplay invocation. Parent PID 26817: bash
File descriptor 11 (pipe:[97272]) leaked on lvdisplay invocation. Parent PID 26817: bash
  One or more specified logical volume(s) not found.
File descriptor 10 (pipe:[97272]) leaked on lvdisplay invocation. Parent PID 26820: bash
File descriptor 11 (pipe:[97272]) leaked on lvdisplay invocation. Parent PID 26820: bash
  One or more specified logical volume(s) not found.
File descriptor 10 (pipe:[97272]) leaked on lvchange invocation. Parent PID 26142: bash
File descriptor 11 (pipe:[97272]) leaked on lvchange invocation. Parent PID 26142: bash
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/treeship-root': No such file or directory
hexdump: /dev/mapper/treeship-root': No such file or directory
File descriptor 10 (pipe:[97272]) leaked on lvdisplay invocation. Parent PID 26848: bash
File descriptor 11 (pipe:[97272]) leaked on lvdisplay invocation. Parent PID 26848: bash
  One or more specified logical volume(s) not found.
File descriptor 10 (pipe:[97272]) leaked on lvdisplay invocation. Parent PID 26851: bash
File descriptor 11 (pipe:[97272]) leaked on lvdisplay invocation. Parent PID 26851: bash
  One or more specified logical volume(s) not found.
File descriptor 10 (pipe:[97272]) leaked on lvchange invocation. Parent PID 26142: bash
File descriptor 11 (pipe:[97272]) leaked on lvchange invocation. Parent PID 26142: bash
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/treeship-swap_1': No such file or directory
hexdump: /dev/mapper/treeship-swap_1': No such file or directory

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-01-05__21h43 ****************
boot-repair version : 3.02-0ppa23~oneiric
clean version : 3.03-0ppa1~oneiric
internet: connected
clean-gui version : 3.02-0ppa33~oneiric
/usr/share/clean/clean-gui-update.sh: line 153:  4241 Terminated              while true; do
done
python-software-properties version : 0.81.13.1-1linuxmint3
/usr/share/clean/clean-gui-update.sh: line 240: type: lvscan: not found
LVM2 package needed
/usr/share/clean/clean-gui-update.sh: line 234:  4922 Terminated              while true; do
done
Reading package lists...

Reading state information...
The following extra packages will be installed:
watershed
The following NEW packages will be installed:
lvm2 watershed
0 upgraded, 2 newly installed, 0 to remove and 257 not upgraded.
Need to get 421 kB of archives.
After this operation, 1,262 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric/main watershed amd64 5 [11.5 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ oneiric/main lvm2 amd64 2.02.66-4ubuntu3 [410 kB]
dpkg-preconfigure: unable to re-open stdin:
Selecting previously deselected package watershed.
125827 files and directories currently installed.)
Unpacking watershed (from .../archives/watershed_5_amd64.deb) ...
Selecting previously deselected package lvm2.
Unpacking lvm2 (from .../lvm2_2.02.66-4ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Setting up watershed (5) ...
update-initramfs is disabled since running on read-only media
Setting up lvm2 (2.02.66-4ubuntu3) ...
update-initramfs is disabled since running on read-only media
LVBKID /dev/loop0: TYPE="squashfs"
/dev/sda1: SEC_TYPE="msdos" UUID="5320-9E6E" TYPE="vfat"
/dev/sda2: UUID="f9a727ec-44b7-4d8d-8178-440a13fb9027" TYPE="ext2"
/dev/sda3: UUID="ycrA2W-6o3j-a4Fb-Dp0m-0rXJ-RHfb-a1RySi" TYPE="LVM2_member"
/dev/sdb1: LABEL="PENDRIVE" UUID="1DED-310F" TYPE="vfat"
MODPROBE
VGSCAN
File descriptor 10 (pipe:[97272]) leaked on vgscan invocation. Parent PID 4217: /bin/bash
File descriptor 11 (pipe:[97272]) leaked on vgscan invocation. Parent PID 4217: /bin/bash
Reading all physical volumes.  This may take a while...
Found volume group "treeship" using metadata type lvm2
VGCHANGE
File descriptor 10 (pipe:[97272]) leaked on vgchange invocation. Parent PID 4217: /bin/bash
File descriptor 11 (pipe:[97272]) leaked on vgchange invocation. Parent PID 4217: /bin/bash
2 logical volume(s) in volume group "treeship" now active
File descriptor 10 (pipe:[97272]) leaked on lvscan invocation. Parent PID 4217: /bin/bash
File descriptor 11 (pipe:[97272]) leaked on lvscan invocation. Parent PID 4217: /bin/bash
LVSCAN:   ACTIVE            '/dev/treeship/root' [2.72 TiB] inherit
ACTIVE            '/dev/treeship/swap_1' [7.60 GiB] inherit
LIVESESSION is : yes
sda3 is LVM2_member
LVLINE ACTIVE            '/dev/treeship/root' [2.72 TiB] inherit
LVLINE ACTIVE            '/dev/treeship/swap_1' [7.60 GiB] inherit
BYTES_BEFORE_PART[1] (sda) = 34 sectors * 512 bytes = 17408 bytes.
OSPROBER: /dev/mapper/treeship-root:Ubuntu 11.10 (11.10):Ubuntu:linux
BLKID: /dev/loop0: TYPE="squashfs"
/dev/sda1: SEC_TYPE="msdos" UUID="5320-9E6E" TYPE="vfat"
/dev/sda2: UUID="f9a727ec-44b7-4d8d-8178-440a13fb9027" TYPE="ext2"
/dev/sda3: UUID="ycrA2W-6o3j-a4Fb-Dp0m-0rXJ-RHfb-a1RySi" TYPE="LVM2_member"
/dev/sdb1: LABEL="PENDRIVE" UUID="1DED-310F" TYPE="vfat"
/dev/mapper/treeship-root: UUID="6347daa6-6fad-4341-9b87-cf7818690db1" TYPE="ext4"
/dev/mapper/treeship-swap_1: UUID="fd27e451-7edb-4db3-bd05-e568e74c736e" TYPE="swap"
ls: cannot access /dev/mapper/treeship: No such file or directory
ls: cannot access /dev/mapper/treeship: No such file or directory
mapper/treeship-root contains Ubuntu 11.10 (linux)
1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
Total of 1 OS detected on mapper disk.
dir: cannot access /tmp/clean/2012-01-05__21h43boot-repair57/mapper: No such file or directory
dir: cannot access /tmp/clean/2012-01-05__21h43boot-repair57/mapper: No such file or directory

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/mapper/treeship-root doesn't contain a valid partition table
Disk /dev/mapper/treeship-swap_1 doesn't contain a valid partition table
FDISK
Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 2038 MB, 2038431744 bytes
2 heads, 63 sectors/track, 31597 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00cf6d90

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3981311     1990640    c  W95 FAT32 (LBA)

Disk /dev/mapper/treeship-root: 2991.8 GB, 2991834791936 bytes
255 heads, 63 sectors/track, 363736 cylinders, total 5843427328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/treeship-swap_1: 8162 MB, 8162115584 bytes
255 heads, 63 sectors/track, 992 cylinders, total 15941632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
LIST_GPTPART[1] is 1 (sda1 , mapper)
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 2038 MB, 2038431744 bytes
2 heads, 63 sectors/track, 31597 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00cf6d90

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3981311     1990640    c  W95 FAT32 (LBA)

Disk /dev/mapper/treeship-root: 2991.8 GB, 2991834791936 bytes
255 heads, 63 sectors/track, 363736 cylinders, total 5843427328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/treeship-swap_1: 8162 MB, 8162115584 bytes
255 heads, 63 sectors/track, 992 cylinders, total 15941632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000
: [    0.000000] EFI v2.00 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x000000000007f000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x000000000007f000-0x0000000000080000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000080000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x000000000056d000) (4MB)
[    0.000000] EFI: mem05: type=7, attr=0xf, range=[0x000000000056d000-0x0000000001000000) (10MB)
[    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000001000000-0x0000000001100000) (1MB)
[    0.000000] EFI: mem07: type=4, attr=0xf, range=[0x0000000001100000-0x000000000150f000) (4MB)
[    0.000000] EFI: mem08: type=3, attr=0xf, range=[0x000000000150f000-0x0000000001513000) (0MB)
[    0.000000] EFI: mem09: type=4, attr=0xf, range=[0x0000000001513000-0x0000000001554000) (0MB)
[    0.000000] EFI: mem10: type=3, attr=0xf, range=[0x0000000001554000-0x000000000155a000) (0MB)
[    0.000000] EFI: mem11: type=4, attr=0xf, range=[0x000000000155a000-0x000000000155c000) (0MB)
[    0.000000] EFI: mem12: type=3, attr=0xf, range=[0x000000000155c000-0x0000000001564000) (0MB)
[    0.000000] EFI: mem13: type=4, attr=0xf, range=[0x0000000001564000-0x0000000001567000) (0MB)
[    0.000000] EFI: mem14: type=3, attr=0xf, range=[0x0000000001567000-0x0000000001568000) (0MB)
[    0.000000] EFI: mem15: type=4, attr=0xf, range=[0x0000000001568000-0x0000000001569000) (0MB)
[    0.000000] EFI: mem16: type=3, attr=0xf, range=[0x0000000001569000-0x000000000156b000) (0MB)
[    0.000000] EFI: mem17: type=4, attr=0xf, range=[0x000000000156b000-0x0000000001574000) (0MB)
[    0.000000] EFI: mem18: type=3, attr=0xf, range=[0x0000000001574000-0x0000000001576000) (0MB)
[    0.000000] EFI: mem19: type=4, attr=0xf, range=[0x0000000001576000-0x000000000157b000) (0MB)
[    0.000000] EFI: mem20: type=3, attr=0xf, range=[0x000000000157b000-0x000000000157f000) (0MB)
[    0.000000] EFI: mem21: type=4, attr=0xf, range=[0x000000000157f000-0x0000000001585000) (0MB)
[    0.000000] EFI: mem22: type=3, attr=0xf, range=[0x0000000001585000-0x0000000001588000) (0MB)
[    0.000000] EFI: mem23: type=4, attr=0xf, range=[0x0000000001588000-0x0000000001596000) (0MB)
[    0.000000] EFI: mem24: type=3, attr=0xf, range=[0x0000000001596000-0x0000000001598000) (0MB)
[    0.000000] EFI: mem25: type=4, attr=0xf, range=[0x0000000001598000-0x00000000015a0000) (0MB)
[    0.000000] EFI: mem26: type=3, attr=0xf, range=[0x00000000015a0000-0x00000000015a4000) (0MB)
[    0.000000] EFI: mem27: type=4, attr=0xf, range=[0x00000000015a4000-0x00000000015a5000) (0MB)
[    0.000000] EFI: mem28: type=3, attr=0xf, range=[0x00000000015a5000-0x00000000015aa000) (0MB)
[    0.000000] EFI: mem29: type=4, attr=0xf, range=[0x00000000015aa000-0x00000000015b8000) (0MB)
[    0.000000] EFI: mem30: type=3, attr=0xf, range=[0x00000000015b8000-0x00000000015b9000) (0MB)
[    0.000000] EFI: mem31: type=4, attr=0xf, range=[0x00000000015b9000-0x00000000019c1000) (4MB)
[    0.000000] EFI: mem32: type=3, attr=0xf, range=[0x00000000019c1000-0x00000000019c3000) (0MB)
[    0.000000] EFI: mem33: type=4, attr=0xf, range=[0x00000000019c3000-0x00000000019d9000) (0MB)
[    0.000000] EFI: mem34: type=3, attr=0xf, range=[0x00000000019d9000-0x00000000019df000) (0MB)
[    0.000000] EFI: mem35: type=4, attr=0xf, range=[0x00000000019df000-0x00000000019ed000) (0MB)
[    0.000000] EFI: mem36: type=3, attr=0xf, range=[0x00000000019ed000-0x00000000019fb000) (0MB)
[    0.000000] EFI: mem37: type=4, attr=0xf, range=[0x00000000019fb000-0x0000000001a35000) (0MB)
[    0.000000] EFI: mem38: type=3, attr=0xf, range=[0x0000000001a35000-0x0000000001a37000) (0MB)
[    0.000000] EFI: mem39: type=4, attr=0xf, range=[0x0000000001a37000-0x0000000001a40000) (0MB)
[    0.000000] EFI: mem40: type=3, attr=0xf, range=[0x0000000001a40000-0x0000000001a5b000) (0MB)
[    0.000000] EFI: mem41: type=4, attr=0xf, range=[0x0000000001a5b000-0x0000000001a5d000) (0MB)
[    0.000000] EFI: mem42: type=3, attr=0xf, range=[0x0000000001a5d000-0x0000000001a5f000) (0MB)
[    0.000000] EFI: mem43: type=4, attr=0xf, range=[0x0000000001a5f000-0x0000000001a60000) (0MB)
[    0.000000] EFI: mem44: type=3, attr=0xf, range=[0x0000000001a60000-0x0000000001a69000) (0MB)
[    0.000000] EFI: mem45: type=4, attr=0xf, range=[0x0000000001a69000-0x0000000001a6b000) (0MB)
[    0.000000] EFI: mem46: type=3, attr=0xf, range=[0x0000000001a6b000-0x0000000001a7b000) (0MB)
[    0.000000] EFI: mem47: type=4, attr=0xf, range=[0x0000000001a7b000-0x0000000001a7f000) (0MB)
[    0.000000] EFI: mem48: type=3, attr=0xf, range=[0x0000000001a7f000-0x0000000001a84000) (0MB)
[    0.000000] EFI: mem49: type=4, attr=0xf, range=[0x0000000001a84000-0x0000000001a8e000) (0MB)
[    0.000000] EFI: mem50: type=3, attr=0xf, range=[0x0000000001a8e000-0x0000000001a96000) (0MB)
[    0.000000] EFI: mem51: type=4, attr=0xf, range=[0x0000000001a96000-0x0000000001a9b000) (0MB)
[    0.000000] EFI: mem52: type=3, attr=0xf, range=[0x0000000001a9b000-0x0000000001aa3000) (0MB)
[    0.000000] EFI: mem53: type=4, attr=0xf, range=[0x0000000001aa3000-0x0000000001aaf000) (0MB)
[    0.000000] EFI: mem54: type=3, attr=0xf, range=[0x0000000001aaf000-0x0000000001abb000) (0MB)
[    0.000000] EFI: mem55: type=4, attr=0xf, range=[0x0000000001abb000-0x0000000001adb000) (0MB)
[    0.000000] EFI: mem56: type=3, attr=0xf, range=[0x0000000001adb000-0x0000000001add000) (0MB)
[    0.000000] EFI: mem57: type=4, attr=0xf, range=[0x0000000001add000-0x0000000001ae3000) (0MB)
[    0.000000] EFI: mem58: type=3, attr=0xf, range=[0x0000000001ae3000-0x0000000001ae9000) (0MB)
[    0.000000] EFI: mem59: type=4, attr=0xf, range=[0x0000000001ae9000-0x0000000001aef000) (0MB)
[    0.000000] EFI: mem60: type=3, attr=0xf, range=[0x0000000001aef000-0x0000000001af4000) (0MB)
[    0.000000] EFI: mem61: type=4, attr=0xf, range=[0x0000000001af4000-0x0000000001b04000) (0MB)
[    0.000000] EFI: mem62: type=3, attr=0xf, range=[0x0000000001b04000-0x0000000001b43000) (0MB)
[    0.000000] EFI: mem63: type=4, attr=0xf, range=[0x0000000001b43000-0x0000000001b44000) (0MB)
[    0.000000] EFI: mem64: type=3, attr=0xf, range=[0x0000000001b44000-0x0000000001b5a000) (0MB)
[    0.000000] EFI: mem65: type=4, attr=0xf, range=[0x0000000001b5a000-0x0000000001b61000) (0MB)
[    0.000000] EFI: mem66: type=3, attr=0xf, range=[0x0000000001b61000-0x0000000001b6b000) (0MB)
[    0.000000] EFI: mem67: type=4, attr=0xf, range=[0x0000000001b6b000-0x0000000001b71000) (0MB)
[    0.000000] EFI: mem68: type=3, attr=0xf, range=[0x0000000001b71000-0x0000000001b74000) (0MB)
[    0.000000] EFI: mem69: type=4, attr=0xf, range=[0x0000000001b74000-0x0000000001c0a000) (0MB)
[    0.000000] EFI: mem70: type=3, attr=0xf, range=[0x0000000001c0a000-0x0000000001c12000) (0MB)
[    0.000000] EFI: mem71: type=4, attr=0xf, range=[0x0000000001c12000-0x0000000001c15000) (0MB)
[    0.000000] EFI: mem72: type=3, attr=0xf, range=[0x0000000001c15000-0x0000000001c18000) (0MB)
[    0.000000] EFI: mem73: type=4, attr=0xf, range=[0x0000000001c18000-0x0000000001c1b000) (0MB)
[    0.000000] EFI: mem74: type=3, attr=0xf, range=[0x0000000001c1b000-0x0000000001c20000) (0MB)
[    0.000000] EFI: mem75: type=4, attr=0xf, range=[0x0000000001c20000-0x0000000001c3e000) (0MB)
[    0.000000] EFI: mem76: type=3, attr=0xf, range=[0x0000000001c3e000-0x0000000001c41000) (0MB)
[    0.000000] EFI: mem77: type=4, attr=0xf, range=[0x0000000001c41000-0x0000000001c44000) (0MB)
[    0.000000] EFI: mem78: type=3, attr=0xf, range=[0x0000000001c44000-0x0000000001c5d000) (0MB)
[    0.000000] EFI: mem79: type=4, attr=0xf, range=[0x0000000001c5d000-0x0000000001c6e000) (0MB)
[    0.000000] EFI: mem80: type=3, attr=0xf, range=[0x0000000001c6e000-0x0000000001c71000) (0MB)
[    0.000000] EFI: mem81: type=4, attr=0xf, range=[0x0000000001c71000-0x0000000001c73000) (0MB)
[    0.000000] EFI: mem82: type=3, attr=0xf, range=[0x0000000001c73000-0x0000000001c7e000) (0MB)
[    0.000000] EFI: mem83: type=4, attr=0xf, range=[0x0000000001c7e000-0x0000000001c81000) (0MB)
[    0.000000] EFI: mem84: type=3, attr=0xf, range=[0x0000000001c81000-0x0000000001c84000) (0MB)
[    0.000000] EFI: mem85: type=4, attr=0xf, range=[0x0000000001c84000-0x0000000001c88000) (0MB)
[    0.000000] EFI: mem86: type=3, attr=0xf, range=[0x0000000001c88000-0x0000000001c8a000) (0MB)
[    0.000000] EFI: mem87: type=4, attr=0xf, range=[0x0000000001c8a000-0x0000000001c8c000) (0MB)
[    0.000000] EFI: mem88: type=3, attr=0xf, range=[0x0000000001c8c000-0x0000000001c90000) (0MB)
[    0.000000] EFI: mem89: type=4, attr=0xf, range=[0x0000000001c90000-0x0000000001caa000) (0MB)
[    0.000000] EFI: mem90: type=3, attr=0xf, range=[0x0000000001caa000-0x0000000001cae000) (0MB)
[    0.000000] EFI: mem91: type=4, attr=0xf, range=[0x0000000001cae000-0x0000000001cba000) (0MB)
[    0.000000] EFI: mem92: type=3, attr=0xf, range=[0x0000000001cba000-0x0000000001cca000) (0MB)
[    0.000000] EFI: mem93: type=4, attr=0xf, range=[0x0000000001cca000-0x0000000001d6f000) (0MB)
[    0.000000] EFI: mem94: type=3, attr=0xf, range=[0x0000000001d6f000-0x0000000001d74000) (0MB)
[    0.000000] EFI: mem95: type=4, attr=0xf, range=[0x0000000001d74000-0x0000000001d9e000) (0MB)
[    0.000000] EFI: mem96: type=7, attr=0xf, range=[0x0000000001d9e000-0x0000000001da0000) (0MB)
[    0.000000] EFI: mem97: type=3, attr=0xf, range=[0x0000000001da0000-0x0000000001db0000) (0MB)
[    0.000000] EFI: mem98: type=7, attr=0xf, range=[0x0000000001db0000-0x0000000001db4000) (0MB)
[    0.000000] EFI: mem99: type=4, attr=0xf, range=[0x0000000001db4000-0x0000000001dc9000) (0MB)
[    0.000000] EFI: mem100: type=3, attr=0xf, range=[0x0000000001dc9000-0x00000000021d0000) (4MB)
[    0.000000] EFI: mem101: type=4, attr=0xf, range=[0x00000000021d0000-0x00000000025d2000) (4MB)
[    0.000000] EFI: mem102: type=7, attr=0xf, range=[0x00000000025d2000-0x00000000025d3000) (0MB)
[    0.000000] EFI: mem103: type=4, attr=0xf, range=[0x00000000025d3000-0x00000000025d7000) (0MB)
[    0.000000] EFI: mem104: type=7, attr=0xf, range=[0x00000000025d7000-0x00000000025f1000) (0MB)
[    0.000000] EFI: mem105: type=4, attr=0xf, range=[0x00000000025f1000-0x00000000026f1000) (1MB)
[    0.000000] EFI: mem106: type=7, attr=0xf, range=[0x00000000026f1000-0x00000000027a6000) (0MB)
[    0.000000] EFI: mem107: type=4, attr=0xf, range=[0x00000000027a6000-0x00000000028ce000) (1MB)
[    0.000000] EFI: mem108: type=7, attr=0xf, range=[0x00000000028ce000-0x000000000291a000) (0MB)
[    0.000000] EFI: mem109: type=4, attr=0xf, range=[0x000000000291a000-0x0000000003572000) (12MB)
[    0.000000] EFI: mem110: type=1, attr=0xf, range=[0x0000000003572000-0x00000000035e8000) (0MB)
[    0.000000] EFI: mem111: type=4, attr=0xf, range=[0x00000000035e8000-0x00000000037bd000) (1MB)
[    0.000000] EFI: mem112: type=7, attr=0xf, range=[0x00000000037bd000-0x0000000004176000) (9MB)
[    0.000000] EFI: mem113: type=4, attr=0xf, range=[0x0000000004176000-0x0000000004178000) (0MB)
[    0.000000] EFI: mem114: type=7, attr=0xf, range=[0x0000000004178000-0x0000000035966000) (791MB)
[    0.000000] EFI: mem115: type=2, attr=0xf, range=[0x0000000035966000-0x0000000036cab000) (19MB)
[    0.000000] EFI: mem116: type=7, attr=0xf, range=[0x0000000036cab000-0x000000007e649000) (1145MB)
[    0.000000] EFI: mem117: type=2, attr=0xf, range=[0x000000007e649000-0x00000000a7b2b000) (660MB)
[    0.000000] EFI: mem118: type=10, attr=0xf, range=[0x00000000a7b2b000-0x00000000a7b80000) (0MB)
[    0.000000] EFI: mem119: type=0, attr=0xf, range=[0x00000000a7b80000-0x00000000a7cb4000) (1MB)
[    0.000000] EFI: mem120: type=10, attr=0xf, range=[0x00000000a7cb4000-0x00000000a7cc5000) (0MB)
[    0.000000] EFI: mem121: type=0, attr=0xf, range=[0x00000000a7cc5000-0x00000000a7cc8000) (0MB)
[    0.000000] EFI: mem122: type=6, attr=0x800000000000000f, range=[0x00000000a7cc8000-0x00000000a7cd9000) (0MB)
[    0.000000] EFI: mem123: type=5, attr=0x800000000000000f, range=[0x00000000a7cd9000-0x00000000a7cda000) (0MB)
[    0.000000] EFI: mem124: type=6, attr=0x800000000000000f, range=[0x00000000a7cda000-0x00000000a7cdb000) (0MB)
[    0.000000] EFI: mem125: type=7, attr=0xf, range=[0x00000000a7cdb000-0x00000000a7cdc000) (0MB)
[    0.000000] EFI: mem126: type=10, attr=0xf, range=[0x00000000a7cdc000-0x00000000a7ce4000) (0MB)
[    0.000000] EFI: mem127: type=6, attr=0x800000000000000f, range=[0x00000000a7ce4000-0x00000000a7ce5000) (0MB)
[    0.000000] EFI: mem128: type=5, attr=0x800000000000000f, range=[0x00000000a7ce5000-0x00000000a7cf7000) (0MB)
[    0.000000] EFI: mem129: type=6, attr=0x800000000000000f, range=[0x00000000a7cf7000-0x00000000a7d39000) (0MB)
[    0.000000] EFI: mem130: type=5, attr=0x800000000000000f, range=[0x00000000a7d39000-0x00000000a7d45000) (0MB)
[    0.000000] EFI: mem131: type=6, attr=0x800000000000000f, range=[0x00000000a7d45000-0x00000000a7d48000) (0MB)
[    0.000000] EFI: mem132: type=10, attr=0xf, range=[0x00000000a7d48000-0x00000000a7d8b000) (0MB)
[    0.000000] EFI: mem133: type=3, attr=0xf, range=[0x00000000a7d8b000-0x00000000a7ef6000) (1MB)
[    0.000000] EFI: mem134: type=4, attr=0xf, range=[0x00000000a7ef6000-0x00000000a7ef7000) (0MB)
[    0.000000] EFI: mem135: type=3, attr=0xf, range=[0x00000000a7ef7000-0x00000000a7f00000) (0MB)
[    0.000000] EFI: mem136: type=7, attr=0xf, range=[0x0000000100001000-0x000000023f000000) (5103MB)
[    0.000000] EFI: mem137: type=11, attr=0x8000000000000001, range=[0x00000000e0000000-0x00000000f0000000) (256MB)
[    0.000000] EFI: mem138: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] EFI: mem139: type=11, attr=0x8000000000000001, range=[0x00000000fec10000-0x00000000fec11000) (0MB)
[    0.000000] EFI: mem140: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed01000) (0MB)
[    0.000000] EFI: mem141: type=11, attr=0x8000000000000001, range=[0x00000000fed61000-0x00000000fed71000) (0MB)
[    0.000000] EFI: mem142: type=11, attr=0x8000000000000001, range=[0x00000000fed80000-0x00000000fed90000) (0MB)
[    0.000000] EFI: mem143: type=11, attr=0x8000000000000001, range=[0x00000000fef00000-0x0000000100000000) (17MB)
[    1.378849] fb0: EFI VGA frame buffer device
[    2.043106] EFI Variables Facility v0.08 2004-May-17
[    2.363531] fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver
ReadEFI: /dev/sda , N 128 , 0 ,  , PRStart 1024 , PRSize 128
part /dev/sda1 is BISEFI
part /dev/sda2 is notBISEFI
TABLE_TYPE of sda is EFI
sda1 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda1, no-os, gpt, BISEFI, no-fstab.
sda2 : sda, is-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda2, no-os, no-gpt, notBISEFI, no-fstab.
PARTED: Model: ATA WDC WD30EZRX-00A (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
1      17.4kB  200MB   200MB   fat16              boot
2      200MB   456MB   256MB   ext2
3      456MB   3001GB  3000GB                     lvm


Model: USB 2.0  (scsi)
Disk /dev/sdb: 2038MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  2038MB  2038MB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/treeship-swap_1: 8162MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
1      0.00B  8162MB  8162MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/treeship-root: 2992GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  2992GB  2992GB  ext4
MOUNT /cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mint/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mint)
/dev/sda1 on /mnt/clean/sda1 type vfat (rw)
/dev/sda2 on /mnt/clean/sda2 type ext2 (rw)
/sys/block/dm-0:  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1:  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev:  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dm-0 dm-1 dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout treeship uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 usbmon8 usbmon9 vga_arbiter zero
/dev/mapper:  control treeship-root treeship-swap_1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/mapper/treeship-root doesn't contain a valid partition table
Disk /dev/mapper/treeship-swap_1 doesn't contain a valid partition table
DF Filesystem    Type    Size  Used Avail Use% Mounted on
/cow     overlayfs    3.8G  249M  3.5G   7% /
udev      devtmpfs    3.8G   12K  3.8G   1% /dev
tmpfs        tmpfs    1.5G  812K  1.5G   1% /run
/dev/sdb1     vfat    1.9G  634M  1.3G  33% /cdrom
/dev/loop0
squashfs    605M  605M     0 100% /rofs
tmpfs        tmpfs    3.8G  120K  3.8G   1% /tmp
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    3.8G  428K  3.8G   1% /run/shm
/dev/sda1     vfat    191M  136K  191M   1% /mnt/clean/sda1
/dev/sda2     ext2    229M   25M  193M  12% /mnt/clean/sda2
FDISK
Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 2038 MB, 2038431744 bytes
2 heads, 63 sectors/track, 31597 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00cf6d90

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3981311     1990640    c  W95 FAT32 (LBA)

Disk /dev/mapper/treeship-root: 2991.8 GB, 2991834791936 bytes
255 heads, 63 sectors/track, 363736 cylinders, total 5843427328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/treeship-swap_1: 8162 MB, 8162115584 bytes
255 heads, 63 sectors/track, 992 cylinders, total 15941632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000
Logs saved into /var/log/clean/log/2012-01-05__21h43boot-repair57
combobox_ostoboot_bydefault_fillin
************************Before mainwindow appear
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, MBR_ACTION restore REINSTALL_POSSIBLE no PURGE_POSSIBLE  UNHIDEBOOT_ACTION yes (10.s) PART_TO_REINSTALL_GRUB  () PART_TO_REINSTALL_GRUB_PURGE  () FORCE_GRUB  NOFORCE_DISK  REMOVABLEDISK  UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART  ()  ()
/usr/share/clean/clean-gui-update.sh: line 48:  6512 Terminated              while true; do
done
internet: connected
************************Before Repairing
FSCK_ACTION no PASTEBIN_ACTION yes
customrepair, MBR_ACTION restore REINSTALL_POSSIBLE no PURGE_POSSIBLE  UNHIDEBOOT_ACTION yes (10.s) PART_TO_REINSTALL_GRUB  () PART_TO_REINSTALL_GRUB_PURGE  () FORCE_GRUB  NOFORCE_DISK  REMOVABLEDISK  UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART  ()  ()
Freed space function
We will restore the MBR_TO_RESTORE : sda (mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 1 boot on

                                                                          
Information: You may need to update /etc/fstab.

Unhide boot menu (10 seconds) if Wubi detected
internet: connected
/usr/share/clean/bootrepair-actions.sh: line 83: 12713 Terminated              while true; do
done
dpkg-preconfigure: unable to re-open stdin:

```

---

### Post by darkod on 2012-01-05
Before you continue, one question: What is your purpose of using LVM?
In your case the root partition is taking all of the 3TB anyway (except small swap partition). No point in using LVM as such.
LVM is used if you plan to create more partitions on it, so you can dynamically resize them later.

Otherwise, the first thing to note is that /dev/sda has the syslinux bootloader, not ubuntu's grub2. It seems it was never installed. You would have to fix that, but in case you decide against using LVM you might as well do a new install.

Also, is there a particular reason you are using EFI boot and not BIOS boot?

---

### Post by rented on 2012-01-06
Thanks for the response. 

Regarding LVM, my thinking was that I wanted the flexibility of splitting it into smaller partitions later. For instance OS & data partitions. I do not know how much space ubuntu and the services I will install take, so I did not partiton during install. Does that make sense? If if makes things simpler down the line then I can forego LVM.

Regarding EFI, well I don't recall ever having a choice. But I do recall reading that it was essential for proper 3TB support so I was quite happy to see it was supported :)

Regarding syslinux, how can I fix that? I certainly never chose to use syslinux. I made a bootable USB drive and put the ISO on there, and I think that uses syslinux right? Appart from that, the ubuntu installer must have installed it. Or maybe the boot-script is confused? (I "usb-booted" into Linux Mint to run the script).

---

### Post by darkod on 2012-01-06
LVM makes perfect sense, but if I am not mistaken from the results in the script it seems that the auto install made the root partition take all of the LVM (and the disk with it). Usually you would create your root partition for example as 10GB, and grow when needed. That would also let you create other Logical Volumes in the LVM space that is not used.
Like this you don't have any space for a new LV unless you shrink the root LV. Even though LVM works fine it's always best to adoid shrinking LVs and partitions.

But I think you can select the size of the root LV only when doing the manual partitioning, the auto methods did as it did.

About the grub2 issue. You do need to try to add it. You could do that using a live cd of ubuntu desktop for example. I don't think it can work with Mint cd, but I have never tried.

Anyway, the procedure would be to chroot into the install, having an LVM makes it little bit complicated, but it can be done. The proccedure would be something like:

First to be able to work with LVM in ubuntu live mode you need to add the package:
sudo apt-get install lvm2

Then to activate the LVM:
sudo vgchange -a y
To scan for the LVs:
sudo lvscan
That will show you the LVs like /dev/VGname/LVname. Now you start mounting it, and you also need to mount the separate /boot partition you have:

```
sudo mount /dev/VGname/LVname /mnt
sudo mount /dev/sda2 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the server install. Try to recreate the grub config files and install it to the MBR:
```
grub-mkconfig
grub-install /dev/sda
```

If that doesn't work or grub2 package isn't even install properly, you can try removing it completely and installing new with:
```
apt-get --purge remove grub-pc
apt-get install grub-pc
grub-mkconfig
grub-install /dev/sda
```

That should do it. Exit the chroot, unmount and restart to check if it helped:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt/boot
sudo umount /mnt
```

---

### Post by rented on 2012-01-06
Thanks for your detailed help darkod! However, I decided to do a fresh install yet again, this time without LVM. Lo and behold it worked. The last thing the installer did was install grub2 (which I don't recall seeing it doing the previous times). It now boots up just fine. There must be some incompatibility with LVM, where it doesn't install the boot loader properly on my setup.

Having one large 3TB partition is not optimal I guess, but this is a home server for stuff like squeezebox, general file server, etc. so it's no biggie!

What is more important is getting the partitions aligned to 4096, as this is an ADF disk. But that's a separate issue.

Thanks again for the help!

---

### Post by rented on 2012-01-07
Well, it seems I spoke too soon :(

I did have a booting installation once, as mentioned above. However, all partitions were misaligned, so I cleared the disk and created the partitions manually with gdisk. The partitions were exactly the same as the ones created by the working installation, except that they were aligned properly. During installation, I obviously chose the created partitions and chose mount points, filesystem, etc..

It installed without errors, but after the installation completed and I rebooted, I'm back to square one. It restarts the machine after "initrd	/boot/initrd.img-3.0.0-12-server".

I tried to get back to a working installation again, by clearing the disk and letting the installer create the partitions (Guided use entire disk, no lVM). Just as I did the one time it worked earlier. I've tried probably 5 or six times but no luck. I've tried the boot repair tool, but that just resulted in no grub menu (just the grub prompt).

Something that may be a hint, is that the one time it worked, the grub menu took up the whole screen, while every other time it sits in the middle of the screen and takes up maybe a third of the screen. When it worked, I just saw the menu for a second so couldn't see if it was a graphical menu or a text menu, but the non-working-menu is def. text.

I'm starting to give up. Two full days seems enough somehow...

Here's a new Boot-info-summary.txt, this time run from Ubuntu LiveCD.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 34 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sda1 has 0 
                       sectors.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 15528 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34        39,096        39,063 EFI System partition
/dev/sda2          39,097 2,623,356,593 2,623,317,497 Data partition (Windows/Linux)
/dev/sda3   2,623,356,594 2,639,307,646    15,951,053 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2038 MB, 2038431744 bytes
2 heads, 63 sectors/track, 31597 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,981,311     3,981,280   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A57F-43C8                              vfat       
/dev/sda2        324d93ec-51d6-4847-9718-bb68b7e86f94   ext4       
/dev/sda3        c35f9613-e126-4219-ad15-e21b4521f2c6   swap       
/dev/sdb1        15F9-3045                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root 324d93ec-51d6-4847-9718-bb68b7e86f94
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root 324d93ec-51d6-4847-9718-bb68b7e86f94
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu, with Linux 3.0.0-12-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root 324d93ec-51d6-4847-9718-bb68b7e86f94
	linux	/boot/vmlinuz-3.0.0-12-server root=UUID=324d93ec-51d6-4847-9718-bb68b7e86f94 ro   
	initrd	/boot/initrd.img-3.0.0-12-server
}
menuentry 'Ubuntu, with Linux 3.0.0-12-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root 324d93ec-51d6-4847-9718-bb68b7e86f94
	echo	'Loading Linux 3.0.0-12-server ...'
	linux	/boot/vmlinuz-3.0.0-12-server root=UUID=324d93ec-51d6-4847-9718-bb68b7e86f94 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root 324d93ec-51d6-4847-9718-bb68b7e86f94
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root 324d93ec-51d6-4847-9718-bb68b7e86f94
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=324d93ec-51d6-4847-9718-bb68b7e86f94 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=A57F-43C8  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=c35f9613-e126-4219-ad15-e21b4521f2c6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 120.143650532 = 129.003262464  boot/grub/grub.cfg                             1
   0.929615498 = 0.998167040    boot/initrd.img-3.0.0-12-server                4
   0.233974934 = 0.251228672    boot/vmlinuz-3.0.0-12-server                   2
   0.233974934 = 0.251228672    vmlinuz                                        2

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

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)


ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-01-07__12h31 ****************
boot-repair version : 3.04-0ppa2~oneiric
boot-sav version : 3.04-0ppa1~oneiric
internet: connected
boot-sav-gui version : 3.04-0ppa5~oneiric
/usr/share/boot-sav/clean-gui-update.sh: line 190:  4289 Terminated              while true; do
done
/usr/share/boot-sav/clean-gui-update.sh: line 200: type: os-uninstaller: not found
/usr/share/boot-sav/clean-gui-update.sh: line 200: type: clean-ubiquity: not found
python-software-properties version : 0.81.10
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/Release  Unable to find expected entry 'restricted/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/ oneiric/main i386 Packages (/var/lib/apt/lists/Ubuntu%2011.10%20%5fOneiric%20Ocelot%5f%20-%20Release%20amd64%20(20111012)_dists_oneiric_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
LIVESESSION is : yes
BYTES_BEFORE_PART[1] (sda) = 34 sectors * 512 bytes = 17408 bytes.
OSPROBER: /dev/sda2:Ubuntu 11.10 (11.10):Ubuntu:linux
BLKID: /dev/loop0: TYPE="squashfs"
/dev/sda1: SEC_TYPE="msdos" UUID="A57F-43C8" TYPE="vfat"
/dev/sda2: UUID="324d93ec-51d6-4847-9718-bb68b7e86f94" TYPE="ext4"
/dev/sda3: UUID="c35f9613-e126-4219-ad15-e21b4521f2c6" TYPE="swap"
/dev/sdb1: LABEL="PENDRIVE" UUID="15F9-3045" TYPE="vfat"
sda2 contains Ubuntu 11.10 (linux)
1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
Total of 1 OS detected on sda disk.
sda contains minimum one OS
EFI_OF_PART[2]  (, )

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

FDISK
Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 2038 MB, 2038431744 bytes
2 heads, 63 sectors/track, 31597 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00cf6d90

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3981311     1990640    c  W95 FAT32 (LBA)

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
LIST_GPTPART[1] is 1 (sda1 , sda)
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 2038 MB, 2038431744 bytes
2 heads, 63 sectors/track, 31597 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00cf6d90

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3981311     1990640    c  W95 FAT32 (LBA)
: [    0.000000] EFI v2.00 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x000000000007f000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x000000000007f000-0x0000000000080000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000080000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x000000000056d000) (4MB)
[    0.000000] EFI: mem05: type=7, attr=0xf, range=[0x000000000056d000-0x0000000001000000) (10MB)
[    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000001000000-0x0000000001100000) (1MB)
[    0.000000] EFI: mem07: type=4, attr=0xf, range=[0x0000000001100000-0x000000000150f000) (4MB)
[    0.000000] EFI: mem08: type=3, attr=0xf, range=[0x000000000150f000-0x0000000001513000) (0MB)
[    0.000000] EFI: mem09: type=4, attr=0xf, range=[0x0000000001513000-0x0000000001554000) (0MB)
[    0.000000] EFI: mem10: type=3, attr=0xf, range=[0x0000000001554000-0x000000000155a000) (0MB)
[    0.000000] EFI: mem11: type=4, attr=0xf, range=[0x000000000155a000-0x000000000155c000) (0MB)
[    0.000000] EFI: mem12: type=3, attr=0xf, range=[0x000000000155c000-0x0000000001564000) (0MB)
[    0.000000] EFI: mem13: type=4, attr=0xf, range=[0x0000000001564000-0x0000000001567000) (0MB)
[    0.000000] EFI: mem14: type=3, attr=0xf, range=[0x0000000001567000-0x0000000001568000) (0MB)
[    0.000000] EFI: mem15: type=4, attr=0xf, range=[0x0000000001568000-0x0000000001569000) (0MB)
[    0.000000] EFI: mem16: type=3, attr=0xf, range=[0x0000000001569000-0x000000000156b000) (0MB)
[    0.000000] EFI: mem17: type=4, attr=0xf, range=[0x000000000156b000-0x0000000001574000) (0MB)
[    0.000000] EFI: mem18: type=3, attr=0xf, range=[0x0000000001574000-0x0000000001576000) (0MB)
[    0.000000] EFI: mem19: type=4, attr=0xf, range=[0x0000000001576000-0x000000000157b000) (0MB)
[    0.000000] EFI: mem20: type=3, attr=0xf, range=[0x000000000157b000-0x000000000157f000) (0MB)
[    0.000000] EFI: mem21: type=4, attr=0xf, range=[0x000000000157f000-0x0000000001585000) (0MB)
[    0.000000] EFI: mem22: type=3, attr=0xf, range=[0x0000000001585000-0x0000000001588000) (0MB)
[    0.000000] EFI: mem23: type=4, attr=0xf, range=[0x0000000001588000-0x0000000001596000) (0MB)
[    0.000000] EFI: mem24: type=3, attr=0xf, range=[0x0000000001596000-0x0000000001598000) (0MB)
[    0.000000] EFI: mem25: type=4, attr=0xf, range=[0x0000000001598000-0x00000000015a0000) (0MB)
[    0.000000] EFI: mem26: type=3, attr=0xf, range=[0x00000000015a0000-0x00000000015a4000) (0MB)
[    0.000000] EFI: mem27: type=4, attr=0xf, range=[0x00000000015a4000-0x00000000015a5000) (0MB)
[    0.000000] EFI: mem28: type=3, attr=0xf, range=[0x00000000015a5000-0x00000000015aa000) (0MB)
[    0.000000] EFI: mem29: type=4, attr=0xf, range=[0x00000000015aa000-0x00000000015b8000) (0MB)
[    0.000000] EFI: mem30: type=3, attr=0xf, range=[0x00000000015b8000-0x00000000015b9000) (0MB)
[    0.000000] EFI: mem31: type=4, attr=0xf, range=[0x00000000015b9000-0x00000000019c1000) (4MB)
[    0.000000] EFI: mem32: type=3, attr=0xf, range=[0x00000000019c1000-0x00000000019c3000) (0MB)
[    0.000000] EFI: mem33: type=4, attr=0xf, range=[0x00000000019c3000-0x00000000019d9000) (0MB)
[    0.000000] EFI: mem34: type=3, attr=0xf, range=[0x00000000019d9000-0x00000000019df000) (0MB)
[    0.000000] EFI: mem35: type=4, attr=0xf, range=[0x00000000019df000-0x00000000019ed000) (0MB)
[    0.000000] EFI: mem36: type=3, attr=0xf, range=[0x00000000019ed000-0x00000000019fb000) (0MB)
[    0.000000] EFI: mem37: type=4, attr=0xf, range=[0x00000000019fb000-0x0000000001a35000) (0MB)
[    0.000000] EFI: mem38: type=3, attr=0xf, range=[0x0000000001a35000-0x0000000001a37000) (0MB)
[    0.000000] EFI: mem39: type=4, attr=0xf, range=[0x0000000001a37000-0x0000000001a40000) (0MB)
[    0.000000] EFI: mem40: type=3, attr=0xf, range=[0x0000000001a40000-0x0000000001a5b000) (0MB)
[    0.000000] EFI: mem41: type=4, attr=0xf, range=[0x0000000001a5b000-0x0000000001a5d000) (0MB)
[    0.000000] EFI: mem42: type=3, attr=0xf, range=[0x0000000001a5d000-0x0000000001a5f000) (0MB)
[    0.000000] EFI: mem43: type=4, attr=0xf, range=[0x0000000001a5f000-0x0000000001a60000) (0MB)
[    0.000000] EFI: mem44: type=3, attr=0xf, range=[0x0000000001a60000-0x0000000001a69000) (0MB)
[    0.000000] EFI: mem45: type=4, attr=0xf, range=[0x0000000001a69000-0x0000000001a6b000) (0MB)
[    0.000000] EFI: mem46: type=3, attr=0xf, range=[0x0000000001a6b000-0x0000000001a7b000) (0MB)
[    0.000000] EFI: mem47: type=4, attr=0xf, range=[0x0000000001a7b000-0x0000000001a7f000) (0MB)
[    0.000000] EFI: mem48: type=3, attr=0xf, range=[0x0000000001a7f000-0x0000000001a84000) (0MB)
[    0.000000] EFI: mem49: type=4, attr=0xf, range=[0x0000000001a84000-0x0000000001a8e000) (0MB)
[    0.000000] EFI: mem50: type=3, attr=0xf, range=[0x0000000001a8e000-0x0000000001a96000) (0MB)
[    0.000000] EFI: mem51: type=4, attr=0xf, range=[0x0000000001a96000-0x0000000001a9b000) (0MB)
[    0.000000] EFI: mem52: type=3, attr=0xf, range=[0x0000000001a9b000-0x0000000001aa3000) (0MB)
[    0.000000] EFI: mem53: type=4, attr=0xf, range=[0x0000000001aa3000-0x0000000001aaf000) (0MB)
[    0.000000] EFI: mem54: type=3, attr=0xf, range=[0x0000000001aaf000-0x0000000001abb000) (0MB)
[    0.000000] EFI: mem55: type=4, attr=0xf, range=[0x0000000001abb000-0x0000000001adb000) (0MB)
[    0.000000] EFI: mem56: type=3, attr=0xf, range=[0x0000000001adb000-0x0000000001add000) (0MB)
[    0.000000] EFI: mem57: type=4, attr=0xf, range=[0x0000000001add000-0x0000000001ae3000) (0MB)
[    0.000000] EFI: mem58: type=3, attr=0xf, range=[0x0000000001ae3000-0x0000000001ae9000) (0MB)
[    0.000000] EFI: mem59: type=4, attr=0xf, range=[0x0000000001ae9000-0x0000000001aef000) (0MB)
[    0.000000] EFI: mem60: type=3, attr=0xf, range=[0x0000000001aef000-0x0000000001af4000) (0MB)
[    0.000000] EFI: mem61: type=4, attr=0xf, range=[0x0000000001af4000-0x0000000001b04000) (0MB)
[    0.000000] EFI: mem62: type=3, attr=0xf, range=[0x0000000001b04000-0x0000000001b43000) (0MB)
[    0.000000] EFI: mem63: type=4, attr=0xf, range=[0x0000000001b43000-0x0000000001b44000) (0MB)
[    0.000000] EFI: mem64: type=3, attr=0xf, range=[0x0000000001b44000-0x0000000001b5a000) (0MB)
[    0.000000] EFI: mem65: type=4, attr=0xf, range=[0x0000000001b5a000-0x0000000001b61000) (0MB)
[    0.000000] EFI: mem66: type=3, attr=0xf, range=[0x0000000001b61000-0x0000000001b6b000) (0MB)
[    0.000000] EFI: mem67: type=4, attr=0xf, range=[0x0000000001b6b000-0x0000000001b71000) (0MB)
[    0.000000] EFI: mem68: type=3, attr=0xf, range=[0x0000000001b71000-0x0000000001b74000) (0MB)
[    0.000000] EFI: mem69: type=4, attr=0xf, range=[0x0000000001b74000-0x0000000001c0a000) (0MB)
[    0.000000] EFI: mem70: type=3, attr=0xf, range=[0x0000000001c0a000-0x0000000001c12000) (0MB)
[    0.000000] EFI: mem71: type=4, attr=0xf, range=[0x0000000001c12000-0x0000000001c15000) (0MB)
[    0.000000] EFI: mem72: type=3, attr=0xf, range=[0x0000000001c15000-0x0000000001c18000) (0MB)
[    0.000000] EFI: mem73: type=4, attr=0xf, range=[0x0000000001c18000-0x0000000001c1b000) (0MB)
[    0.000000] EFI: mem74: type=3, attr=0xf, range=[0x0000000001c1b000-0x0000000001c20000) (0MB)
[    0.000000] EFI: mem75: type=4, attr=0xf, range=[0x0000000001c20000-0x0000000001c3e000) (0MB)
[    0.000000] EFI: mem76: type=3, attr=0xf, range=[0x0000000001c3e000-0x0000000001c41000) (0MB)
[    0.000000] EFI: mem77: type=4, attr=0xf, range=[0x0000000001c41000-0x0000000001c44000) (0MB)
[    0.000000] EFI: mem78: type=3, attr=0xf, range=[0x0000000001c44000-0x0000000001c5d000) (0MB)
[    0.000000] EFI: mem79: type=4, attr=0xf, range=[0x0000000001c5d000-0x0000000001c6e000) (0MB)
[    0.000000] EFI: mem80: type=3, attr=0xf, range=[0x0000000001c6e000-0x0000000001c71000) (0MB)
[    0.000000] EFI: mem81: type=4, attr=0xf, range=[0x0000000001c71000-0x0000000001c73000) (0MB)
[    0.000000] EFI: mem82: type=3, attr=0xf, range=[0x0000000001c73000-0x0000000001c7e000) (0MB)
[    0.000000] EFI: mem83: type=4, attr=0xf, range=[0x0000000001c7e000-0x0000000001c81000) (0MB)
[    0.000000] EFI: mem84: type=3, attr=0xf, range=[0x0000000001c81000-0x0000000001c84000) (0MB)
[    0.000000] EFI: mem85: type=4, attr=0xf, range=[0x0000000001c84000-0x0000000001c88000) (0MB)
[    0.000000] EFI: mem86: type=3, attr=0xf, range=[0x0000000001c88000-0x0000000001c8a000) (0MB)
[    0.000000] EFI: mem87: type=4, attr=0xf, range=[0x0000000001c8a000-0x0000000001c8c000) (0MB)
[    0.000000] EFI: mem88: type=3, attr=0xf, range=[0x0000000001c8c000-0x0000000001c90000) (0MB)
[    0.000000] EFI: mem89: type=4, attr=0xf, range=[0x0000000001c90000-0x0000000001caa000) (0MB)
[    0.000000] EFI: mem90: type=3, attr=0xf, range=[0x0000000001caa000-0x0000000001cae000) (0MB)
[    0.000000] EFI: mem91: type=4, attr=0xf, range=[0x0000000001cae000-0x0000000001cba000) (0MB)
[    0.000000] EFI: mem92: type=3, attr=0xf, range=[0x0000000001cba000-0x0000000001cca000) (0MB)
[    0.000000] EFI: mem93: type=4, attr=0xf, range=[0x0000000001cca000-0x0000000001d6f000) (0MB)
[    0.000000] EFI: mem94: type=3, attr=0xf, range=[0x0000000001d6f000-0x0000000001d74000) (0MB)
[    0.000000] EFI: mem95: type=4, attr=0xf, range=[0x0000000001d74000-0x0000000001d9f000) (0MB)
[    0.000000] EFI: mem96: type=7, attr=0xf, range=[0x0000000001d9f000-0x0000000001da0000) (0MB)
[    0.000000] EFI: mem97: type=3, attr=0xf, range=[0x0000000001da0000-0x0000000001db0000) (0MB)
[    0.000000] EFI: mem98: type=7, attr=0xf, range=[0x0000000001db0000-0x0000000001db4000) (0MB)
[    0.000000] EFI: mem99: type=4, attr=0xf, range=[0x0000000001db4000-0x0000000001dc9000) (0MB)
[    0.000000] EFI: mem100: type=3, attr=0xf, range=[0x0000000001dc9000-0x00000000021d0000) (4MB)
[    0.000000] EFI: mem101: type=4, attr=0xf, range=[0x00000000021d0000-0x00000000025d2000) (4MB)
[    0.000000] EFI: mem102: type=7, attr=0xf, range=[0x00000000025d2000-0x00000000025d3000) (0MB)
[    0.000000] EFI: mem103: type=4, attr=0xf, range=[0x00000000025d3000-0x00000000025d6000) (0MB)
[    0.000000] EFI: mem104: type=7, attr=0xf, range=[0x00000000025d6000-0x00000000025f0000) (0MB)
[    0.000000] EFI: mem105: type=4, attr=0xf, range=[0x00000000025f0000-0x00000000026f0000) (1MB)
[    0.000000] EFI: mem106: type=7, attr=0xf, range=[0x00000000026f0000-0x00000000027a6000) (0MB)
[    0.000000] EFI: mem107: type=4, attr=0xf, range=[0x00000000027a6000-0x00000000028ce000) (1MB)
[    0.000000] EFI: mem108: type=7, attr=0xf, range=[0x00000000028ce000-0x000000000291a000) (0MB)
[    0.000000] EFI: mem109: type=4, attr=0xf, range=[0x000000000291a000-0x0000000003573000) (12MB)
[    0.000000] EFI: mem110: type=1, attr=0xf, range=[0x0000000003573000-0x00000000035e9000) (0MB)
[    0.000000] EFI: mem111: type=4, attr=0xf, range=[0x00000000035e9000-0x00000000037be000) (1MB)
[    0.000000] EFI: mem112: type=7, attr=0xf, range=[0x00000000037be000-0x0000000004177000) (9MB)
[    0.000000] EFI: mem113: type=4, attr=0xf, range=[0x0000000004177000-0x0000000004178000) (0MB)
[    0.000000] EFI: mem114: type=7, attr=0xf, range=[0x0000000004178000-0x00000000047c5000) (6MB)
[    0.000000] EFI: mem115: type=4, attr=0xf, range=[0x00000000047c5000-0x00000000047c6000) (0MB)
[    0.000000] EFI: mem116: type=7, attr=0xf, range=[0x00000000047c6000-0x000000003642a000) (796MB)
[    0.000000] EFI: mem117: type=2, attr=0xf, range=[0x000000003642a000-0x000000003720d000) (13MB)
[    0.000000] EFI: mem118: type=7, attr=0xf, range=[0x000000003720d000-0x000000007e649000) (1140MB)
[    0.000000] EFI: mem119: type=2, attr=0xf, range=[0x000000007e649000-0x00000000a7b2b000) (660MB)
[    0.000000] EFI: mem120: type=10, attr=0xf, range=[0x00000000a7b2b000-0x00000000a7b80000) (0MB)
[    0.000000] EFI: mem121: type=0, attr=0xf, range=[0x00000000a7b80000-0x00000000a7cb4000) (1MB)
[    0.000000] EFI: mem122: type=10, attr=0xf, range=[0x00000000a7cb4000-0x00000000a7cc5000) (0MB)
[    0.000000] EFI: mem123: type=0, attr=0xf, range=[0x00000000a7cc5000-0x00000000a7cc8000) (0MB)
[    0.000000] EFI: mem124: type=6, attr=0x800000000000000f, range=[0x00000000a7cc8000-0x00000000a7cd9000) (0MB)
[    0.000000] EFI: mem125: type=5, attr=0x800000000000000f, range=[0x00000000a7cd9000-0x00000000a7cda000) (0MB)
[    0.000000] EFI: mem126: type=6, attr=0x800000000000000f, range=[0x00000000a7cda000-0x00000000a7cdb000) (0MB)
[    0.000000] EFI: mem127: type=7, attr=0xf, range=[0x00000000a7cdb000-0x00000000a7cdc000) (0MB)
[    0.000000] EFI: mem128: type=10, attr=0xf, range=[0x00000000a7cdc000-0x00000000a7ce4000) (0MB)
[    0.000000] EFI: mem129: type=6, attr=0x800000000000000f, range=[0x00000000a7ce4000-0x00000000a7ce5000) (0MB)
[    0.000000] EFI: mem130: type=5, attr=0x800000000000000f, range=[0x00000000a7ce5000-0x00000000a7cf7000) (0MB)
[    0.000000] EFI: mem131: type=6, attr=0x800000000000000f, range=[0x00000000a7cf7000-0x00000000a7d39000) (0MB)
[    0.000000] EFI: mem132: type=5, attr=0x800000000000000f, range=[0x00000000a7d39000-0x00000000a7d45000) (0MB)
[    0.000000] EFI: mem133: type=6, attr=0x800000000000000f, range=[0x00000000a7d45000-0x00000000a7d48000) (0MB)
[    0.000000] EFI: mem134: type=10, attr=0xf, range=[0x00000000a7d48000-0x00000000a7d8b000) (0MB)
[    0.000000] EFI: mem135: type=3, attr=0xf, range=[0x00000000a7d8b000-0x00000000a7ef6000) (1MB)
[    0.000000] EFI: mem136: type=4, attr=0xf, range=[0x00000000a7ef6000-0x00000000a7ef7000) (0MB)
[    0.000000] EFI: mem137: type=3, attr=0xf, range=[0x00000000a7ef7000-0x00000000a7f00000) (0MB)
[    0.000000] EFI: mem138: type=7, attr=0xf, range=[0x0000000100001000-0x000000023f000000) (5103MB)
[    0.000000] EFI: mem139: type=11, attr=0x8000000000000001, range=[0x00000000e0000000-0x00000000f0000000) (256MB)
[    0.000000] EFI: mem140: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] EFI: mem141: type=11, attr=0x8000000000000001, range=[0x00000000fec10000-0x00000000fec11000) (0MB)
[    0.000000] EFI: mem142: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed01000) (0MB)
[    0.000000] EFI: mem143: type=11, attr=0x8000000000000001, range=[0x00000000fed61000-0x00000000fed71000) (0MB)
[    0.000000] EFI: mem144: type=11, attr=0x8000000000000001, range=[0x00000000fed80000-0x00000000fed90000) (0MB)
[    0.000000] EFI: mem145: type=11, attr=0x8000000000000001, range=[0x00000000fef00000-0x0000000100000000) (17MB)
[    6.752258] fb0: EFI VGA frame buffer device
[    7.115018] EFI Variables Facility v0.08 2004-May-17
[    7.944665] fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver
ReadEFI: /dev/sda , N 128 , 0 ,  , PRStart 1024 , PRSize 128
part /dev/sda1 is BISEFI
part /dev/sda2 is notBISEFI
TABLE_TYPE of sda is EFI
sda1 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/boot-sav/sda1, no-os, gpt, BISEFI, no-fstab.
sda2 : sda, not-sepboot, grub, aptget, 64, with boot, /mnt/boot-sav/sda2, with-os, no-gpt, notBISEFI, fstab-efi.
PARTED: Model: ATA WDC WD30EZRX-00A (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      17.4kB  20.0MB  20.0MB  fat16                 boot
2      20.0MB  2992GB  2992GB  ext4
3      2992GB  3001GB  8167MB  linux-swap(v1)


Model: USB 2.0  (scsi)
Disk /dev/sdb: 2038MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  2038MB  2038MB  primary  fat32        boot, lba
MOUNT /cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type ext4 (rw)
/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev:  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 usbmon8 usbmon9 vga_arbiter zero
/dev/mapper:  control

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

DF Filesystem    Type    Size  Used Avail Use% Mounted on
/cow     overlayfs    3.8G  124M  3.6G   4% /
udev      devtmpfs    3.8G   12K  3.8G   1% /dev
tmpfs        tmpfs    1.5G  804K  1.5G   1% /run
/dev/sdb1     vfat    1.9G  697M  1.3G  36% /cdrom
/dev/loop0
squashfs    663M  663M     0 100% /rofs
tmpfs        tmpfs    3.8G   76K  3.8G   1% /tmp
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    3.8G  216K  3.8G   1% /run/shm
/dev/sda1     vfat     19M  129K   19M   1% /mnt/boot-sav/sda1
/dev/sda2     ext4    2.7T  1.3G  2.6T   1% /mnt/boot-sav/sda2
FDISK
Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 2038 MB, 2038431744 bytes
2 heads, 63 sectors/track, 31597 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00cf6d90

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3981311     1990640    c  W95 FAT32 (LBA)
Logs saved into /mnt/boot-sav/sda2/var/log/boot-sav/log/2012-01-07__12h31boot-repair20
combobox_ostoboot_bydefault_fillin
Order Linux according to their /boot type noorder
set_checkbutton_reinstall_grub
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda2
efi_show_hide 2 (no-gpt)
combobox_efi_fillin sda2
************************Before mainwindow appear
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, MBR_ACTION purge REINSTALL_POSSIBLE no PURGE_POSSIBLE yes UNHIDEBOOT_ACTION yes (10.s) PART_TO_REINSTALL_GRUB  () PART_TO_REINSTALL_GRUB_PURGE 2 (sda2) FORCE_GRUB no NOFORCE_DISK  REMOVABLEDISK  UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sda1) grub-efi (sda1)
/usr/share/boot-sav/clean-gui-update.sh: line 40:  5009 Terminated              while true; do
done
RETOURCOMBO_purge_grub : sda2 (Ubuntu 11.10)
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda2
efi_show_hide 2 (no-gpt)
combobox_efi_fillin sda2
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda1
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
set_checkbutton_reinstall_grub
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda2
efi_show_hide 2 (no-gpt)
combobox_efi_fillin sda2
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda1
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda1
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
set_checkbutton_reinstall_grub
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda2
efi_show_hide 2 (no-gpt)
combobox_efi_fillin sda2
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda1
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
internet: connected
************************Before Repairing
FSCK_ACTION no PASTEBIN_ACTION yes
bootinfo, MBR_ACTION nombraction REINSTALL_POSSIBLE no PURGE_POSSIBLE yes UNHIDEBOOT_ACTION no (10.s) PART_TO_REINSTALL_GRUB  () PART_TO_REINSTALL_GRUB_PURGE 2 (sda2) FORCE_GRUB no NOFORCE_DISK  REMOVABLEDISK  UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sda1) grub-efi (sda1)
internet: connected
/usr/share/boot-sav/bootrepair-actions.sh: line 250: 10390 Terminated              while true; do
done

```

---

### Post by darkod on 2012-01-07
Grub2 is not installed properly, core.img is missing. I don't use EFI so I'm not sure if any special steps are needed for EFI boot.
Also, the installation now doesn't use the whole disk, barely half of it. Not sure why.

Use gdisk again and create a new blank gpt table.
Then create 1MB EFI boot partition, your root partition and swap. Do you know how to create this, especially the EFI partition?
Install again using the existing partitions and make sure to notice if grub2 installs at the end.

Regardless whether it works or not, DON'T just reinstall another time. Post a new results from the script so we can see what is going on, maybe only grub2 will need to be installed.

At the moment I think it can be installed too, but you will be using only half of the disk according to the current results. That's why I suggest a new install.

---

### Post by rented on 2012-01-07
> **darkod said:**
> 
Use gdisk again and create a new blank gpt table.
Then create 1MB EFI boot partition, your root partition and swap. Do you know how to create this, especially the EFI partition?


Yes, I think I can do it in my sleep by now :)

I'll get back soon with the script results.

---

### Post by darkod on 2012-01-07
> **rented said:**
> Yes, I think I can do it in my sleep by now :)

I'll get back soon with the script results.

My mistake, the EFI system partition should be at least 200MB in size, not only 1MB.

---

### Post by MAFoElffen on 2012-01-07
> **rented said:**
> Yes, I think I can do it in my sleep by now :)

I'll get back soon with the script results.
Sounds like your busy trying things and in very capable hands (darko)... If it happens again/still, mount and chroot the installed system from a LiveCD, as darko explained...

Edit you're grub config file
```

gedit /etc/default/grub

```At the line that says 
```

GRUB_CMDLINE_LINUX_DEFAULT=""

```Change it to 
```

GRUB_CMDLINE_LINUX_DEFAULT="--verbose*

```Go to the last line and add another line saying
```

GRUB_GFXPAYLOAD_LINUX=text

```Save and exit. Pickup the changes.
```

update grub

```Then while still in the chroot, update your apt-cache and get your upgrades
```

aptitude update && aptitude upgrade

```Then get out of the chroot (exit) and unmount all the mounts... like darko described.

The grub edit tells it to use "text" explicitly.  Sometimes helps with server edition when someone uses a GPU or APU that has a whole lot of capabilities, when just VGA is needed for Server.  Other edit turns on verbose kernel boot messaging on. This is something you might want on to see where it's getting in the boot process or any errors it might be throwing.  This also seems to help with mounts... 

The update/upgrade- Well, I've had 2 servers, one of my own 4 servers and one of a customers. that didn't like kernel 3.0.0.12.  That kernel is the kernel in the install snapshot.  Once you do the update/upgrade, it installs the current kernel.

Worth a try right?

---

### Post by rented on 2012-01-07
OK, results of darko's suggestion first, then I'll try MAFoElffen's tips.

This is the result of the manual partitioning I did. First is gdisk's printout, then parted's printout.

```
Command (? for help): p
Disk /dev/sda: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 8C89AE2A-30CD-4025-A80C-8F3BD9298E7B
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3151 sectors (1.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          432127   210.0 MiB   EF00  EFI System
   2          432128      5843755918   2.7 TiB     8300  Linux filesystem
   3      5843757056      5860533134   8.0 GiB     8200  Linux swap

(parted) print                                                            
Model: ATA WDC WD30EZRX-00A (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name              Flags
 1      1049kB  221MB   220MB                EFI System        boot
 2      221MB   2992GB  2992GB               Linux filesystem
 3      2992GB  3001GB  8589MB               Linux swap
```

Installation went fine. I chose partitons manually, selecting EFI Boot, ext4 (mounted on /) and swap.

I saw that the installer installed grub and noticed several grub-efi related installations too. The only thing funny was that command "grub update dummy" (or was it "install dummy"? can't remember now). "dummy" sounds a bit fishy :)

After reboot, it *did not restart the machine*!!! I heard the disk working for a while, but all the while my screen looked like some artwork, with vertical multicolored lines and what looked like audio waveforms. I had to hard reset the machine...sigh. I rebooted and tried the recovery option, and then the regular option but changed gfxpayload to text, but the same thing happens all the time. That is, a machine reboot after/during initrd.

Here's the bootinfoscript results. 
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 31132 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       432,127       430,080 EFI System partition
/dev/sda2         432,128 2,622,530,446 2,622,098,319 Data partition (Windows/Linux)
/dev/sda3   2,622,531,584 2,639,307,662    16,776,079 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4110 MB, 4110188544 bytes
128 heads, 63 sectors/track, 995 cylinders, total 8027712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *            192     7,991,423     7,991,232   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        511C-CC2C                              vfat       
/dev/sda2        a38ab5df-1363-4453-ae1c-a012518f5151   ext4       
/dev/sda3        e6ab6541-5a90-4924-b935-b6f681ba176e   swap       
/dev/sdb1        15FA-171A                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root a38ab5df-1363-4453-ae1c-a012518f5151
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root a38ab5df-1363-4453-ae1c-a012518f5151
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu, with Linux 3.0.0-12-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root a38ab5df-1363-4453-ae1c-a012518f5151
	linux	/boot/vmlinuz-3.0.0-12-server root=UUID=a38ab5df-1363-4453-ae1c-a012518f5151 ro   
	initrd	/boot/initrd.img-3.0.0-12-server
}
menuentry 'Ubuntu, with Linux 3.0.0-12-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root a38ab5df-1363-4453-ae1c-a012518f5151
	echo	'Loading Linux 3.0.0-12-server ...'
	linux	/boot/vmlinuz-3.0.0-12-server root=UUID=a38ab5df-1363-4453-ae1c-a012518f5151 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root a38ab5df-1363-4453-ae1c-a012518f5151
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root a38ab5df-1363-4453-ae1c-a012518f5151
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=a38ab5df-1363-4453-ae1c-a012518f5151 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=511C-CC2C  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=e6ab6541-5a90-4924-b935-b6f681ba176e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-server                2
               =                boot/vmlinuz-3.0.0-12-server                   2
               =                vmlinuz                                        2

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

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```

I'm not qualified to interpret this, but the line "=> No boot loader is installed in the MBR of /dev/sda." looks worrying. But I am using GPT so maybe that exlains it?

Thanks for your continued assistance! Now I'll try the other tip.

---

### Post by rented on 2012-01-07
OK, I tried to follow the instructions provided but nothing seems to have happened. I probably did something wrong.

```

sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

```

Different from what darko wrote, but I'm not using LVM now, and surely sda1 (the EFI boot part) should mount to /mnt/boot ?

I edited the grub config file, as described. But "update grub" didn't work, so I went ahead with aptitude update && aptitude upgrade and then thought to try "update-grub". update-grub ran with a couple of errors about files not found, and so did the upgrade.
unmounting stopped at /mnt/dev, saying it was busy, ditto for /mnt. Shutdown anyway, and restarted machine.

grub looks just like before, even down to the 3.0.0.12 kernel instead of the 3.0.0.14 (which I saw was upgraded when running aptitude upgrade).

Still the same problem, reboot during boot.

---

### Post by darkod on 2012-01-07
OK. There is no bootloader installed, as you noticed. Not sure if this makes it reboot all the time, as I said I haven't worked with EFI and don't know if the missing bootloader is related to the reboot.

You did the chroot correctly, enter it again but this time try to install the grub-efi package which is the grub2 for efi boot. Once you are inside the chroot:

```
apt-get install grub-efi
grub-mkconfig
grub-install /dev/sda
update-grub
```Lets see how that goes. After you do that even before rebooting you can run the script again and see if the message about bootloader not installed on /dev/sda is chaged.

PS. On second thought, don't do the mount of /dev/sda1 as /mnt/boot, because now you have no separate /boot partition as with LVM. Yes, sda1 is for the EFI grub files but it should know according to the partition type and put the files there automatically. So, don't mount anything as /mnt/boot during the chroot procedure. You now have only /, no separate /boot.

---

### Post by rented on 2012-01-07
No luck. Boot Info still says that there is no bootloader. But this IS using GPT so maybe there shouldn't be one? 

Some thoughts/questions. I upgraded as per MAFoElffen's instructions, ans saw 3.0.0-14 get downloaded and installed. How come the grub commands still say 3.0.0-12. After mounting and chroot, I don't see any -14 files in /boot, only -12 files.

The grub commands still say set gfxpayload=$linux_gfx_mode. After my edit, shouldn't it say "text"? Or does $linux_gfx_mode contain "text" and is evaluated? The --verbose part got added.

The grub menu title says GRUB version 1.99-12ubuntu5. Should it be version 2? grub2?

Seeing as I DO get the grub menu, and it seems to execute all lines , is there really a problem with the bootloader and/or grub? Or is the problem more specific to the ramdisk image initrd.img-3.0.0-12-server? Maybe some driver/module causing the system restart? Is there no way to get that part of the loading to spit out some warnings or errors?

Just throwing around some ideas and thoughts :)

---

### Post by darkod on 2012-01-07
Hmmm...

1. Grub ver 1.99 is grub2. Don't ask me why they call it 1.99 I have no answer. :)

2. When you did the edit in the /etc/default/grub file, did you do it in your chrooted partition?

Then you save it and run
update-grub

to create a new grub.cfg file with the change inside. At the same time it will check for all present kernels and it should find the 3.0.0-14 in /boot. If the update-grub doesn't show 3.0.0-14 listed check whether you have it in the folder with:
ls /boot

Don't forget you are doing everything inside the chroot.

3. I actually have no idea if the message not to have a bootloader on MBR is normal for EFI, you might be right. If you are seeing a grub menu, it sounds OK.

---

### Post by rented on 2012-01-07
I think I did all the edits while chrooted. But due to my hazy mind right then I missed the update-grub before doing the kernel upgrade. Still, the --verbose did show up so I guess the edits did stick. Why the -14 kernel is missing I don't know, as I saw it download and install. However, there was an error message about some path not being found. Something like "/var/opt/aptitude".

I'll try again from scratch tomorrow, but my head is spinning now. 10 hours yesterday and 10 today, and still no login prompt! :mad:

---

