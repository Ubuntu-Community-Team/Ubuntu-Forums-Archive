---
title: "Dual Boot from 2 HDDs"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by WESTNINE9 on 2011-01-16
I just installed Ubuntu 10.10 
I have windows7 installed on 1 hard drive and Ubuntu on another.
I can't figure how to configure GRUB so I can dual boot.
As it stands I can no longer boot into windows7.
I get the "GRUB rescue - no such device" error when I attempt to boot windows7.
Ubuntu boots just fine.

Can anyone provide detail on how to go about configuring grub to dual boot from the 2 HDDs??

windows7 was installed 1st on my primary disc btw.

---

### Post by wilee-nilee on 2011-01-16
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by WESTNINE9 on 2011-01-16
Will do.
It takes about 30min to fully boot from flash (is this normal?).
please bear with me.

---

### Post by wilee-nilee on 2011-01-16
> **WESTNINE9 said:**
> Will do.
It takes about 30min to fully boot from flash **(is this normal?).**
please bear with me.

No this is not normal, but once your there stay there a little while once you post the script. If I can see the problem it can probably be fixed from there, or at least do what needs to be done from there..

---

### Post by Rubi1200 on 2011-01-16
+ to the boot script that wilee-nilee asked for.

Quick question, how is the boot priority set in BIOS?

---

### Post by WESTNINE9 on 2011-01-16
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   468,520,959   468,518,912  83 Linux
/dev/sda2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   195,809,279   195,807,232   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc2    *         16,065 2,930,272,064 2,930,256,000   5 Extended
/dev/sdc5              16,128 2,930,272,064 2,930,255,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        37b91d8b-5357-4667-838b-ad9e726ea4c6   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        44065079-191d-4165-a27c-0139ea728c87   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EEA458CBA4589843                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        40F436CFF0598959                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd         15F7-020F                              vfat       PENDRIVE                      
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=37b91d8b-5357-4667-838b-ad9e726ea4c6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=37b91d8b-5357-4667-838b-ad9e726ea4c6

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

title        Ubuntu 10.10, kernel 2.6.35-24-generic-pae
uuid        37b91d8b-5357-4667-838b-ad9e726ea4c6
kernel        /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=37b91d8b-5357-4667-838b-ad9e726ea4c6 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic-pae

title        Ubuntu 10.10, kernel 2.6.35-24-generic-pae (recovery mode)
uuid        37b91d8b-5357-4667-838b-ad9e726ea4c6
kernel        /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=37b91d8b-5357-4667-838b-ad9e726ea4c6 ro  single
initrd        /boot/initrd.img-2.6.35-24-generic-pae

title        Chainload into GRUB 2
root        37b91d8b-5357-4667-838b-ad9e726ea4c6
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        37b91d8b-5357-4667-838b-ad9e726ea4c6
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 37b91d8b-5357-4667-838b-ad9e726ea4c6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 37b91d8b-5357-4667-838b-ad9e726ea4c6
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 37b91d8b-5357-4667-838b-ad9e726ea4c6
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=37b91d8b-5357-4667-838b-ad9e726ea4c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 37b91d8b-5357-4667-838b-ad9e726ea4c6
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=37b91d8b-5357-4667-838b-ad9e726ea4c6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 37b91d8b-5357-4667-838b-ad9e726ea4c6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 37b91d8b-5357-4667-838b-ad9e726ea4c6
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=44065079-191d-4165-a27c-0139ea728c87 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  21.6GB: boot/grub/grub.cfg
  21.6GB: boot/grub/menu.lst
    .6GB: boot/initrd.img-2.6.35-24-generic-pae
  21.6GB: boot/vmlinuz-2.6.35-24-generic-pae
    .6GB: initrd.img
  21.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  fc 21 8f e8 fc 7e 3c da  0c b1 77 87 c5 de 8c 4f  |.!...~<...w....O|
00000010  2a 55 27 bd e4 ce 6b 12  84 b0 65 00 dc 06 03 e0  |*U'...k...e.....|
00000020  a1 05 04 2f 2f b2 89 56  40 3a ac b8 78 3c 1f dc  |...//..V@:..x<..|
00000030  ff e0 f8 7f c5 57 f2 0e  ae 7c c2 5c 4b 08 00 1a  |.....W...|.\K...|
00000040  24 80 70 41 12 01 a8 20  0f cb c2 10 41 06 81 04  |$.pA... ....A...|
00000050  ba 80 61 7c b0 0f 89 40  c0 a0 c0 3c 5e 22 ed bf  |..a|...@...<^"..|
00000060  97 f0 77 66 33 fc 3e 0f  01 fe 08 3c 07 f9 a0 f0  |..wf3.>....<....|
00000070  1f d5 83 c0 7f 72 0f 01  fe 08 90 01 e1 00 18 03  |.....r..........|
00000080  c1 80 34 10 41 a8 42 06  56 0c ac 48 06 12 42 08  |..4.A.B.V..H..B.|
00000090  90 3a 50 24 83 51 23 d9  0b c7 5e dd 57 07 4a 3d  |.:P$.Q#...^.W.J=|
000000a0  64 3a 2b 4f 2e 07 80 80  fc 03 a0 3c 04 06 60 f0  |d:+O.......<..`.|
000000b0  1f d9 80 68 30 06 83 4f  89 40 de 80 f0 1f e7 83  |...h0..O.@......|
000000c0  c0 40 6a 0d f2 e0 78 0f  f0 c4 b1 2c ba 09 65 e0  |.@j...x....,..e.|
000000d0  d4 10 4b 87 f0 49 06 12  28 43 98 ad 5d fe 7a 00  |..K..I..(C..].z.|
000000e0  77 ea b0 38 ab c0 79 42  8f 83 00 48 3c 07 f8 e0  |w..8..yB...H<...|
000000f0  c0 1e 0f 01 fe 78 07 83  c0 7f 8a 01 90 b8 1b e1  |.....x..........|
00000100  07 e0 c0 a2 00 c0 86 10  84 af 82 10 42 f0 97 e0  |............B...|
00000110  0c 00 f5 45 c0 86 01 ca  87 fe 51 fa a9 50 41 2e  |...E......Q..PA.|
00000120  54 3f 55 b6 e2 8c e1 fb  d4 20 8e 43 b3 66 36 c0  |T?U...... .C.f6.|
00000130  d9 1c 38 9e 25 83 c0 40  6a 0f 01 01 e8 3c 04 0e  |..8.%..@j....<..|
00000140  22 58 30 06 2b 06 54 0f  01 fc f8 30 40 06 12 40  |"X0.+.T....0@..@|
00000150  34 10 42 08 20 80 68 92  3f 06 1f 84 02 f0 85 fb  |4.B. .h.?.......|
00000160  3e 3f f4 8a 40 f0 fe a9  55 14 2a 9d 2e b3 ff 97  |>?..@...U.*.....|
00000170  16 7f 82 10 3c 04 11 a0  f0 10 1f 84 0d 56 0f 01  |....<........V..|
00000180  02 f8 3c 07 ea e1 0c 1e  02 03 b5 52 60 90 0f 01  |..<........R`...|
00000190  01 98 3c 07 f6 20 ca 84  90 0f 06 12 ad 8c 2b 1f  |..<.. ........+.|
000001a0  83 65 f9 74 ce 73 ea ea  d6 47 2e 80 b0 98 1d c5  |.e.t.s...G......|
000001b0  93 bc 8e 2a bb 07 80 ff  3c 1a 03 c0 40 8e 00 fe  |...*....<...@...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 40 2f 01 00 00  |...........@/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  8d 46 7a 00 83 1e 00 00  00 00 00 00 02 00 00 00  |.Fz.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 0f 02 f7 15 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 2e 3d 00 00  66 ba 00 00 00 00 bb 00  |}.f..=..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf 
```

This is what I got.

---

### Post by WESTNINE9 on 2011-01-16
> **Rubi1200 said:**
> + to the boot script that wilee-nilee asked for.

Quick question, how is the boot priority set in BIOS?

HD
CD
Flash

---

### Post by wilee-nilee on 2011-01-16
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   **/boot/grub/menu.lst** /boot/grub/grub.cfg /etc/fstab 
                       **/boot/grub/core.img**

**First problem see next post for information and link.**

second problem is your missing these highlighted parts to windows.
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

This can be fixed by first putting a boot flag on this partition with gparted in Ubuntu, do it now when your in the live environment and remove the one from sda. Then unplug the sda drive and boot a W7 recovery disc and choosing the language then repair and using the auto repair 3 times.

You then want the sda drive first again in the bios to have grub be the bootloader.
When you have fixed all of this and get booted into the installed Ubuntu just run
sudo update-grub
to pick up the W7 boot.

Hey Rubi1200, nice to see you on the forum as usual.:)

---

### Post by wilee-nilee on 2011-01-16
Make sure your using a 10.10 loaded thumb to do the purge and reinstall of grub2. I Just realized you can boot to Ubuntu so you can fix it from itself, the same link. Use the from OS fix.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You have grub-legacy and grub2 that is what the highlighted sections in the sda1 partition show. The two should be keeping you from booting at all generally.

---

### Post by WESTNINE9 on 2011-01-16
Thanks for all your input.
It's very late here.
I will post my results in the morning.
Again, thank you for the timely responses.

---

### Post by wilee-nilee on 2011-01-16
> **WESTNINE9 said:**
> Thanks for all your input.
It's very late here.
I will post my results in the morning.
Again, thank you for the timely responses.

No problem notice the revisions, after realizing that you can boot into Ubuntu. I think your in good shape, it is just a matter of getting both grubs out and grub2 in alone, then running the repairs on the sdd hd with the sda unplugged.

---

### Post by WESTNINE9 on 2011-01-16
> **wilee-nilee said:**
> No problem notice the revisions, after realizing that you can boot into Ubuntu. I think your in good shape, it is just a matter of getting both grubs out and grub2 in alone, then running the repairs on the sdd hd with the sda unplugged.

Your instructions worked perfectly.
GRUB is working fine and I'm having no issues dual booting now.

Again, Thanks! :KS

---

### Post by WESTNINE9 on 2011-01-16
> **wilee-nilee said:**
> No problem notice the revisions, after realizing that you can boot into Ubuntu. I think your in good shape, it is just a matter of getting both grubs out and grub2 in alone, then running the repairs on the sdd hd with the sda unplugged.

Your instructions worked perfectly.
GRUB is working fine and I'm having no issues dual booting now.

Again, Thanks! :KS

---

### Post by WESTNINE9 on 2011-01-16
> **wilee-nilee said:**
> No problem notice the revisions, after realizing that you can boot into Ubuntu. I think your in good shape, it is just a matter of getting both grubs out and grub2 in alone, then running the repairs on the sdd hd with the sda unplugged.

Your instructions worked perfectly.
GRUB is working fine and I'm having no issues dual booting now.

Again, Thanks! :KS

---

### Post by WESTNINE9 on 2011-01-16
> **wilee-nilee said:**
> No problem notice the revisions, after realizing that you can boot into Ubuntu. I think your in good shape, it is just a matter of getting both grubs out and grub2 in alone, then running the repairs on the sdd hd with the sda unplugged.

Your instructions worked perfectly.
GRUB is working fine and I'm having no issues dual booting now.

Again, Thanks! :KS

---

### Post by WESTNINE9 on 2011-01-16
> **wilee-nilee said:**
> No problem notice the revisions, after realizing that you can boot into Ubuntu. I think your in good shape, it is just a matter of getting both grubs out and grub2 in alone, then running the repairs on the sdd hd with the sda unplugged.

oh boy, sorry.
browser was acting funny.
Thanks again.

---

### Post by wilee-nilee on 2011-01-16
> **WESTNINE9 said:**
> Your instructions worked perfectly.
Grub is working fine and I'm having no issues dual booting Windows7.
Again, Thanks! :KS

I got them convoluted, glad you got it done in spite of this.:)

---

