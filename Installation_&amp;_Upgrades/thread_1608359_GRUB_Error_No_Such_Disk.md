---
title: "GRUB Error: No Such Disk"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Raptor354 on 2010-10-28
Interesting problem...

I just dropped some new hard drives in my computer and used the motherboard utils to put them in RAID0.  I installed Ubuntu 10.10 64-bit (alternate installer, if it matters) without any problems.

When I try and boot, it posts, finds my RAID array (successfully), and tries to continue into the OS.  Unfortunately, I get this happy little prompt:
```
error: no such disk.
grub rescue> 
```

By the way, I have an ASRock A780FullDisplayPort.

Any thoughts?

Raptor354

---

### Post by ronparent on 2010-10-29
Go to this site: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

Download and run the script. Post the results here. When we see your layout we will be better able to help.

---

### Post by foxsick on 2010-11-05
Up!!!
I updated from 9.10 to 10.10 and now have the same problem
Log from the script:
> boot info script 0.55    dated february 15th, 2010                    

============================= boot info summary: ==============================

 => grub 2 is installed in the mbr of /dev/sda and looks for 
    (uuid=8caa2418-2326-41b9-915c-fc58a7f8777a)/boot/grub.
 => grub 2 is installed in the mbr of /dev/sdg and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

Sda1: _________________________________________________________________________

    file system:       Ext3
    boot sector type:  -
    boot sector info:  
    Operating system:  
    Boot files/dirs:   

Sda2: _________________________________________________________________________

    file system:       Ntfs
    boot sector type:  Windows xp
    boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda2 starts at sector 122881248.
    Operating system:  
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sdg1: _________________________________________________________________________

    file system:       Extended partition
    boot sector type:  Unknown
    boot sector info:  

Sdg5: _________________________________________________________________________

    file system:       Swap
    boot sector type:  -
    boot sector info:  

Sdg2: _________________________________________________________________________

    file system:       Ext4
    boot sector type:  Grub 2
    boot sector info:  Grub 2 is installed in the boot sector of sdg2 and 
                       looks at sector 151268176 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating system:  Ubuntu 10.10
    boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== drive/partition info: =============================

drive: Sda ___________________ _____________________________________________________

disk /dev/sda: 300.1 gb, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
units = sectors of 1 * 512 = 512 bytes
sector size (logical/physical): 512 bytes / 512 bytes

partition  boot         start           end          size  id system

/dev/sda1                  63   122,881,184   122,881,122  83 linux
/dev/sda2         122,881,248   586,067,264   463,186,017   7 hpfs/ntfs


drive: Sdg ___________________ _____________________________________________________

disk /dev/sdg: 163.9 gb, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
units = sectors of 1 * 512 = 512 bytes
sector size (logical/physical): 512 bytes / 512 bytes

partition  boot         start           end          size  id system

/dev/sdg1         314,173,438   320,172,031     5,998,594   5 extended
/dev/sdg5         314,173,440   320,172,031     5,998,592  82 linux swap / solaris
/dev/sdg2    *          2,048   314,171,391   314,169,344  83 linux


blkid -c /dev/null: ____________________________________________________________

device           uuid                                   type       label                         

/dev/loop0                                              squashfs                                 
/dev/sda1        48450cd2-6b51-4554-86ef-fc82bb97d499   ext3       music                         
/dev/sda2        b67c660b7c65c6a9                       ntfs       files                         
/dev/sda: Pttype="dos" 
/dev/sdg1: Pttype="dos" 
/dev/sdg2        384beb54-2765-4c44-98b4-470b6a409e61   ext4                                     
/dev/sdg5        59a0978e-aed9-445d-b378-eab2c976079a   swap                                     
/dev/sdg: Pttype="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

device           mount_point              type       options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg2        /mnt                     ext4       (rw)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(1)partition(2)\windows 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\windows="microsoft windows xp professional ru" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\windows="microsoft windows xp professional ru" /noexecute=optin /fastdetect 

=========================== sdg2/boot/grub/grub.cfg: ===========================

#
# do not edit this file
#
# it is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### begin /etc/grub.d/00_header ###
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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 384beb54-2765-4c44-98b4-470b6a409e61
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 384beb54-2765-4c44-98b4-470b6a409e61
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### end /etc/grub.d/00_header ###

### begin /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### end /etc/grub.d/05_debian_theme ###

### begin /etc/grub.d/10_linux ###
menuentry 'ubuntu, with linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 384beb54-2765-4c44-98b4-470b6a409e61
    linux    /boot/vmlinuz-2.6.35-22-generic root=uuid=384beb54-2765-4c44-98b4-470b6a409e61 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'ubuntu, with linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 384beb54-2765-4c44-98b4-470b6a409e61
    echo    'loading linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=uuid=384beb54-2765-4c44-98b4-470b6a409e61 ro single 
    echo    'loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### end /etc/grub.d/10_linux ###

### begin /etc/grub.d/20_linux_xen ###
### end /etc/grub.d/20_linux_xen ###

### begin /etc/grub.d/20_memtest86+ ###
menuentry "memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 384beb54-2765-4c44-98b4-470b6a409e61
    linux16    /boot/memtest86+.bin
}
menuentry "memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 384beb54-2765-4c44-98b4-470b6a409e61
    linux16    /boot/memtest86+.bin console=ttys0,115200n8
}
### end /etc/grub.d/20_memtest86+ ###

### begin /etc/grub.d/30_os-prober ###
menuentry "windows nt/2000/xp (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set b67c660b7c65c6a9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### end /etc/grub.d/30_os-prober ###

### begin /etc/grub.d/40_custom ###
# this file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### end /etc/grub.d/40_custom ###

### begin /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### end /etc/grub.d/41_custom ###

=============================== sdg2/etc/fstab: ===============================

# /etc/fstab: Static file system information.
#
# use 'blkid -o value -s uuid' to print the universally unique identifier
# for a device; this may be used with uuid= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdg2 during installation
uuid=384beb54-2765-4c44-98b4-470b6a409e61 /               ext4    errors=remount-ro 0       1
# /media/files was on /dev/sda2 during installation
uuid=b67c660b7c65c6a9 /media/files    ntfs    defaults,umask=007,gid=46 0       0
# /media/music was on /dev/sda1 during installation
uuid=48450cd2-6b51-4554-86ef-fc82bb97d499 /media/music    ext3    defaults        0       2
# swap was on /dev/sdg5 during installation
uuid=59a0978e-aed9-445d-b378-eab2c976079a none            swap    sw              0       0

=================== sdg2: Location of files loaded by grub: ===================


  77.4gb: Boot/grub/core.img
  73.1gb: Boot/grub/grub.cfg
  73.3gb: Boot/initrd.img-2.6.35-22-generic
    .3gb: Boot/vmlinuz-2.6.35-22-generic
  73.3gb: Initrd.img
    .3gb: Vmlinuz
=========================== unknown mbrs/boot sectors/etc =======================

unknown bootloader  on sdg1

00000000  8a ce c9 14 47 c2 f2 40  8d 2c aa 5f 4f 00 43 7d  |....g..@.,._o.c}|
00000010  f7 9b 9c 39 7a 44 76 2b  4e 1b bb 1e 2d 8d 1f ea  |...9zdv+n...-...|
00000020  01 ba 08 69 13 b5 51 e1  08 80 1e 01 ff 27 a7 a1  |...i..q......'..|
00000030  a0 fc 45 5a 15 cd bc e8  11 e3 e9 37 75 e1 1c e7  |..ez.......7u...|
00000040  cb 5f 92 d2 75 ca 96 91  20 9a c9 67 5a 36 6b 7c  |._..u... ..gz6k||
00000050  4a b6 48 6c 18 71 da 28  dc 16 29 f2 ab 36 08 ca  |j.hl.q.(..)..6..|
00000060  d2 e2 91 5d ef 27 0c 8c  a6 b1 ad 19 d6 99 45 17  |...].'........e.|
00000070  f7 d2 a8 14 21 6f 2f ce  25 82 64 15 3b 40 cf 21  |....!o/.%.d.;@.!|
00000080  64 e5 e6 e4 e9 fe 96 cc  59 d4 f6 94 77 02 9f 29  |d.......y...w..)|
00000090  0e d2 26 25 ea 32 b2 e9  97 0b 15 7f 2e 64 c0 aa  |..&%.2.......d..|
000000a0  9c 7e 73 ed 93 d3 a2 0f  ac 0e 0a 13 c8 ed ce 24  |.~s............$|
000000b0  0b ee 2b 9a cb 54 bd c3  7e 47 b8 e5 12 62 ab e8  |..+..t..~g...b..|
000000c0  14 e7 d7 9d 07 3c 1b 8f  dd 35 24 c5 a4 d3 09 51  |.....<...5$....q|
000000d0  e1 b9 d6 39 3d 5d 42 87  54 35 f9 52 8b 3d dc 92  |...9=]b.t5.r.=..|
000000e0  31 3d 47 e8 1c fd a5 c8  11 a8 9b f0 e0 77 a4 4d  |1=g..........w.m|
000000f0  7a a2 61 81 21 3e 7c e7  76 a1 88 b4 1d b9 57 fa  |z.a.!>|.v.....w.|
00000100  87 b2 4e 23 be a7 1d 4c  54 42 f5 fc 4a ba e4 5a  |..n#...ltb..j..z|
00000110  2c 79 42 ee 77 e1 96 1a  d8 23 b0 3b c3 58 3e 9b  |,yb.w....#.;.x>.|
00000120  e6 a3 c0 58 4d 56 f7 3b  d5 4f 7b 87 90 7f 7c 84  |...xmv.;.o{...|.|
00000130  70 73 ef c1 b6 ed d3 3e  7b 09 ee 83 1b 71 97 97  |ps.....>{....q..|
00000140  05 bf fb 45 36 a4 a0 28  cc c0 a9 0c 07 00 79 7c  |...e6..(......y||
00000150  54 fc b5 c9 6a 70 64 cd  e7 23 44 d8 e0 a1 00 c5  |t...jpd..#d.....|
00000160  33 97 b7 2f 2e 77 94 ff  18 c0 49 30 1d ca 57 4c  |3../.w....i0..wl|
00000170  bf 6f 3d 67 67 b2 49 b5  30 32 00 aa c8 26 80 e4  |.o=gg.i.02...&..|
00000180  f0 51 a5 9e 80 fa 24 c3  0f 47 c0 b4 7e 71 06 1f  |.q....$..g..~q..|
00000190  96 e4 9b 0d 6c 35 5b c2  c2 32 b0 4c 5e 75 ed 64  |....l5[..2.l^u.d|
000001a0  60 0a f5 6e 58 82 11 f8  72 cb e3 48 7c f5 82 d0  |`..nx...r..h|...|
000001b0  f5 ce b5 9e cd 65 9a cf  a3 96 44 bd 4f 35 00 fe  |.....e....d.o5..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 88 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............u.|
00000200


=======devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 


What can I do to launch Ubuntu 10.10?

---

### Post by mpourdas on 2011-01-17
> **Raptor354 said:**
> Interesting problem...

I just dropped some new hard drives in my computer and used the motherboard utils to put them in RAID0.  I installed Ubuntu 10.10 64-bit (alternate installer, if it matters) without any problems.

When I try and boot, it posts, finds my RAID array (successfully), and tries to continue into the OS.  Unfortunately, I get this happy little prompt:
```
error: no such disk.
grub rescue> 
```By the way, I have an ASRock A780FullDisplayPort.

Any thoughts?

Raptor354

Almost same problem here. I have an ASROCK 880GM-LE (AMD-ATI SB700/SB800 RAID chipset) motherboard and use an IDE disk running Ubuntu 9.10 as my OS disk. Whenever i attempt to install 2 SATA disks as RAID with the onboard RAID controller, grub fails to load and sends me in grub-rescue mode. This is logical since my boot disk gets renamed from sda to sdb (or hd0 to hd1 anyway). But the weird part is that in grub-rescue mode, "ls" prints *nothing*, so i cannot change the root disk to hd1 and therefore booting is impossible...

---

