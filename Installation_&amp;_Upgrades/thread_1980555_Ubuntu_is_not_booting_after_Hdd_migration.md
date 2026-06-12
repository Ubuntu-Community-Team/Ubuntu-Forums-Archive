---
title: "Ubuntu is not booting after Hdd migration"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by penn919 on 2012-05-15
Hi,

I recently decided that I wanted to migrate my Lucid Lynx ubuntu installation from an external 80GB hdd onto a internal 120GB  hdd. I didn't use ghost or anything like that, I simply created a backup.tgz of my file system (excluding proc, lost+found, backup.tgz, media, and sys) and I restored the backup on a fresh install of Lucid Lynx on the internal 120Gb; however, after I rebooted I get the following error when I try to boot into Ubuntu from Grub:

 [IMG]https://lh3.googleusercontent.com/-EvftSyC9n5I/T7G60Pnt8kI/AAAAAAAANH4/BhQEekY7zJY/s490/2012-05-14%252021.55.13.jpg[/IMG]

I can still boot into Windows 7 (which is installed on a different Hdd) via Grub, but I can't get into Ubuntu. I'll try running a boot info script and posting the results here. Maybe that will help.

---

### Post by roelforg on 2012-05-15
Just use the livecd to run update-grub
Your partition layout changed when you moved but grub isn't updated yet to incorperate the changes. So, grub looks for a partition that *used* to be there, but isn't anymore now (well, it is but not under the id grub expects it to be).

If it doesn't work,
[https://help.ubuntu.com/community/Grub2/Installing#Reinstall_from_the_LiveCD](https://help.ubuntu.com/community/Grub2/Installing#Reinstall_from_the_LiveCD)
is information about reinstalling grub. This WILL fix it but may cause you to lose any mods to boot options.

---

### Post by darkod on 2012-05-15
Yes, if you are using grub2 from this installation, it has to be reinstalled to the MBR so it can look for the core.img file at the correct place.

But in that case it wouldn't be able to boot windows too, usually.

Also, the UUID reported as missing is ntfs partition, not linux. I wonder if that is your windows partition and it's booting windows in a different way.

I think you definitely need to reinstall grub2 to the MBR so it can connect to the new partition.

Note that you will need to change the UUID to the one of the new partition in /etc/fstab also. In fstab there are still gonna be the UUIDs of the old partitions.

---

### Post by roelforg on 2012-05-15
> **darkod said:**
> Yes, if you are using grub2 from this installation, it has to be reinstalled to the MBR so it can look for the core.img file at the correct place.

But in that case it wouldn't be able to boot windows too, usually.

Also, the UUID reported as missing is ntfs partition, not linux. I wonder if that is your windows partition and it's booting windows in a different way.

I think you definitely need to reinstall grub2 to the MBR so it can connect to the new partition.

Note that you will need to change the UUID to the one of the new partition in /etc/fstab also. In fstab there are still gonna be the UUIDs of the old partitions.

Maybe he has a seperate /boot partition? That, for some miracle, still has the same location/id as grub expects but it looks for / on the wrong partition?

---

### Post by penn919 on 2012-05-15
Well here's the results of the boot info script:

```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sda2    *     10,233,405   312,576,094   302,342,690   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 3,292,626,943 3,292,624,896   7 NTFS / exFAT / HPFS
/dev/sdb2       3,292,626,944 3,907,024,895   614,397,952   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   224,827,391   224,825,344  83 Linux
/dev/sdc2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sdc5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 999 MB, 999817216 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1952768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63     1,952,767     1,952,705   6 FAT16


Drive: sde _____________________________________________________________________

Disk /dev/sde: 31.2 GB, 31247564800 bytes
122 heads, 34 sectors/track, 14713 cylinders, total 61030400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               8,192    61,030,399    61,022,208   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0E4E-05CE                              vfat       PQSERVICE
/dev/sda2        B214DB7F14DB44CF                       ntfs       
/dev/sdb1        74287014286FD420                       ntfs       Samsung
/dev/sdb2        4EDED02CDED00E59                       ntfs       Backup
/dev/sdc1        37354ddb-6634-4a11-8ee1-ec84098224ff   ext4       
/dev/sdc5        b1943cae-a8e8-4cbb-af5f-37d8de1137b3   swap       
/dev/sdd1        1C52-9119                              vfat       KINGSTON
/dev/sde1        D493-AF44                              vfat       32GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/B214DB7F14DB44CF  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd5,1)'
search --no-floppy --fs-uuid --set 407410CD7410C814
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd5,1)'
search --no-floppy --fs-uuid --set 407410CD7410C814
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-41-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-41-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-41-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-41-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-41-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-41-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-34-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-34-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-34-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-34-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-34-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-34-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-33-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-33-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-33-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-33-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-33-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-33-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-32-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-32-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-32-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-32-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-32-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-32-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-30-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-30-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-29-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-29-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-29-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-29-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-29-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-28-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-28-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-27-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-27-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-26-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-26-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-25-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-25-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-24-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-24-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-23-generic-pae" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-23-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd5,1)'
	search --no-floppy --fs-uuid --set 407410CD7410C814
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-23-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0e4e-05ce
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set B214DB7F14DB44CF
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  68.142070770 = 73.166991360   boot/grub/core.img                             1
  68.141586304 = 73.166471168   boot/grub/grub.cfg                             1
  68.149490356 = 73.174958080   boot/initrd.img-2.6.32-21-generic              1
  68.157161713 = 73.183195136   boot/initrd.img-2.6.32-23-generic-pae          1
  68.164783478 = 73.191378944   boot/initrd.img-2.6.32-24-generic-pae          1
  68.321147919 = 73.359273984   boot/initrd.img-2.6.32-25-generic-pae          1
  68.273986816 = 73.308635136   boot/initrd.img-2.6.32-26-generic-pae          1
  68.172454834 = 73.199616000   boot/initrd.img-2.6.32-27-generic-pae          1
  68.266315460 = 73.300398080   boot/initrd.img-2.6.32-28-generic-pae          1
  68.258644104 = 73.292161024   boot/initrd.img-2.6.32-29-generic-pae          1
  68.336578369 = 73.375842304   boot/initrd.img-2.6.32-30-generic-pae          1
  68.196147919 = 73.225056256   boot/initrd.img-2.6.32-32-generic-pae          1
  68.180152893 = 73.207881728   boot/initrd.img-2.6.32-33-generic-pae          1
  68.281684875 = 73.316900864   boot/initrd.img-2.6.32-34-generic-pae          1
  68.215526581 = 73.245863936   boot/initrd.img-2.6.32-41-generic-pae          1
   0.137542725 = 0.147685376    boot/vmlinuz-2.6.32-21-generic                 1
  68.328910828 = 73.367609344   boot/vmlinuz-2.6.32-23-generic-pae             1
  68.224475861 = 73.255473152   boot/vmlinuz-2.6.32-24-generic-pae             1
  68.325031281 = 73.363443712   boot/vmlinuz-2.6.32-25-generic-pae             1
  68.340461731 = 73.380012032   boot/vmlinuz-2.6.32-26-generic-pae             1
  68.137676239 = 73.162272768   boot/vmlinuz-2.6.32-27-generic-pae             1
  68.241584778 = 73.273843712   boot/vmlinuz-2.6.32-28-generic-pae             1
  68.344348907 = 73.384185856   boot/vmlinuz-2.6.32-29-generic-pae             1
  68.207824707 = 73.237594112   boot/vmlinuz-2.6.32-30-generic-pae             1
  68.186374664 = 73.214562304   boot/vmlinuz-2.6.32-32-generic-pae             1
  68.200035095 = 73.229230080   boot/vmlinuz-2.6.32-33-generic-pae             1
  68.228363037 = 73.259646976   boot/vmlinuz-2.6.32-34-generic-pae             1
  68.203933716 = 73.233416192   boot/vmlinuz-2.6.32-41-generic-pae             1
  68.215526581 = 73.245863936   initrd.img                                     1
  68.281684875 = 73.316900864   initrd.img.old                                 1
  68.203933716 = 73.233416192   vmlinuz                                        1
  68.228363037 = 73.259646976   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  2e ac 59 e8 b9 fc 50 90  1e b9 c0 f7 c3 00 26 79  |..Y...P.......&y|
00000010  1d 49 e9 7d 2a f5 05 20  a1 b6 ff 84 6b 17 c9 e4  |.I.}*.. ....k...|
00000020  cf 39 c3 eb 84 4f d3 ca  c5 59 0d d4 25 fa c6 f7  |.9...O...Y..%...|
00000030  ef 0e 4a a2 aa 4a 2f eb  34 88 9e d5 3e dc 11 6d  |..J..J/.4...>..m|
00000040  a9 27 84 27 76 5d 8a 6a  f3 a0 ce 09 80 f4 a6 71  |.'.'v].j.......q|
00000050  bb 05 10 e6 49 67 59 6d  7e 8b 9a 6f e3 ac bc 56  |....IgYm~..o...V|
00000060  79 34 c4 88 5b 6f 03 6a  a5 12 57 75 ba 23 73 13  |y4..[o.j..Wu.#s.|
00000070  14 8c e1 9a ba 63 1a 6e  13 f0 ba cf ac 0d 0e 33  |.....c.n.......3|
00000080  67 f7 f2 0a d0 e4 ce e4  a9 bf a3 43 0a db 03 39  |g..........C...9|
00000090  08 53 b7 31 d4 c5 ea 2b  18 29 0d 2f dc a0 47 30  |.S.1...+.)./..G0|
000000a0  15 01 f1 7d 7a 6f 4c 16  33 24 77 56 a1 93 63 f4  |...}zoL.3$wV..c.|
000000b0  7b 4f 9c a2 b0 26 a9 41  97 85 f0 85 10 75 03 6d  |{O...&.A.....u.m|
000000c0  63 2c dc bb 82 61 7b fc  85 9a d9 f4 7f db a0 23  |c,...a{........#|
000000d0  4f 2c 70 6c 22 78 4e a5  35 98 ba 05 dd 9b 88 52  |O,pl"xN.5......R|
000000e0  3f ab 81 95 12 83 1e 30  ab 6f 5b f0 ad 90 3e 23  |?......0.o[...>#|
000000f0  d8 6b 67 5f fa 98 76 21  3d 03 7b 6c 9d 1c 03 8c  |.kg_..v!=.{l....|
00000100  1f 1e 18 26 31 cf e0 4b  a4 a3 2f cb 29 c8 f1 78  |...&1..K../.)..x|
00000110  0d 0d ac 1d ab 81 7b 25  cb 46 db 50 32 0c 30 eb  |......{%.F.P2.0.|
00000120  c9 2e e2 73 a1 dc c3 05  a5 a1 c8 6b a7 cd 33 0f  |...s.......k..3.|
00000130  2b 03 b9 a4 c3 35 65 68  79 f9 4f 07 da f7 68 33  |+....5ehy.O...h3|
00000140  6d 95 4c 93 83 c3 1d a5  19 71 05 c1 e1 09 44 b7  |m.L......q....D.|
00000150  32 65 16 44 69 a1 fb 56  b6 af d8 ce ab b9 db bd  |2e.Di..V........|
00000160  9a ef cd 8c b3 69 ef f9  96 9a 50 77 ac 6b 49 8e  |.....i....Pw.kI.|
00000170  81 8d 91 e1 7d 4a 63 f4  e4 61 ea 98 44 6b e3 c0  |....}Jc..a..Dk..|
00000180  5d 7b fb 07 af c4 37 5b  e2 5d f1 82 c9 36 c7 b2  |]{....7[.]...6..|
00000190  62 a0 de dc 16 e3 67 49  79 11 b6 a3 84 09 3d 22  |b.....gIy.....="|
000001a0  06 be 33 32 c3 36 54 b6  0b 73 cc 10 c0 f8 51 e3  |..32.6T..s....Q.|
000001b0  c4 0f 51 92 40 1d ff 91  16 1a dc 75 3e 0d 00 fe  |..Q.@......u>...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdf sdg sdh sdi sdj 
```

@roelforg

I tired running update-grub, but I got this:
```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

@darkod
At the grub menu, the version number says 1.98. Does that count as Grub2?

---

### Post by roelforg on 2012-05-15
> **penn919 said:**
> Well here's the results of the boot info script:

```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sda2    *     10,233,405   312,576,094   302,342,690   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 3,292,626,943 3,292,624,896   7 NTFS / exFAT / HPFS
/dev/sdb2       3,292,626,944 3,907,024,895   614,397,952   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   224,827,391   224,825,344  83 Linux
/dev/sdc2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sdc5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 999 MB, 999817216 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1952768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63     1,952,767     1,952,705   6 FAT16


Drive: sde _____________________________________________________________________

Disk /dev/sde: 31.2 GB, 31247564800 bytes
122 heads, 34 sectors/track, 14713 cylinders, total 61030400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               8,192    61,030,399    61,022,208   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0E4E-05CE                              vfat       PQSERVICE
/dev/sda2        B214DB7F14DB44CF                       ntfs       
/dev/sdb1        74287014286FD420                       ntfs       Samsung
/dev/sdb2        4EDED02CDED00E59                       ntfs       Backup
/dev/sdc1        37354ddb-6634-4a11-8ee1-ec84098224ff   ext4       
/dev/sdc5        b1943cae-a8e8-4cbb-af5f-37d8de1137b3   swap       
/dev/sdd1        1C52-9119                              vfat       KINGSTON
/dev/sde1        D493-AF44                              vfat       32GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/B214DB7F14DB44CF  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd5,1)'
search --no-floppy --fs-uuid --set 407410CD7410C814
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd5,1)'
search --no-floppy --fs-uuid --set 407410CD7410C814
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-41-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-41-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-41-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-41-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-41-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-41-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-34-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-34-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-34-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-34-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-34-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-34-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-33-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-33-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-33-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-33-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-33-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-33-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-32-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-32-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-32-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-32-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-32-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-32-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-30-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-30-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-29-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-29-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-29-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-29-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-29-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-29-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-28-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-28-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-27-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-27-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-26-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-26-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-25-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-25-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-24-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-24-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-23-generic-pae" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-23-generic-pae (recovery mode)" {
    insmod ntfs
    set root='(hd5,1)'
    search --no-floppy --fs-uuid --set 407410CD7410C814
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=407410CD7410C814 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-23-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0e4e-05ce
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set B214DB7F14DB44CF
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  68.142070770 = 73.166991360   boot/grub/core.img                             1
  68.141586304 = 73.166471168   boot/grub/grub.cfg                             1
  68.149490356 = 73.174958080   boot/initrd.img-2.6.32-21-generic              1
  68.157161713 = 73.183195136   boot/initrd.img-2.6.32-23-generic-pae          1
  68.164783478 = 73.191378944   boot/initrd.img-2.6.32-24-generic-pae          1
  68.321147919 = 73.359273984   boot/initrd.img-2.6.32-25-generic-pae          1
  68.273986816 = 73.308635136   boot/initrd.img-2.6.32-26-generic-pae          1
  68.172454834 = 73.199616000   boot/initrd.img-2.6.32-27-generic-pae          1
  68.266315460 = 73.300398080   boot/initrd.img-2.6.32-28-generic-pae          1
  68.258644104 = 73.292161024   boot/initrd.img-2.6.32-29-generic-pae          1
  68.336578369 = 73.375842304   boot/initrd.img-2.6.32-30-generic-pae          1
  68.196147919 = 73.225056256   boot/initrd.img-2.6.32-32-generic-pae          1
  68.180152893 = 73.207881728   boot/initrd.img-2.6.32-33-generic-pae          1
  68.281684875 = 73.316900864   boot/initrd.img-2.6.32-34-generic-pae          1
  68.215526581 = 73.245863936   boot/initrd.img-2.6.32-41-generic-pae          1
   0.137542725 = 0.147685376    boot/vmlinuz-2.6.32-21-generic                 1
  68.328910828 = 73.367609344   boot/vmlinuz-2.6.32-23-generic-pae             1
  68.224475861 = 73.255473152   boot/vmlinuz-2.6.32-24-generic-pae             1
  68.325031281 = 73.363443712   boot/vmlinuz-2.6.32-25-generic-pae             1
  68.340461731 = 73.380012032   boot/vmlinuz-2.6.32-26-generic-pae             1
  68.137676239 = 73.162272768   boot/vmlinuz-2.6.32-27-generic-pae             1
  68.241584778 = 73.273843712   boot/vmlinuz-2.6.32-28-generic-pae             1
  68.344348907 = 73.384185856   boot/vmlinuz-2.6.32-29-generic-pae             1
  68.207824707 = 73.237594112   boot/vmlinuz-2.6.32-30-generic-pae             1
  68.186374664 = 73.214562304   boot/vmlinuz-2.6.32-32-generic-pae             1
  68.200035095 = 73.229230080   boot/vmlinuz-2.6.32-33-generic-pae             1
  68.228363037 = 73.259646976   boot/vmlinuz-2.6.32-34-generic-pae             1
  68.203933716 = 73.233416192   boot/vmlinuz-2.6.32-41-generic-pae             1
  68.215526581 = 73.245863936   initrd.img                                     1
  68.281684875 = 73.316900864   initrd.img.old                                 1
  68.203933716 = 73.233416192   vmlinuz                                        1
  68.228363037 = 73.259646976   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  2e ac 59 e8 b9 fc 50 90  1e b9 c0 f7 c3 00 26 79  |..Y...P.......&y|
00000010  1d 49 e9 7d 2a f5 05 20  a1 b6 ff 84 6b 17 c9 e4  |.I.}*.. ....k...|
00000020  cf 39 c3 eb 84 4f d3 ca  c5 59 0d d4 25 fa c6 f7  |.9...O...Y..%...|
00000030  ef 0e 4a a2 aa 4a 2f eb  34 88 9e d5 3e dc 11 6d  |..J..J/.4...>..m|
00000040  a9 27 84 27 76 5d 8a 6a  f3 a0 ce 09 80 f4 a6 71  |.'.'v].j.......q|
00000050  bb 05 10 e6 49 67 59 6d  7e 8b 9a 6f e3 ac bc 56  |....IgYm~..o...V|
00000060  79 34 c4 88 5b 6f 03 6a  a5 12 57 75 ba 23 73 13  |y4..[o.j..Wu.#s.|
00000070  14 8c e1 9a ba 63 1a 6e  13 f0 ba cf ac 0d 0e 33  |.....c.n.......3|
00000080  67 f7 f2 0a d0 e4 ce e4  a9 bf a3 43 0a db 03 39  |g..........C...9|
00000090  08 53 b7 31 d4 c5 ea 2b  18 29 0d 2f dc a0 47 30  |.S.1...+.)./..G0|
000000a0  15 01 f1 7d 7a 6f 4c 16  33 24 77 56 a1 93 63 f4  |...}zoL.3$wV..c.|
000000b0  7b 4f 9c a2 b0 26 a9 41  97 85 f0 85 10 75 03 6d  |{O...&.A.....u.m|
000000c0  63 2c dc bb 82 61 7b fc  85 9a d9 f4 7f db a0 23  |c,...a{........#|
000000d0  4f 2c 70 6c 22 78 4e a5  35 98 ba 05 dd 9b 88 52  |O,pl"xN.5......R|
000000e0  3f ab 81 95 12 83 1e 30  ab 6f 5b f0 ad 90 3e 23  |?......0.o[...>#|
000000f0  d8 6b 67 5f fa 98 76 21  3d 03 7b 6c 9d 1c 03 8c  |.kg_..v!=.{l....|
00000100  1f 1e 18 26 31 cf e0 4b  a4 a3 2f cb 29 c8 f1 78  |...&1..K../.)..x|
00000110  0d 0d ac 1d ab 81 7b 25  cb 46 db 50 32 0c 30 eb  |......{%.F.P2.0.|
00000120  c9 2e e2 73 a1 dc c3 05  a5 a1 c8 6b a7 cd 33 0f  |...s.......k..3.|
00000130  2b 03 b9 a4 c3 35 65 68  79 f9 4f 07 da f7 68 33  |+....5ehy.O...h3|
00000140  6d 95 4c 93 83 c3 1d a5  19 71 05 c1 e1 09 44 b7  |m.L......q....D.|
00000150  32 65 16 44 69 a1 fb 56  b6 af d8 ce ab b9 db bd  |2e.Di..V........|
00000160  9a ef cd 8c b3 69 ef f9  96 9a 50 77 ac 6b 49 8e  |.....i....Pw.kI.|
00000170  81 8d 91 e1 7d 4a 63 f4  e4 61 ea 98 44 6b e3 c0  |....}Jc..a..Dk..|
00000180  5d 7b fb 07 af c4 37 5b  e2 5d f1 82 c9 36 c7 b2  |]{....7[.]...6..|
00000190  62 a0 de dc 16 e3 67 49  79 11 b6 a3 84 09 3d 22  |b.....gIy.....="|
000001a0  06 be 33 32 c3 36 54 b6  0b 73 cc 10 c0 f8 51 e3  |..32.6T..s....Q.|
000001b0  c4 0f 51 92 40 1d ff 91  16 1a dc 75 3e 0d 00 fe  |..Q.@......u>...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdf sdg sdh sdi sdj 
```@roelforg

I tired running update-grub, but I got this:
```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```@darkod
At the grub menu, the version number says 1.98. Does that count as Grub2?

Yeah, that's my bad.

1.98 does count as grub2

And could you tell us which harddrives are supposed to be what? I'm counting at least 5 that the script recorgnises.

---

### Post by penn919 on 2012-05-15
> **roelforg said:**
> Yeah, that's my bad.

1.98 does count as grub2

And could you tell us which harddrives are supposed to be what? I'm counting at least 5 that the script recorgnises.

Sure, 
sda1 is a utility partition

sda2 is where Windows 7 is installed

sdb1,2 are on my 2TB samesung drive with a 300GB backup partition *No operating system*

sdc1 is where I installed Ubuntu. The other two partitions were made by the installer.

sdd and sde were flash drives that I forgot to unplug.

Do you still advise that I reinstall grub2?

---

### Post by roelforg on 2012-05-15
> **penn919 said:**
> Sure, 
sda1 is a utility partition

sda2 is where Windows 7 is installed

sdb1,2 are on my 2TB samesung drive with a 300GB backup partition *No operating system*

sdc1 is where I installed Ubuntu. The other two partitions were made by the installer.

sdd and sde were flash drives that I forgot to unplug.

Do you still advise that I reinstall grub2?

Yes, but i couldn't figure out what was supposed to be what and it's a prereq to know which hd you're using and it's useful for us to know incase problems arise while doing the reinstall.

---

### Post by penn919 on 2012-05-15
> **roelforg said:**
> Yes, but i couldn't figure out what was supposed to be what and it's a prereq to know which hd you're using and it's useful for us to know incase problems arise while doing the reinstall.

Sorry, I'm just a bit confused. I thought you just wanted me to identify all the hard drives. Right now I'm using a live CD, but I installed Ubuntu on sdc1. My external (which is where I used to boot Ubuntu from) isn't plugged in at the moment.

---

### Post by roelforg on 2012-05-15
> **penn919 said:**
> Sorry, I'm just a bit confused. I thought you just wanted me to identify all the hard drives. Right now I'm using a live CD, but I installed Ubuntu on sdc1. My external (which is where I used to boot Ubuntu from) isn't plugged in at the moment.

Doesn't matter, but if you're going to post error messages if something failes...
Those usually mention the hd as /dev/sd<char>
And it's easier if we know what /dev/sd<char> is supposed to be.

---

### Post by penn919 on 2012-05-15
> **roelforg said:**
> Doesn't matter, but if you're going to post error messages if something failes...
Those usually mention the hd as /dev/sd<char>
And it's easier if we know what /dev/sd<char> is supposed to be.

Ok, so does it help you any if I tell you that my Ubuntu is installed on /dev/sdc1 which is what I thought I mentioned earlier? 

Let me try this again:

/dev/sda1 ---->PQSERVICE partition (Utility)
/dev/sda2----->Windows 7 (Which I can still boot via grub)
/dev/sdb1----->1.7TB free space on Samsung drive
/dev/sdb2----->300GB Backup partition on Samsung Drive
/dev/sdc1----->Ubuntu that I just installed on 120GB hdd
/dev/sdc2----->Extended Partition that the installer created(?)
/dev/sdc5----->Ubuntu Swap Partition
/dev/sdd1----->1GB Kingston flash drive
/dev/sde1----->32GB Flash drive

Is that better?

---

### Post by darkod on 2012-05-15
OK, stop for a moment. There is something important.

Did you had a wubi install earlier that you tried to move to its own partition?

Or maybe the wubi install was on the 80GB disk and you simply copied everything to the 120GB disk?

The /etc/fstab refers to wubi disks. Also, the grub.cfg refers to wubi disks.

I don't work much with wubi, but I don't think you can simply copy a wubi install. But there is a procedure to move it to its own partition.

That's why the grub error reports UUID of ntfs type as missing, because wubi is installed on ntfs.

Answer the first two questions, then we will proceed. It's very important to explain in details how did you install the first time (wubi inside windows or ubuntu on separate partition) and how you moved it (you said simple copy-paste so I guess that is clear).

---

### Post by penn919 on 2012-05-15
> **darkod said:**
> OK, stop for a moment. There is something important.

Did you had a wubi install earlier that you tried to move to its own partition?

Or maybe the wubi install was on the 80GB disk and you simply copied everything to the 120GB disk?

The /etc/fstab refers to wubi disks. Also, the grub.cfg refers to wubi disks.

I don't work much with wubi, but I don't think you can simply copy a wubi install. But there is a procedure to move it to its own partition.

That's why the grub error reports UUID of ntfs type as missing, because wubi is installed on ntfs.

Answer the first two questions, then we will proceed. It's very important to explain in details how did you install the first time (wubi inside windows or ubuntu on separate partition) and how you moved it (you said simple copy-paste so I guess that is clear).

Well I installed Ubuntu on the 80GB external drive Via wubi install on my primary Hdd which is where my Windows 7 installation is. However, I don't recall ever trying to move anything to a new partition. However, once I remember accidently deleting the wubi files from the root directory of my main hdd while I was booted in Windows 7. I had to copy over some wubi files from my 80GB external, but I'm not sure that's relevant to this particular issue. 

The only things that I brought over to the 120GB drive was from the backup.tgz and I don't think any wubi files would've been included.

---

### Post by darkod on 2012-05-15
You think wrong. At least I think so.

Once you are in wubi, it might look like a "normal" ubuntu but it's not. So, simply moving over all files on a separate ext4 partition will not make it stand alone ubuntu.

As you can see in the script results, all the references are pointing to wubi setup, which sdc1 is not. Look at the /etc/fstab content. And the /boot/grub/grub.cfg content.

I wouldn't know whether you only need to make changes in these two files, or somewhere else too. But you can try, if you want to.

Feeling up to it?

---

### Post by penn919 on 2012-05-15
> **darkod said:**
> You think wrong. At least I think so.

Once you are in wubi, it might look like a "normal" ubuntu but it's not. So, simply moving over all files on a separate ext4 partition will not make it stand alone ubuntu.

As you can see in the script results, all the references are pointing to wubi setup, which sdc1 is not. Look at the /etc/fstab content. And the /boot/grub/grub.cfg content.

I wouldn't know whether you only need to make changes in these two files, or somewhere else too. But you can try, if you want to.

Feeling up to it?

Sure, why not?

---

### Post by darkod on 2012-05-15
OK. Boot into live mode, and lets try to enter with chroot in your new install:
```
sudo mount /dev/sdc1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the installation. Edit the /etc/fstab with:
```
gedit /etc/fstab
```

In the line specifying the root, change the wubi root.disk device with /dev/sdc1, and delete the loop in the options, so the line should look something like:
/dev/sdc1   /   ext4   errors=remount-ro   0   1

In the swap line change the device with /dev/sdc5 and also delete the loop in options. Save and close the file.

Then lets try to update grub and install it on the MBR of /dev/sdc:
```
update-grub
grub-install /dev/sdc
```

If you are lucky, you will see that it found the linux kernels. Exit the chroot and unmount:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart, go into BIOS and make the 120GB disk first hdd to boot from. The new grub2 will be on it.

See if you get a working grub2 menu and whether it can boot ubuntu.

---

### Post by penn919 on 2012-05-15
> **darkod said:**
> OK. Boot into live mode, and lets try to enter with chroot in your new install:
```
sudo mount /dev/sdc1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the installation. Edit the /etc/fstab with:
```
gedit /etc/fstab
```

In the line specifying the root, change the wubi root.disk device with /dev/sdc1, and delete the loop in the options, so the line should look something like:
/dev/sdc1   /   ext4   errors=remount-ro   0   1

In the swap line change the device with /dev/sdc5 and also delete the loop in options. Save and close the file.

Then lets try to update grub and install it on the MBR of /dev/sdc:
```
update-grub
grub-install /dev/sdc
```

If you are lucky, you will see that it found the linux kernels. Exit the chroot and unmount:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart, go into BIOS and make the 120GB disk first hdd to boot from. The new grub2 will be on it.

See if you get a working grub2 menu and whether it can boot ubuntu.


I've got a problem. After I enter gedit /etc/fstab I get the following results:

```
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# gedit /etc/fstab
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-Hif1ePC5ZN: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-XEtOOJvApL: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-mA0G4DmlII: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-QCLkbSsdyL: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-dORhfKcw6D: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-4MFuAEkv9I: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-IR6gWw7EUA: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-LBJLds0plY: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-j66xBQIxsj: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-PYGStkFlpG: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-5zZPt91dLi: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-l2CHXIclDW: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-DU542TbpPd: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-0AzkvSpHe4: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-tF4duz6hTR: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-FeTeLp0TXU: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-XbPPtBc8Ll: Connection refused)
stop
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-jEv2e7rG0r: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-nf9yb0XlQ0: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-COUGWwdlX1: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-w9MHfIC4Ir: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-Me3QPFVyAJ: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-7tBdrVKb9w: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-yuSoX4ILo7: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-VZyB6U3l80: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-6JhaijWj0B: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-Bs5rgoIdmh: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-q0p5O5fbrl: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-pKHCF4SqaZ: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-L7Cbmlql4E: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-U34BE6EZIz: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-5u3JlnWN4C: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-ejRqgH9Fzs: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-gwxvcP75sl: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-t9mTFV7Vzv: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-hbL1rU3ufX: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-n9Jj9E0lKF: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-dHWVLlWs1s: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-aDKTz0sr2J: Connection refused)
```

---

### Post by darkod on 2012-05-15
OK, instead of that line try:
nano /etc/fstab

That should open the text editor in terminal. You move the cursor with the arrows keys, edit what you need to edit, save the file with Ctrl + O (hit Enter to accept the same filename), you exit with Ctrl + X.

---

### Post by penn919 on 2012-05-15
All right, never-mind. I just noticed that a fstab file had opened. I'll get around to editing it later, right now I've got to go. I'll be back with the results probably tonight or tomorrow morning.

---

### Post by penn919 on 2012-05-15
Alright. I'm back. I edited the file as you said, and I ran update-grub and grub-install /dev/sdc. It looks like we've got kernels!

```
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-41-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-41-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-34-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-34-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-33-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-33-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-32-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-32-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-30-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-30-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-29-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-29-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-28-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-27-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-27-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-26-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-26-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-25-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-23-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP on /dev/sda1
done
root@ubuntu:/# grub-install /dev/sdc
Installation finished. No error reported.
```

As you can see above, it seems as though grub successfully installed on sdc too. I'll try booting from the 120gb drive right now. I'll be back in a moment...

---

### Post by penn919 on 2012-05-15
I'm in! looks like it worked, but the only problem is that I'm not getting the option to boot into windows 7 via the grub2 menu. Is there a way I can update grub2 to include windows 7 or will I have to keep changing the boot priority of the two drives?

Lastly, how would I go about properly uninstalling wubi from windows? Every time I boot into windows the boot manager  menu prompts me to select between Windows 7 and Ubuntu and I want to remove the Ubuntu option and have it boot immediately into Windows 7 every time I choose Windows 7 from grub2 (assuming I'll be able to get it to re-appear there).

Thanks a ton for the help!

---

### Post by darkod on 2012-05-16
Yeah, you have many kernels. Older ones can be removed, but that's not an issue, so you can do it later.

I am slightly surprised it didn't detect the win7 with the update-grub, maybe it has something to do with wubi.

If you boot from sdb, you should get your windows bootloader (which at this moment will have both win7 and wubi). So you should be able to load win7 that way.

Then go in to Control Panel, Programs, and simply select to uninstall wubi (ubuntu) like any other program. Now, the destination folder for wubi doesn't exist any more, you removed that disk, so there might be some errors while uninstalling, but hopefully it will figure it out and remove the wubi entry from the windows bootloader.

After that boot from sdc again into ubuntu, and run the update-grub to see if win7 gets detected. If it still doesn't work, we'll look around whether all wubi files were removed or not.

---

### Post by penn919 on 2012-05-16
> **darkod said:**
> Yeah, you have many kernels. Older ones can be removed, but that's not an issue, so you can do it later.

I am slightly surprised it didn't detect the win7 with the update-grub, maybe it has something to do with wubi.

If you boot from sdb, you should get your windows bootloader (which at this moment will have both win7 and wubi). So you should be able to load win7 that way.

Then go in to Control Panel, Programs, and simply select to uninstall wubi (ubuntu) like any other program. Now, the destination folder for wubi doesn't exist any more, you removed that disk, so there might be some errors while uninstalling, but hopefully it will figure it out and remove the wubi entry from the windows bootloader.

After that boot from sdc again into ubuntu, and run the update-grub to see if win7 gets detected. If it still doesn't work, we'll look around whether all wubi files were removed or not.

I purged all the excess kernels via the terminal and I managed to get Windows 7 to appear by simply running update-grub again. 

I had to uninstall Wubi via the EasyBCD program because for some reason wubi wasn't listed in the add/remove programs list in the control panel. 

One thing I forgot to mention was when Ubuntu is starting up I'm encountering the following message on the splash screen:

"Press S to skip mounting or M for manual recovery" and at first I waited well over 15min before I decided to press S to skip I managed to boot just fine with all hard rives mounted. I googled the the issue and many forum posts were saying that I needed to use  UUID in the fstab file so I did. My fstab now looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  	<options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid         0       0
UUID=37354ddb-6634-4a11-8ee1-ec84098224ff /         ext4    errors=remount-ro 0       1
UUID=b1943cae-a8e8-4cbb-af5f-37d8de1137b3           swap    sw      0       0
```

But I'm getting the same message at start-up. Any suggestions?

---

### Post by darkod on 2012-05-16
Yes, it's better to use UUIDs but I wanted to see if it works one step at a time, so I suggested to start off with sda1 and sda5.

You are missing one entry in the swap line in /etc/fstab. You have:
<UUID>   swap    sw......

It should be:
<UUID>   none   swap   sw.....

You are missing 'none' in between. I guess that should sort out that error. It's only the swap partition that's why it still works after you press S to skip mounting it.

---

### Post by penn919 on 2012-05-16
> **darkod said:**
> Yes, it's better to use UUIDs but I wanted to see if it works one step at a time, so I suggested to start off with sda1 and sda5.

You are missing one entry in the swap line in /etc/fstab. You have:
<UUID>   swap    sw......

It should be:
<UUID>   none   swap   sw.....

You are missing 'none' in between. I guess that should sort out that error. It's only the swap partition that's why it still works after you press S to skip mounting it.

Yep. that worked. I just added the 'none' and now it boots instantly to the log-in screen. Thanks a ton man! I'll go ahead and mark this thread as officially solved.

---

