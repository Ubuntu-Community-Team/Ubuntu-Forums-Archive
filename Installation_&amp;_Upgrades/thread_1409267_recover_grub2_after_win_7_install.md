---
title: "recover grub2 after win 7 install"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by Cavsfan on 2010-02-17
I had to reinstall Win 7 yesterday and it did not touch my Karmic Koala partition, but after installation, 
I can only boot into win 7 .
I tried to recover grub2 yesterday, but then borked the win 7 boot and like to never got that back. 
But, my customized picture was there on the grub2 boot screen, so all is good with that.
So, I am back to square one. I can boot into win 7, but not Ubuntu (my favorite OS :D).
I did the sudo fdisk -l and here is what it showed:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa55f55ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47870   384513000    7  HPFS/NTFS
/dev/sda2           59806       60801     8000370   82  Linux swap / Solaris
/dev/sda3           47871       59805    95867887+  83  Linux

What I did yesterday would allow me to boot into Ubuntu, but the win 7 loader was wrong.

I believe it is something like this: sudo grub-install /dev/sda (but not sure if this would apply to my system and I don't want to mess it up again).
(I booted into Ubuntu w/o installing - I think the top option)
Thanks in advance for any help!

---

### Post by darkod on 2010-02-17
I didn't quite understand whether you can't boot ubuntu or win7 right now, because you mentioned both. Also, for detailed information about the boot process, you can download the script in my signature, move it on desktop for example, and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. Post the content of the file here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above when writing the post).

If you can't boot the hdd ubuntu you can do this procedure from the live desktop too, doesn't matter.

---

### Post by Hansmc on 2010-02-17
Check out this link: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html"). If you need any help with the steps come back here and maybe some one can help.

---

### Post by Cavsfan on 2010-02-17
> **darkod said:**
> I didn't quite understand whether you can't boot ubuntu or win7 right now, because you mentioned both. Also, for detailed information about the boot process, you can download the script in my signature, move it on desktop for example, and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. Post the content of the file here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above when writing the post).

If you can't boot the hdd ubuntu you can do this procedure from the live desktop too, doesn't matter.

Thanks! I can only boot into win 7 right now. I want to fix grub2 to where it comes up at boot and the win 7 boot option will go to win 7.
Here is the contents of your script: (ignore sdb and sdc - they are USB drives)
(I think I accidentally installed GRUB2 on the sda3 partition last night. Can I remove that too?) Thanks immensely!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on boot drive #1 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 787945302 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #3 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa55f55ec

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   769,028,047   769,026,000   7 HPFS/NTFS
/dev/sda2         960,767,325   976,768,064    16,000,740  82 Linux swap / Solaris
/dev/sda3         769,031,550   960,767,324   191,735,775  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4651a0a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63        64,259        64,197  de Dell Utility
/dev/sdb2    *         64,260   234,370,555   234,306,296   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf87b4c9a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,383 1,953,520,321   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1CFC7A8DFC7A60C6                       ntfs                                     
/dev/sda2        53d632f0-bfe2-4588-a9a1-23b6a030090b   swap                                     
/dev/sda3        a31b7ce3-880c-4a55-b62a-a48f0c509cf4   ext4                                     
/dev/sdb1        07D2-030B                              vfat       DellUtility                   
/dev/sdb2        96AE4C3FAE4C1A5F                       ntfs                                     
/dev/sdc1        78B8D1A1B8D15DE6                       ntfs       Fantom                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb2        /media/96AE4C3FAE4C1A5F  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /media/Fantom            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda3/boot/grub/menu.lst: ===========================

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
default        2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        30

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
# kopt=root=UUID=a31b7ce3-880c-4a55-b62a-a48f0c509cf4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a31b7ce3-880c-4a55-b62a-a48f0c509cf4

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        a31b7ce3-880c-4a55-b62a-a48f0c509cf4
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=a31b7ce3-880c-4a55-b62a-a48f0c509cf4 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        a31b7ce3-880c-4a55-b62a-a48f0c509cf4
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=a31b7ce3-880c-4a55-b62a-a48f0c509cf4 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title           Windows 7
root            (hd0,0)
savedefault
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set default="2"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set a31b7ce3-880c-4a55-b62a-a48f0c509cf4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  set gfxpayload=keep
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
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set a31b7ce3-880c-4a55-b62a-a48f0c509cf4
insmod tga
if background_image /usr/share/images/grub/Blue_Beautiful_Boat.tga ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set a31b7ce3-880c-4a55-b62a-a48f0c509cf4
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=a31b7ce3-880c-4a55-b62a-a48f0c509cf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set a31b7ce3-880c-4a55-b62a-a48f0c509cf4
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=a31b7ce3-880c-4a55-b62a-a48f0c509cf4 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 12aac3a8aac38727
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=a31b7ce3-880c-4a55-b62a-a48f0c509cf4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=53d632f0-bfe2-4588-a9a1-23b6a030090b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 403.4GB: boot/grub/core.img
 398.4GB: boot/grub/grub.cfg
 399.1GB: boot/grub/menu.lst
 419.4GB: boot/initrd.img-2.6.31-19-generic
 432.7GB: boot/vmlinuz-2.6.31-19-generic
 419.4GB: initrd.img
 432.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 44 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.D.Dell 4.1.....|
00000010  02 00 02 00 00 f8 3f 00  3f 00 ff 00 3f 00 00 00  |......?.?...?...|
00000020  c5 fa 00 00 80 00 29 0b  03 d2 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 fa b8  00 00 8e c0 8e d0 bc fc  |................|
00000050  7b fb 0e 1f fc be ae 7d  e8 cd 00 e8 1d 01 0f 82  |{......}........|
00000060  b9 00 66 0f b7 06 16 7c  66 d1 e0 66 0f b7 1e 0e  |..f....|f..f....|
00000070  7c 66 03 c3 66 03 06 1c  7c 66 a3 3e 7c a1 11 7c  ||f..f...|f.>|..||
00000080  ba 20 00 f7 e2 bb 00 02  f7 f3 8b e8 bb 00 05 e8  |. ..............|
00000090  a5 00 0f 82 85 00 ba 10  00 b9 0b 00 be ef 7d 8b  |..............}.|
000000a0  fb f3 a6 74 13 83 c3 20  4a 75 ee 66 ff 06 3e 7c  |...t... Ju.f..>||
000000b0  4d 75 d9 be e3 7d eb 6b  66 0f b7 06 11 7c 66 ba  |Mu...}.kf....|f.|
000000c0  20 00 00 00 66 f7 e2 66  0f b7 0e 0b 7c 66 03 c1  | ...f..f....|f..|
000000d0  66 48 66 f7 f1 66 01 06  3e 7c 66 a1 3e 7c 66 26  |fHf..f..>|f.>|f&|
000000e0  a3 fc 7b 66 26 0f b7 47  1a 8b f8 2d 02 00 66 0f  |..{f&..G...-..f.|
000000f0  b6 1e 0d 7c 66 f7 e3 66  01 06 3e 7c bb 00 07 bd  |...|f..f..>|....|
00000100  04 00 e8 32 00 72 14 81  c3 00 02 66 ff 06 3e 7c  |...2.r.....f..>||
00000110  4d 75 ef bd 00 7c ea 00  02 70 00 be d6 7d eb 03  |Mu...|...p...}..|
00000120  be e3 7d e8 02 00 eb fe  ac 3c 00 74 09 b4 0e bb  |..}......<.t....|
00000130  07 00 cd 10 eb f2 c3 66  a1 3e 7c 66 33 d2 66 0f  |.......f.>|f3.f.|
00000140  b7 0e 18 7c 66 f7 f1 66  42 88 16 45 7c 66 33 d2  |...|f..fB..E|f3.|
00000150  66 0f b7 0e 1a 7c 66 f7  f1 88 16 44 7c a3 42 7c  |f....|f....D|.B||
00000160  b8 01 02 8b 0e 42 7c c0  e5 06 0a 2e 45 7c 86 e9  |.....B|.....E|..|
00000170  8a 36 44 7c 8a 16 24 7c  cd 13 c3 26 80 3e c2 07  |.6D|..$|...&.>..|
00000180  06 74 2a b8 01 02 bb 00  06 b9 01 00 b6 00 8a 16  |.t*.............|
00000190  24 7c cd 13 72 17 26 c6  06 c2 07 06 b8 01 03 bb  |$|..r.&.........|
000001a0  00 06 b9 01 00 b6 00 8a  16 24 7c cd 13 c3 0d 0a  |.........$|.....|
000001b0  42 6f 6f 74 69 6e 67 20  66 72 6f 6d 20 75 74 69  |Booting from uti|
000001c0  6c 69 74 79 20 70 61 72  74 69 74 69 6f 6e 2e 2e  |lity partition..|
000001d0  2e 0d 0a 0d 0a 00 44 69  73 6b 20 65 72 72 6f 72  |......Disk error|
000001e0  0d 0a 00 4e 6f 20 6c 6f  61 64 65 72 0d 0a 00 49  |...No loader...I|
000001f0  4f 20 20 20 20 20 20 53  59 53 00 00 00 00 55 aa  |O      SYS....U.|
00000200
```

---

### Post by Cavsfan on 2010-02-17
> **Hansmc said:**
> Check out this link: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html). If you need any help with the steps come back here and maybe some one can help.

Thanks Hansmc! That is the page I found and thought I could do it last night, but borked it instead. I believe Darkod knows his stuff and he has helped me before.

---

### Post by darkod on 2010-02-17
It's a bit of a mess, but hopefully it will be OK.

First of all, use a 9.10 cd to boot into the live desktop. Then to install grub2 onto the MBR of /dev/sda, in terminal do:

sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Make sure the int hdd is first option before USB in BIOS. You need to boot from it, that's /dev/sda.

Try to boot ubuntu, the win7 entry in grub menu will not work right now after you reinstalled. If booting ubuntu worked let me know because there are few more things to do.

---

### Post by Cavsfan on 2010-02-17
> **darkod said:**
> It's a bit of a mess, but hopefully it will be OK.

First of all, use a 9.10 cd to boot into the live desktop. Then to install grub2 onto the MBR of /dev/sda, in terminal do:

sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Make sure the int hdd is first option before USB in BIOS. You need to boot from it, that's /dev/sda.

Try to boot ubuntu, the win7 entry in grub menu will not work right now after you reinstalled. If booting ubuntu worked let me know because there are few more things to do.

This is exactly what I had yesterday. When I installed win 7, I could only boot into that.
When I tried to fix the GRUB2, I could boot into Ubuntu, but no longer get to win 7.
So, my custom grub2 screen appears and I am booted into Ubuntu now.
We just need to fix my ability to get to win 7 from grub2.
Thanks!!! :D

---

### Post by darkod on 2010-02-17
> **Cavsfan said:**
> This is exactly what I had yesterday. When I installed win 7, I could only boot into that.
When I tried to fix the GRUB2, I could boot into Ubuntu, but no longer get to win 7.
So, my custom grub2 screen appears and I am booted into Ubuntu now.
We just need to fix my ability to get to win 7 from grub2.
Thanks!!! :D

It's much easier than you think (hopefully). Reinstalling win7 included reformatting the partition and the UUID string (unique string allocated to partitions after format) doesn't match any more.
If all is well you only need to run:

sudo update-grub

and it should take care of that.
Also it seems that somehow you have installed grub1 (ver 0.97) to /dev/sdc and you have its menu.lst in your /boot/grub folder in ubuntu. Move that file from there, the new grub2 works only with grub.cfg. Move menu.lst first before running update-grub so it doesn't confuse it. Put it in your home folder for example, keep it for a while in case you need it.

---

### Post by Cavsfan on 2010-02-17
> **darkod said:**
> It's much easier than you think (hopefully). Reinstalling win7 included reformatting the partition and the UUID string (unique string allocated to partitions after format) doesn't match any more.
If all is well you only need to run:

sudo update-grub

and it should take care of that.
Also it seems that somehow you have installed grub1 (ver 0.97) to /dev/sdc and you have its menu.lst in your /boot/grub folder in ubuntu. Move that file from there, the new grub2 works only with grub.cfg. Move menu.lst first before running update-grub so it doesn't confuse it. Put it in your home folder for example, keep it for a while in case you need it.

Thanks! So, you are saying that all I needed to do was update-grub after win 7 install and I would have been good to go?
I did as you said and here is the output of update-grub:

$ sudo update-grub
Generating grub.cfg ...
Found Debian background: Blue_Beautiful_Boat.tga
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found Windows 7 (loader) on /dev/sda1
done

Can I get the grub1 stuff off of the 3rd partition /dev/sdc safely and if so, how do I go about it?
I am going to try to boot into win 7 now as Ubuntu is good to go.
Thanks!!!

---

### Post by darkod on 2010-02-17
> **Cavsfan said:**
> Thanks! So, you are saying that all I needed to do was update-grub after win 7 install and I would have been good to go?
I did as you said and here is the output of update-grub:

$ sudo update-grub
Generating grub.cfg ...
Found Debian background: Blue_Beautiful_Boat.tga
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found Windows 7 (loader) on /dev/sda1
done

Can I get the grub1 stuff off of the 3rd partition /dev/sdc safely and if so, how do I go about it?
I am going to try to boot into win 7 now as Ubuntu is good to go.
Thanks!!!

Yes, after restoring grub2 to /dev/sda (because windows would overwrite it there during the install), all you needed to do is boot ubuntu and do update-grub to detect the new UUID for the windows partition.

You can write generic mbr on /dev/sdc from ubuntu with:

sudo apt-get install lilo
sudo lilo -M /dev/sdc mbr

Ignore any warnings. That will write generic windows mbr there.

---

### Post by Cavsfan on 2010-02-17
[FONT=Verdana]Dual boot is back to normal! Thanks Darko!
So, if I have to install win 7 again (I would hope not), I would just do update-grub?
I am glad I didn't loose my customized boot screen! 

And can I get the boot stuff off of the 3rd partition?
I entered this command last night in desperation: "[/FONT][FONT=Verdana]grub-install /dev/sdc"
and that is how I ended up with the grub on the 3rd partition. And it gave me a warning
message too!
[/FONT]

---

### Post by darkod on 2010-02-17
After reinstalling windows you need to boot the live desktop, run the two commands for reinstalling grub back on the MBR, and then boot into the hdd ubuntu and do update-grub.

In the previous post I gave you commands to write generic mbr on /dev/sdc. That will get rid of grub from /dev/sdc.

Glad it worked. :)

PS. If you are talking about Grub2 on /dev/sda3, leave it right now. It doesn't matter. I was giving you the commands to remove grub1 from /dev/sdc which is still there.

---

### Post by Cavsfan on 2010-02-17
> **darkod said:**
> After reinstalling windows you need to boot the live desktop, run the two commands for reinstalling grub back on the MBR, and then boot into the hdd ubuntu and do update-grub.

In the previous post I gave you commands to write generic mbr on /dev/sdc. That will get rid of grub from /dev/sdc.

Glad it worked. :)

PS. If you are talking about Grub2 on /dev/sda3, leave it right now. It doesn't matter. I was giving you the commands to remove grub1 from /dev/sdc which is still there.

Thanks! You're help was incredible! 
I am back to cooking with gas! :)

---

### Post by Cavsfan on 2010-02-17
> **darkod said:**
> Yes, after restoring grub2 to /dev/sda (because windows would overwrite it there during the install), all you needed to do is boot ubuntu and do update-grub to detect the new UUID for the windows partition.

You can write generic mbr on /dev/sdc from ubuntu with:

sudo apt-get install lilo
sudo lilo -M /dev/sdc mbr

Ignore any warnings. That will write generic windows mbr there.

That worked perfectly! I ran your boot script again just to verify and it looks good!
You are very good and I very much appreciate your help!!!
Thanks again!

---

### Post by Onael on 2010-02-18
Will this thread help me? I'm in the same boat with Windows XP.

---

### Post by darkod on 2010-02-18
> **Onael said:**
> Will this thread help me? I'm in the same boat with Windows XP.

And how are we supposed to know that? If you think you have the same problem you can try the same solution. But even if the problem is the same sometimes there might be small differences in the solution.

Or you can follow the instructions to run the boot info script and post your results in a new thread you will open for your specific problem.

Without more info I can't really say anything.

---

### Post by Onael on 2010-02-18
Cool. Thank you. I thought I'd ask before punching-in commands.

---

