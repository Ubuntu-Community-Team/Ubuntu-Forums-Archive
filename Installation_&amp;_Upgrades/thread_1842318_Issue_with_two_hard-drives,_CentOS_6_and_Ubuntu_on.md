---
title: "Issue with two hard-drives, CentOS 6 and Ubuntu on each"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by vrkrao on 2011-09-11
Hi,


I had CentOS 6 running fine until I decided to procure a second hard disk and loaded Ubuntu 11.04 on it.
I use CentOS 6 for work. I wanted a more user-friendly (in terms of tools and apps available) for home use.
Hence, loaded Ubuntu 11.04 on a second hard disk. The idea was to specify the Hard-disk to boot from, at the time of booting.

The background:
* Motherboard + Processor = Intel DH67BL + i-5
* The Machine had CentOS 6 (64-bit) fully working with Hard-drive 1 - Western Digital 1TB, Sata3, CentOS 6, sitting on SATA port 0 (This Mobo has 2 SATA, 2 eSATA, 2 SATA3 ports)
* Hard-drive 2 - Seagate 500GB, Sata with Ubuntu 11.04, SATA port 3
While installing Ubuntu, it asked me where to install showing both the hard disks. I installed on the new one (500GB). Installation went fine and working
fine.
* Both drives are recognized by BIOS

The problem:
* On boot, i get two options on boot screen (F2 - Bios setup) and (F10 - Boot menu) - Not from the OS.
* I press F10, I see both hard-disks
* Irrespective of my selection, It's always booting Ubuntu from hard disk 2.
* I unplugged the hard disk with Ubuntu, the system still tries to boot from Ubuntu disk. Intel Boot Agent loads, displays MAC and GUID and It's coming to some grub prompt 'grub rescue'

* I connected the hard disk with Ubuntu back, again, it boots in Ubuntu only.
* I'm not able to boot CentOS 6 at all.

With little knowledge I discover that, from the disk utility in Ubuntu, I see both the hard disks as sda and sdb. The Hard-disk with CentOS has 'bootable' in partition-flags section. The one with Ubuntu doesn't. There is no boot partition on the HD2 (Ubuntu hard disk). It appears that the boot loader has been loaded on the disk with CentOS.

I've really liked Ubuntu and done DVD authoring using openshot. I would like to use both the versions of Linux. 

Please help.

PS: CentOS is 64-bit and Ubuntu loaded is 32-bit, if that matters

regds.,
Ramki.

---

### Post by vrkrao on 2011-09-12
Hi,

  A little update.

    Following these two threads.
[http://ubuntuforums.org/showthread.php?t=1476603](http://ubuntuforums.org/showthread.php?t=1476603)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

   Was able to add the CentOS menu to Ubuntu grub.
But, looks like i'm not able to link the linux, initrd execs correctly.

Ubuntu uses Grub2 whereas CentOS uses grub. Have used the script
as sourceforge.net to get the following bootinfo on the disks. The results are as follows.
(Cut - Paste of result file)


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid fa89048e-f583-4626-add3-4f78265bcac7 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda1 and looks at sector 543186 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #1 
                       for /grub/grub.conf.
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda2: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000  83 Linux
/dev/sda2           1,026,048 1,953,523,711 1,952,497,664  8e Linux LVM


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   960,036,863   960,034,816  83 Linux
/dev/sdb2         960,038,910   976,771,071    16,732,162   5 Extended
/dev/sdb5         960,038,912   976,771,071    16,732,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2df7c975-c906-4105-981a-3a623b978202   ext4       
/dev/sda2        ocY2Gf-ZdPu-4OH7-yZxD-m3eC-MNFL-lXUjNA LVM2_member 
/dev/sdb1        fa89048e-f583-4626-add3-4f78265bcac7   ext4       
/dev/sdb5        ade4674d-b6ab-44e2-b38e-345cceb231cf   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/CentOS_6.0_Final  iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


============================= sda1/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_prabha-lv_root
#          initrd /initrd-[generic-]version.img
boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title CentOS Linux (2.6.32-71.29.1.el6.x86_64)
	root (hd0,0)
	kernel /vmlinuz-2.6.32-71.29.1.el6.x86_64 ro root=/dev/mapper/vg_prabha-lv_root rd_LVM_LV=vg_prabha/lv_root rd_LVM_LV=vg_prabha/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us crashkernel=128M rhgb quiet
	initrd /initramfs-2.6.32-71.29.1.el6.x86_64.img
title CentOS (2.6.32-71.el6.x86_64)
	root (hd0,0)
	kernel /vmlinuz-2.6.32-71.el6.x86_64 ro root=/dev/mapper/vg_prabha-lv_root rd_LVM_LV=vg_prabha/lv_root rd_LVM_LV=vg_prabha/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us crashkernel=128M rhgb quiet
	initrd /initramfs-2.6.32-71.el6.x86_64.img
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.260256767 = 0.279448576    grub/grub.conf                                 1
   0.260256767 = 0.279448576    grub/menu.lst                                  1
   0.259117126 = 0.278224896    grub/stage2                                    1
   0.062965393 = 0.067608576    initramfs-2.6.32-71.29.1.el6.x86_64.img        2
   0.031665802 = 0.034000896    initramfs-2.6.32-71.el6.x86_64.img             2
   0.054862976 = 0.058908672    initrd-2.6.32-71.29.1.el6.x86_64kdump.img      1
   0.035314560 = 0.037918720    initrd-2.6.32-71.el6.x86_64kdump.img           2
   0.043575287 = 0.046788608    vmlinuz-2.6.32-71.29.1.el6.x86_64              2
   0.016227722 = 0.017424384    vmlinuz-2.6.32-71.el6.x86_64                   1

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root fa89048e-f583-4626-add3-4f78265bcac7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root fa89048e-f583-4626-add3-4f78265bcac7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=50
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root fa89048e-f583-4626-add3-4f78265bcac7
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=fa89048e-f583-4626-add3-4f78265bcac7 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root fa89048e-f583-4626-add3-4f78265bcac7
	echo	'Loading Linux 2.6.38-11-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=fa89048e-f583-4626-add3-4f78265bcac7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root fa89048e-f583-4626-add3-4f78265bcac7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root fa89048e-f583-4626-add3-4f78265bcac7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=fa89048e-f583-4626-add3-4f78265bcac7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=ade4674d-b6ab-44e2-b38e-345cceb231cf none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 248.135002136 = 266.432929792  boot/grub/core.img                             1
 248.139904022 = 266.438193152  boot/grub/grub.cfg                             1
   1.133983612 = 1.217605632    boot/initrd.img-2.6.38-11-generic-pae          2
   0.892032623 = 0.957812736    boot/vmlinuz-2.6.38-11-generic-pae             1
   1.133983612 = 1.217605632    initrd.img                                     2
   0.892032623 = 0.957812736    vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
##############

I see /dev/sda1 mounted in ubuntu as /media/UUID (the big hex number).
 
This is what, I have written in 40_custom  the custom menu file of Ubuntu to list CentOS.
-----
menuentry "CentOS Linux (2.6.32-71.29.1.el6.x86_64)" {
insmod ext4
#set root='(hd0,1)'
set root= '(/dev/sda,1)'     
search --no-floppy --fs-uuid --set=root 2df7c975-c906-4105-981a-3a623b978202
linux /vmlinuz-2.6.32-71.29.1.el6.x86_64 root=UUID=2df7c975-c906-4105-981a-3a623b978202 
initrd /initramfs-2.6.32-71.29.1.el6.x86_64.img
-------
This shows up in grub.cfg (equivalent to grub.conf) when i update the grub. Also shows up in boot
menu. But, unable to link the linux image of centOS.


Any help appreciated. Stuck with this for two days over the weekend.

regds.,
Ramki.

---

