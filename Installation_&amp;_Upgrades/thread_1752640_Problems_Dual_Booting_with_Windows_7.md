---
title: "Problems Dual Booting with Windows 7"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by banlocke on 2011-05-08
I am very eager to explore Ubuntu, but I have been running into a series of problems. First off I must state that I am basically completely foreign to linux. 

I have 2 hard drives, one with windows 7 and storage partitions, and the other with my linux partition, linux swap, and unpartitioned space. 

I initially partitioned my drives with Disk Management in Windows 7. I created an NTFS partition on sda and installed Ubuntu from within Windows (a Wubi install I suppose). I originally intended to install by booting from the iso I burned onto a CD, but the installer was failing to load (fonts would change and it would error message). LiveCD was failing to load too in the same fashion. After hitting alt and tweaking the F6 settings, LiveCD successfully loaded (my very first taste of Ubuntu, albeit somewhat bland). I then decided to reinstall Ubuntu with proper linux partitions from within LiveCD. Now when I select Ubuntu in the Windows Boot Manager, a WBM screen says the file: \ubuntu\winboot\wubildr.mbr is missing or corrupt. I do not know if this file is the problem or merely a symptom of it. I have been exploring these forums for answers but have yet find them. Below I have copied my  Boot Summary (my apologies for the length and extra partitions):

                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    30,273,535    30,271,488  83 Linux
/dev/sda2          30,273,536    40,038,399     9,764,864  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdb2          81,915,435   268,414,019   186,498,585   f W95 Ext d (LBA)
/dev/sdb5          81,915,498   268,414,019   186,498,522   7 HPFS/NTFS
/dev/sdb3         268,414,976   625,137,663   356,722,688   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f7337b1e-51f9-4a20-993d-1799ea54d36c   ext4                                     
/dev/sda2        d0076339-c2ad-44de-9342-e82a37c6f1a7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        46902FA6902F9B85                       ntfs       Windows 7                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        60343F2E343F0716                       ntfs       New Volume                    
/dev/sdb5        C24C11DB4C11CB55                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/f7337b1e-51f9-4a20-993d-1799ea54d36c ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=f7337b1e-51f9-4a20-993d-1799ea54d36c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=f7337b1e-51f9-4a20-993d-1799ea54d36c ro single 
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 46902FA6902F9B85
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
/dev/sda2       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.7GB: boot/grub/core.img
   2.4GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.38-8-generic
   4.7GB: boot/vmlinuz-2.6.38-8-generic
   1.7GB: initrd.img
   4.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 c0 b6 8e 00  |................|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  1f f9 d2 5e a8 38 66 69  63 18 f2 d3 80 b0 e4 f7  |...^.8fic.......|
00000010  c8 60 95 ff 95 85 3f dc  ae 3b fd 1a 54 fe 57 72  |.`....?..;..T.Wr|
00000020  7f a7 ff b3 7f 8a 89 89  7f 38 78 b6 fe 61 bf ff  |.........8x..a..|
00000030  7f f1 61 81 3f 16 25 83  f4 26 9a 8e 53 0a 8a 88  |..a.?.%..&..S...|
00000040  90 00 24 92 02 4d 4a 18  a2 15 05 aa 69 a3 0e 78  |..$..MJ.....i..x|
00000050  96 63 77 ba c4 f1 7b a2  cf 04 fb 54 92 0e 88 8e  |.cw...{....T....|
00000060  0c ad 94 56 e9 2a 74 14  ff fb 90 64 cf 80 03 1f  |...V.*t....d....|
00000070  63 d4 d3 0b 2a d4 55 8c  5a 9d 61 05 5d 4c 39 87  |c...*.U.Z.a.]L9.|
00000080  53 ac 34 ad 19 6b b1 6a  75 83 96 4b c1 20 c7 b5  |S.4..k.ju..K. ..|
00000090  20 d3 01 f4 a0 87 f6 18  63 3f f2 87 55 5b f5 11  | .......c?..U[..|
000000a0  1a 01 2b ff 14 bb 9f fc  68 6b d1 f9 84 cc ff ea  |..+.....hk......|
000000b0  d6 ff 75 ff 71 e4 10 1b  ff 30 a0 6f eb 28 b2 bf  |..u.q....0.o.(..|
000000c0  d0 c8 26 a1 a2 b2 da 61  b3 7e a8 04 a4 82 92 6e  |..&....a.~.....n|
000000d0  b4 10 40 d1 01 f0 31 c4  78 9a 97 ca b9 d8 e6 cb  |..@...1.x.......|
000000e0  8d af 9f 1a 57 d5 32 90  9b fa 28 23 55 c1 b8 14  |....W.2...(#U...|
000000f0  88 1e ed 48 e1 58 e5 57  f6 52 32 6d f8 98 67 f8  |...H.X.W.R2m..g.|
00000100  88 a0 79 5f f5 75 76 3f  f9 ff f2 bf fc 4d 7f f3  |..y_.uv?.....M..|
00000110  9d bf a2 10 17 ff 67 fd  02 c7 07 84 c5 fd 5a 51  |......g.......ZQ|
00000120  77 17 6a db 11 11 61 94  10 00 04 00 01 4e 39 cb  |w.j...a......N9.|
00000130  01 18 1a e0 13 10 a1 62  38 ce 53 a9 3f 50 00 86  |.......b8.S.?P..|
00000140  22 9e 54 a6 b1 49 a2 6c  66 25 75 ba 4e cd 58 41  |".T..I.lf%u.N.XA|
00000150  8c 93 04 e6 e5 02 e0 61  1f f1 c7 37 fe 3c ef fd  |.......a...7.<..|
00000160  50 68 0f 47 5f f5 38 d6  37 fa a2 8c e8 fe c4 cc  |Ph.G_.8.7.......|
00000170  ff 56 5f fd 3f ec 85 13  ff 73 bf d1 55 bf 73 ce  |.V_.?....s..U.s.|
00000180  40 85 fc ea 79 7c 00 00  02 00 00 02 02 ad 04 97  |@...y|..........|
00000190  50 85 0c 95 26 52 cf 81  e9 25 d5 94 8b e7 3d 2e  |P...&R...%....=.|
000001a0  55 47 94 b6 06 10 be 1f  cf f4 5d 40 64 82 c5 03  |UG........]@d...|
000001b0  67 41 77 5a 46 a1 6c 33  47 ea 79 2a 62 bf 00 01  |gAwZF.l3G.y*b...|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 da bd 1d 0b 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by kansasnoob on 2011-05-08
I see you have two drives, both 320GB. Ubuntu is on /dev/sda and Windows is on /dev/sdb. But grub is not installed to the MBR of either drive:

> => No boot loader is installed in the MBR of /dev/sda
=> Windows is installed in the MBR of /dev/sdb

If I were you I'd use the Ubuntu Live CD/USB you installed with, boot choosing to Try Ubuntu and from the live desktop copy-n-paste these commands into the terminal:

First make sure that the Ubuntu drive is still recognized as /dev/sda by running:

```
sudo fdisk -l
```

The output should indicate that /dev/sda1 is indeed your "Linux" partition. I bring this up because on rare occasions Linux will recognize devices in a different order on subsequent reboots, **and we do NOT want to accidentally mount the Windows partition!** So, **only if /dev/sda1 is still recognized as your "Linux" partition**, proceed:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

Don't worry about errors from that last command, sometimes things fail to unmount, just reboot.

But on reboot you'll need to enter the system BIOS and change the hard disc boot priority so the Ubuntu drive boots first. That should be all there is to it.

---

### Post by banlocke on 2011-05-08
First off, I want to thank you for your reply. All the code worked perfectly after checking if the Linux partitions were maintained on /dev/sda. I installed grub to that partition and rearranged the boot settings so it would load first. 

However, when I boot the Ubuntu kernel (and this is not the first time I have encountered this error) the screen goes all white with black bars that move at first and then stop. I tried recovery mode and essentially the same thing happened (though the black bars were more block/brick like in appearance).

I suspect Ubuntu is having problems with some of the drivers for my hardware configuration. I am running an Asus A8N-SLI Deluxe Motherboard with an AMD Athlon 64 4000+ processor. I am using 2 video cards with the SLI technology. I also have 2 different pairs of RAM.  

The reason I suspect this (in my super noobish opinion) is because the only way I can get LiveCD to boot is when I check off 'acpi=off', 'noapic', and 'nolapic'. Perhaps these boot parameters control which drivers to load.

---

### Post by banlocke on 2011-05-08
Here is my new boot summary updated right after the aforementioned changes.

 ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    30,273,535    30,271,488  83 Linux
/dev/sda2          30,273,536    40,038,399     9,764,864  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdb2          81,915,435   268,414,019   186,498,585   f W95 Ext d (LBA)
/dev/sdb5          81,915,498   268,414,019   186,498,522   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f7337b1e-51f9-4a20-993d-1799ea54d36c   ext4                                     
/dev/sda2        d0076339-c2ad-44de-9342-e82a37c6f1a7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        46902FA6902F9B85                       ntfs       Windows 7                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        C24C11DB4C11CB55                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=f7337b1e-51f9-4a20-993d-1799ea54d36c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=f7337b1e-51f9-4a20-993d-1799ea54d36c ro single 
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f7337b1e-51f9-4a20-993d-1799ea54d36c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 46902FA6902F9B85
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
/dev/sda2       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
   4.7GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.38-8-generic
   4.7GB: boot/vmlinuz-2.6.38-8-generic
   1.7GB: initrd.img
   4.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 c0 b6 8e 00  |................|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  1f f9 d2 5e a8 38 66 69  63 18 f2 d3 80 b0 e4 f7  |...^.8fic.......|
00000010  c8 60 95 ff 95 85 3f dc  ae 3b fd 1a 54 fe 57 72  |.`....?..;..T.Wr|
00000020  7f a7 ff b3 7f 8a 89 89  7f 38 78 b6 fe 61 bf ff  |.........8x..a..|
00000030  7f f1 61 81 3f 16 25 83  f4 26 9a 8e 53 0a 8a 88  |..a.?.%..&..S...|
00000040  90 00 24 92 02 4d 4a 18  a2 15 05 aa 69 a3 0e 78  |..$..MJ.....i..x|
00000050  96 63 77 ba c4 f1 7b a2  cf 04 fb 54 92 0e 88 8e  |.cw...{....T....|
00000060  0c ad 94 56 e9 2a 74 14  ff fb 90 64 cf 80 03 1f  |...V.*t....d....|
00000070  63 d4 d3 0b 2a d4 55 8c  5a 9d 61 05 5d 4c 39 87  |c...*.U.Z.a.]L9.|
00000080  53 ac 34 ad 19 6b b1 6a  75 83 96 4b c1 20 c7 b5  |S.4..k.ju..K. ..|
00000090  20 d3 01 f4 a0 87 f6 18  63 3f f2 87 55 5b f5 11  | .......c?..U[..|
000000a0  1a 01 2b ff 14 bb 9f fc  68 6b d1 f9 84 cc ff ea  |..+.....hk......|
000000b0  d6 ff 75 ff 71 e4 10 1b  ff 30 a0 6f eb 28 b2 bf  |..u.q....0.o.(..|
000000c0  d0 c8 26 a1 a2 b2 da 61  b3 7e a8 04 a4 82 92 6e  |..&....a.~.....n|
000000d0  b4 10 40 d1 01 f0 31 c4  78 9a 97 ca b9 d8 e6 cb  |..@...1.x.......|
000000e0  8d af 9f 1a 57 d5 32 90  9b fa 28 23 55 c1 b8 14  |....W.2...(#U...|
000000f0  88 1e ed 48 e1 58 e5 57  f6 52 32 6d f8 98 67 f8  |...H.X.W.R2m..g.|
00000100  88 a0 79 5f f5 75 76 3f  f9 ff f2 bf fc 4d 7f f3  |..y_.uv?.....M..|
00000110  9d bf a2 10 17 ff 67 fd  02 c7 07 84 c5 fd 5a 51  |......g.......ZQ|
00000120  77 17 6a db 11 11 61 94  10 00 04 00 01 4e 39 cb  |w.j...a......N9.|
00000130  01 18 1a e0 13 10 a1 62  38 ce 53 a9 3f 50 00 86  |.......b8.S.?P..|
00000140  22 9e 54 a6 b1 49 a2 6c  66 25 75 ba 4e cd 58 41  |".T..I.lf%u.N.XA|
00000150  8c 93 04 e6 e5 02 e0 61  1f f1 c7 37 fe 3c ef fd  |.......a...7.<..|
00000160  50 68 0f 47 5f f5 38 d6  37 fa a2 8c e8 fe c4 cc  |Ph.G_.8.7.......|
00000170  ff 56 5f fd 3f ec 85 13  ff 73 bf d1 55 bf 73 ce  |.V_.?....s..U.s.|
00000180  40 85 fc ea 79 7c 00 00  02 00 00 02 02 ad 04 97  |@...y|..........|
00000190  50 85 0c 95 26 52 cf 81  e9 25 d5 94 8b e7 3d 2e  |P...&R...%....=.|
000001a0  55 47 94 b6 06 10 be 1f  cf f4 5d 40 64 82 c5 03  |UG........]@d...|
000001b0  67 41 77 5a 46 a1 6c 33  47 ea 79 2a 62 bf 00 01  |gAwZF.l3G.y*b...|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 da bd 1d 0b 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```


Grub2 is now my initial boot loader. Instead of getting the white screen with bars, now I just get a flashing cursor that repeats ad infinitum. When I boot Ubuntu in recovery mode, everything looks good for a few seconds, then it gets hung up at 'no IPv6 Routers Present', a common freeze point I suspect. 

When I go to the Windows Boot Manager (from Grub2), Ubuntu is still an option there and it still gives me a missing wubildr.mbr when I try to use it. Fortunately Windows 7 is still booting without problem. 

The next thing I'm going to try is to use the command line in Grub 2 to set 'acpi=off', 'noapic', 'nolapic' if it is even possible since that seemed to help LiveCD boot.

---

### Post by Quackers on 2011-05-09
I would first suggest that you try the "nomodeset" option as a one time boot option to see if the desktop then loads.
To do this when booting from the hard drive you should first see the grub menu which offers a choice of operating system to boot (not the Windows one).If you don't get this screen, hold down the shift key during boot and it should then show up.
When that screen appears, the top item is highlighted. This should be your Ubuntu installation (not the wubi one).
At this stage press the "e" key and a new screen will appear.
With the up/down arrows navigate to the end of the line which currently ends with "quiet splash" (but without quotes).
With the backspace key delete those 2 words and in their place type in "nomodeset" but without the quotes.
Then press ctrl + X to boot.

---

### Post by bcbc on 2011-05-09
Wherever your original wubi install is, it's now gone. So all you really have left of Wubi is an entry in your windows boot manager (BCD) which you should delete.

Since you've wiped out the \ubuntu directory I don't believe the wubi uninstall program will work, but there might be registry entries as well so follow the advice here: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

To remove the boot entry manually, you can use bcdedit or download and run easyBCD. 
For bcdedit, open a CMD.exe prompt as an administrator, run "bcdedit" to see what the {guid} entry for Ubuntu is. Then copy it and paste the guid into this command to remove it "bcdedit /delete {guid}"
(That's from my memory so check the help instructions: "bcdedit /h" to confirm).

---

### Post by kansasnoob on 2011-05-09
Please, if possible, also post the output of:

```
lspci | grep VGA
```

That will provide specific graphics card info.

---

### Post by Kfiat on 2011-05-09
Hi, i have recently installed ubuntu on my laptop (as one and only os) and i`m pretty happy with it. Now I would like to dual boot between win7 hp64 and ubuntu 10.10 on my desktop. I would like to install ubuntu 10.10 on a separate ssd drive, as win 7 is placed on a raid 0 BIOS made array, which I know is incompatible with ubuntu. Could you please give me some advice how to achieve the following:

1) ubuntu 10.10 as a default booting os without showing boot selection screen,
2) win 7 as a secondary boot os via boot selection screen (which keyboard shortcut activates boot selection screen btw ?)
3) make those 2 os`s totally and absolutely separate when it comes to boot manager so I can simply physically remove ssd with ubuntu anytime without dire consequences for win 7 boot.

I realize this is an offtopic, and probably noobish on my side to ask it here, but I`d really appreciate if someone could point me in the right direction.

Cheers

---

### Post by banlocke on 2011-05-09
> That will provide specific graphics card info.

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)

About to try a nomodeset boot and then work on the advice laid out by bcbc.

---

### Post by banlocke on 2011-05-09
> **bcbc said:**
> To remove the boot entry manually, you can use bcdedit or download and run easyBCD. 


When I run both easyBCD and bcdedit I get the same error:
"The boot configuration data store could not be opened.
The system cannot find the file specified."

This can't be good. On a note of progress...
> **Quackers said:**
> I would first suggest that you try the "nomodeset" option as a one time boot option to see if the desktop then loads.


This worked! I booted into Ubuntu off the hard disk for the first time. I installed video card drivers and got Unity working as well. 

I think bcbc is correct in that Wubi has probably conflicted matters when I failed to uninstall it properly before installing Ubuntu off LiveCD. The question now is, how do I fix my boot loader and do I need to clean Wubi from my registry?

---

### Post by banlocke on 2011-05-09
After editing my folder options and finding the windows boot file (BCD) manually with easyBCD, I deleted the Ubuntu portion in the windows boot loader. Now Grub is my sole boot loader and it seems to be booting both operating systems just fine. For some reason when I boot Ubuntu, I still see the white screen with black bars, but now instead of freezing, it loads into the operating system. 

I understand that getting Linux and Windows to coexist requires know-how and maintenance, however, for the time being this problem might be considered solved. 

bcbc thank you so much for your input, I have seen your posts solve many problems in other threads and I'm appreciative that you took the time to comment on my situation. To everyone else, thank you very much for your time and input as well.

---

### Post by bcbc on 2011-05-09
> **banlocke said:**
> After editing my folder options and finding the windows boot file (BCD) manually with easyBCD, I deleted the Ubuntu portion in the windows boot loader. Now Grub is my sole boot loader and it seems to be booting both operating systems just fine. For some reason when I boot Ubuntu, I still see the white screen with black bars, but now instead of freezing, it loads into the operating system. 

I understand that getting Linux and Windows to coexist requires know-how and maintenance, however, for the time being this problem might be considered solved. 

bcbc thank you so much for your input, I have seen your posts solve many problems in other threads and I'm appreciative that you took the time to comment on my situation. To everyone else, thank you very much for your time and input as well.
You're very welcome :)
I'm glad you sorted it out - and also thanks for the feedback on how to remove the bcd entry (I'll 'file it' for future use).

---

