---
title: "Help Win7 and Unbuntu 8.10 (Grub2) on seperate drives"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by muad on 2009-12-29
Ok, So I'm not new to dual booting, however I can not get this figured out. 

I have my old primary sda drive that has ubuntu 8.1064bit installed. I have added a new 1TB drive, and installed win7 64bit on it (which I need for work), which is now my sda or primary drive.

I then re-installed my old primary drive, which is now sdb, and want to dual boot these operating systems using GRUB 2. 

I've googled, and everything I've tried does not work. I'm trying to install GRUB 2 in the MBR of the Win7 drive (sda) using a ubuntu 9.10 (x86) install or live CD.

Here is my fdisk -l info:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0e6cb9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      121602   976657408    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0279c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1033     8297541   82  Linux swap / Solaris
/dev/sdb2   *        1034       60801   480086460   83  Linux

When I try to mount sda, it says:

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

Any help is greatly appreciated!

-Will

EDIT: Here is are my results from running the boot_info_script042.sh

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 1.96 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sde
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0e6cb9a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0279c74

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    16,595,144    16,595,082  82 Linux swap / Solaris
/dev/sdb2    *     16,595,145   976,768,064   960,172,920  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 2048 MB, 2048901120 bytes
64 heads, 63 sectors/track, 992 cylinders, total 4001760 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63     3,995,711     3,995,649   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="AEAA4668AA462CE1" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="6E8848F18848B8FB" TYPE="ntfs" 
/dev/sdb1: UUID="4cbc2c5b-010c-4bb9-878c-72ee088aaea0" TYPE="swap" 
/dev/sdb2: UUID="dcdcacaf-209b-4c54-af30-7bffa7456618" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sde1: SEC_TYPE="msdos" LABEL="EOS_DIGITAL" UUID="76F0-5829" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr1 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sde1 on /media/EOS_DIGITAL type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb2/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dcdcacaf-209b-4c54-af30-7bffa7456618

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
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title        Chainload into GRUB 2
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Debian GNU/Linux, kernel 2.6.27-16-generic
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/vmlinuz-2.6.27-16-generic root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro quiet splash
initrd        /boot/initrd.img-2.6.27-16-generic

title        Debian GNU/Linux, kernel 2.6.27-16-generic (recovery mode)
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/vmlinuz-2.6.27-16-generic root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro single
initrd        /boot/initrd.img-2.6.27-16-generic

title        Debian GNU/Linux, kernel 2.6.27-15-generic
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/vmlinuz-2.6.27-15-generic root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro quiet splash
initrd        /boot/initrd.img-2.6.27-15-generic

title        Debian GNU/Linux, kernel 2.6.27-15-generic (recovery mode)
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/vmlinuz-2.6.27-15-generic root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro single
initrd        /boot/initrd.img-2.6.27-15-generic

title        Debian GNU/Linux, kernel 2.6.27-14-generic
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/vmlinuz-2.6.27-14-generic root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro quiet splash
initrd        /boot/initrd.img-2.6.27-14-generic

title        Debian GNU/Linux, kernel 2.6.27-14-generic (recovery mode)
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/vmlinuz-2.6.27-14-generic root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Debian GNU/Linux, kernel 2.6.27-11-generic
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/vmlinuz-2.6.27-11-generic root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro quiet splash
initrd        /boot/initrd.img-2.6.27-11-generic

title        Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/vmlinuz-2.6.27-11-generic root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Debian GNU/Linux, kernel 2.6.27-7-generic
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/vmlinuz-2.6.27-7-generic root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro quiet splash
initrd        /boot/initrd.img-2.6.27-7-generic

title        Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/vmlinuz-2.6.27-7-generic root=uuid=dcdcacaf-209b-4c54-af30-7bffa7456618 ro single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Debian GNU/Linux, kernel memtest86+
root        dcdcacaf-209b-4c54-af30-7bffa7456618
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Dell Utility Partition
root        (hd1,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Media Center Edition
rootnoverify        (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1




=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=10
set root=(hd0,2)
if font (hd0,2)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.27-7-generic" {
    linux    (hd0,2)/boot/vmlinuz-2.6.27-7-generic root=UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 ro quiet splash 
    initrd    (hd0,2)/boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu, linux 2.6.27-7-generic (single-user mode)" {
    linux    (hd0,2)/boot/vmlinuz-2.6.27-7-generic root=UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 ro single
    initrd    (hd0,2)/boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu, linux 2.6.27-16-generic" {
    linux    (hd0,2)/boot/vmlinuz-2.6.27-16-generic root=UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 ro quiet splash 
    initrd    (hd0,2)/boot/initrd.img-2.6.27-16-generic
}
menuentry "Ubuntu, linux 2.6.27-16-generic (single-user mode)" {
    linux    (hd0,2)/boot/vmlinuz-2.6.27-16-generic root=UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 ro single
    initrd    (hd0,2)/boot/initrd.img-2.6.27-16-generic
}
menuentry "Ubuntu, linux 2.6.27-15-generic" {
    linux    (hd0,2)/boot/vmlinuz-2.6.27-15-generic root=UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 ro quiet splash 
    initrd    (hd0,2)/boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu, linux 2.6.27-15-generic (single-user mode)" {
    linux    (hd0,2)/boot/vmlinuz-2.6.27-15-generic root=UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 ro single
    initrd    (hd0,2)/boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu, linux 2.6.27-14-generic" {
    linux    (hd0,2)/boot/vmlinuz-2.6.27-14-generic root=UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 ro quiet splash 
    initrd    (hd0,2)/boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu, linux 2.6.27-14-generic (single-user mode)" {
    linux    (hd0,2)/boot/vmlinuz-2.6.27-14-generic root=UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 ro single
    initrd    (hd0,2)/boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu, linux 2.6.27-11-generic" {
    linux    (hd0,2)/boot/vmlinuz-2.6.27-11-generic root=UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 ro quiet splash 
    initrd    (hd0,2)/boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu, linux 2.6.27-11-generic (single-user mode)" {
    linux    (hd0,2)/boot/vmlinuz-2.6.27-11-generic root=UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 ro single
    initrd    (hd0,2)/boot/initrd.img-2.6.27-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    (hd0,2)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=dcdcacaf-209b-4c54-af30-7bffa7456618 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=4cbc2c5b-010c-4bb9-878c-72ee088aaea0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

=================== sdb2: Location of files loaded by Grub: ===================


   8.4GB: boot/grub/grub.cfg
   8.4GB: boot/grub/menu.lst
   8.4GB: boot/initrd.img-2.6.27-11-generic
   8.4GB: boot/initrd.img-2.6.27-14-generic
   8.4GB: boot/initrd.img-2.6.27-15-generic
   8.4GB: boot/initrd.img-2.6.27-16-generic
   8.4GB: boot/initrd.img-2.6.27-7-generic
   8.4GB: boot/vmlinuz-2.6.27-11-generic
   8.4GB: boot/vmlinuz-2.6.27-14-generic
   8.4GB: boot/vmlinuz-2.6.27-15-generic
   8.4GB: boot/vmlinuz-2.6.27-16-generic
   8.4GB: boot/vmlinuz-2.6.27-7-generic
   8.4GB: initrd.img
   8.4GB: initrd.img.old
   8.4GB: vmlinuz
   8.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde1

00000000  eb 3e 90 50 77 72 53 68  6f 74 20 00 02 40 01 00  |.>.PwrShot ..@..|
00000010  02 00 02 00 00 f8 f4 00  3f 00 40 00 3f 00 00 00  |........?.@.?...|
00000020  01 f8 3c 00 80 00 29 29  58 f0 76 45 4f 53 5f 44  |..<...))X.vEOS_D|
00000030  49 47 49 54 41 4c 46 41  54 31 36 20 20 20 33 ff  |IGITALFAT16   3.|
00000040  8e df be 00 7c 8d 9c e4  01 8e 47 02 fc b9 00 02  |....|.....G.....|
00000050  f3 a4 c7 07 58 00 ff 2f  8c c8 fa 8e d0 bc 00 06  |....X../........|
00000060  fb 8b ec 83 ec 16 c5 36  78 00 89 76 f6 8c 5e f8  |.......6x..v..^.|
00000070  8d 7e ea b9 0b 00 57 f3  a4 5f 8e d9 be 78 00 89  |.~....W.._...x..|
00000080  3c 8c 44 02 0e 1f c6 45  04 12 c6 45 09 0f b2 00  |<.D....E...E....|
00000090  91 cd 13 a0 18 00 f6 26  1a 00 89 46 fa 83 3e ea  |.......&...F..>.|
000000a0  01 00 75 20 a0 10 00 98  f6 26 16 00 03 06 0e 00  |..u .....&......|
000000b0  a3 ea 01 91 b8 20 00 f7  26 11 00 f7 36 0b 00 03  |..... ..&...6...|
000000c0  c1 a3 ec 01 33 d2 a1 ea  01 b9 01 00 c4 1e e0 01  |....3...........|
000000d0  e8 90 00 b0 20 f6 26 e8  01 c4 3e e0 01 03 f8 be  |.... .&...>.....|
000000e0  f1 01 b9 0b 00 f3 a6 74  24 be a5 01 e8 49 00 32  |.......t$....I.2|
000000f0  e4 cd 16 e8 02 00 cd 19  33 c0 8e d8 bb 78 00 c4  |........3....x..|
00000100  7e f6 89 3f 8c 47 02 c3  be cc 01 eb df c4 1e e0  |~..?.G..........|
00000110  01 8b 16 ee 01 a1 ec 01  8a 0e f0 01 b5 00 e8 42  |...............B|
00000120  00 e8 d4 ff bb 84 00 2e  8a 16 24 00 c7 47 02 ff  |..........$..G..|
00000130  ff 89 17 2e ff 2e e0 01  ac 0a c0 74 25 b4 0e bb  |...........t%...|
00000140  07 00 cd 10 eb f2 03 06  1c 00 13 16 1e 00 f7 76  |...............v|
00000150  fa 89 46 fe 8b c2 f6 36  18 00 88 46 fc fe c4 88  |..F....6...F....|
00000160  66 fd c3 e3 fd 52 50 51  e8 db ff b8 01 00 50 e8  |f....RPQ......P.|
00000170  19 00 58 72 93 59 5f 5a  2b c8 03 f8 83 d2 00 52  |..Xr.Y_Z+......R|
00000180  57 f7 26 0b 00 03 d8 58  5a eb d8 8b 56 fe b1 06  |W.&....XZ...V...|
00000190  d2 e6 0a 76 fd 8b ca 86  e9 8a 16 24 00 8a 76 fc  |...v.......$..v.|
000001a0  b4 02 cd 13 c3 4e 6f 20  53 79 73 74 65 6d 20 6f  |.....No System o|
000001b0  6e 20 44 69 73 6b 0d 0a  50 72 65 73 73 20 45 73  |n Disk..Press Es|
000001c0  63 20 74 6f 20 52 65 62  6f 6f 74 00 44 69 73 6b  |c to Reboot.Disk|
000001d0  20 42 6f 6f 74 20 46 61  69 6c 75 72 65 00 00 00  | Boot Failure...|
000001e0  00 00 70 00 00 00 00 0c  00 00 00 00 00 00 00 00  |..p.............|
000001f0  00 49 42 4d 42 49 4f 20  20 43 4f 4d 00 80 55 aa  |.IBMBIO  COM..U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sdf sdg sdh 
```

---

### Post by meierfra. on 2009-12-29
Why do you want Grub to be installed on the Windows drive?  I'm asking since Grub2 often boots very slowly if it is not installed on the same drive as Ubuntu.

Are you currently able to boot into Ubuntu?  (You should be able to boot into Ubuntu if you set your bios to boot from the 500 GB Ubuntu drive)
If yes, I would suggest to add just add Window 7 to the Grub menu via

```

cd /boot/grub
sudo mv device.map device.map.bu
sudo update-grub2
```


If you    really want to install Grub to the MBR of the Windows drive, use

```
sudo grub-install --recheck /dev/sda
```


If you cannot boot into Ubuntu, or these commands did not work from Ubuntu 8.10,  boot from the Ubuntu 9.10 Live CD. Then do

```
sudo mount /dev/sdb2 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```



> When I try to mount sda, it says:

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

You  don't need  to mount Window 7 to reinstall Grub, but if you want to mount Windows 7 use

```
sudo mkdir /media/"Windows 7"
sudo mount /dev/sda1 /media/"Windows 7"
```
( here you can replace "Window 7" by anything you want to)

If you want to  mount  Window 7 automatically, you need to edit "/etc/fstab". Ask for help if needed.

---

### Post by muad on 2009-12-29
I was only trying to install GRUB on the win7 drive because I was told by a friend that I had to, since Windows "likes" to be on the primary drive. In the past, I had XP on a secondary drive, and it was a pain in the butt to get it to boot properly with GRUB Legacy.  

At the moment, I can not dual boot. Well, I can by swapping the sata cables, LOL. I am going to try your first suggestion, as that sounds like the best bet. I run ubuntu 85% of the time, I only need win7 for some work software, and gaming. I normally run windows in a VM via sun's vbox, but that doesn't work well for gaming. 

Thanks for your help thus far.

---

### Post by muad on 2009-12-29
> **meierfra. said:**
> Why do you want Grub to be installed on the Windows drive? I'm asking since Grub2 often boots very slowly if it is not installed on the same drive as Ubuntu.

Are you currently able to boot into Ubuntu? (You should be able to boot into Ubuntu if you set your bios to boot from the 500 GB Ubuntu drive)
If yes, I would suggest to add just add Window 7 to the Grub menu via

```

cd /boot/grub
sudo mv device.map device.map.bu
sudo update-grub2
```

This worked perfectly, and I didn't need to go into the bios either. Because I had swapped the sata cables so I could boot ubuntu, it was already set to boot from that drive (which is now sda again). My win7 drive is now sdb, and when I used the commands you gave me above in a terminal, it updated my Grub and everything boots perfectly. 

I'd like to note that it seems win7 doens't have to be on the primary drive, like XP did. It seems more than happy to boot from sdb with no issues at all. 

Thanks again for your help, I am truly thankful. 

All the best, 

-Will

---

### Post by meierfra. on 2009-12-29
Glad it worked out so easily.  


About Windows liking to be on the primary drive:  That is  an urban legend with only a very small kernel of truth:

To **install** XP, Vista or Windows 7 one needs a fat/ntfs primary partition on the primary drive to hold the boot files. But the operating system can be on any partition one would like. After installation, if one uses Grub to boot, one can switch the order of the hard drives, move the boot files to a different partition and/or move the partition with the operating system in any way one would like (of course one might have to adjust Grub and the Windows boot loader).

---

