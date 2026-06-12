---
title: "Initial Ubuntu Boot - GRUB rescue"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Sebastianj on 2010-02-11
Hello,
I am fresh to Ubuntu and am having trouble getting it to boot on my system. I normally run XP, but recently added a second internal hard drive and installed Ubuntu on it.  The installation went fine and upon initial reboot I received - 

GRUB loading.
error: no such disk
grub rescue>

I am wondering if there is an issue between two different operating systems upon boot. I am not familiar with GRUB commands. Any help is appreciated. 

Thanks
Sebastian

---

### Post by meierfra. on 2010-02-11
> error: no such disk

That can be caused by various things, so lets gather some information:


At the "grub>rescue" prompt type

```
ls

set
```

and post the output.

Also follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt

How old is your computer?

---

### Post by Sebastianj on 2010-02-11
ls:
(hd0) (hd0,3) (hd0,2) (hd0,1) (fd0)
error: cannot get C/H/S values

set:
prefix=(UUID=6f2571c0-194c-4d3b-b0d4-ac4db960cda1)/boot/grub
root=(UUID=6f2571c0-194c-4d3b-b0d4-ac4db960cda1


============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   149,468,759   149,388,435   7 HPFS/NTFS
/dev/sda3         149,468,760   156,232,124     6,763,365  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8c0c203

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D5-0802                              vfat       DellUtility                   
/dev/sda2        CC08758E087577F2                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sdb1        6f2571c0-194c-4d3b-b0d4-ac4bd960cda1   ext4                                     
/dev/sdb5        84919f12-61dc-467c-8dab-395908db8893   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda2        /media/CC08758E087577F2  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ext4       (rw,nosuid,nodev,uhelper=devkit)


================================ sda2/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set cc08758e087577f2
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=84919f12-61dc-467c-8dab-395908db8893 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz



Computer is about 5 years old

---

### Post by meierfra. on 2010-02-11
> ls:  (hd0) (hd0,3) (hd0,2) (hd0,1) (fd0)
error: cannot get C/H/S values

Grub is not able to detect your Ubuntu drive. Usually that is caused by the Bios.  Maybe the drive is somehow disabled in the Bios. Or not plugged in correctly? Is your Ubuntu drive  a USB drive?  

Are you able to set you bios to boot from the Ubuntu drive?  If  yes, I suggest to restore the Windows MBR in /dev/sda and install grub to the MBR of /dev/sdb:

Boot from the LiveCD. Install lilo via

```
sudo apt-get install lilo
```
(ignore any warning you might get. Just press enter to continue)

Install a Windows type MBR in /dev/sda via

```
sudo lilo -M /dev/sda mbr
```

Install Grub to the MBR of /dev/sdb via

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
```

Reboot. If you set your bios to boot from the  Windows drive, you should boot directly into Windows XP. If you set your bios to boot from the Ubuntu drive, you should get the Grub menu with Ubuntu and XP.

---

### Post by Sebastianj on 2010-02-13
Yea you were correct, the disk was not recognized in BIOS.  However everything works great now. Thanks for your help.

Sebastian

---

