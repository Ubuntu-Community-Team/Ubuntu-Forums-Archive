---
title: "Looking for best way to switch from ubuntu 10.04 to Lubuntu 14"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by roger40 on 2014-09-24
I've finally decided to delve into the intricacies of upgrading my OS to something that is still supported. Because it's an old laptop I figured it's wise to use Lubuntu and have burned a live cd and tried it out. I was thinking of trying to resize the windows partition then adding a new partition to put lubuntu into while still keeping  Ubuntu in it's partition. Then I was hoping I could just copy whatever data files from my old (10.04) home to my new (14.04) home and go on with life.

I tried gparted from the live cd to modify the windows partition until I found that there's something goofy my windows xp install and gparted can't do anything with the partition. I read that this might be solved by booting into windows but when I tried to from grub it went into some sort of safe mode where it will only give me the option of re formatting the C drive back to its original configuration. Since it now seems that I'll never get into xp again I then thought I'd just install lubuntu over xp but I'm not sure if it'll boot then because it seems to boot through /dev/sda which is the windows partition. Wouldn't installing over this screw up the boot system? Here's the boot info:

Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,594,960   174,385,151   161,790,192   7 NTFS / exFAT / HPFS
/dev/sda3         174,387,198   232,355,839    57,968,642   5 Extended
/dev/sda5         174,387,200   224,112,639    49,725,440  83 Linux
/dev/sda6         224,114,688   232,355,839     8,241,152  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        220CFF700CFF3D7B                       ntfs       
/dev/sda2        FE34B84334B80127                       ntfs       laptopHD
/dev/sda5        318c0a5c-9464-4c99-9162-2e02d38f0383   ext4       
/dev/sda6        ea289193-2c41-4479-9193-71e141cb7783   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /PAE 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
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
menuentry 'Ubuntu, with Linux 2.6.35-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    echo    'Loading Linux 2.6.35-32-generic ...'
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    linux    /boot/vmlinuz-2.6.35-31-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    echo    'Loading Linux 2.6.35-31-generic ...'
    linux    /boot/vmlinuz-2.6.35-31-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 318c0a5c-9464-4c99-9162-2e02d38f0383
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 220CFF700CFF3D7B
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set FE34B84334B80127
    drivemap -s (hd0) ${root}
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=318c0a5c-9464-4c99-9162-2e02d38f0383 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ea289193-2c41-4479-9193-71e141cb7783 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  89.303867340 = 95.889297408   boot/grub/core.img                             1
  97.375286102 = 104.555917312  boot/grub/grub.cfg                             1
  95.542594910 = 102.588080128  boot/initrd.img-2.6.35-22-generic              2
  95.548191071 = 102.594088960  boot/initrd.img-2.6.35-27-generic              2
 101.784378052 = 109.290143744  boot/initrd.img-2.6.35-28-generic              2
 103.193534851 = 110.803214336  boot/initrd.img-2.6.35-30-generic              2
  94.693359375 = 101.676220416  boot/initrd.img-2.6.35-31-generic              2
 104.945613861 = 112.684494848  boot/initrd.img-2.6.35-32-generic              1
  89.537475586 = 96.140132352   boot/vmlinuz-2.6.35-22-generic                 1
  89.541477203 = 96.144429056   boot/vmlinuz-2.6.35-27-generic                 1
  89.599979401 = 96.207245312   boot/vmlinuz-2.6.35-28-generic                 1
  89.564277649 = 96.168910848   boot/vmlinuz-2.6.35-30-generic                 1
  89.584869385 = 96.191021056   boot/vmlinuz-2.6.35-31-generic                 1
  89.658306122 = 96.269873152   boot/vmlinuz-2.6.35-32-generic                 1
 104.945613861 = 112.684494848  initrd.img                                     1
  94.693359375 = 101.676220416  initrd.img.old                                 2
  89.658306122 = 96.269873152   vmlinuz                                        1
  89.584869385 = 96.191021056   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  4c 44 42 58 00 01 10 00  5e 0c 95 00 00 00 51 0c  |LDBX....^.....Q.|
00000010  a9 7f 55 07 00 00 00 ce  5b 5b 86 aa 39 33 33 38  |..U.....[[..9338|
00000020  5b 5a 54 06 00 00 00 79  7f 5b 86 aa 86 5d 3a 80  |[ZT....y.[...]:.|
00000030  5b 54 31 00 00 00 00 00  a9 55 aa a9 87 87 88 87  |[T1......U......|
00000040  86 30 00 00 00 00 00 00  4f a3 81 ce ab ac ac e9  |.0......O.......|
00000050  31 00 00 00 00 00 00 00  00 2b a3 a9 aa 80 db 00  |1........+......|
00000060  00 00 00 00 00 00 00 00  00 00 00 2a 4f 2a 00 00  |...........*O*..|
00000070  00 00 00 00 00 f8 7f f0  1f e0 07 c0 03 c0 01 80  |................|
00000080  01 00 01 00 00 80 00 80  00 80 01 80 01 c0 03 c0  |................|
00000090  07 e0 1f ff 9f 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 f6 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c0  f6 02 00 c8 7d 00 00 00  |............}...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


I'm hoping someone can point me in the right direction for formulating a strategy to get lubuntu working without too many problems. I've been reading a lot of info from the forums and other sources and can't seem to put it all together for my particular case. There's not a lot of important data to transfer around mostly pix and some docs that I figure I can copy to external storage then access that from new lubuntu install so all I think I need to know is how to safely install to sda2 without screwing the boot!

Boy I wish I hadn't skipped updating over the years!

---

### Post by mörgæs on 2014-09-25
Hi, welcome to the fora.

When posting terminal output please use CODE tags.

So, the Windows install is fubar, and in Ubuntu you only have a few documents worth saving. I would do a fresh install during which you erase the entire drive.

I noticed that you have a lot of old kernels taking up space. When you have 14.04.1 working I suggest running **sudo apt-get autoremove **once in a while to remove them.

---

