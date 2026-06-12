---
title: "GRUB2 Out of Memory Error"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2011-03-15
I have an AMD system with Kubuntu 10.10 64-bit, Grub2 and 2.6.37.1 custom kernel. There are several disks in the system, the boot disk is on an OCZ-AGILITY 120GB SATA SSD. After several weeks of normal operation, for some reason the system stopped booting, giving the message ...

error: out of memory > Entering rescue mode > grub rescue>

I can thereafter boot the system with the Kubuntu install disk, go into system rescue mode, go into a root shell on the boot disk, issue update-grub, and the system will then boot correctly the following time. But the time after that, back to the grub out of memory error.

The output from the boot_info_script.sh is below

Can someone tell me what's wrong and how to fix?

Thx, Gus

---------------------------------

$ cat RESULTS.txt
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location on 
    BIOS drive 1 (0x80) and looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location on 
    BIOS drive 1 (0x80) and looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location on 
    BIOS drive 1 (0x80) and looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 71572671 of the same hard 
                       drive for core.img. core.img is at this location on 
                       BIOS drive 1 (0x80) and looks in partition 256 for 
                       /boot/grub.
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

md0: ___________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   122,849,054   122,848,992  83 Linux
/dev/sda2         122,849,055   143,331,929    20,482,875  82 Linux swap / Solaris
/dev/sda3    *    143,331,930   234,436,544    91,104,615   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   838,882,169   838,882,107  fd Linux raid autodetect
/dev/sdb2         838,882,170   976,768,064   137,885,895   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   838,882,169   838,882,107  fd Linux raid autodetect
/dev/sdc2         838,882,170   976,768,064   137,885,895   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/md0         46a79a27-b4a7-484b-bab3-23776b846cfe   ext4       
/dev/sda1        7fd38d40-ed45-4d44-ab14-5cf7dc2020b3   ext4       
/dev/sda2        46ecc0c4-ead4-4b8a-a455-5232ff1e2a99   swap       
/dev/sda3        2C2B442124EDF860                       ntfs       
/dev/sdb1        7da7d435-e3c9-6dd7-a977-e92bf3733aeb   linux_raid_member 
/dev/sdb2        D2BA5A8FBA5A6FC9                       ntfs       
/dev/sdc1        7da7d435-e3c9-6dd7-a977-e92bf3733aeb   linux_raid_member 
/dev/sdc2        4E2A654B2A6530DF                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/md0         /home                    ext4       (rw)
/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3

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

title           Ubuntu 10.10, kernel 2.6.37.1a
uuid            7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
kernel          /boot/vmlinuz-2.6.37.1a root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro quiet splash 
initrd          /boot/initrd.img-2.6.37.1a
quiet

title           Ubuntu 10.10, kernel 2.6.37.1a (recovery mode)
uuid            7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
kernel          /boot/vmlinuz-2.6.37.1a root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro  single
initrd          /boot/initrd.img-2.6.37.1a

title           Ubuntu 10.10, kernel 2.6.35-25-generic
uuid            7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
kernel          /boot/vmlinuz-2.6.35-25-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro quiet splash 
initrd          /boot/initrd.img-2.6.35-25-generic
quiet

title           Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid            7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
kernel          /boot/vmlinuz-2.6.35-25-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro  single
initrd          /boot/initrd.img-2.6.35-25-generic

title           Ubuntu 10.10, memtest86+
uuid            7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.37.1c' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
        linux   /boot/vmlinuz-2.6.37.1c root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro   quiet splash
        initrd  /boot/initrd.img-2.6.37.1c
}
menuentry 'Ubuntu, with Linux 2.6.37.1c (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
        echo    'Loading Linux 2.6.37.1c ...'
        linux   /boot/vmlinuz-2.6.37.1c root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.37.1c
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
        linux   /boot/vmlinuz-2.6.35-27-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro   quiet splash
        initrd  /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
        echo    'Loading Linux 2.6.35-27-generic ...'
        linux   /boot/vmlinuz-2.6.35-27-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
        linux   /boot/vmlinuz-2.6.35-25-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro   quiet splash
        initrd  /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
        echo    'Loading Linux 2.6.35-25-generic ...'
        linux   /boot/vmlinuz-2.6.35-25-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set 2c2b442124edf860
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
# / was on /dev/sda1 during installation
UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 /  ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=46ecc0c4-ead4-4b8a-a455-5232ff1e2a99 none swap    sw         0       0
# Mount /home on /dev/md0
UUID=46a79a27-b4a7-484b-bab3-23776b846cfe /home ext4 errors=remount-ro 0       1

UUID=2C2B442124EDF860     /media/Win7boot   ntfs-3g   defaults,locale=en_US.utf8   0    2

UUID=D2BA5A8FBA5A6FC9     /media/Win7diskE  ntfs-3g   defaults,locale=en_US.utf8   0    2

UUID=4E2A654B2A6530DF     /media/Win7diskF  ntfs-3g   defaults,locale=en_US.utf8   0    2

# 192.168.1.17:/        /mnt    nfs4    _netdev,auto  0  2

# /dev/md1       /mnt/LinuxBackup    ext3 atime,rw,exec,auto,dev  0 3
# /dev/md2       /mnt/WinBackup      ntfs-3g atime,rw,exec,auto,dev  0 4
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  34.128531933 = 36.645232128   boot/grub/core.img                             1
  34.222693920 = 36.746337792   boot/grub/grub.cfg                             1
   0.796958447 = 0.855727616    boot/grub/menu.lst                             1
   6.100455761 = 6.550314496    boot/initrd.img-2.6.35-25-generic              2
   4.426833630 = 4.753276416    boot/initrd.img-2.6.35-25-server               2
   3.553847790 = 3.815915008    boot/initrd.img-2.6.35-27-generic              2
   3.654582500 = 3.924078080    boot/initrd.img-2.6.37.1c                      4
  34.258113384 = 36.784369152   boot/vmlinuz-2.6.35-25-generic                 1
  34.273276806 = 36.800650752   boot/vmlinuz-2.6.35-27-generic                 1
  34.269229412 = 36.796304896   boot/vmlinuz-2.6.37.1c                         1
   3.553847790 = 3.815915008    initrd.img                                     2
   4.426833630 = 4.753276416    initrd.img.old                                 2
  34.273276806 = 36.800650752   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc1

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 e0 5f 00 20  |........ ...._. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 ec 82  |............. ..|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 f2 07 00 20  |........ ...... |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 29 8c  |............. ).|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 9c 07 00 20  |........ ...... |
00000050  00 00 05 00 00 00 00 00  00 00 00 00 00 20 3b d8  |............. ;.|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 fd 07 00 20  |........ ...... |
00000070  00 00 05 00 00 00 00 00  00 00 00 00 00 20 af 9a  |............. ..|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 00 00 20  |........ ...... |
00000090  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b8 95  |............. ..|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 00 00 20  |........ ...... |
000000b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 63 35  |............. c5|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 00 00 20  |........ ...... |
000000d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 0d 94  |............. ..|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 00 00 20  |........ ...... |
000000f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 d6 34  |............. .4|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 00 00 20  |........ ...... |
00000110  00 00 05 00 00 00 00 00  00 00 00 00 00 20 06 90  |............. ..|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 00 00 20  |........ ...... |
00000130  00 00 05 00 00 00 00 00  00 00 00 00 00 20 dd 30  |............. .0|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 00 00 20  |........ ...... |
00000150  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b3 91  |............. ..|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 ff 07 00 20  |........ ...... |
00000170  00 00 05 00 00 00 00 00  00 00 00 00 00 20 da 24  |............. .$|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 e6 07 00 20  |........ ...... |
00000190  00 00 05 00 00 00 00 00  00 00 00 00 00 20 09 dd  |............. ..|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 00 00 20  |........ ...... |
000001b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b7 33  |............. .3|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 00 00 20  |........ ...... |
000001d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 d9 92  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 00 00 20  |........ ...... |
000001f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 02 32  |............. .2|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
mdadm: no devices found for /dev/md1
mdadm: no devices found for /dev/md2
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.

---

