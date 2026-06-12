---
title: "Stuck at Natty Grub Rescue Prompt"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by ancaleth on 2011-05-06
Can anybody help with this?

I have tried to follow the different possibilites discussed here [http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/]("http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/#comment-44944")

But I am not getting anywhere.

Btw, this is not my screenshot. Mine shows GNU GRUB version 1.98-1ubuntu5.



[IMG]http://aaron-kelley.net/wp-content/uploads/2011/04/grub.png[/IMG]

---

### Post by kansasnoob on 2011-05-06
> **ancaleth said:**
> Can anybody help with this?

I have tried to follow the different possibilites discussed here [http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/]("http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/#comment-44944")

But I am not getting anywhere.

Btw, this is not my screenshot. Mine shows GNU GRUB version 1.98-1ubuntu5.



[IMG]http://aaron-kelley.net/wp-content/uploads/2011/04/grub.png[/IMG]

Post the info requested in post #2 of this thread.

---

### Post by ancaleth on 2011-05-06
```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 115350296 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,800,325   102,478,634    71,678,310   7 NTFS / exFAT / HPFS
/dev/sda4         102,481,918 1,250,256,895 1,147,774,978   f W95 Extended (LBA)
/dev/sda5         145,484,703 1,231,826,943 1,086,342,241   7 NTFS / exFAT / HPFS
/dev/sda6       1,231,828,992 1,250,256,895    18,427,904  82 Linux swap / Solaris
/dev/sda7         102,481,920   145,481,727    42,999,808  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        943272BC3272A2C2                       ntfs       RECOVERY
/dev/sda3        EC2E74FF2E74C3DC                       ntfs       OS
/dev/sda5        01CBAB548FF39920                       ntfs       Data
/dev/sda6        efc8e491-924c-480b-9c76-af95d81e5436   swap       linux swap
/dev/sda7        84ef4cda-5f52-4d8b-b8f3-f225d18ab31e   ext4       
/dev/sdb1        364C70584C7014B9                       ntfs       BigMama

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/84ef4cda-5f52-4d8b-b8f3-f225d18ab31e ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/BigMama           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=/home/ubuntu/aufs ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 10.04 LTS, kernel 2.6.38-8-generic Default
root        (hd0,0)
kernel        /boot/vmlinuz root=/home/ubuntu/aufs ro quiet splash 
initrd        /boot/initrd.img

title        Ubuntu 10.04 LTS, kernel 2.6.38-8-generic Default (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz root=/home/ubuntu/aufs ro  single
initrd        /boot/initrd.img

title        Ubuntu 10.04 LTS, kernel 2.6.35-28-generic Previous
root        (hd0,0)
kernel        /boot/vmlinuz.old root=/home/ubuntu/aufs ro quiet splash 
initrd        /boot/initrd.img.old

title        Ubuntu 10.04 LTS, kernel 2.6.35-28-generic Previous (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz.old root=/home/ubuntu/aufs ro  single
initrd        /boot/initrd.img.old

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
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
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=84ef4cda-5f52-4d8b-b8f3-f225d18ab31e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=84ef4cda-5f52-4d8b-b8f3-f225d18ab31e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=84ef4cda-5f52-4d8b-b8f3-f225d18ab31e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=84ef4cda-5f52-4d8b-b8f3-f225d18ab31e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 943272BC3272A2C2
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=84ef4cda-5f52-4d8b-b8f3-f225d18ab31e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=efc8e491-924c-480b-9c76-af95d81e5436 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  54.996124268 = 59.051638784   boot/grub/core.img                             1
  60.338973999 = 64.788480000   boot/grub/grub.cfg                             1
  54.998992920 = 59.054718976   boot/grub/menu.lst                             2
  49.932132721 = 53.614219264   boot/initrd.img-2.6.35-28-generic              2
  60.414062500 = 64.869105664   boot/initrd.img-2.6.38-8-generic               2
  57.558734894 = 61.803220992   boot/vmlinuz-2.6.35-28-generic                 1
  50.847965240 = 54.597586944   boot/vmlinuz-2.6.38-8-generic                  1
  60.414062500 = 64.869105664   initrd.img                                     2
  49.932132721 = 53.614219264   initrd.img.old                                 2
  50.847965240 = 54.597586944   vmlinuz                                        1
  57.558734894 = 61.803220992   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  6a de 23 61 00 00 80 01  |........j.#a....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda4

00000000  89 b1 40 8f 3c 4b 94 33  32 79 0c b9 f2 a8 04 d7  |..@.<K.32y......|
00000010  d5 19 e1 4e 6b 49 c1 c8  dd e7 a4 bc 4c 16 68 12  |...NkI......L.h.|
00000020  a2 b7 8b 7e df ad 3b 51  a4 b1 62 09 88 31 83 59  |...~..;Q..b..1.Y|
00000030  21 42 1f d8 75 a9 9f 07  5e 3e b3 03 bd b8 f8 94  |!B..u...^>......|
00000040  d1 79 f0 ab 72 2f 57 62  07 12 57 57 89 db ac 53  |.y..r/Wb..WW...S|
00000050  bc 7c 3e 28 d6 e5 03 96  52 62 5f 90 41 57 ac 45  |.|>(....Rb_.AW.E|
00000060  dd 61 9b 3c 42 9c 3f 1b  a9 48 cc d8 94 6f 72 c7  |.a.<B.?..H...or.|
00000070  3f cc 5c 68 54 78 8b eb  10 15 07 42 aa 5a c6 f2  |?.\hTx.....B.Z..|
00000080  7f 3d b2 b9 80 3b b8 6f  f3 cf d1 bd 3d e7 d1 8b  |.=...;.o....=...|
00000090  83 f2 0f 95 9f 3f eb be  2b f4 a0 95 52 70 a9 c4  |.....?..+...Rp..|
000000a0  a0 1b 5f 37 98 a9 9a 58  f6 88 77 9d 20 a9 17 9d  |.._7...X..w. ...|
000000b0  ab 54 91 1b 62 3a 03 f5  e2 dc 84 95 4e 5d ed 59  |.T..b:......N].Y|
000000c0  d3 b4 36 89 db 0b 10 5d  9a 72 aa e9 1b 06 13 57  |..6....].r.....W|
000000d0  e4 39 bd b1 58 56 03 7a  0e cb d7 5d 54 8e 85 4a  |.9..XV.z...]T..J|
000000e0  a1 7c d3 03 b5 23 cf ba  5d 14 9a 21 ef 47 11 80  |.|...#..]..!.G..|
000000f0  e8 10 2f ae 66 aa a4 d8  84 13 ea 58 c8 67 fc 83  |../.f......X.g..|
00000100  39 cb d9 7f 8a 0d 0a 76  a2 8f cf 50 3d f9 54 14  |9......v...P=.T.|
00000110  98 08 30 ed 96 95 d7 7a  60 14 a3 54 75 43 8a 2c  |..0....z`..TuC.,|
00000120  de d3 1b 7c 71 75 8a d8  12 94 54 68 a6 90 52 21  |...|qu....Th..R!|
00000130  4c c1 c1 d2 7e f8 ab f3  8a a5 d5 b2 4b 8c 6f 46  |L...~.......K.oF|
00000140  00 3a ad 9f 25 21 32 ef  be 91 55 43 6d 8d 8d 0e  |.:..%!2...UCm...|
00000150  70 f4 7f 66 09 78 89 aa  67 77 a7 aa 97 f0 c7 e3  |p..f.x..gw......|
00000160  16 b4 15 74 ad 84 38 3e  96 1a bf 29 8c 12 d5 e8  |...t..8>...)....|
00000170  57 a6 96 43 8f 6c 56 22  26 9e 70 92 c2 89 29 27  |W..C.lV"&.p...)'|
00000180  35 78 a1 a8 d7 63 a2 40  6a 10 4a 4b f8 af 24 24  |5x...c.@j.JK..$$|
00000190  8e d3 52 95 f5 45 73 ea  c8 25 aa 78 13 c7 30 f8  |..R..Es..%.x..0.|
000001a0  ee 29 ba 47 4e 53 e0 ad  ad e9 6d eb f6 f4 91 fa  |.).GNS....m.....|
000001b0  8c ef 8d 8c 85 3d 28 fa  a7 ff f5 50 52 c9 00 fe  |.....=(....PR...|
000001c0  ff ff 07 fe ff ff a1 2b  90 02 61 44 c0 40 00 fe  |.......+..aD.@..|
000001d0  ff ff 05 fe ff ff 02 70  50 43 00 38 19 01 00 00  |.......pPC.8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

Thanks for the help.

---

### Post by Dutch70 on 2011-05-06
Please start your own thread so that you & the OP can get the undivided attention your problem deserves. 
Although I'm sure you meant no harm, this is thread hijacking.

Give this a quick read first.
[how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by drs305 on 2011-05-06
Applicable posts moved to new thread.

---

### Post by drs305 on 2011-05-06
Grub2 is not pointing to the correct partition.

Boot the LiveCD, mount your Ubuntu partition (sda7), then run the 'reinstall' command.
```

sudo mount /dev/sda7 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
Note you do NOT include the partition number in the second command.

Reboot and it should work correctly. You have both Grub and Grub2 installed but we can deal with that conflict if it creates a problem.

---

### Post by ancaleth on 2011-05-06
Sorry about the thread, I used it because the problem had evolved from the original problem posted there.

This is what the commands above returned. 

```
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
Unrecognized option `--boot-directory=/mnt/boot'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.

```

---

### Post by oldfred on 2011-05-06
Is your liveCD not 11.04?

They have changed the root to boot and drs305 assumed you have the new liveCD so it should be boot. 

Try this, but perhaps some of the issues we are seeing is users with the wrong CD.

This is the same except using root not boot.

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by drs305 on 2011-05-06
If the "--root-directory" switch *oldfred* suggested still doesn't boot, it may be necessary to purge all the Grub variations and pick a version to install. Part of the problem if it still doesn't boot may be that we have remnants of Grub legacy as well as several versions of Grub 2 in your installation. 

This would be easiest by using the Grub version on the LiveCD you are using. If you are still having problems let us know which LiveCD you are using (Natty, Maverick, etc).

---

### Post by ancaleth on 2011-05-06
No, sorry, it is a 10.04 lts CD. The only other computer in the house is a Mac and it has decided it does not want to write the 11.04 iso to a disk.

I have tried to run that command several times. However, upon reboot, nothing has changed although it indicates that the installation has worked.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
mount: /dev/sda7 already mounted or /mnt busy
mount: according to mtab, /dev/sda7 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.

```

---

### Post by oldfred on 2011-05-06
Would you please repost boot script, just for curiosity. Want to see if it shows any error.

I think if you cannot easily get an 11.04 liveCD then the full chroot method may work.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by drs305 on 2011-05-06
@ oldfred: Sorry, didn't see your post before adding this one. It took me a bit of time to type it up. I've added changing the repository so the OP can use a Maverick CD but still install the Natty Grub 1.99.

I'd recommend getting rid of all grub versions and reinstalling them. From the LiveCD, you will use the 'chroot' procedure to allow the CD system files alter your real installation's files. Because you have a Maverick CD, we will have to change the repositories to point to Natty's packages. Then we will chroot, purge the Grub files, and install Grub 1.99 (grub-pc).

```

sudo umount /dev/sda7 # Just in case it is already mounted
sudo mkdir /mnt/temp 
sudo mount /dev/sda7 /mnt/temp 
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet. If you don't have it, continue anyway.
sudo chroot /mnt/temp
```

Next we will change the CD's sources.list to look for Natty packages:
```
gedit /etc/apt/sources.list
```

Find the line which includes "main" and change the release from Maverick to Natty. Note the text in dark red will be different for you:

> deb [COLOR="DarkRed"]http://www.gtlib.gatech.edu[/COLOR]/pub/ubuntu/ **natty** main restricted universe

Save the file, then continue:
```
apt-get update
```


This should run, updating the repositories and ensuring you have an internet connection. If you don't have a connection, don't continue. The first command may produce a message stating grub is not installed. That's ok.

```
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
```

You will be asked for kernel options. If you don't know what to put. TAB to OK and ENTER.

When asked where to install, use the SPACEBAR to designatethe first entry:  **sda**. Do NOT select a partition. TAB to OK, ENTER.

Exit chroot, umount the system folders, and reboot:
```
exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```

---

### Post by ancaleth on 2011-05-06
It won`t unmount the partition... and I am not using it, so I don`t know why it`s busy =/


```
ubuntu@ubuntu:~$ sudo umount /dev/sda7
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```


---------------


New boot script version
```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 115350296 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,800,325   102,478,634    71,678,310   7 NTFS / exFAT / HPFS
/dev/sda4         102,481,918 1,250,256,895 1,147,774,978   f W95 Extended (LBA)
/dev/sda5         145,484,703 1,231,826,943 1,086,342,241   7 NTFS / exFAT / HPFS
/dev/sda6       1,231,828,992 1,250,256,895    18,427,904  82 Linux swap / Solaris
/dev/sda7         102,481,920   145,481,727    42,999,808  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        943272BC3272A2C2                       ntfs       RECOVERY
/dev/sda3        EC2E74FF2E74C3DC                       ntfs       OS
/dev/sda5        01CBAB548FF39920                       ntfs       Data
/dev/sda6        efc8e491-924c-480b-9c76-af95d81e5436   swap       linux swap
/dev/sda7        84ef4cda-5f52-4d8b-b8f3-f225d18ab31e   ext4       
/dev/sdb1        364C70584C7014B9                       ntfs       BigMama

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev             /mnt/temp/dev            none       (rw,bind)
/dev             /mnt/temp/dev            none       (rw,bind)
/dev/pts         /mnt/temp/dev/pts        none       (rw,bind)
/dev/pts         /mnt/temp/dev/pts        none       (rw,bind)
/dev/sda5        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /mnt/temp                ext4       (rw)
/dev/sdb1        /media/BigMama           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=/home/ubuntu/aufs ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 10.04 LTS, kernel 2.6.38-8-generic Default
root        (hd0,0)
kernel        /boot/vmlinuz root=/home/ubuntu/aufs ro quiet splash 
initrd        /boot/initrd.img

title        Ubuntu 10.04 LTS, kernel 2.6.38-8-generic Default (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz root=/home/ubuntu/aufs ro  single
initrd        /boot/initrd.img

title        Ubuntu 10.04 LTS, kernel 2.6.35-28-generic Previous
root        (hd0,0)
kernel        /boot/vmlinuz.old root=/home/ubuntu/aufs ro quiet splash 
initrd        /boot/initrd.img.old

title        Ubuntu 10.04 LTS, kernel 2.6.35-28-generic Previous (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz.old root=/home/ubuntu/aufs ro  single
initrd        /boot/initrd.img.old

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
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
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=84ef4cda-5f52-4d8b-b8f3-f225d18ab31e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=84ef4cda-5f52-4d8b-b8f3-f225d18ab31e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=84ef4cda-5f52-4d8b-b8f3-f225d18ab31e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=84ef4cda-5f52-4d8b-b8f3-f225d18ab31e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 84ef4cda-5f52-4d8b-b8f3-f225d18ab31e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 943272BC3272A2C2
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=84ef4cda-5f52-4d8b-b8f3-f225d18ab31e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=efc8e491-924c-480b-9c76-af95d81e5436 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  54.996124268 = 59.051638784   boot/grub/core.img                             1
  60.338973999 = 64.788480000   boot/grub/grub.cfg                             1
  54.998992920 = 59.054718976   boot/grub/menu.lst                             2
  49.932132721 = 53.614219264   boot/initrd.img-2.6.35-28-generic              2
  60.414062500 = 64.869105664   boot/initrd.img-2.6.38-8-generic               2
  57.558734894 = 61.803220992   boot/vmlinuz-2.6.35-28-generic                 1
  50.847965240 = 54.597586944   boot/vmlinuz-2.6.38-8-generic                  1
  60.414062500 = 64.869105664   initrd.img                                     2
  49.932132721 = 53.614219264   initrd.img.old                                 2
  50.847965240 = 54.597586944   vmlinuz                                        1
  57.558734894 = 61.803220992   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  6a de 23 61 00 00 80 01  |........j.#a....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda4

00000000  89 b1 40 8f 3c 4b 94 33  32 79 0c b9 f2 a8 04 d7  |..@.<K.32y......|
00000010  d5 19 e1 4e 6b 49 c1 c8  dd e7 a4 bc 4c 16 68 12  |...NkI......L.h.|
00000020  a2 b7 8b 7e df ad 3b 51  a4 b1 62 09 88 31 83 59  |...~..;Q..b..1.Y|
00000030  21 42 1f d8 75 a9 9f 07  5e 3e b3 03 bd b8 f8 94  |!B..u...^>......|
00000040  d1 79 f0 ab 72 2f 57 62  07 12 57 57 89 db ac 53  |.y..r/Wb..WW...S|
00000050  bc 7c 3e 28 d6 e5 03 96  52 62 5f 90 41 57 ac 45  |.|>(....Rb_.AW.E|
00000060  dd 61 9b 3c 42 9c 3f 1b  a9 48 cc d8 94 6f 72 c7  |.a.<B.?..H...or.|
00000070  3f cc 5c 68 54 78 8b eb  10 15 07 42 aa 5a c6 f2  |?.\hTx.....B.Z..|
00000080  7f 3d b2 b9 80 3b b8 6f  f3 cf d1 bd 3d e7 d1 8b  |.=...;.o....=...|
00000090  83 f2 0f 95 9f 3f eb be  2b f4 a0 95 52 70 a9 c4  |.....?..+...Rp..|
000000a0  a0 1b 5f 37 98 a9 9a 58  f6 88 77 9d 20 a9 17 9d  |.._7...X..w. ...|
000000b0  ab 54 91 1b 62 3a 03 f5  e2 dc 84 95 4e 5d ed 59  |.T..b:......N].Y|
000000c0  d3 b4 36 89 db 0b 10 5d  9a 72 aa e9 1b 06 13 57  |..6....].r.....W|
000000d0  e4 39 bd b1 58 56 03 7a  0e cb d7 5d 54 8e 85 4a  |.9..XV.z...]T..J|
000000e0  a1 7c d3 03 b5 23 cf ba  5d 14 9a 21 ef 47 11 80  |.|...#..]..!.G..|
000000f0  e8 10 2f ae 66 aa a4 d8  84 13 ea 58 c8 67 fc 83  |../.f......X.g..|
00000100  39 cb d9 7f 8a 0d 0a 76  a2 8f cf 50 3d f9 54 14  |9......v...P=.T.|
00000110  98 08 30 ed 96 95 d7 7a  60 14 a3 54 75 43 8a 2c  |..0....z`..TuC.,|
00000120  de d3 1b 7c 71 75 8a d8  12 94 54 68 a6 90 52 21  |...|qu....Th..R!|
00000130  4c c1 c1 d2 7e f8 ab f3  8a a5 d5 b2 4b 8c 6f 46  |L...~.......K.oF|
00000140  00 3a ad 9f 25 21 32 ef  be 91 55 43 6d 8d 8d 0e  |.:..%!2...UCm...|
00000150  70 f4 7f 66 09 78 89 aa  67 77 a7 aa 97 f0 c7 e3  |p..f.x..gw......|
00000160  16 b4 15 74 ad 84 38 3e  96 1a bf 29 8c 12 d5 e8  |...t..8>...)....|
00000170  57 a6 96 43 8f 6c 56 22  26 9e 70 92 c2 89 29 27  |W..C.lV"&.p...)'|
00000180  35 78 a1 a8 d7 63 a2 40  6a 10 4a 4b f8 af 24 24  |5x...c.@j.JK..$$|
00000190  8e d3 52 95 f5 45 73 ea  c8 25 aa 78 13 c7 30 f8  |..R..Es..%.x..0.|
000001a0  ee 29 ba 47 4e 53 e0 ad  ad e9 6d eb f6 f4 91 fa  |.).GNS....m.....|
000001b0  8c ef 8d 8c 85 3d 28 fa  a7 ff f5 50 52 c9 00 fe  |.....=(....PR...|
000001c0  ff ff 07 fe ff ff a1 2b  90 02 61 44 c0 40 00 fe  |.......+..aD.@..|
000001d0  ff ff 05 fe ff ff 02 70  50 43 00 38 19 01 00 00  |.......pPC.8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```> **oldfred said:**
> Would you please repost boot script, just for curiosity. Want to see if it shows any error.

I think if you cannot easily get an 11.04 liveCD then the full chroot method may work.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

As for chroot, I have also tried this a few times. It does not work and returns this

```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda7 /mnt
root@ubuntu:~# mount --bind /dev /mnt/dev
root@ubuntu:~# mount --bind /proc /mnt/proc
root@ubuntu:~# mount --bind /sys /mnt/sys
root@ubuntu:~# mount --bind /usr/ /mnt/usr
root@ubuntu:~# chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error
```

I am not quite sure whether a 32/ or 64/bit version is on the CD. Might that be causing interference with the chroot?

---

### Post by drs305 on 2011-05-06
> **ancaleth said:**
> 
I am not quite sure whether a 32/ or 64/bit version is on the CD. Might that be causing interference with the chroot?

Yes, that is the most likely reason.

It would make things much simpler if you can get a copy of the Natty LiveCD in the correct architecture but to chroot you will at least need to have a compatible CD (64/64 or 32/32) to chroot.

---

### Post by oldfred on 2011-05-06
It is good to know that the new version of boot script shows grub version and that older grub2 (v1.97-1.98 )  in the MBR will not boot 1.99. So liveCD does have to be same version.

---

### Post by ancaleth on 2011-05-06
I should be able to obtain a natty CD with 64bit tomorrow and will try the chroot again and let you know. thank you very much so far though.

---

### Post by ancaleth on 2011-05-08
> **drs305 said:**
> 
```

sudo umount /dev/sda7 # Just in case it is already mounted
sudo mkdir /mnt/temp 
sudo mount /dev/sda7 /mnt/temp 
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet. If you don't have it, continue anyway.
sudo chroot /mnt/temp
```Next we will change the CD's sources.list to look for Natty packages:
```
gedit /etc/apt/sources.list
```

On 11.04 live CD now. I got until here, but no further.

```
ubuntu@ubuntu:~$ sudo umount /dev/sda7
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# gedit /etc/apt/sources.list
No protocol specified

(gedit:6078): Gtk-WARNING **: cannot open display: :
```

---

### Post by drs305 on 2011-05-08
Now that you have the 11.04 CD, editing the sources.list isn't necessary. Hopefully you won't get this error message when you run the following commands from a terminal.

Chroot into your normal Ubuntu partition (sda7), ensure you have an Internet connection, and then purge and reinstall Grub.

Once you have done the steps through "sudo chroot /mnt/temp" and are at the root prompt:
```
apt-get update
purge grub grub-pc grub-common # Tab to OK when given the bootloader warning.
apt-get install grub-pc # It will also install grub-common

```
During the installation, TAB to OK if asked for kernel options. On the next screen, select "sda" with the SPACEBAR, then TAB to OK and ENTER.
When finished, 
```

exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done

```
Reboot (don't forget to remove the CD).

---

### Post by ancaleth on 2011-05-08
Yes! Thank you very much... after three days I have a running system once more. Everything worked perfectly, once the right live CD was here, so I guess that will be something important to remember for the future. Thanks again.

---

