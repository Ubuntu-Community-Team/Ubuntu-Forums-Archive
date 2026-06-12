---
title: "dual boot HP 'Recovery' partition caused Grub error no such partition"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by jayzymill on 2011-11-20
I've had dual boot Windows 7 and Ubuntu 11.10 on a HP G62.
It was fine until I accidentally the last option in the dual boot menu on startup, which I think might have been the 'Recovery' partition (I think I deleted the HP System Tools partition to install Ubuntu originally).

Now on startup I get a Grub error no such partition. So I think by booting into the 'Recovery' partition it wiped the master boot record. I'm worried I've lost my Ubuntu installation (don't care much about the Windows one). When I boot with Live CD I can see the Windows partition in the file manager but not the ubuntu files. In gparted have the disk is shown as unallocated, I fear that might be the ubuntu partition. 

I'm newbie with all this, if there is any way I can get my ubuntu installation back I would be very grateful for any advice, thanks.

I get the following about from fdisk:

ubuntu@ubuntu:~$ sudo fdisk -l
```
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce9043ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   500402175   249996288    7  HPFS/NTFS/exFAT
/dev/sda3   *   500404222   940722175   220158977    5  Extended
/dev/sda4       940722176   976560127    17918976    7  HPFS/NTFS/exFAT
/dev/sda5       932868096   940722175     3927040   82  Linux swap / Solaris

Disk /dev/sdb: 3997 MB, 3997171712 bytes
17 heads, 17 sectors/track, 27013 cylinders, total 7806976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001bdcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7806975     3899456    c  W95 FAT32 (LBA)

```

---

### Post by drs305 on 2011-11-20
jayzymill,

Welcome to the Ubuntu Forums.  

Please boot the LiveCD or another CD which gets you to a linux desktop. Download and run the boot info script and post the contents of RESULTS.txt

This file will show us the status of your boot files. You could also try creating a Boot Repair CD, which also provides the boot info script if it can't repair things.

Click the "BIS" or "Boot Repair" link in my signature to take you to the appropriate page.

---

### Post by jayzymill on 2011-11-20
Many thanks. Here is the Results.txt from the script:
```

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......g..V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1447552 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   500,402,175   499,992,576   7 NTFS / exFAT / HPFS
/dev/sda3    *    500,404,222   940,722,175   440,317,954   5 Extended
/dev/sda5         932,868,096   940,722,175     7,854,080  82 Linux swap / Solaris
/dev/sda4         940,722,176   976,560,127    35,837,952   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3997 MB, 3997171712 bytes
17 heads, 17 sectors/track, 27013 cylinders, total 7806976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     7,806,975     7,798,912   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       f920c34a-8a29-474b-83e3-eb99f2eb3320   ext3       
/dev/sda1        F0CE3898CE385954                       ntfs       SYSTEM
/dev/sda2        828EF8618EF84EE3                       ntfs       
/dev/sda4        967EF1707EF14A0F                       ntfs       RECOVERY
/dev/sda5        a7fc88aa-d10e-4227-b9db-811e3ac2dd92   swap       
/dev/sdb1        8A7F-04EE                              vfat       FLASH DRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/828EF8618EF84EE3  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by drs305 on 2011-11-20
> /dev/sda3    *    500,404,222   940,722,175   440,317,954   5 Extended
/dev/sda5         932,868,096   940,722,175     7,854,080  82 Linux swap / Solaris

The Ubuntu partition is not being located by the boot info script. There is a large gap in the partition table where your Ubuntu partition probably is.

I am not a partitioning expert. I think you will be able to use TestDisk to restore your old partition but can't be sure. 

I can give you a link on using TestDisk, but unless you are comfortable with partitioning options you might want to play with TestDisk but not save any operations until someone with more expertise can weigh in.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

### Post by jayzymill on 2011-11-21
Thanks for the Testdisk lead. I'm not all that confident I'll be able to get things back as they were, but I'll try.

It sounds like the lesson here is if installing ubuntu as a dual boot, first delete the Windows Recovery partition, because accidentally selecting this partition to boot into on startup will be very very bad :(

---

### Post by Mark Phelps on 2011-11-21
> **jayzymill said:**
> It sounds like the lesson here is if installing ubuntu as a dual boot, first delete the Windows Recovery partition ...
That is -- if you don't ever want to restore Windows.

Maybe a better first thing would be to back up Windows to an external drive -- so that you can restore it if anything goes wrong.

That way, when you THEN remove the Recovery partition, you still have a way of restoring Windows.

---

### Post by jayzymill on 2011-11-29
Ok I have an update to this!

I restored just the Linux partition, the /dev/sda2 of 499,992,576 sectors, which allowed me mount the partition from LiveCD (and copy some files in case..).

Of course I overwrote the existing partiton table and was left with just the Linux partition 
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce9043ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   500404224   917161983   208378880   83  Linux

```I now want to restore the partition table with the Windows 7 partition alongside the Linux & swap, as it was. Should I proceed with the following?
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
P HPFS - NTFS              0  32 33    25 126 37     407552 [SYSTEM]
P HPFS - NTFS             25 126 38 31148 151 43  499992576
L Linux                31148 184 13 57090 176 46  416757760
L Linux Swap           57090 209 16 57578 241 55    7841776
D Linux Swap           57579 149 43 58067 247 20    7845872
D Linux Swap           58068  90  7 58557  62 49    7854064
D HPFS - NTFS          58557  63  3 60788  14 26   35837952 [RECOVERY]
D FAT32 LBA            60788  14 27 60801  48 31     210992 [HP_TOOLS]

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue
SWAP2 version 1, 4014 MB / 3828 MiB


```You can see I have changed the first 4 partitions from D to P,P,L and L.
I'm not sure where the Grub loader will come into this. Did I overwrite this at the start of the disk when I accidentally booted into Window's RECOVERY partition...is the first partition above (SYSTEM) really needed to boot Win7?

I will hold off on writing this partition table in case anyone can advise, many thanks.

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63

     Partition                  Start        End    Size in sectors

 1 P HPFS - NTFS              0  32 33    25 126 37     407552 [SYSTEM]
 2 P HPFS - NTFS             25 126 38 31148 151 43  499992576
 3 E extended LBA         31148 184  1 57578 254 63  424602423
 5 L Linux                31148 184 13 57090 176 46  416757760
 6 L Linux Swap           57090 209 16 57578 241 55    7841776

[  Quit  ]  [Deeper Search]  [ Write  ]  [Extd Part]
                          Try to find more partitions

```

---

### Post by jayzymill on 2011-11-30
I have recreated my partitions, the RESULTS.txt from the boot info script are pasted below.
Does anyone know how I can get Grub working again for dual boot? I currently get the Grub error no such partition. Thanks

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......g..V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1447552 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   500,402,175   499,992,576   7 NTFS / exFAT / HPFS
/dev/sda3         500,404,212   925,006,634   424,602,423   f W95 Extended (LBA)
/dev/sda5         500,404,224   917,161,983   416,757,760  83 Linux
/dev/sda6         917,164,032   925,005,807     7,841,776  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3997 MB, 3997171712 bytes
17 heads, 17 sectors/track, 27013 cylinders, total 7806976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     7,806,975     7,798,912   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       f920c34a-8a29-474b-83e3-eb99f2eb3320   ext3       
/dev/sda1        F0CE3898CE385954                       ntfs       SYSTEM
/dev/sda2        828EF8618EF84EE3                       ntfs       
/dev/sda5        18cae7cb-29e8-4807-a7b6-63a9f7103255   ext4       
/dev/sda6        9f0acf3b-d14c-4a98-946b-1d4267c369f9   swap       
/dev/sdb1        8A7F-04EE                              vfat       FLASH DRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 18cae7cb-29e8-4807-a7b6-63a9f7103255
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root 18cae7cb-29e8-4807-a7b6-63a9f7103255
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IE
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 18cae7cb-29e8-4807-a7b6-63a9f7103255
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=18cae7cb-29e8-4807-a7b6-63a9f7103255 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 18cae7cb-29e8-4807-a7b6-63a9f7103255
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=18cae7cb-29e8-4807-a7b6-63a9f7103255 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 18cae7cb-29e8-4807-a7b6-63a9f7103255
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=18cae7cb-29e8-4807-a7b6-63a9f7103255 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 18cae7cb-29e8-4807-a7b6-63a9f7103255
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=18cae7cb-29e8-4807-a7b6-63a9f7103255 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 18cae7cb-29e8-4807-a7b6-63a9f7103255
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 18cae7cb-29e8-4807-a7b6-63a9f7103255
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root F0CE3898CE385954
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 828EF8618EF84EE3
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 967EF1707EF14A0F
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
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=9f0acf3b-d14c-4a98-946b-1d4267c369f9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-12-generic              2
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-2.6.38-12-generic                 1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                    32
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by jayzymill on 2011-11-30
I will try to fix my MBR from LiveCD as follows:

```
*sudo mount /dev/sda5*
``````
*sudo grub-install --boot-directory=/mnt/boot/ /dev/sda*
```

---

### Post by drs305 on 2011-11-30
Looking at the RESULTS.txt, your fstab still refers to sda7 rather than sda5:
> =============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
**/dev/sda7       /               ext4    errors=remount-ro 0       1**
# swap was on /dev/sda8 during installation
UUID=9f0acf3b-d14c-4a98-946b-1d4267c369f9 none            swap    sw              0  


Boot the LiveCD, mount sda5 so you can edit your fstab, then open gedit as root:
```
sudo mount /dev/sda5 /mnt
gksu gedit /mnt/etc/fstab
```

Change the **bold** line above to this:
```
UUID=18cae7cb-29e8-4807-a7b6-63a9f7103255  /  ext4  errors=remount-ro 0  0 
```

Save the file, then run:
```
sudo grub-install --root-directory=/mnt /dev/sda
```


Added:
Your command is actually more correct for Grub 1.99. I've used a more universally applicable Grub command above. Either will work.
```
sudo grub-install --boot-directory=/mnt/boot/ /dev/sda 
```

---

### Post by jayzymill on 2011-11-30
Many thanks for taking the time to look at this.
I will correct the fstab file before reinstalling grub, and will post the result.

---

### Post by jayzymill on 2011-11-30
The laptop now boots straight to the Grub command line. I can't boot into ubuntu to run "sudo grub-update" to rebuild the grub menu. I tried mounting from LiveCD but couldn't run the bash I think maybe because LiveCD is 32bit while laptop is 64bit.

I tried to boot directly from Grub:
root (hd0,4)
kernel /boot/vmlinuz-3.XXX root=/dev/sda5

but got error: "VFS: Cannot open root device "sda5" or unknown-block(0,0)" :(
I tried with sda3 in the last root parameter and got same.

---

### Post by drs305 on 2011-11-30
The commands you used are for Grub legacy but you should have Grub 1.99 on your system.

If the grub files are intact, you can try this from the grub prompt:

```
ls (hd0,5)/boot/grub  # See if it locates all the *.mod files. If not, don't continue.
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod (hd0,5)/boot/grub/linux.mod
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot
```

If it boots, run "sudo update-grub".

---

### Post by jayzymill on 2011-11-30
Thanks I realised from your comment that I was using Grub legacy (I'd accidentally replaced Grub2 previously). I reinstalled Grub 2 from Software Centre, mounted /dev/sda and did a sudo grub-install and then the laptop booted straight into the Grub menu :D

And I can boot Windows 7 (if someday I have reason...)

When I boot into Ubuntu 11.10 now it appears to be Gnome or something rather than Unity. The bar at the top is empty except for File Edit View Go Bookmarks and Help. Quite strange but seems to be something superficial. I'm sure after some sleep it can be tackled.

Thanks for you help drs I never thought I'd get the dual boot restored really.

---

