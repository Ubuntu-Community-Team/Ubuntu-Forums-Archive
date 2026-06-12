---
title: "dualboot w7 ubuntu, w7 doesn't load"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by herrolsen on 2011-05-02
Hi! 
I installed ubuntu 10.10 on my laptop that already had w7 on it, lazy as I am I used the installers autopartition solution. My problem is that when I choose w7 in GRUB, my screen goes blank and then GRUB pops up again. I've googled around a bit, but haven't quite understood what's wrong with my setup. 

this is my output from sudo fdisk -l 


Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9c6d9c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        5675    45479121    7  HPFS/NTFS
/dev/sda3            5675        7113    11551745    5  Extended
/dev/sda5            5675        7047    11014144   83  Linux
/dev/sda6            7047        7113      536576   82  Linux swap / Solaris

Disk /dev/mmcblk0: 4013 MB, 4013948928 bytes
25 heads, 24 sectors/track, 13066 cylinders
Units = cylinders of 600 * 512 = 307200 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              14       13067     3915776    b  W95 FAT32

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS


Hoping someone can help me here.

---

### Post by Dutch70 on 2011-05-02
Hi and welcome to UF

Lets have a look at your boot info script. Someone should be able to help if I can't, but we will need to see this.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags. 
Do not skip this step or you will lose the formatting & I doubt if anyone will even look at it.

Please edit your previous post & put that info between "code" tags also, by highlighting it and then clicking the # symbol.
Or just delete it, all of that info will be in the boot script.

---

### Post by Squrdel on 2011-05-02
I have exactly the same problem except that I installed 11.04 after Win 7 on my laptop. It all works fine on my desktop where Ubuntu 11.04 is an upgrade of 10.10 which was installed using wubi.

---

### Post by Dutch70 on 2011-05-02
> **Squrdel said:**
> I have exactly the same problem except that I installed 11.04 after Win 7 on my laptop. It all works fine on my desktop where Ubuntu 11.04 is an upgrade of 10.10 which was installed using wubi.

Well that's not good. If you have trouble fixing it yourself & decide that you want some help. 
You can always start a thread like herrolsen did, but please give this a quick read first...
[[COLOR="Red"]how to get your support questions answered as quickly as possible[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by herrolsen on 2011-05-02
Thanks for the help dutch70! 

Here's my boot info script. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
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

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders, total 114270345 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    91,165,089    90,958,242   7 HPFS/NTFS
/dev/sda3          91,166,718   114,270,207    23,103,490   5 Extended
/dev/sda5          91,166,720   113,195,007    22,028,288  83 Linux
/dev/sda6         113,197,056   114,270,207     1,073,152  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2021 MB, 2021654016 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948543 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,948,542     3,948,480   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       100d9e2b-a796-42c5-bbca-03d2e777b2f5   ext3                                     
/dev/mmcblk0p1   0101-0014                              vfat       CANON_DC                      
/dev/sda1        68769A76769A44AA                       ntfs       System Reserved               
/dev/sda2        64769E3F769E1242                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        28da3c9b-659e-4bbe-8411-d563fee61ef5   ext4                                     
/dev/sda6        317c73ce-60b4-4431-a778-3d191d7b1ee3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5760-7056                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/28da3c9b-659e-4bbe-8411-d563fee61ef5 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/loop1       /media/100d9e2b-a796-42c5-bbca-03d2e777b2f5 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/64769E3F769E1242  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/mmcblk0p1   /media/CANON_DC          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 28da3c9b-659e-4bbe-8411-d563fee61ef5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 28da3c9b-659e-4bbe-8411-d563fee61ef5
set locale_dir=($root)/boot/grub/locale
set lang=nb_NO
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
menuentry 'Ubuntu, med Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 28da3c9b-659e-4bbe-8411-d563fee61ef5
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=28da3c9b-659e-4bbe-8411-d563fee61ef5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 28da3c9b-659e-4bbe-8411-d563fee61ef5
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=28da3c9b-659e-4bbe-8411-d563fee61ef5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, med Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 28da3c9b-659e-4bbe-8411-d563fee61ef5
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=28da3c9b-659e-4bbe-8411-d563fee61ef5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 28da3c9b-659e-4bbe-8411-d563fee61ef5
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=28da3c9b-659e-4bbe-8411-d563fee61ef5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, med Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 28da3c9b-659e-4bbe-8411-d563fee61ef5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=28da3c9b-659e-4bbe-8411-d563fee61ef5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 28da3c9b-659e-4bbe-8411-d563fee61ef5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=28da3c9b-659e-4bbe-8411-d563fee61ef5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 28da3c9b-659e-4bbe-8411-d563fee61ef5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 28da3c9b-659e-4bbe-8411-d563fee61ef5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 68769A76769A44AA
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
UUID=28da3c9b-659e-4bbe-8411-d563fee61ef5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=317c73ce-60b4-4431-a778-3d191d7b1ee3 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  51.3GB: boot/grub/core.img
  49.5GB: boot/grub/grub.cfg
  48.2GB: boot/initrd.img-2.6.35-22-generic
  55.8GB: boot/initrd.img-2.6.35-28-generic
  50.4GB: boot/initrd.img-2.6.38-8-generic
  51.8GB: boot/vmlinuz-2.6.35-22-generic
  51.8GB: boot/vmlinuz-2.6.35-28-generic
  49.3GB: boot/vmlinuz-2.6.38-8-generic
  50.4GB: initrd.img
  55.8GB: initrd.img.old
  49.3GB: vmlinuz
  51.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 63 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.c.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  aa 44 9a 76 76 9a 76 68  |.........D.vv.vh|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 80 30 ec f8 05  |.....3......0...|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  73 73 69 6e 67 00 0d 0a  |...<.u..ssing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

Unknown BootLoader  on sda3

00000000  06 a2 c9 ec 80 f7 21 58  a0 b6 bf c2 98 4f fd bd  |......!X.....O..|
00000010  af be 31 4b c0 d0 37 73  b2 6f 34 37 94 31 7e 07  |..1K..7s.o47.1~.|
00000020  8a 12 a9 c5 9c 84 a0 c9  8f 8c a6 bc 46 6e 1e 1f  |............Fn..|
00000030  9c 76 17 f7 ea 97 7f ef  b5 45 28 3a ad f7 fe f0  |.v.......E(:....|
00000040  e6 9d 86 89 d7 87 bd 60  c3 6c 0e 09 6c 71 b2 8d  |.......`.l..lq..|
00000050  5b df 1b 9c fc a6 3e e3  0f d4 6f 9d 1a 6b a4 7f  |[.....>...o..k..|
00000060  e8 78 e8 71 7f 35 ad 4a  b3 3b b4 69 5e 40 cf c1  |.x.q.5.J.;.i^@..|
00000070  f4 39 b6 1d d8 5f 13 f9  c6 95 97 cf b1 5e e2 21  |.9..._.......^.!|
00000080  8d 15 b1 b7 24 4c cd d3  93 0d 93 ab af 25 f3 aa  |....$L.......%..|
00000090  b6 bf e2 42 98 38 e5 af  e9 4f 07 ee 31 cd 85 7e  |...B.8...O..1..~|
000000a0  39 40 36 4d 48 93 a8 16  72 e5 48 22 f6 2f d1 45  |9@6MH...r.H"./.E|
000000b0  6b 73 2f 36 59 06 9c bf  7e 5b 60 63 3f 50 3d 5c  |ks/6Y...~[`c?P=\|
000000c0  bc 5d ee 0e 7e c0 ff ff  f5 36 fc 26 8a 7d e7 6f  |.]..~....6.&.}.o|
000000d0  f7 77 fc b7 d3 28 ab 6d  68 ba 56 80 bd 24 bf 3b  |.w...(.mh.V..$.;|
000000e0  df f4 7f 85 35 f7 ae 8b  7f bf 45 ac fc 4a 73 7b  |....5.....E..Js{|
000000f0  e7 59 56 4d 96 41 65 2d  22 b6 63 35 62 f1 29 39  |.YVM.Ae-".c5b.)9|
00000100  af e9 e0 2c 5d 63 55 13  5a fc b1 d3 ec 39 29 41  |...,]cU.Z....9)A|
00000110  c4 86 47 f4 df 3c b7 1e  d0 fc c3 dc c8 d5 f1 61  |..G..<.........a|
00000120  8d 8d d4 4a 9b 2d d5 3a  00 96 9c 40 0d 2a f7 11  |...J.-.:...@.*..|
00000130  1b 87 e8 30 5e b7 d4 71  d4 5e 0c cc a9 77 e9 09  |...0^..q.^...w..|
00000140  3c fd 26 9a 4e 08 ae b7  47 8f 84 68 8b 9d 7d 1f  |<.&.N...G..h..}.|
00000150  24 48 09 f3 a4 a5 6c f8  5f be 89 0c 9a 7f db 93  |$H....l._.......|
00000160  7c b9 2b cb dc 88 cf dc  31 37 1d af 99 f6 24 5a  ||.+.....17....$Z|
00000170  1f 6f 47 89 fc 47 ef fc  e0 f6 f8 57 7d cb 0e 11  |.oG..G.....W}...|
00000180  ca 0d b8 9b ff 45 f4 fe  22 33 34 a6 35 48 9d c6  |.....E.."34.5H..|
00000190  f8 38 98 d1 c1 87 08 24  ce e7 e3 0c d6 44 87 7e  |.8.....$.....D.~|
000001a0  c3 1b 31 7b 07 c9 fe 7c  3f 3f 66 7f 52 db 32 6c  |..1{...|??f.R.2l|
000001b0  26 01 19 66 30 e8 26 d6  8d 8a e3 e5 f8 00 00 fe  |&..f0.&.........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 20 50 01 00 fe  |........... P...|
000001d0  ff ff 05 fe ff ff 02 20  50 01 00 68 10 00 00 00  |....... P..h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 3f 00 00 00 00 00  |........>.?.....|
00000020  c0 3f 3c 00 10 0f 00 00  00 00 00 00 02 00 00 00  |.?<.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 56 70 60 57 20  20 20 20 20 20 20 20 20  |..)Vp`W         |
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
00000100  7d 00 66 b8 28 87 15 00  66 ba 00 00 00 00 bb 00  |}.f.(...f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e ce 0d 08 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

### Post by Dutch70 on 2011-05-02
According to this..
> => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
You don't even have Grub installed.

And...according to this.
> menuentry 'Ubuntu, med Linux 2.6.38-8-generic
That is an 11.04 linux kernel. What else have you done?

If you can login to Ubuntu, try running this command before we do anything else. Then you may need to do another boot script.

---

### Post by herrolsen on 2011-05-02
GRUB is most definitely installed, showing up at boot and enabling me to choose the different kernels, memory test or W7. 
I updated to 11.04 from my 10.10. I tried repairing my boot sector with w7 repair disc, and repairing with testdisk, nothing worked.

---

### Post by herrolsen on 2011-05-02
but can it be installed to the wrong partition?

---

### Post by Dutch70 on 2011-05-02
Ok, for 11.04 you need to download a different boot info script. The one I gave you is for 10.10, per your first post. 

If there is something wrong with windows, I don't know much about it, but there are others here that do. 

Does Ubuntu 11.04 still boot up and work properly?

---

### Post by herrolsen on 2011-05-02
Ubuntu boots just fine, tried to boot other kernels as well, so the problem is with my windows bootloader. Just don't know how to fix it.

---

### Post by Dutch70 on 2011-05-02
Try running this command from within the installed Ubuntu, then see if you can boot into windows.
```
sudo update-grub
```

---

### Post by herrolsen on 2011-05-02
noticed something when I updated GRUB : Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1

I read somewhere that windows in general isn't too happy about being the secondary OS, does the order here matter?

---

### Post by Dutch70 on 2011-05-02
Yeah, windows does not play well with others, however the order you're seeing there makes no difference and you can change it, but there is no need.

Can you boot windows now?

---

### Post by herrolsen on 2011-05-02
ahh. ok. No, just tried. It just goes back to grub when I choose w7.

---

### Post by satanselbow on 2011-05-02
Grub should be booting W7 from /sda2 ... 

Not a solution but definitely where your problem lies ;)

---

### Post by Dutch70 on 2011-05-02
oldfred posted some good info here...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1747215[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1747215")

Hopefully that will help, cause I don't know much about fixing windows.

---

### Post by herrolsen on 2011-05-02
why should it boot from /sda2? thought it was weird that w7 had one separate partition just for booting up! 
Thanks for the link Dutch70, seems like it's the same problem. Will now try my luck with those links!

---

### Post by Dutch70 on 2011-05-02
AFAIK sda1 is your boot partition, it has the boot manager in it. 
Anyway, your welcome. I've also asked a friend to have a look at this when he gets time.

---

### Post by oldfred on 2011-05-02
Dutch70's link to my post should also work for you. You have exactly the same issue of a windows boot sector that the boot script has some grub info in it.

Window 7's standard install is now to 2 partitions. A 100MB boot/recovery and the main install. You boot thru the first partition which has the boot flag, in your case sda1. 

Did you just do a standard install, or other fixes before posting. It is starting to look like a bug when several users are getting exactly the same errror and that error is grub in the windows boot partition. We had  something similar with 10.04, but that was just confusing instructions.

---

### Post by herrolsen on 2011-05-02
I did exactly as it said in the guide, and when doing so, completely removing anything that could make my computer boot! I think maybe 
```
bootsect /nt60 SYS /mbr
```
should be 
```
bootsect /nt60 D: /mbr 
```
where D: is my windows drive. 
After completing the guide my computer simply didn't boot at all. It just kept blinking, nothing happened. So now I'm back in windows again! Maybe I'll try again later, really enjoyed ubuntu!

---

### Post by herrolsen on 2011-05-02
I tried some other stuff before posting, using the w7 rescuedisc to fix my bootloader (not with bootrec), and testdisk. Didn't change anything else. Hope someone can fix it!

---

### Post by herrolsen on 2011-05-02
And thanks for all your help Dutch70! 
And if anybody that actually fixed this problem without replacing/removing GRUB reads this, please post a walkthrough!

---

### Post by oldfred on 2011-05-02
Did you run the fixboot command as that should repair your problem. The command you ran installs the windows boot loader to the MBR. And if windows is not fully repaired then nothing will boot.

If you run all the windows fixes you can then test that windows works, as grub will only boot windows if it works anyway. Then you can reinstall grub2's bootloader to the MBR to boot Ubuntu.

To reinstall grub2's boot loader:
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

