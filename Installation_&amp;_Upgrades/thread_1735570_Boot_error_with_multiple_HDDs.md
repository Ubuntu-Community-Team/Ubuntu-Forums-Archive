---
title: "Boot error with multiple HDDs"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by DestroiTe on 2011-04-21
Hi guys!

I'm using ubuntu on my notebook for sometime now, and decided to install it on my desktop as well. 

To avoid messing with my partitions I picked up an old 80GB HDD and installed ubuntu on it. 

My desktop has a 1,5TB HDD (with a 50GB partition for W7 and the rest to files) and this 80GB HDD.

After the installation finished, I rebooted and now can't run either OS. All I get is the grub rescue screen with a "out of disk" error.

Now, I've googled around and saw some tips. 

This is what I've alredy tried: 

sudo do fdisk -l
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX

My 1,5TB HDD is sda and the 80GB one is sdb. I've tried installing grub in both of them and still can't fix this. I wanna know where I should install grub, if it's already installed... I just don't know what to do anymore.

---

### Post by DestroiTe on 2011-04-21
Ok so this is the RESULTS.TXT from boot script v0.55:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr /boot/grub/core.img

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,399,999   102,193,152   7 HPFS/NTFS
/dev/sda3         102,400,000 2,930,274,303 2,827,874,304   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F02E0A5B2E0A1AEC                       ntfs       System Reserved               
/dev/sda2        B4E210FDE210C590                       ntfs                                     
/dev/sda3        DE5601F05601CA6B                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        675ca3fe-5ecd-41d7-9401-587bbf85b0d2   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        9037d7ad-039a-4730-8684-04c28a78383c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 675ca3fe-5ecd-41d7-9401-587bbf85b0d2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 675ca3fe-5ecd-41d7-9401-587bbf85b0d2
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 675ca3fe-5ecd-41d7-9401-587bbf85b0d2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=675ca3fe-5ecd-41d7-9401-587bbf85b0d2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 675ca3fe-5ecd-41d7-9401-587bbf85b0d2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=675ca3fe-5ecd-41d7-9401-587bbf85b0d2 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 675ca3fe-5ecd-41d7-9401-587bbf85b0d2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 675ca3fe-5ecd-41d7-9401-587bbf85b0d2
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  53.8GB: boot/grub/core.img
  51.7GB: boot/grub/grub.cfg
    .4GB: boot/initrd.img-2.6.35-22-generic
    .2GB: boot/vmlinuz-2.6.35-22-generic
    .4GB: initrd.img
    .2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  8c 01 e9 b7 f7 47 4d 62  e1 42 bb 31 6e 88 98 c1  |.....GMb.B.1n...|
00000010  13 c4 7b d5 ba f0 77 73  ad 8f 18 ab df 2d 41 89  |..{...ws.....-A.|
00000020  29 87 88 d1 54 bc 3e 4d  5b 96 3e f9 39 13 c6 60  |)...T.>M[.>.9..`|
00000030  ca b0 77 c3 ff c5 58 ae  77 d4 e7 47 03 42 fa 3e  |..w...X.w..G.B.>|
00000040  04 31 20 49 05 46 06 66  40 a7 7a 54 b3 da 2a 18  |.1 I.F.f@.zT..*.|
00000050  c5 0b 5a a8 0a 52 b6 ce  f1 2e 45 cb 6d 27 3a 2b  |..Z..R....E.m':+|
00000060  7e ed bb ba 27 69 5a 10  05 d0 6e f4 eb 76 75 61  |~...'iZ...n..vua|
00000070  7b f7 a8 e3 f3 a4 0f b9  52 34 c3 15 f7 ad 9a 91  |{.......R4......|
00000080  b1 cd dc a5 1a 64 0a 89  27 9a 6a 76 dc 4e 60 3a  |.....d..'.jv.N`:|
00000090  82 fb 87 e1 18 14 4c 9a  d7 49 aa 49 a8 fa 81 cd  |......L..I.I....|
000000a0  b2 cb 01 36 92 9d 7d 5c  f8 b1 f4 2c d9 22 74 0a  |...6..}\...,."t.|
000000b0  d1 59 fd 10 c7 24 18 4a  93 7d f4 54 3d dc 03 b1  |.Y...$.J.}.T=...|
000000c0  42 8f a4 ff af f6 a4 62  9c 40 d3 89 e1 9e 69 6c  |B......b.@....il|
000000d0  c4 0a aa 10 cb ec 79 23  9f 7d 56 e5 68 88 94 8f  |......y#.}V.h...|
000000e0  fa 3b a3 61 57 33 8b 51  96 e5 6d 8e 90 89 d4 98  |.;.aW3.Q..m.....|
000000f0  56 f7 77 c3 94 12 dd ac  3f 48 ca b4 9c 67 d8 1a  |V.w.....?H...g..|
00000100  68 6e e9 82 98 c3 28 64  84 0a 1f 17 ab 00 ef 83  |hn....(d........|
00000110  61 7c f7 d4 82 10 96 cd  2e d4 c0 65 f4 cd 9b cd  |a|.........e....|
00000120  bb 73 48 84 46 8e 9c 4c  92 b9 61 80 67 fc 0c 25  |.sH.F..L..a.g..%|
00000130  79 78 b0 14 f6 3d 9f e3  50 18 86 b7 a4 5f 8d 40  |yx...=..P...._.@|
00000140  2b 46 15 6a 17 91 82 1a  a5 b1 7e 1a de c1 d8 8c  |+F.j......~.....|
00000150  56 2a a5 55 e3 bc f9 13  d2 d7 80 f7 a8 16 a0 67  |V*.U...........g|
00000160  d3 35 35 06 27 12 07 85  fe b3 aa 95 b0 cf a8 ac  |.55.'...........|
00000170  0a 0d 02 9d 45 53 39 2b  66 fe da ba 0a 8e 12 59  |....ES9+f......Y|
00000180  ce ad 4f e6 5b b5 ba f7  b8 8a e9 3e a3 e6 5e 4e  |..O.[......>..^N|
00000190  33 c0 2e bd f6 b4 4e f0  23 0b 4d 2d 45 22 f1 e6  |3.....N.#.M-E"..|
000001a0  29 f0 f4 1f 1e 00 dd b9  7d 4f a6 24 58 20 0f e8  |).......}O.$X ..|
000001b0  30 6d 04 f4 a7 01 4f bf  fe dc 82 16 bb d3 00 fe  |0m....O.........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-04-21
If you set BIOS to boot the 80GB drive does it not boot?

Boot script or grub2 report drive incorrectly so the bootloader in sda may also boot the sdb1 partition.

You have installed some grub files to the windows boot partition sda1 which stops windows from working:

sda1: ________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=Red]/grldr /boot/grub/core.img[/COLOR]

Windows is not case sensitive so the /Boot and /boot folders look the same to windows and it gets confused. You have to delete the /boot folder with grub, but do not delete the /Boot with the BCD as that is essential to windows. /grldr is grub4dos which is not windows.

I would also use a windows repair CD to restore the windows boot loader to the windows drive.

---

### Post by DestroiTe on 2011-04-22
> **oldfred said:**
> If you set BIOS to boot the 80GB drive does it not boot?

Boot script or grub2 report drive incorrectly so the bootloader in sda may also boot the sdb1 partition.

You have installed some grub files to the windows boot partition sda1 which stops windows from working:

sda1: ________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=Red]/grldr /boot/grub/core.img[/COLOR]

Windows is not case sensitive so the /Boot and /boot folders look the same to windows and it gets confused. You have to delete the /boot folder with grub, but do not delete the /Boot with the BCD as that is essential to windows. /grldr is grub4dos which is not windows.

I would also use a windows repair CD to restore the windows boot loader to the windows drive.

Ok, so I reinstalled ubuntu for the third time and this time I set the 80GB HDD to be a primary drive, instead of a logical one. By doing this I could boot ubuntu, but GRUB didn't appear at all and I couldn't select windows. 

Then I read your reply and did what you told me to do and deleted /grldr and grub from the sda1. After that I did a grub-update and grub did find the W7 partition and I thought that everything would be ok. Then I restarted the PC and all that I could see was a grub prompt, not the rescue one, just the normal prompt. 

I've already tried reinstalling grub to the sdb partition, but no luck.

Also, to answer your question, before I deleted those files if I tried to boot directly from the sdb (80GB HDD) the boot would fail, I would only see a black screen. After deleting those files I didn't try that yet.

Also, am I installing grub to the right place (sdb)? Here's the new RESULTS.TXT

```
 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,399,999   102,193,152   7 HPFS/NTFS
/dev/sda3         102,400,000 2,930,274,303 2,827,874,304   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   140,625,919   140,623,872  83 Linux
/dev/sdb2         140,627,966   156,299,263    15,671,298   5 Extended
/dev/sdb5         140,627,968   156,299,263    15,671,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F02E0A5B2E0A1AEC                       ntfs       System Reserved               
/dev/sda2        B4E210FDE210C590                       ntfs                                     
/dev/sda3        DE5601F05601CA6B                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        437e1217-57f2-4c2b-863a-5c0e6856ff91   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        1c4f5394-08c2-4040-9fcc-6b7e9f516ce1   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/DE5601F05601CA6B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 437e1217-57f2-4c2b-863a-5c0e6856ff91
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 437e1217-57f2-4c2b-863a-5c0e6856ff91
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 437e1217-57f2-4c2b-863a-5c0e6856ff91
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=437e1217-57f2-4c2b-863a-5c0e6856ff91 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 437e1217-57f2-4c2b-863a-5c0e6856ff91
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=437e1217-57f2-4c2b-863a-5c0e6856ff91 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 437e1217-57f2-4c2b-863a-5c0e6856ff91
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=437e1217-57f2-4c2b-863a-5c0e6856ff91 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 437e1217-57f2-4c2b-863a-5c0e6856ff91
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=437e1217-57f2-4c2b-863a-5c0e6856ff91 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 437e1217-57f2-4c2b-863a-5c0e6856ff91
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 437e1217-57f2-4c2b-863a-5c0e6856ff91
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f02e0a5b2e0a1aec
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=437e1217-57f2-4c2b-863a-5c0e6856ff91 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sdb5 during installation
UUID=1c4f5394-08c2-4040-9fcc-6b7e9f516ce1 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
   4.5GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-28-generic
  26.1GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: boot/vmlinuz-2.6.35-28-generic
    .9GB: initrd.img
    .9GB: initrd.img.old
    .8GB: vmlinuz
  26.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  18 c9 03 8c e1 24 c7 c4  d0 bc 08 a8 63 68 82 52  |.....$......ch.R|
00000010  20 00 40 11 f8 30 31 11  8c 28 bc c1 d2 8c 74 4a  | .@..01..(....tJ|
00000020  94 38 b8 28 10 20 45 10  02 13 0d 98 90 f1 8b 0f  |.8.(. E.........|
00000030  11 12 17 28 88 1c 44 4e  18 be 6e 08 81 c2 06 2a  |...(..DN..n....*|
00000040  68 61 c2 00 16 21 24 50  71 60 b3 32 94 a0 a2 c3  |ha...!$Pq`.2....|
00000050  ac d4 54 28 3e 31 83 03  08 05 81 04 40 e3 80 a0  |..T(>1......@...|
00000060  26 b0 50 38 b1 68 d0 02  65 aa b3 10 9f 14 05 bc  |&.P8.h..e.......|
00000070  8a 48 22 4e 82 f0 26 3a  2a 11 03 a7 28 54 15 2d  |.H"N..&:*...(T.-|
00000080  42 c0 4d 28 b9 4b 95 9e  27 40 71 25 86 38 c6 93  |B.M(.K..'@q%.8..|
00000090  f1 32 9d c5 0c 58 65 34  aa 4a 01 2b 2c e3 d2 9c  |.2...Xe4.J.+,...|
000000a0  6c d1 57 29 8b b5 21 74  16 92 3d 33 e6 26 86 aa  |l.W)..!t..=3.&..|
000000b0  5a 15 00 65 4f 33 b4 af  e1 2d 39 df c6 3a e8 98  |Z..eO3...-9..:..|
000000c0  68 7a b7 3e 8a 4c b9 e8  e6 a5 a9 b8 a6 8b 40 38  |hz.>.L........@8|
000000d0  00 18 16 5e 50 b0 3b 0c  50 75 05 60 4d 15 da 47  |...^P.;.Pu.`M..G|
000000e0  d5 84 76 6c 4b e5 d4 10  fc 3f 61 d9 88 d6 98 a0  |..vlK....?a.....|
000000f0  ff 78 d4 c3 91 86 56 bc  8b 88 90 4a 69 15 58 46  |.x....V....Ji.XF|
00000100  32 ae ff d5 13 46 68 8c  cd a4 a5 8a 96 41 6a d8  |2....Fh......Aj.|
00000110  ce 9d 86 45 06 83 80 9b  27 e6 58 b1 e5 4c 4c d0  |...E....'.X..LL.|
00000120  f2 71 35 aa 83 95 1c 00  a0 c2 61 60 28 36 62 04  |.q5.......a`(6b.|
00000130  8d 16 41 39 84 04 8d 82  d1 50 8c 1d da 57 18 11  |..A9.....P...W..|
00000140  17 f9 0e c8 e2 30 c1 15  0b d8 39 c9 23 b8 10 81  |.....0....9.#...|
00000150  67 c7 45 19 19 3c 93 48  80 90 a0 8e 8a c9 22 1d  |g.E..<.H......".|
00000160  da 7b 19 f2 9b 36 45 60  4a 92 10 1c 44 33 2d a2  |.{...6E`J...D3-.|
00000170  a5 28 b1 65 a6 f3 b9 2e  94 3b f7 df f8 76 1c 2d  |.(.e.....;...v.-|
00000180  ba 91 8c 3c 30 45 57 f6  53 3d 56 52 c3 a8 69 2f  |...<0EW.S=VR..i/|
00000190  c3 14 f5 2b dd 97 b7 9d  9d 8b e1 0d 63 4c fa 45  |...+........cL.E|
000001a0  9e 47 f2 9f 94 9b d4 7f  57 66 ae bf 32 f8 f5 13  |.G......Wf..2...|
000001b0  a1 49 2f bd da 5a 09 76  52 07 9e af 24 57 00 fe  |.I/..Z.vR...$W..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 20 ef 00 00 00  |........... ....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

I'm going to try to repair windows too, but as of now I can't boot either OS.

---

### Post by DestroiTe on 2011-04-22
Setting the system to boot from the 80GB HDD also shows the grub prompt. I'm completely lost and have no idea of what to do next.

---

### Post by Quackers on 2011-04-22
How did you set the boot device? By going into the bios settings or by using a one time only key (like F12 for instance).

---

### Post by DestroiTe on 2011-04-22
By going into the bios and altering the boot order for the hard drives.

---

### Post by oldfred on 2011-04-22
I really do not see anything wrong in boot script. I do not understand why it booted once. It had only found windows and with one system it does not normally show menu. And it updated to find windows ok. Perhaps the grub in the MBR of sda was using the files in the windows partition and somehow that worked. But booting sdb should work.

Sometimes the full chroot reinstall is required or using Supergrub which seems to do its own thing and bypass the MBR.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

Sometimes as part of chroot a total uninstall & reinstall works.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If you do the chroot or supergrub gets you into your system run this as  grub has probably remembered to reinstall to sda.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by DestroiTe on 2011-04-22
Windows repair disk cannot find windows install files either. I've alredy tried doing a chroot before, didn't really solve it.

I just don't understand why Grub can't show the menu to let me select the OS. I'm gonna try those things you said, but, if it all fails, I'm gonna have to reinstall both Windows and Ubuntu?

---

### Post by DestroiTe on 2011-04-22
Which partition should I install grub? To sda or sdb? I'm chroot-ing now.

---

### Post by oldfred on 2011-04-22
Drive sdb. 

Partitions are sdb1, sda1 etc and you almost never install grub2 to a partition.

---

### Post by DestroiTe on 2011-04-22
OMG!

Doing [https://help.ubuntu.com/community/Grub2#METHOD 3 - CHROOT]("this") solved it! I now can boot both ubuntu and w7. I'm now afraid of installing x64 ubuntu and losing all this work...

I'm not going to mark this as solved yet because I'm going to install x64 now (replacing x86). Let's see if it doesn't screw things up.

---

### Post by DestroiTe on 2011-04-22
No luck. I'm back at square one. Grub rescue prompt (out of disk). I'm going to do the chroot again to try and fix this.

UPDATE:
No luck, again. Just chroot-ed but grub still is out of disk. This is the new results.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,399,999   102,193,152   7 HPFS/NTFS
/dev/sda3         102,400,000 2,930,274,303 2,827,874,304   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   140,625,919   140,623,872  83 Linux
/dev/sdb2         140,627,966   156,299,263    15,671,298   5 Extended
/dev/sdb5         140,627,968   156,299,263    15,671,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F02E0A5B2E0A1AEC                       ntfs       System Reserved               
/dev/sda2        B4E210FDE210C590                       ntfs                                     
/dev/sda3        DE5601F05601CA6B                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6d124bdd-8c08-47e8-87e3-29cdd69b4ebe   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        1c4f5394-08c2-4040-9fcc-6b7e9f516ce1   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6d124bdd-8c08-47e8-87e3-29cdd69b4ebe ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6d124bdd-8c08-47e8-87e3-29cdd69b4ebe ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f02e0a5b2e0a1aec
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=6d124bdd-8c08-47e8-87e3-29cdd69b4ebe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1c4f5394-08c2-4040-9fcc-6b7e9f516ce1 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  51.7GB: boot/grub/core.img
  68.9GB: boot/grub/grub.cfg
  69.0GB: boot/initrd.img-2.6.35-22-generic
  51.7GB: boot/vmlinuz-2.6.35-22-generic
  69.0GB: initrd.img
  51.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  18 c9 03 8c e1 24 c7 c4  d0 bc 08 a8 63 68 82 52  |.....$......ch.R|
00000010  20 00 40 11 f8 30 31 11  8c 28 bc c1 d2 8c 74 4a  | .@..01..(....tJ|
00000020  94 38 b8 28 10 20 45 10  02 13 0d 98 90 f1 8b 0f  |.8.(. E.........|
00000030  11 12 17 28 88 1c 44 4e  18 be 6e 08 81 c2 06 2a  |...(..DN..n....*|
00000040  68 61 c2 00 16 21 24 50  71 60 b3 32 94 a0 a2 c3  |ha...!$Pq`.2....|
00000050  ac d4 54 28 3e 31 83 03  08 05 81 04 40 e3 80 a0  |..T(>1......@...|
00000060  26 b0 50 38 b1 68 d0 02  65 aa b3 10 9f 14 05 bc  |&.P8.h..e.......|
00000070  8a 48 22 4e 82 f0 26 3a  2a 11 03 a7 28 54 15 2d  |.H"N..&:*...(T.-|
00000080  42 c0 4d 28 b9 4b 95 9e  27 40 71 25 86 38 c6 93  |B.M(.K..'@q%.8..|
00000090  f1 32 9d c5 0c 58 65 34  aa 4a 01 2b 2c e3 d2 9c  |.2...Xe4.J.+,...|
000000a0  6c d1 57 29 8b b5 21 74  16 92 3d 33 e6 26 86 aa  |l.W)..!t..=3.&..|
000000b0  5a 15 00 65 4f 33 b4 af  e1 2d 39 df c6 3a e8 98  |Z..eO3...-9..:..|
000000c0  68 7a b7 3e 8a 4c b9 e8  e6 a5 a9 b8 a6 8b 40 38  |hz.>.L........@8|
000000d0  00 18 16 5e 50 b0 3b 0c  50 75 05 60 4d 15 da 47  |...^P.;.Pu.`M..G|
000000e0  d5 84 76 6c 4b e5 d4 10  fc 3f 61 d9 88 d6 98 a0  |..vlK....?a.....|
000000f0  ff 78 d4 c3 91 86 56 bc  8b 88 90 4a 69 15 58 46  |.x....V....Ji.XF|
00000100  32 ae ff d5 13 46 68 8c  cd a4 a5 8a 96 41 6a d8  |2....Fh......Aj.|
00000110  ce 9d 86 45 06 83 80 9b  27 e6 58 b1 e5 4c 4c d0  |...E....'.X..LL.|
00000120  f2 71 35 aa 83 95 1c 00  a0 c2 61 60 28 36 62 04  |.q5.......a`(6b.|
00000130  8d 16 41 39 84 04 8d 82  d1 50 8c 1d da 57 18 11  |..A9.....P...W..|
00000140  17 f9 0e c8 e2 30 c1 15  0b d8 39 c9 23 b8 10 81  |.....0....9.#...|
00000150  67 c7 45 19 19 3c 93 48  80 90 a0 8e 8a c9 22 1d  |g.E..<.H......".|
00000160  da 7b 19 f2 9b 36 45 60  4a 92 10 1c 44 33 2d a2  |.{...6E`J...D3-.|
00000170  a5 28 b1 65 a6 f3 b9 2e  94 3b f7 df f8 76 1c 2d  |.(.e.....;...v.-|
00000180  ba 91 8c 3c 30 45 57 f6  53 3d 56 52 c3 a8 69 2f  |...<0EW.S=VR..i/|
00000190  c3 14 f5 2b dd 97 b7 9d  9d 8b e1 0d 63 4c fa 45  |...+........cL.E|
000001a0  9e 47 f2 9f 94 9b d4 7f  57 66 ae bf 32 f8 f5 13  |.G......Wf..2...|
000001b0  a1 49 2f bd da 5a 09 76  52 07 9e af 24 57 00 fe  |.I/..Z.vR...$W..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 20 ef 00 00 00  |........... ....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

GRUB.CFG

```
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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6d124bdd-8c08-47e8-87e3-29cdd69b4ebe ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6d124bdd-8c08-47e8-87e3-29cdd69b4ebe ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f02e0a5b2e0a1aec
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
```

---

### Post by DestroiTe on 2011-04-22
Installed grub2 to sdb. This is the new results.txt:

```
 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,399,999   102,193,152   7 HPFS/NTFS
/dev/sda3         102,400,000 2,930,274,303 2,827,874,304   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   140,625,919   140,623,872  83 Linux
/dev/sdb2         140,627,966   156,299,263    15,671,298   5 Extended
/dev/sdb5         140,627,968   156,299,263    15,671,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F02E0A5B2E0A1AEC                       ntfs       System Reserved               
/dev/sda2        B4E210FDE210C590                       ntfs                                     
/dev/sda3        DE5601F05601CA6B                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6d124bdd-8c08-47e8-87e3-29cdd69b4ebe   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        1c4f5394-08c2-4040-9fcc-6b7e9f516ce1   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6d124bdd-8c08-47e8-87e3-29cdd69b4ebe ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6d124bdd-8c08-47e8-87e3-29cdd69b4ebe ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6d124bdd-8c08-47e8-87e3-29cdd69b4ebe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f02e0a5b2e0a1aec
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=6d124bdd-8c08-47e8-87e3-29cdd69b4ebe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1c4f5394-08c2-4040-9fcc-6b7e9f516ce1 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  51.6GB: boot/grub/core.img
  51.7GB: boot/grub/grub.cfg
  69.0GB: boot/initrd.img-2.6.35-22-generic
  51.7GB: boot/vmlinuz-2.6.35-22-generic
  69.0GB: initrd.img
  51.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  18 c9 03 8c e1 24 c7 c4  d0 bc 08 a8 63 68 82 52  |.....$......ch.R|
00000010  20 00 40 11 f8 30 31 11  8c 28 bc c1 d2 8c 74 4a  | .@..01..(....tJ|
00000020  94 38 b8 28 10 20 45 10  02 13 0d 98 90 f1 8b 0f  |.8.(. E.........|
00000030  11 12 17 28 88 1c 44 4e  18 be 6e 08 81 c2 06 2a  |...(..DN..n....*|
00000040  68 61 c2 00 16 21 24 50  71 60 b3 32 94 a0 a2 c3  |ha...!$Pq`.2....|
00000050  ac d4 54 28 3e 31 83 03  08 05 81 04 40 e3 80 a0  |..T(>1......@...|
00000060  26 b0 50 38 b1 68 d0 02  65 aa b3 10 9f 14 05 bc  |&.P8.h..e.......|
00000070  8a 48 22 4e 82 f0 26 3a  2a 11 03 a7 28 54 15 2d  |.H"N..&:*...(T.-|
00000080  42 c0 4d 28 b9 4b 95 9e  27 40 71 25 86 38 c6 93  |B.M(.K..'@q%.8..|
00000090  f1 32 9d c5 0c 58 65 34  aa 4a 01 2b 2c e3 d2 9c  |.2...Xe4.J.+,...|
000000a0  6c d1 57 29 8b b5 21 74  16 92 3d 33 e6 26 86 aa  |l.W)..!t..=3.&..|
000000b0  5a 15 00 65 4f 33 b4 af  e1 2d 39 df c6 3a e8 98  |Z..eO3...-9..:..|
000000c0  68 7a b7 3e 8a 4c b9 e8  e6 a5 a9 b8 a6 8b 40 38  |hz.>.L........@8|
000000d0  00 18 16 5e 50 b0 3b 0c  50 75 05 60 4d 15 da 47  |...^P.;.Pu.`M..G|
000000e0  d5 84 76 6c 4b e5 d4 10  fc 3f 61 d9 88 d6 98 a0  |..vlK....?a.....|
000000f0  ff 78 d4 c3 91 86 56 bc  8b 88 90 4a 69 15 58 46  |.x....V....Ji.XF|
00000100  32 ae ff d5 13 46 68 8c  cd a4 a5 8a 96 41 6a d8  |2....Fh......Aj.|
00000110  ce 9d 86 45 06 83 80 9b  27 e6 58 b1 e5 4c 4c d0  |...E....'.X..LL.|
00000120  f2 71 35 aa 83 95 1c 00  a0 c2 61 60 28 36 62 04  |.q5.......a`(6b.|
00000130  8d 16 41 39 84 04 8d 82  d1 50 8c 1d da 57 18 11  |..A9.....P...W..|
00000140  17 f9 0e c8 e2 30 c1 15  0b d8 39 c9 23 b8 10 81  |.....0....9.#...|
00000150  67 c7 45 19 19 3c 93 48  80 90 a0 8e 8a c9 22 1d  |g.E..<.H......".|
00000160  da 7b 19 f2 9b 36 45 60  4a 92 10 1c 44 33 2d a2  |.{...6E`J...D3-.|
00000170  a5 28 b1 65 a6 f3 b9 2e  94 3b f7 df f8 76 1c 2d  |.(.e.....;...v.-|
00000180  ba 91 8c 3c 30 45 57 f6  53 3d 56 52 c3 a8 69 2f  |...<0EW.S=VR..i/|
00000190  c3 14 f5 2b dd 97 b7 9d  9d 8b e1 0d 63 4c fa 45  |...+........cL.E|
000001a0  9e 47 f2 9f 94 9b d4 7f  57 66 ae bf 32 f8 f5 13  |.G......Wf..2...|
000001b0  a1 49 2f bd da 5a 09 76  52 07 9e af 24 57 00 fe  |.I/..Z.vR...$W..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 20 ef 00 00 00  |........... ....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-04-22
Boot script looks normal.

You should be able to boot sdb the 80GB drive.

You can also install the windows boot loader to sda with a windows repair CD.
You can run the auto repair 3 times or run this from the command line.
BootRec.exe /fixMBR 

Or from Ubuntu liveCd install lilo's bool loader which works like windows boot loader:

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Did you try the full chroot and put grub2's boot loader into sdb again?

---

### Post by DestroiTe on 2011-04-22
Tried to repair windows with a windows repair disk but the repair didn't fix it. So while I should be able to boot with the 80GB drive, I couldn't. Just the grub rescue prompt. 

For now I've given up on the hole 2 HDDs thing. I just created another partition on my SATA disk and ubuntu installed just fine, everything is running as it should. 

I did that because I had already spent almost 2 days on this, and was running out of time, as I have a important test on monday. When I get my vacations I'll fix this situation, but for now, I consider my setup to be, if not ideal, suitable for my current needs. It would be better to have 2 HDDs, but we tried. I spent some good hours this afternoon on IRC #ubuntu but still couldn't fix it. So I somewhat gave up. Anyway, I really appreciate the help, and I'll be around.

I won't give up completely. =)

---

### Post by Quackers on 2011-04-22
How many times did you run the repair function (if that's what you did)?

---

### Post by DestroiTe on 2011-04-23
Just one. Didn't find any errors so nothing was fixed.

---

### Post by oldfred on 2011-04-23
The windows auto repair has to be run 3 times. Chkdsk has to be rerun until there are no errors. Windows does not fix everything on one pass.

Most suggest the manual command line fixes for windows (what windows uses command line?). I have posted before:

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

