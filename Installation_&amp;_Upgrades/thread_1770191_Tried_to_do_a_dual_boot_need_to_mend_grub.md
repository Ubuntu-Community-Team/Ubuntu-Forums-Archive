---
title: "Tried to do a dual boot need to mend grub"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by NoNameWill on 2011-05-28
I have installed knoppix in a partition I created through gparted. I selected to have knoppix but in a bootloader. Now I can't get into ubuntu. I need to add it to the grub but I am doing it wrong. 

So what do I need to do to remedy this? I am currently in a live cd as knoppix is booting to 3d and it is scrambling my screen.

---

### Post by drs305 on 2011-05-28
From an Ubuntu LiveCd or other running linux system, click on the "BIS" link in my signature line, download and run the boot info script and post the contents of the RESULTS.txt

It will show us the status of your boot files.

---

### Post by NoNameWill on 2011-05-28
Thank you!

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 15666 of /dev/sda1 for its 
                       second stage. According to the info in the boot 
                       sector, sda1 starts at sector 0. But according to the 
                       info from fdisk, sda1 starts at sector 2760.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 6.0
    Boot files:        /boot/grub/menu.lst /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 4105 MB, 4105175040 bytes
37 heads, 37 sectors/track, 5856 cylinders, total 8017920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,760     8,017,919     8,015,160   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   124,180,479   124,178,432  83 Linux
/dev/sdb2         226,584,574   234,440,703     7,856,130   5 Extended
/dev/sdb5         226,584,576   234,440,703     7,856,128  82 Linux swap / Solaris
/dev/sdb3         124,180,480   226,582,527   102,402,048  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0A13-2049                              vfat       New Volume
/dev/sdb1        67888204-8b98-4ea6-b886-3e572f34abdd   ext4       
/dev/sdb3        9e8e823a-a0fa-4c10-a403-af544078728f   reiserfs   
/dev/sdb5        7efd9a31-c4a4-42f1-a259-fcb82040cf8a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 67888204-8b98-4ea6-b886-3e572f34abdd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 67888204-8b98-4ea6-b886-3e572f34abdd
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 67888204-8b98-4ea6-b886-3e572f34abdd
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=67888204-8b98-4ea6-b886-3e572f34abdd ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 67888204-8b98-4ea6-b886-3e572f34abdd
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=67888204-8b98-4ea6-b886-3e572f34abdd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 67888204-8b98-4ea6-b886-3e572f34abdd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 67888204-8b98-4ea6-b886-3e572f34abdd
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=67888204-8b98-4ea6-b886-3e572f34abdd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=7efd9a31-c4a4-42f1-a259-fcb82040cf8a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.608036041 = 0.652873728    boot/grub/core.img                             1
   0.608043671 = 0.652881920    boot/grub/grub.cfg                             1
   2.394546509 = 2.571124736    boot/initrd.img-2.6.38-8-generic               2
   0.598419189 = 0.642547712    boot/vmlinuz-2.6.38-8-generic                 22
   2.394546509 = 2.571124736    initrd.img                                     2
   0.598419189 = 0.642547712    vmlinuz                                       22

=========================== sdb3/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
default 0
timeout 30
color cyan/blue white/blue

title KNOPPIX
root (hd0,2)
kernel /boot/vmlinuz root=/dev/sda3 rootwait lang=us apm=power-off nomce libata.force=noncq tz=localtime loglevel=1  rw
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# DEFAULT BASE FSTAB, UNCONFIGURED
proc       /proc         proc       noauto             0 0
sysfs      /sys          sysfs      noauto             0 0
/dev/sda3 / reiserfs relatime 0 0
/dev/sda5 none swap defaults 0 0
# Added by KNOPPIX
/dev/sr0 /media/sr0 auto ro,noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sdb1 /media/sdb1 vfat noauto,users,exec,umask=000,shortname=winnt,uid=knoppix,gid=knoppix 0 0
# Added by KNOPPIX
/dev/sda3 /media/sda3 reiserfs noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda1 /media/sda1 ext4 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda5 none swap defaults 0 0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst                             0
            ?? = ??             boot/grub/stage2                               1
            ?? = ??             boot/vmlinuz                                   5
            ?? = ??             boot/vmlinuz-2.6.37                            1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  53 01 56 1e 1a 00 b1 6f  e1 00 57 f0 1c 01 56 a5  |S.V....o..W...V.|
00000010  36 01 04 9b 63 02 31 b6  32 02 32 55 36 00 5c ac  |6...c.1.2.2U6.\.|
00000020  f3 00 1e 11 a8 00 59 9e  74 00 92 ae 67 01 0d 8e  |......Y.t...g...|
00000030  b4 01 55 8e b4 01 ab af  48 01 3d 8e b4 01 25 8e  |..U.....H.=...%.|
00000040  b4 01 6d 8e b4 01 20 ef  35 00 c6 1e 79 00 14 1a  |..m... .5...y...|
00000050  0f 03 ce cb ec 00 6e 5d  89 01 e2 59 13 00 0b 20  |......n]...Y... |
00000060  33 03 68 0b 51 02 58 92  9d 01 a6 00 3a 01 eb 48  |3.h.Q.X.....:..H|
00000070  56 02 d4 48 56 02 02 49  56 02 a6 48 56 02 61 48  |V..HV..IV..HV.aH|
00000080  56 02 78 48 56 02 8f 48  56 02 bd 48 56 02 19 49  |V.xHV..HV..HV..I|
00000090  56 02 95 03 5c 03 69 c0  52 03 c1 6d ae 00 75 1c  |V...\.i.R..m..u.|
000000a0  dc 00 1e 35 ae 02 2c c3  75 00 5d bb a0 02 63 93  |...5..,.u.]...c.|
000000b0  cb 02 35 7b 75 00 4e 1e  8c 02 0d 4f 34 01 32 bc  |..5{u.N....O4.2.|
000000c0  c9 01 49 bc c9 01 0c 83  3f 00 97 77 e4 00 01 01  |..I.....?..w....|
000000d0  92 01 d7 54 82 02 53 d9  a9 01 f9 b7 ce 00 d2 a0  |...T..S.........|
000000e0  c4 02 8f 47 5a 03 73 fc  7d 00 37 d9 f7 02 f8 19  |...GZ.s.}.7.....|
000000f0  6a 01 55 e8 45 03 20 c3  39 00 30 be 52 00 7b 7a  |j.U.E. .9.0.R.{z|
00000100  87 00 a4 a9 25 00 ca f5  ec 00 ab e1 53 00 1f 24  |....%.......S..$|
00000110  fe 00 07 24 fe 00 b5 50  85 00 9b 56 43 01 52 7a  |...$...P...VC.Rz|
00000120  48 03 53 4d 87 02 97 f3  b2 02 2c 27 3e 03 81 ff  |H.SM......,'>...|
00000130  60 01 a9 c7 86 01 c0 c7  86 01 d7 c7 86 01 92 c7  |`...............|
00000140  86 01 64 c7 86 01 7b c7  86 01 08 c7 86 01 4d c7  |..d...{.......M.|
00000150  86 01 36 c7 86 01 67 cd  d2 01 1f c7 86 01 e8 23  |..6...g........#|
00000160  24 03 b7 83 9b 01 54 02  fc 01 0f 7f 48 03 82 35  |$.....T.....H..5|
00000170  9a 00 83 6a 66 00 32 dc  dc 02 36 2b 06 03 f1 fc  |...jf.2...6+....|
00000180  77 01 3f c1 db 00 ab e8  1a 00 50 81 cc 02 4e 9a  |w.?.......P...N.|
00000190  21 03 35 3d b7 02 38 c9  56 01 2c 4f 1a 01 1b bd  |!.5=..8.V.,O....|
000001a0  89 00 ed 24 43 02 9b b5  30 00 40 01 88 01 64 ed  |...$C...0.@...d.|
000001b0  21 01 b8 61 20 02 1b 92  80 01 36 f8 57 02 00 fe  |!..a .....6.W...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e0 77 00 00 00  |............w...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by drs305 on 2011-05-28
I can't really help much with syslinux on sda or grub legacy on sdb3. But I can help you get Grub 2 installed on sdb and your Ubuntu partition on sdb1 if that is what you want.

You will need to use a Natty LiveCD. Boot the LiveCD, then mount your Ubuntu partition and install Grub 2. Do *not* include the partition number in the second command:
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdb
```

Reboot, and as it boots you may need to enter BIOS to ensure the computer boots the sdb (120 GB Ubuntu) drive first.

---

### Post by NoNameWill on 2011-05-28
That worked. So what do I need to do to get Knoppix in the grub?

---

### Post by drs305 on 2011-05-28
> **NoNameWill said:**
> That worked. So what do I need to do to get Knoppix in the grub?


I'm not familiar with the knoppix menu structure. If it was a standard entry in Grub 2 just running "sudo update-grub" should find it and put it into the menu. 

Based on what the Grub legacy menu had, it might look something like this:
> 
menuentry "Knoppix" {
set root=([COLOR="Red"]hd0,3[/COLOR])
linux /boot/vmlinuz root=/dev/sd[COLOR="Red"]a3[/COLOR] rootwait lang=us apm=power-off nomce libata.force=noncq tz=localtime loglevel=1  rw
}

G2 counts the first hard drive as 0, but the first partition as 1. Change the red items above to the appropriate values.

You could paste this into /etc/grub.d/40_custom and save the file. Run "sudo update-grub" to include it in the grub menu but I have doubts it will work. There is usually an "initrd" line in a G2 entry, but I didn't see it in the Grub Legacy one so I don't know. 

The best thing to do would be to search the forums. I'm sure there are people using Knoppix and G2.

Added: See the ISO link in my signature line if you are trying to boot ISOs.

---

### Post by NoNameWill on 2011-05-28
I just did that I editted 

the grub.d/40_custom 

to menuentry "Knoppix" {
set root=([COLOR=Red]hd0,2[/COLOR])
linux /boot/vmlinuz root=/dev/sd[COLOR=Red]a3[/COLOR] rootwait lang=us apm=power-off nomce libata.force=noncq tz=localtime loglevel=1  rw
}

Then updated grub

this is what I got 

```
will@will-Mobilepc:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Debian GNU/Linux (6.0) on /dev/sda3
done

```


I am going to reboot now see what happens. Thank you again.

---

### Post by NoNameWill on 2011-05-28
Going to mark this one as solved. Didn't need to edit 40_custom file. I may have inputted the wrong info. But it did show up in grub just didn't load anything. 

Just the update-grub command as that added the knoppix partition.

---

