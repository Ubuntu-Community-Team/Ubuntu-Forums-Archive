---
title: "Cannot boot Ubuntu after install (11.04, 10.10), dual boot"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by paxmaniac on 2011-07-09
I'm having a frustrating time trying to install Ubuntu as a dual boot with Windows 7 on a new Acer Aspire 5750.

The initial install proceeded without incident until an error along the lines of "Cannot install GRUB to /dev/sda".  

I continued without installing GRUB, and attempted to install GRUB from the live CD:

```

sudo mount /dev/sda5 /mnt
sudo grub-setup -d /mnt/boot/grub /dev/sda

```

This installed GRUB, but only linking to my Windows 7 partition (sda2).

I tried to use the chroot method to run update-grub, but this gave me the error:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory

```

This is quite odd: /mnt/bin does not contain bash although it does contain most of the usual /bin files.

I have tried most of the suggestions in the Grub2 documentation without success.  I tried reinstalling 11.04, and also tried installing 10.10 (including repartitioning), but the result is the same.

I tried using the SuperGRUB live CD to "detect OS", but it can only find Windows 7.

boot-script output attached (10.10 being the latest install).

Any wise advice welcome!

---

### Post by oldfred on 2011-07-09
You did manage to get grub installed, but you have no kernels??
You also have part of grub installed to sda1. Are your kernels in sda1?

>     Boot files:        /BOOTMGR /BOOT/BCD /boot/grub/core.img

Windows is not case sensitive, so you will not be able to boot your recovery partiton until you delete the /boot/grub folder, but be caredful to not delete /BOOT that has the BCD as that is part of windows.

Are your kernels in sda1 or else it may just be quicker to reinstall.

This should also include a list of kernels & initrd files:
> =================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 343.123573303 = 368.426131456  boot/grub/core.img                             1
 399.202415466 = 428.640329728  boot/grub/grub.cfg                             1



---

### Post by Quackers on 2011-07-09
Your boot script output in code tags
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......)(.8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 7491342 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     31,459,328    31,664,127       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          31,664,128   383,736,544   352,072,417   7 NTFS / exFAT / HPFS
/dev/sda4         383,737,854   976,771,071   593,033,218   5 Extended
/dev/sda5         383,737,856   960,772,095   577,034,240  83 Linux
/dev/sda6         960,774,144   976,771,071    15,996,928  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3997 MB, 3997695488 bytes
4 heads, 32 sectors/track, 60999 cylinders, total 7807999 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,807,998     7,807,967   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       283dd90d-e7e5-da41-8f7c-af51eabd04a6   ext2       
/dev/sda1        DEC620D9C620B3A5                       ntfs       PQSERVICE
/dev/sda2        089021419021369A                       ntfs       SYSTEM RESERVED
/dev/sda3        E81C22B51C227F26                       ntfs       Acer
/dev/sda5        7f8d927d-e1da-4fee-ab40-8e1b76bee209   ext4       
/dev/sda6        59e2923f-737f-4259-8e94-fa93f0b3ba59   swap       
/dev/sdb1        1EFC-2952                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev             /mnt/dev                 none       (rw,bind)
/dev/pts         /mnt/dev/pts             none       (rw,bind)
/dev/sda5        /mnt                     ext4       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
search --no-floppy --fs-uuid --set 7f8d927d-e1da-4fee-ab40-8e1b76bee209
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 7f8d927d-e1da-4fee-ab40-8e1b76bee209
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7f8d927d-e1da-4fee-ab40-8e1b76bee209
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7f8d927d-e1da-4fee-ab40-8e1b76bee209
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 089021419021369a
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
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 343.123573303 = 368.426131456  boot/grub/core.img                             1
 399.202415466 = 428.640329728  boot/grub/grub.cfg                             1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32

prompt 0

menu title UNetbootin

timeout 100



label unetbootindefault

menu label Default

kernel /ubnkern

append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent



label ubnentry0

menu label ^Help

kernel /ubnkern

append initrd=/ubninit  persistent



label ubnentry1

menu label ^Try Ubuntu without installing

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- persistent



label ubnentry2

menu label ^Install Ubuntu

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- persistent



label ubnentry3

menu label ^Check disc for defects

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- persistent



label ubnentry4

menu label Test ^memory

kernel /install/mt86plus

append initrd=/ubninit  persistent



label ubnentry5

menu label ^Boot from first hard disk

kernel /ubnkern

append initrd=/ubninit  persistent



--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v3.xx)


```
Let me take a look at it and get back to you.

EDIT  please see oldfred's post above :-)

---

### Post by paxmaniac on 2011-07-09
You're absolutely right of course: there were no kernels.  Why this is, I have no idea (and based on the symptoms, I'm pretty sure it was the same problem on the previous two install attempts).  The kernels were not on sda1, which is the windows recovery partition.  I'm not sure how GRUB got onto sda1, but it's possible I did a grub-install on the wrong partition at some point.

Anyway, I did another reinstall - the 4th altogether (upgraded 10.10 to 11.04 from the iso), and we now have kernels and a correctly installed grub.  I also removed grub from sda1 as suggested.

Thanks for the replies.

---

### Post by oldfred on 2011-07-09
Whatever works. But now you are an expert on installs. It only takes 2 or 3 to be an expert.:)

---

### Post by Quackers on 2011-07-10
Glad to see that your problems are solved :-)

---

