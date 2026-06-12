---
title: "Grub2 problem"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by blackhill on 2011-05-18
I had a PC with win XP on one disk and ubuntu 10.04 on a second disk both working normally.
I tried to upgrade to 10.10 and all seemed to go well
However, on trying to reboot the computer, all I got was Error: the symbol grob_xputs not found. This was followed by the grub rescue prompt.
 Having had a similar probl;em during a previous upgrade from ubuntu 9.10 to 10.04 I ran the boot info script.
The output from this is detailed below

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdd.

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Restore: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 15336 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *         80,325   146,496,734   146,416,410   7 NTFS / exFAT / HPFS
/dev/sda3         146,496,735   156,232,124     9,735,390  1c Hidden W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb2    *    184,313,745   470,367,134   286,053,390   7 NTFS / exFAT / HPFS
/dev/sdb3                  63   184,313,744   184,313,682   5 Extended
/dev/sdb5         178,578,666   181,341,719     2,763,054  82 Linux swap / Solaris
/dev/sdb6         181,341,783   184,313,744     2,971,962  82 Linux swap / Solaris
/dev/sdb7                 189   171,220,769   171,220,581  83 Linux
/dev/sdb8         171,220,833   178,578,539     7,357,707  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 8210 MB, 8210350080 bytes
74 heads, 10 sectors/track, 21670 cylinders, total 16035840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               5,568    16,035,839    16,030,272   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       e0edf1f7-4780-4fbd-9758-88ed930ff139   ext3       
/dev/sda2        065C05945C058024                       ntfs       WinXP
/dev/sda3                                               vfat       DellRestore
/dev/sdb2        1CC055D9C055B9AA                       ntfs       Win Backup
/dev/sdb5        2be06894-172a-471e-823b-0646c2da2942   swap       
/dev/sdb6        612cdcb1-5de0-4f8a-a458-2bdfd025a9ac   swap       
/dev/sdb7        726ccc36-ad9e-443e-99f5-0ce704562f7e   ext4       
/dev/sdb8        195eed8b-1870-4882-aadf-0960fa20881e   swap       
/dev/sdc1        831A-B9B8                              vfat       
/dev/sdd1        3433-3231                              vfat       UDISK

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set 726ccc36-ad9e-443e-99f5-0ce704562f7e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set 726ccc36-ad9e-443e-99f5-0ce704562f7e
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
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 726ccc36-ad9e-443e-99f5-0ce704562f7e
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=726ccc36-ad9e-443e-99f5-0ce704562f7e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 726ccc36-ad9e-443e-99f5-0ce704562f7e
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=726ccc36-ad9e-443e-99f5-0ce704562f7e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 726ccc36-ad9e-443e-99f5-0ce704562f7e
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=726ccc36-ad9e-443e-99f5-0ce704562f7e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 726ccc36-ad9e-443e-99f5-0ce704562f7e
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=726ccc36-ad9e-443e-99f5-0ce704562f7e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 726ccc36-ad9e-443e-99f5-0ce704562f7e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 726ccc36-ad9e-443e-99f5-0ce704562f7e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda2)" {
    savedefault
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 065c05945c058024
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

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=726ccc36-ad9e-443e-99f5-0ce704562f7e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=195eed8b-1870-4882-aadf-0960fa20881e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.136282444 = 0.146332160    boot/grub/core.img                             1
   3.837194920 = 4.120156672    boot/grub/grub.cfg                             1
  15.802343845 = 16.967637504   boot/initrd.img-2.6.32-28-generic              2
  17.556990147 = 18.851674624   boot/initrd.img-2.6.35-28-generic              1
  14.057672977 = 15.094311424   boot/vmlinuz-2.6.32-28-generic                 1
  17.173491001 = 18.439895552   boot/vmlinuz-2.6.35-28-generic                 1
  17.556990147 = 18.851674624   initrd.img                                     1
  15.802343845 = 16.967637504   initrd.img.old                                 2
  17.173491001 = 18.439895552   vmlinuz                                        1
  14.057672977 = 15.094311424   vmlinuz.old                                    1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

I would be very grateful for any help as to how to procede

---

### Post by kansasnoob on 2011-05-18
OK, I'm looking back at this old thread:

[http://ubuntuforums.org/showthread.php?t=1364928](http://ubuntuforums.org/showthread.php?t=1364928)

I know how to fix this, and hopefully this time we'll fix it so future upgrades don't break grub :D

Just give me a little time to type things and make sure I get it right.

I'm also nursing an old sick dog so please be patient.

---

### Post by kansasnoob on 2011-05-18
Please copy-n-paste the following commands:

```
sudo mount /dev/sdb7 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
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

Note: Don't worry about any errors from that last command, sometimes things fail to unmount!

Now just reboot. Hopefully you'll be able to boot into both Ubuntu and Windows.

If so let's try to fix things so future updates/upgrades don't break grub :)

While booted into your installed Ubuntu copy-n-paste:

```
sudo dpkg-reconfigure grub-pc
```

That should present a number of debconf windows similar to this:

[ATTACH]192557[/ATTACH]

[ATTACH]192558[/ATTACH]

[ATTACH]192559[/ATTACH]

[ATTACH]192560[/ATTACH]

To select OK on the first three just hit the Tab key. On the last use the up and down arrows along with the spacebar to select both /dev/sda and /dev/sdb, then again Tab to select OK.

That will hopefully keep things from breaking again in the future, reason being that 'dpkg' stores previous grub-install info.

A nifty tool you might like to have:

[http://www.bootproblems.com/super-grub2-disk/](http://www.bootproblems.com/super-grub2-disk/)

The download link is at the bottom of the page. As it says there, "Super GRUB2 Disk can only be used to boot a broken system, it cannot fix it directly." But I've found the "Detect any OS" option to work [COLOR="Red"]very[/COLOR] reliably.

---

### Post by blackhill on 2011-05-19
You are a genius.
Seems to have worked completely
Extremely grateful
John

---

