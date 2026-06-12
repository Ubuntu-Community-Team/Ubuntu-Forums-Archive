---
title: "fresh install 10.04 not starting"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by zoran.a on 2010-05-26
Hallo,
I have just made a fresh install of Ubuntu 10.04 on my laptop which was already running on windows 7. The installation itself was ok, however, after the restart in the end it did not want to load anything. I get just a blank screen. I am not much of a linux expert, so all I could do is start thee computer via a live cd and see what is there. And it looks normal - windows is intact, new linux partitions are there, GRUB is also there. What should I do? Reinstalling everything is not a proper solution...

---

### Post by darkod on 2010-05-26
You do get the grub boot menu at start right?

Highlight the ubuntu entry, but don't hit Enter, hit 'e' instead. It will show you the boot lines/commands. Use the arrows keys and End to go to the end of the line starting with 'linux'.

Delete quiet splash, and add nomodeset. Press Ctrl + X to try to boot.

If that worked it might need to update the video driver, or we will make that fix permanent if there is no other way.

---

### Post by zoran.a on 2010-05-26
Hi Darko,

that is exactly the strange thing - I get nothing. No grub screen, not even a single letter. Nothing.

---

### Post by darkod on 2010-05-26
OK, follow these instructions and run the boot info script. Post the content of the results file in CODE tags and it will show us more.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by zoran.a on 2010-05-26
here are the results:

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    81,922,047    81,715,200   7 HPFS/NTFS
/dev/sda3          81,922,048   187,394,047   105,472,000   7 HPFS/NTFS
/dev/sda4         187,396,094   234,440,703    47,044,610   5 Extended
/dev/sda5         187,396,096   232,398,847    45,002,752  83 Linux
/dev/sda6         232,400,896   234,440,703     2,039,808  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8040 MB, 8040480256 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15704063 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        CC9043889043784A                       ntfs       System Reserved               
/dev/sda2        44C46907C468FD14                       ntfs                                     
/dev/sda3        3A3E70953E704C3F                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        91b2bc0b-7c4c-4f28-966f-c478d1475c61   ext4                                     
/dev/sda6        61915c89-1d49-4072-9b16-0a9341e3ba11   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2072-2E28                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/2072-2E28         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 91b2bc0b-7c4c-4f28-966f-c478d1475c61
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 91b2bc0b-7c4c-4f28-966f-c478d1475c61
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 91b2bc0b-7c4c-4f28-966f-c478d1475c61
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=91b2bc0b-7c4c-4f28-966f-c478d1475c61 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 91b2bc0b-7c4c-4f28-966f-c478d1475c61
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=91b2bc0b-7c4c-4f28-966f-c478d1475c61 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 91b2bc0b-7c4c-4f28-966f-c478d1475c61
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 91b2bc0b-7c4c-4f28-966f-c478d1475c61
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cc9043889043784a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=91b2bc0b-7c4c-4f28-966f-c478d1475c61 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=61915c89-1d49-4072-9b16-0a9341e3ba11 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 102.6GB: boot/grub/core.img
 107.5GB: boot/grub/grub.cfg
 102.7GB: boot/initrd.img-2.6.32-21-generic
 102.6GB: boot/vmlinuz-2.6.32-21-generic
 102.7GB: initrd.img
 102.6GB: vmlinuz

================================ sdb1/menu.lst: ================================

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
default        4

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
# kopt=root=UUID=3ced1c71-94a6-444a-b516-1f20dbfc44e7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3ced1c71-94a6-444a-b516-1f20dbfc44e7

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        3ced1c71-94a6-444a-b516-1f20dbfc44e7
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=3ced1c71-94a6-444a-b516-1f20dbfc44e7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        3ced1c71-94a6-444a-b516-1f20dbfc44e7
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=3ced1c71-94a6-444a-b516-1f20dbfc44e7 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

# title        Ubuntu 9.04, kernel 2.6.28-15-generic
# uuid        3ced1c71-94a6-444a-b516-1f20dbfc44e7
# kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3ced1c71-94a6-444a-b516-1f20dbfc44e7 ro quiet splash 
# initrd        /boot/initrd.img-2.6.28-15-generic
# quiet

# title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
# uuid        3ced1c71-94a6-444a-b516-1f20dbfc44e7
# kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3ced1c71-94a6-444a-b516-1f20dbfc44e7 ro  single
# initrd        /boot/initrd.img-2.6.28-15-generic

# title        Ubuntu 9.04, kernel 2.6.28-11-generic
# uuid        3ced1c71-94a6-444a-b516-1f20dbfc44e7
# kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3ced1c71-94a6-444a-b516-1f20dbfc44e7 ro quiet splash 
# initrd        /boot/initrd.img-2.6.28-11-generic
# quiet

# title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
# uuid        3ced1c71-94a6-444a-b516-1f20dbfc44e7
# kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3ced1c71-94a6-444a-b516-1f20dbfc44e7 ro  single
# initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3ced1c71-94a6-444a-b516-1f20dbfc44e7
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: menu.lst
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  92 52 37 97 f6 b2 ef bc  a1 7d 7c a3 23 13 3c 29  |.R7......}|.#.<)|
00000010  91 91 93 61 37 b7 18 49  00 32 5e 4b 18 32 85 cd  |...a7..I.2^K.2..|
00000020  22 c0 ea 0b 5e 35 b2 54  7a 74 e5 8e 42 28 98 72  |"...^5.Tzt..B(.r|
00000030  6c a8 ef 42 bf 8b 51 c2  53 47 79 d4 23 7f b4 df  |l..B..Q.SGy.#...|
00000040  97 f9 cf 9f ff cb fc 99  34 57 6f 37 ee 9f e4 4a  |........4Wo7...J|
00000050  69 8b e0 cd 7e 0e 00 8e  54 08 00 02 4b 92 fe c3  |i...~...T...K...|
00000060  c4 39 02 0c 57 0d 42 8e  02 68 13 34 d7 69 d7 27  |.9..W.B..h.4.i.'|
00000070  4f f4 9a 44 8a 49 27 a0  e3 e2 42 71 67 cf c7 d8  |O..D.I'...Bqg...|
00000080  6d 08 8d 6b 38 d9 06 92  37 85 e8 94 51 34 e3 79  |m..k8...7...Q4.y|
00000090  21 9b 93 ce ff 6c 90 2a  6b 83 f0 1c 40 12 00 70  |!....l.*k...@..p|
000000a0  30 9b b8 5b 90 61 04 ff  fb 92 6c f8 00 04 71 67  |0..[.a....l...qg|
000000b0  d7 6b 2c 33 72 38 04 2b  1c 3d 67 3a 12 01 9f 5f  |.k,3r8.+.=g:..._|
000000c0  ac a4 cb 89 24 23 ec fc  f4 89 70 83 1d 75 cf 26  |....$#....p..u.&|
000000d0  05 ff c3 90 d5 7b bb 09  3f df 92 5d 9b 13 f6 51  |.....{..?..]...Q|
000000e0  0e 75 f4 1b 21 48 11 3f  d5 21 8f 38 a5 e9 68 e1  |.u..!H.?.!.8..h.|
000000f0  34 d3 62 06 aa bb 85 04  ef d1 46 26 63 eb ac e7  |4.b.......F&c...|
00000100  7d 63 14 8b 04 50 f5 29  64 1d 8d 4c 23 fc e7 17  |}c...P.)d..L#...|
00000110  52 49 33 1c d9 02 49 20  80 49 36 b1 02 84 0d 13  |RI3...I .I6.....|
00000120  18 12 e3 5c 46 64 cc 7b  4e 91 ff ab a9 5b 35 4e  |...\Fd.{N....[5N|
00000130  79 90 f6 48 f2 0e 9f 53  3a 4b 08 1e e8 c1 59 1c  |y..H...S:K....Y.|
00000140  ba 23 d9 f6 f4 3f b9 2f  c4 eb 53 66 27 2e b6 a3  |.#...?./..Sf'...|
00000150  7f fc cd ff fd 7d f9 b9  5c 7d 43 5e 7e 84 14 41  |.....}..\}C^~..A|
00000160  73 2a 91 20 74 c4 42 da  f3 fe ff dc df d1 28 00  |s*. t.B.......(.|
00000170  20 14 9c 95 af 1a 16 a9  7a ac 2f 7a 03 a6 99 6b  | .......z./z...k|
00000180  ec f2 2b 9d ab 92 cc ca  e5 09 4b ab e5 ec 09 fc  |..+.......K.....|
00000190  0a cd bf 1a 7f d0 e8 30  6c 10 f3 79 83 84 d6 62  |.......0l..y...b|
000001a0  21 57 7f 94 5f b7 56 72  78 7d 99 77 64 27 69 98  |!W.._.Vrx}.wd'i.|
000001b0  31 24 10 16 89 e6 04 66  c1 e7 16 3f b1 ab 00 23  |1$.....f...?...#|
000001c0  d2 ff 83 23 d2 ff 02 00  00 00 00 b0 ae 02 00 23  |...#...........#|
000001d0  d2 ff 05 23 d2 ff 1a b7  ae 02 e8 20 1f 00 00 00  |...#....... ....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by darkod on 2010-05-26
Hmmm, it looks fine. What model of video card do you have? It might have issues with ubuntu. Although in that case usually live mode wouldn't work also.

---

### Post by zoran.a on 2010-05-26
The laptop model is Toshiba Satellite Pro L40 and the graphics chip should be something like Intel GMA 900. However, I doubt that Ubuntu has problems with it since I have already used Ubuntu 7 parallel with XP on the same computer. And, as you said, the live version should also not work in that case (and I am writing this post from it).

Anyway, thanks for help, have to get some sleep now, if anybody can think of something I could try I would be grateful, if not brute force always works - reinstall.

Cheers

---

### Post by darkod on 2010-05-26
It doesn't hurt reinstalling grub2 but I doubt that will change anything:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by Catharsis on 2010-05-27
Hold down Shift while booting. Does that get you to the grub menu? If so, then follow Darkod's original suggestion.

---

### Post by phr33k-dc on 2010-05-27
I believe i have the same problem. I can only boot up when i have my usb inserted.

---

### Post by zoran.a on 2010-05-27
> Hold down Shift while booting. Does that get you to the grub menu? If so, then follow Darkod's original suggestion.

Funny, that does not get me the menu, but gets me the sentance "GRUB loading." and it stops there again.

---

### Post by darkod on 2010-05-27
> **phr33k-dc said:**
> I believe i have the same problem. I can only boot up when i have my usb inserted.

phr33k, your problem is not the same. And on another thread where you have posted the results I replied to you, but it seems you never replied back.

Even better, create your own thread and post the results file in CODE tags, not as attachment, because you also have some specific setup, there was some encryption reported in your results. Anyway, I told you your problem, you don't have a bootloader on any disk. So of course you can't boot.

---

### Post by Catharsis on 2010-05-28
> **zoran.a said:**
> Funny, that does not get me the menu, but gets me the sentance "GRUB loading." and it stops there again.

Really weird. You should really try reinstalling Grub2 per Darko's instructions in Comment #8.

There's an old menu.lst on sdb1; could that be causing the problem? It looks like a removable flash drive or an SD card; can you remove it and see if you can get to GRUB?

---

### Post by zoran.a on 2010-05-28
> **Catharsis said:**
> Really weird. You should really try reinstalling Grub2 per Darko's instructions in Comment #8.

Done that. It said it was successful, but there was no change.

>  There's an old menu.lst on sdb1; could that be causing the problem? It looks like a removable flash drive or an SD card; can you remove it and see if you can get to GRUB?Yes, I have seen that as well and it is also strange - it refers to Ubuntu 9, although I had nothing to do with it.

And I have no flash drive or any other removable drives except the CD. It reminds me of the problem I had on my girlfiend's Eee PC: after the installation everything was correct, except that it wanted to load GRUB from the USB stick (which I used for installation). Could it be that it's doing the same thing now with the live CD? Unfortunately I naively did not bother to remember how I solved that problem a year ago.

---

### Post by darkod on 2010-05-28
There is the possibility that you somehow have a mix of grub1 and grub2 on the computer. So even though all looks fine, it can't boot properly.

kansasnoob is expert for that, I don't know the commands. Let me see if I can dig up any of his posts...

---

### Post by darkod on 2010-05-28
Here it is, you can start reading from post #13:
[http://ubuntuforums.org/showthread.php?t=1494042&highlight=grub2&page=2](http://ubuntuforums.org/showthread.php?t=1494042&highlight=grub2&page=2)

PS. Some of the commands in post #13 are for that thread specifically, you don't have to do all of them. I mainly mean the grub-install commands towards the end of the post. That user had two disks, so grub2 was reinstalled to both /dev/sda and /dev/sdb. For you, you might need only /dev/sda, or only /dev/sdb, depending where you want grub2 present.

---

