---
title: "cant boot my linux"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by xXx8004 on 2010-02-18
Hi
 
I have installed ubuntu 9.10 side by side with vista on same harddisk but i cant see it when i start my system 
I have Grub.
I need help to choise betweem vista and ubuntu (litle guide) easy guide
 
Thank u

---

### Post by suseendran.rengabashyam on 2010-02-18
Hi,

When you see the "GRUB Loading" screen, press the 'Shift' key so that you can enter the GRUB menu and select your desired OS.

Hope this helps.

---

### Post by xXx8004 on 2010-02-18
Grub not commint its going direct to windows vista

---

### Post by darkod on 2010-02-18
Boot with the ubuntu cd, Try Ubuntu option if your hdd ubuntu is not booting. If it is, you can do this from the hdd ubuntu too. Download the script in my signature, move it on desktop for example, and execute it in terminal with:

sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with detailed info about your boot process. Post the content of that file here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above when writing the post).

---

### Post by xXx8004 on 2010-02-18
Hi again
 
i did exact as u said
 
and the result was:
 
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=ce844bf8-c16c-4dd3-9529-10bc60f276d0)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sdb1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x209f0bce
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63   390,716,864   390,716,802   7 HPFS/NTFS

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x991a3e00
Partition  Boot         Start           End          Size  Id System
/dev/sdb1    *          2,048   574,789,634   574,787,587   7 HPFS/NTFS
/dev/sdb2         574,789,635   625,137,344    50,347,710   5 Extended
/dev/sdb5         574,789,698   622,968,569    48,178,872  83 Linux
/dev/sdb6         622,968,633   625,137,344     2,168,712  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        1AF16EBF50AF2452                       ntfs                                     
/dev/sdb1        E830A84930A82094                       ntfs                                     
/dev/sdb5        ce844bf8-c16c-4dd3-9529-10bc60f276d0   ext4                                     
/dev/sdb6        a5be0773-a66b-422d-8ca0-777c7a75b026   swap                                     
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/1AF16EBF50AF2452  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

=========================== sdb5/boot/grub/grub.cfg: ===========================
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set ce844bf8-c16c-4dd3-9529-10bc60f276d0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 set quiet=1
 insmod ext2
 set root=(hd1,5)
 search --no-floppy --fs-uuid --set ce844bf8-c16c-4dd3-9529-10bc60f276d0
 linux /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=ce844bf8-c16c-4dd3-9529-10bc60f276d0 ro   quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 insmod ext2
 set root=(hd1,5)
 search --no-floppy --fs-uuid --set ce844bf8-c16c-4dd3-9529-10bc60f276d0
 linux /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=ce844bf8-c16c-4dd3-9529-10bc60f276d0 ro single 
 initrd /boot/initrd.img-2.6.31-14-generic-pae
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
 insmod ntfs
 set root=(hd1,1)
 search --no-floppy --fs-uuid --set e830a84930a82094
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sdb5/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=ce844bf8-c16c-4dd3-9529-10bc60f276d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a5be0773-a66b-422d-8ca0-777c7a75b026 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=================== sdb5: Location of files loaded by Grub: ===================

 296.3GB: boot/grub/core.img
 307.6GB: boot/grub/grub.cfg
 295.2GB: boot/initrd.img-2.6.31-14-generic-pae
 310.5GB: boot/vmlinuz-2.6.31-14-generic-pae
 295.2GB: initrd.img
 310.5GB: vmlinuz

 
Thank for helping

---

### Post by darkod on 2010-02-18
You just need to add grub2 to the MBR of your 320GB hdd. It went to the other disk. Boot with the 9.10 cd into the live desktop and do:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Restart without the cd and it should be fine.

---

### Post by xXx8004 on 2010-02-18
Now work perfect Thank u very much Darko

---

### Post by msharelick on 2010-05-26
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:

sda5: _________________________________________________________________________

    File system:
    Boot sector type:  -
    Boot sector info:
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e3a2e39

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   491,524,739   491,524,677   7 HPFS/NTFS
/dev/sda2         491,524,740   976,751,999   485,227,260   f W95 Ext d (LBA)
/dev/sda5         491,524,803   976,751,999   485,227,197   e W95 FAT16 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00023499

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   957,875,624   957,875,562  83 Linux
/dev/sdb2         957,875,625   976,768,064    18,892,440   5 Extended
/dev/sdb5         957,875,688   976,768,064    18,892,377  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1640971A4096FFA3                       ntfs
/dev/sdb1        29e33691-9470-4292-ac20-990c0dd788f9   ext3
/dev/sdb5        fe7c60f7-2f8d-4c10-a845-25ae3053bea7   swap

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]^M
timeout=30^M
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS^M
[operating systems]^M
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect^
=========================== sdb1/boot/grub/menu.lst: ===========================

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
timeout         10

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
# kopt=root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=29e33691-9470-4292-ac20-990c0dd788f9

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

title           Ubuntu 9.04, kernel 2.6.28-18-generic
uuid            29e33691-9470-4292-ac20-990c0dd788f9
kernel          /boot/vmlinuz-2.6.28-18-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro quiet splash
initrd          /boot/initrd.img-2.6.28-18-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid            29e33691-9470-4292-ac20-990c0dd788f9
kernel          /boot/vmlinuz-2.6.28-18-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro  single
initrd          /boot/initrd.img-2.6.28-18-generic

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            29e33691-9470-4292-ac20-990c0dd788f9
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            29e33691-9470-4292-ac20-990c0dd788f9
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            29e33691-9470-4292-ac20-990c0dd788f9
kernel          /boot/vmlinuz-2.6.28-18-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro  single
initrd          /boot/initrd.img-2.6.28-18-generic

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            29e33691-9470-4292-ac20-990c0dd788f9
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            29e33691-9470-4292-ac20-990c0dd788f9
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            29e33691-9470-4292-ac20-990c0dd788f9
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=29e33691-9470-4292-ac20-990c0dd788f9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=fe7c60f7-2f8d-4c10-a845-25ae3053bea7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sdb1: Location of files loaded by Grub: ===================


 273.5GB: boot/grub/menu.lst
 273.4GB: boot/grub/stage2
 273.4GB: boot/initrd.img-2.6.28-11-generic
 273.4GB: boot/initrd.img-2.6.28-18-generic
 273.4GB: boot/vmlinuz-2.6.28-11-generic
 273.4GB: boot/vmlinuz-2.6.28-18-generic
 273.4GB: initrd.img
 273.4GB: initrd.img.old
 273.4GB: vmlinuz
 273.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  05 33 f6 46 eb 02 33 f6  8b 45 14 6a 60 89 7d f4  |.3.F..3..E.j`.}.|
00000010  89 7d fc 89 38 e8 6b 6c  f9 ff 3b c7 74 0f ff 75  |.}..8.kl..;.t..u|
00000020  0c 8b c8 e8 a9 4f 04 00  89 45 20 eb 03 89 7d 20  |.....O...E ...} |
00000030  39 7d 20 75 0a bf 0d fc  ff ff e9 97 02 00 00 8b  |9} u............|
00000040  4d 20 53 e8 a8 17 04 00  8b 4d 20 e8 92 58 04 00  |M S......M ..X..|
00000050  8b f8 bb bd f9 ff ff 3b  fb 75 0f 8b 4d 20 6a 01  |.......;.u..M j.|
00000060  e8 16 f8 ff ff 33 ff 89  7d 20 85 ff 0f 8c 47 02  |.....3..} ....G.|
00000070  00 00 85 f6 74 5c 6a 60  e8 08 6c f9 ff 85 c0 74  |....t\j`..l....t|
00000080  12 8b 4d f8 ff 71 1c 8b  c8 e8 43 4f 04 00 89 45  |..M..q....CO...E|
00000090  fc eb 04 83 65 fc 00 8b  75 fc 85 f6 75 0a bf 0d  |....e...u...u...|
000000a0  fc ff ff e9 11 02 00 00  8b ce e8 41 17 04 00 8b  |...........A....|
000000b0  ce e8 2c 58 04 00 8b f8  3b fb 75 0e 6a 01 8b ce  |..,X....;.u.j...|
000000c0  e8 b6 f7 ff ff 33 ff 89  7d fc 85 ff 0f 8c e7 01  |.....3..}.......|
000000d0  00 00 8b 75 1c 66 81 fe  00 01 0f 82 aa 00 00 00  |...u.f..........|
000000e0  83 7d 20 00 75 18 eb 4d  8b 4d 20 e8 f2 57 04 00  |.} .u..M.M ..W..|
000000f0  8b f8 3b fb 74 30 85 ff  0f 8c bb 01 00 00 ff 75  |..;.t0.........u|
00000100  f8 56 e8 d7 f4 ff ff 8b  4d 20 50 56 e8 66 4f 04  |.V......M PV.fO.|
00000110  00 8b 4d 20 50 e8 ff 4e  04 00 50 e8 3c f5 ff ff  |..M P..N..P.<...|
00000120  85 c0 7d 11 eb c2 8b 4d  20 6a 01 e8 4b f7 ff ff  |..}....M j..K...|
00000130  33 ff 89 7d 20 83 7d fc  00 75 18 eb 4d 8b 4d fc  |3..} .}..u..M.M.|
00000140  e8 9d 57 04 00 8b f8 3b  fb 74 30 85 ff 0f 8c 66  |..W....;.t0....f|
00000150  01 00 00 ff 75 f8 56 e8  82 f4 ff ff 8b 4d fc 50  |....u.V......M.P|
00000160  56 e8 11 4f 04 00 8b 4d  fc 50 e8 aa 4e 04 00 50  |V..O...M.P..N..P|
00000170  e8 e7 f4 ff ff 85 c0 7d  11 eb c2 8b 4d fc 6a 01  |.......}....M.j.|
00000180  e8 f6 f6 ff ff 33 ff 89  7d fc 33 f6 39 75 fc 89  |.....3..}.3.9u..|
00000190  75 0c 74 0b 8b 75 fc 33  db 43 89 5d 0c eb 03 8b  |u.t..u.3.C.]....|
000001a0  5d 10 33 c0 39 45 20 74  2b ff 45 0c 8b 75 20 83  |].3.9E t+.E..u .|
000001b0  cb ff 83 7d 0c 02 75 1c  8b 4d fc 89 45 e8 00 fe  |...}..u..M..E...|
000001c0  ff ff 0e fe ff ff 3f 00  00 00 bd fa eb 1c 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

```

---

### Post by oldfred on 2010-05-27
msharelick - this is an old solved thread. Usually only those looking for solutions will look at this thread.

You should post the results.txt in your own thread. Are you booting from sda? I would also suggest installing grub legacy to sdb as I prefer having the bootloader on the same drive as the install. If you install to sdb then you have to set sdb as the boot drive (primary master) in BIOS. Some BIOS require a boot flag on a primary partition. Even though linux does not need it I would use gparted on liveCD right click to manage flags and add a boot flag to sdb1.

---

### Post by confused_user on 2010-05-31
....

---

### Post by drs305 on 2010-05-31
confused_user,

Since this is your first post in this thread, and the thread was already marked SOLVED by the OP, would you please start your own thread. State what problem you are having with Grub and then include the results as you posted them here. 

Thanks.

Added: Looks like it was done.

---

### Post by kannanni on 2010-06-02
hi Darko,

impossible to boot from ubuntu hdd,
instead i managed to boot from live cd and run the script u mentioned, i am posting this from the live cd :)


    ```
            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   156,299,263   156,092,416   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   605,483,007   605,480,960  83 Linux
/dev/sdc2         605,485,054   625,141,759    19,656,706   5 Extended
/dev/sdc5         605,485,056   625,141,759    19,656,704  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        06EAFF18EAFF032B                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9CF404F9F404D802                       ntfs       System Reserved               
/dev/sdb2        4E760E25760E0F01                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        c076aff2-cf8f-46c3-bdf3-cf0cc61bf5dd   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        ed08ddbf-e9d9-408c-ab7e-55d3c8640fa3   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdc1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set c076aff2-cf8f-46c3-bdf3-cf0cc61bf5dd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set c076aff2-cf8f-46c3-bdf3-cf0cc61bf5dd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c076aff2-cf8f-46c3-bdf3-cf0cc61bf5dd
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=c076aff2-cf8f-46c3-bdf3-cf0cc61bf5dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c076aff2-cf8f-46c3-bdf3-cf0cc61bf5dd
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=c076aff2-cf8f-46c3-bdf3-cf0cc61bf5dd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c076aff2-cf8f-46c3-bdf3-cf0cc61bf5dd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c076aff2-cf8f-46c3-bdf3-cf0cc61bf5dd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9cf404f9f404d802
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=c076aff2-cf8f-46c3-bdf3-cf0cc61bf5dd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=ed08ddbf-e9d9-408c-ab7e-55d3c8640fa3 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


  28.0GB: boot/grub/core.img
  19.5GB: boot/grub/grub.cfg
  28.1GB: boot/initrd.img-2.6.32-22-generic-pae
  28.0GB: boot/vmlinuz-2.6.32-22-generic-pae
  28.1GB: initrd.img
  28.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by darkod on 2010-06-02
> **kannanni said:**
> hi Darko,

impossible to boot from ubuntu hdd,
instead i managed to boot from live cd and run the script u mentioned, i am posting this from the live cd :)


Make the 320GB disk first option in the hdd boot order in BIOS. Then again boot in live mode and do:

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc

Restart and you should get grub2 working.

---

### Post by jfedor on 2010-06-03
> **darkod said:**
> Boot with the ubuntu cd, Try Ubuntu option if your hdd ubuntu is not booting. If it is, you can do this from the hdd ubuntu too. Download the script in my signature, move it on desktop for example, and execute it in terminal with:

sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with detailed info about your boot process. Post the content of that file here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above when writing the post).

Here are the results from the script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 483393 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #256 for /grub.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 479629 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb1 starts at sector 0. But according to the info 
                       from fdisk, sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.0 GB, 499989348352 bytes
255 heads, 63 sectors/track, 60786 cylinders, total 976541696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       498,014       497,952  83 Linux
/dev/sda2             498,015    29,794,863    29,296,849  83 Linux
/dev/sda3          29,794,864    45,417,910    15,623,047  82 Linux swap / Solaris
/dev/sda4          45,417,911   976,541,695   931,123,785  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b5590d0e-2d08-4a7a-8510-08f0e2cd671d   ext3       mbr                           
/dev/sda2        018c5214-5a80-469b-b3a4-63f271ca06d6   ext3                                     
/dev/sda3        9ee93eed-2231-4385-9125-b87b680812e9   swap                                     
/dev/sda4        4a5ea30e-237b-416d-a794-dcecd4cbdc39   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4637-7ED5                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8807-2C2B                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/mbr               ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/018c5214-5a80-469b-b3a4-63f271ca06d6 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/8807-2C2B         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


============================= sda1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 018c5214-5a80-469b-b3a4-63f271ca06d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-21-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-21-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-21-server
}
menuentry "Ubuntu, Linux 2.6.31-21-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-21-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-21-server
}
menuentry "Ubuntu, Linux 2.6.31-20-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-20-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-20-server
}
menuentry "Ubuntu, Linux 2.6.31-20-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-20-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-20-server
}
menuentry "Ubuntu, Linux 2.6.31-19-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-19-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-19-server
}
menuentry "Ubuntu, Linux 2.6.31-19-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-19-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-19-server
}
menuentry "Ubuntu, Linux 2.6.31-17-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-17-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-17-server
}
menuentry "Ubuntu, Linux 2.6.31-17-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-17-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-17-server
}
menuentry "Ubuntu, Linux 2.6.31-16-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-16-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-16-server
}
menuentry "Ubuntu, Linux 2.6.31-16-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-16-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-16-server
}
menuentry "Ubuntu, Linux 2.6.31-14-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-14-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro   quiet splash
	initrd	/initrd.img-2.6.31-14-server
}
menuentry "Ubuntu, Linux 2.6.31-14-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b5590d0e-2d08-4a7a-8510-08f0e2cd671d
	linux	/vmlinuz-2.6.31-14-server root=UUID=018c5214-5a80-469b-b3a4-63f271ca06d6 ro single 
	initrd	/initrd.img-2.6.31-14-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: grub/core.img
    .2GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-server
    .0GB: initrd.img-2.6.31-16-server
    .0GB: initrd.img-2.6.31-17-server
    .0GB: initrd.img-2.6.31-19-server
    .0GB: initrd.img-2.6.31-20-server
    .1GB: initrd.img-2.6.31-21-server
    .0GB: vmlinuz-2.6.31-14-server
    .0GB: vmlinuz-2.6.31-16-server
    .0GB: vmlinuz-2.6.31-17-server
    .0GB: vmlinuz-2.6.31-19-server
    .0GB: vmlinuz-2.6.31-20-server
    .0GB: vmlinuz-2.6.31-21-server

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc	/proc	proc	defaults	0	0
# / was on /dev/sda2 during installation
UUID=018c5214-5a80-469b-b3a4-63f271ca06d6	/	ext3	errors=remount-ro	0	1	# /dev/sda2
# /boot was on /dev/sda1 during installation
UUID=b5590d0e-2d08-4a7a-8510-08f0e2cd671d	/boot	ext3	defaults	0	2	# /dev/sda1
# /home was on /dev/sda4 during installation
UUID=4a5ea30e-237b-416d-a794-dcecd4cbdc39	/home	ext3	defaults	0	2	# /dev/sda4
# swap was on /dev/sda3 during installation
UUID=56c8381e-bc2f-46da-83a1-bb10fc3272c6	none	swap	sw	0	0	# /dev/sda3
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

```

---

### Post by oldfred on 2010-06-03
jfedor - Please see post #11. In your new thread what is your problem. Describe it as much as you can in the first post.

---

### Post by enduroktm300 on 2010-06-06
Sorry for the schizophrenic posts.  I truly am learning as I go  :)


```
/dev/sda2: PTTYPE="dos" 
/dev/sda5        NUlTTv-100X-x4G3-HLSp-BHXb-ONQs-yO7uzb LVM2_member                               
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod lvm
insmod ext2
set root='(ubuntutheserver-root)'
search --no-floppy --fs-uuid --set e913e614-8710-405f-b449-656ae0a0f977
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b6aadc3-b4ef-411f-8738-bb25378d06df
set locale_dir=($root)/grub/locale
set lang=C.UTF-8
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0b6aadc3-b4ef-411f-8738-bb25378d06df
    linux    /vmlinuz-2.6.32-21-generic-pae root=/dev/mapper/ubuntutheserver-root ro   quiet
    initrd    /initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0b6aadc3-b4ef-411f-8738-bb25378d06df
    echo    'Loading Linux 2.6.32-21-generic-pae ...'
    linux    /vmlinuz-2.6.32-21-generic-pae root=/dev/mapper/ubuntutheserver-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0b6aadc3-b4ef-411f-8738-bb25378d06df
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0b6aadc3-b4ef-411f-8738-bb25378d06df
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic-pae
    .0GB: vmlinuz-2.6.32-21-generic-pae
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  14 8b 00 85 c0 74 6b 8b  8f 50 12 00 00 51 8d 8c  |.....tk..P...Q..|
00000010  24 74 03 00 00 51 8d 8c  24 a8 00 00 00 51 8b 8f  |$t...Q..$....Q..|
00000020  a8 0f 00 00 51 8b 8f d4  0e 00 00 03 cb 51 8b 4c  |....Q........Q.L|
00000030  24 50 51 8b 8f a4 0f 00  00 51 8d 8f 38 11 00 00  |$PQ......Q..8...|
00000040  51 8b 4c 24 38 51 8b 8f  00 05 00 00 03 cb 51 8b  |Q.L$8Q........Q.|
00000050  4c 24 38 51 68 f4 dd 6f  68 8b ca 68 cc dd 6f 68  |L$8Qh..oh..h..oh|
00000060  ba a4 dd 6f 68 e8 b6 41  ff ff 83 c4 34 e9 84 00  |...oh..A....4...|
00000070  00 00 8b 87 50 12 00 00  50 8d 8c 24 74 03 00 00  |....P...P..$t...|
00000080  51 8b 8f a8 0f 00 00 8d  84 24 a8 00 00 00 50 8b  |Q........$....P.|
00000090  87 d4 0e 00 00 51 8b 4c  24 4c 03 c3 50 8b 87 a4  |.....Q.L$L..P...|
000000a0  0f 00 00 51 50 8b 44 24  34 8d 8c 24 88 00 00 00  |...QP.D$4..$....|
000000b0  51 8b 8f 00 05 00 00 50  8b 44 24 34 03 cb 51 50  |Q......P.D$4..QP|
000000c0  68 f4 dd 6f 68 8b ca 68  cc dd 6f 68 ba a4 dd 6f  |h..oh..h..oh...o|
000000d0  68 33 c0 e8 48 41 ff ff  83 c4 34 83 7c 24 38 00  |h3..HA....4.|$8.|
000000e0  74 14 8b b7 a8 0f 00 00  b9 28 00 00 00 8d bc 24  |t........(.....$|
000000f0  00 06 00 00 f3 a5 b9 28  00 00 00 8d b4 24 70 03  |.......(.....$p.|
00000100  00 00 8d bc 24 c0 04 00  00 f3 a5 8b 75 08 8b 7d  |....$.......u..}|
00000110  14 8d 4c 24 68 51 8d 55  10 52 8d 84 24 9c 00 00  |..L$hQ.U.R..$...|
00000120  00 50 8d 4c 24 40 51 8d  54 24 60 52 8d 44 24 40  |.P.L$@Q.T$`R.D$@|
00000130  50 8b 44 24 60 8d 8c 24  a8 01 00 00 51 8d 94 24  |P.D$`..$....Q..$|
00000140  7c 05 00 00 52 50 8b 86  d4 0e 00 00 8d 8c 24 c4  ||...RP........$.|
00000150  00 00 00 51 8b 8e a8 0f  00 00 8d 94 24 e8 04 00  |...Q........$...|
00000160  00 52 03 c3 50 8b 44 24  44 51 8b 0f 8d 94 24 8c  |.R..P.D$DQ....$.|
00000170  00 00 00 52 8b 96 00 11  00 00 50 8b 86 f4 10 00  |...R......P.....|
00000180  00 51 8b 08 52 51 e8 45  51 ff ff 8b 4c 24 68 83  |.Q..RQ.EQ...L$h.|
00000190  c4 48 66 85 c9 75 19 d9  ee d8 9e e4 09 00 00 df  |.Hf..u..........|
000001a0  e0 f6 c4 05 7a 0a 8b 54  24 2c 89 96 d4 09 00 00  |....z..T$,......|
000001b0  66 83 f9 03 75 19 d9 ee  d8 9e e8 09 00 00 00 3b  |f...u..........;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 f0 99 12 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by darkod on 2010-06-06
You are missing a large part of the start of the results file. Or at least it looks like that.

Also, from this incomplete info, it seems you installed ubuntu with LVM right?

---

### Post by kgorton on 2010-07-09
Darkod.  I know this Thread shows as closed,  but I did not see anywhere else to post and find some answers.   Here is my results.txt file.   One day all of a sudden my grub stopped working.  the best I can figure from what I see is that the GRUB2 sector on sda6 got corrupted.   i know i have grub 0.97 installed on sda2, but that has not been used since in a long time.  I just havent cleaned up the partition.  I have done the reinstall using 

sudo grub-install --root-directory=/mnt/sdc6

after appropriately mounting it.  and I have also used a copy of grub (not grub2) ans setup the MBR to boot to sda2 and do get that menu  although nothing works as the imageg and lernel files there point to nothing. 

any help would be apreciated


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 102674792 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   102,687,479       289,170  83 Linux
/dev/sda3         102,687,480 1,953,520,064 1,850,832,585   5 Extended
/dev/sda5         102,687,543   395,648,819   292,961,277  83 Linux
/dev/sda6         395,648,883   424,951,379    29,302,497  83 Linux
/dev/sda7         976,960,908 1,953,520,064   976,559,157  83 Linux
/dev/sda8         957,425,868   976,960,844    19,534,977  82 Linux swap / Solaris
/dev/sda9         424,951,443   620,269,649   195,318,207  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1                                              squashfs                                 
/dev/loop2                                              squashfs                                 
/dev/sda1        C664997964996D45                       ntfs                                     
/dev/sda2        97262b9f-67ed-4870-b79d-a8301bc535e0   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e2516c08-9ddf-4a1f-8f8e-b5d19e7e2247   reiserfs                                 
/dev/sda6        48570eb2-26f9-4a15-a6e7-25bfcaac83e5   ext4                                     
/dev/sda7        198a592f-370e-4c62-a17e-f61b565e28f9   reiserfs                                 
/dev/sda8        b8ddbab1-10cb-4779-8dbb-15a550c5be1e   swap                                     
/dev/sda9        72b72833-030a-414f-8bc4-ceaac1fc44b8   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /lib/unionfs/usr         squashfs   (rw)
/dev/loop1       /lib/unionfs/firmware    squashfs   (rw)
/dev/loop2       /lib/unionfs/modules     squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

============================= sda2/grub/menu.lst: =============================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=97262b9f-67ed-4870-b79d-a8301bc535e0

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-9-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-9-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-7-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/vmlinuz-2.6.27-7-generic root=UUID=ab992d88-aa7d-4919-ad36-4b7bf059a1e0 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		97262b9f-67ed-4870-b79d-a8301bc535e0
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=================== sda2: Location of files loaded by Grub: ===================


  52.5GB: grub/menu.lst
  52.5GB: grub/stage2
  52.4GB: initrd.img-2.6.27-7-generic
  52.4GB: initrd.img-2.6.27-9-generic
  52.4GB: vmlinuz-2.6.27-7-generic
  52.4GB: vmlinuz-2.6.27-9-generic

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	echo	'Loading Linux 2.6.31-19-generic ...'
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 48570eb2-26f9-4a15-a6e7-25bfcaac83e5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c664997964996d45
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=48570eb2-26f9-4a15-a6e7-25bfcaac83e5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=72b72833-030a-414f-8bc4-ceaac1fc44b8 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=b8ddbab1-10cb-4779-8dbb-15a550c5be1e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda7	/media/storage	reiserfs	defaults,rw,nosuid,nodev	0	0

=================== sda6: Location of files loaded by Grub: ===================


 203.6GB: boot/grub/core.img
 204.0GB: boot/grub/grub.cfg
 215.8GB: boot/initrd.img-2.6.31-19-generic
 215.5GB: boot/initrd.img-2.6.31-20-generic
 204.7GB: boot/initrd.img-2.6.31-21-generic
 213.0GB: boot/initrd.img-2.6.31-22-generic
 215.0GB: boot/initrd.img-2.6.32-23-generic
 202.8GB: boot/vmlinuz-2.6.31-19-generic
 215.5GB: boot/vmlinuz-2.6.31-20-generic
 204.7GB: boot/vmlinuz-2.6.31-21-generic
 216.9GB: boot/vmlinuz-2.6.31-22-generic
 212.7GB: boot/vmlinuz-2.6.32-23-generic
 215.0GB: initrd.img
 213.0GB: initrd.img.old
 212.7GB: vmlinuz
 216.9GB: vmlinuz.old
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

```

---

### Post by drs305 on 2010-07-09
kgorton,]

Welcome to the Ubuntu forums.

You have mixed various parts of a grub-install. The command you cited would have installed Grub2 to a partition instead of the MBR, which is generally not what you want to do.  On the plus side, it shouldn't be too hard to fix.

Boot from a recent LiveCD and mount sda6 on /mnt:
```
sudo mount /dev/sda6 /mnt
```
Then install grub to the MBR, and place the files in sda6 with the following command. Note that you do not designate the partition in the command, which will ensure Grub2 is installed in the MBR. The configuration files will be placed in /boot/grub of sda6 since that is the partition that is mounted:
```
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by kgorton on 2010-07-10
Thanks.  did not work,  but since the thread is actually closed i reposted at

[http://ubuntuforums.org/showthread.php?p=9571888](http://ubuntuforums.org/showthread.php?p=9571888)

---

