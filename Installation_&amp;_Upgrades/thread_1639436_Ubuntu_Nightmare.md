---
title: "Ubuntu Nightmare"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by RabbiMenda on 2010-12-06
I was just installing ubuntu 10.10 netbook next to my win7, somehow it is now the only OS!
There is no prompt at the beging about which OS I want.
Is there a way to know for sure what heppened to win7?
MOST importantly my final project which was 20 pages of shool research was in my win7
 if win7 is indeed gone, is there a way of retreving this lost data?

---

### Post by uRock on 2010-12-06
In the Places menu, do you see a selection called __GB Filesystem?

 I realize that your menus are different, but if the Windows partition is still there, then it should be listed in the menu.

---

### Post by kansasnoob on 2010-12-06
The very first thing to do is STOP using the newly installed OS and start using the Live CD/USB to perform some diagnostics!

Since you say "netbook" I assume you used a Live USB, eh?

If so boot into it and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions for the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

If you wiped out your Windows we should be able to use PhotoRec to recover your important files but that comes later!

---

### Post by RabbiMenda on 2010-12-06
Ok pasted it below

---

### Post by RabbiMenda on 2010-12-06
I dont have places on my version its 10.10 for netbooks, in fact i cannot find a lot of the options that i saw in 9.4, like I dont have a general menu

---

### Post by RabbiMenda on 2010-12-06
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: __________________________________________________  _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________  _______________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________  _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________  _______________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________  ___

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   476,108,799   476,106,752  83 Linux
/dev/sda2         476,110,846   488,396,799    12,285,954   5 Extended
/dev/sda5         476,110,848   488,396,799    12,285,952  82 Linux swap / Solaris


Drive: sdb ___________________ __________________________________________________  ___

Disk /dev/sdb: 4009 MB, 4009754624 bytes
128 heads, 22 sectors/track, 2781 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          1,128     7,831,551     7,830,424   c W95 FAT32 (LBA)


blkid -c /dev/null: __________________________________________________  __________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e6c92043-6785-4c05-be05-6924d74b6996   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f6043120-49e4-485e-aafd-fc3ba07e32ec   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F98B-1ED0                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat        (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,   iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set e6c92043-6785-4c05-be05-6924d74b6996
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e6c92043-6785-4c05-be05-6924d74b6996
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e6c92043-6785-4c05-be05-6924d74b6996
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e6c92043-6785-4c05-be05-6924d74b6996 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e6c92043-6785-4c05-be05-6924d74b6996
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e6c92043-6785-4c05-be05-6924d74b6996 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e6c92043-6785-4c05-be05-6924d74b6996
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e6c92043-6785-4c05-be05-6924d74b6996 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e6c92043-6785-4c05-be05-6924d74b6996
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e6c92043-6785-4c05-be05-6924d74b6996 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e6c92043-6785-4c05-be05-6924d74b6996
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e6c92043-6785-4c05-be05-6924d74b6996
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
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  68.8GB: boot/grub/core.img
 223.6GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-23-generic
  68.8GB: boot/vmlinuz-2.6.35-22-generic
  68.9GB: boot/vmlinuz-2.6.35-23-generic
    .9GB: initrd.img
    .9GB: initrd.img.old
  68.9GB: vmlinuz
  68.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 68 04 00 00  |........?...h...|
00000020  98 7b 77 00 d0 1d 00 00  00 00 00 00 02 00 00 00  |.{w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 d0 1e 8b f9 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
00000100  7d 00 66 b8 88 f9 5d 00  66 ba 00 00 00 00 bb 00  |}.f...].f.......|
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
```

---

### Post by kansasnoob on 2010-12-07
I don't know why no one else responded but you did wipe out Windows!

You may be able to recover your data using PhotoRec:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

I've used it but I'm in no way proficient with it.

While it's no help to you now I've been working to get this fixed:

[http://ubuntuforums.org/showthread.php?t=1595807](http://ubuntuforums.org/showthread.php?t=1595807)

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by Carharttjimmy on 2010-12-07
> **kansasnoob said:**
> I don't know why no one else responded but you did wipe out Windows!

You may be able to recover your data using PhotoRec:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

I've used it but I'm in no way proficient with it.

While it's no help to you now I've been working to get this fixed:

[http://ubuntuforums.org/showthread.php?t=1595807](http://ubuntuforums.org/showthread.php?t=1595807)

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

There is a way, do you a recovery disk or have you contacted the manufacturer?

Tell them first that you are a Linux user and that you like Arch (most IT techs will stop telling you dont know what you are talking about, even if you dont use arch). Next ask for a recovery CD and install the OS by creating a new partition. Or get partitioner software to do that for you.

You should be fine.


If you are worried about lost data, well thats why you create backups....and if you didnt well....:/ I wont tell you about that because its 50/50 you can recover.

---

### Post by kansasnoob on 2010-12-07
> **Carharttjimmy said:**
> There is a way, do you a recovery disk or have you contacted the manufacturer?

Tell them first that you are a Linux user and that you like Arch (most IT techs will stop telling you dont know what you are talking about, even if you dont use arch). Next ask for a recovery CD and install the OS by creating a new partition. Or get partitioner software to do that for you.

You should be fine.


If you are worried about lost data, well thats why you create backups....and if you didnt well....:/ I wont tell you about that because its 50/50 you can recover.

The OP said,

> MOST importantly my final project which was 20 pages of shool research was in my win7

PhotoRec first from live media :D

But this should not happen!

---

### Post by RabbiMenda on 2010-12-08
[SIZE=5]thank you!!
photo rec worked.
It took a while to figure it out. the interface is not friendly, ie the terminal is alittle bland.
i got  my work back!! 
[/SIZE]

---

