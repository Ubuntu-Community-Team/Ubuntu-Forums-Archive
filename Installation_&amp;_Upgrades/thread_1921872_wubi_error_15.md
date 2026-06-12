---
title: "wubi error 15"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by BigFoot2012 on 2012-02-07
I  deleted a partition with no information on it and extended  the space  back to the C drive on Win 7. Afterward, I tried to boot ubuntu and received the following:

     [Minimal BASH-like line editing is supported. For
                                           the first word, TAB lists possible command 
                                           completions. Anywhere else TAB lists the possible
                                           completions of a device/filename.]                                          


I was able to boot by:root (hd0,0), chainloader +1, boot. Any advice on how to fix this?

Disk /dev/sda: 500.1 GB, 500107862016 bytes
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x5bcbe6e8
 
    Device Boot      Start         End      Blocks   Id  System
 /dev/sda1            2048     3074047     1536000   27  Unknown
 Partition 1 does not end on cylinder boundary.
 /dev/sda2   *     3074048   956002303   476464128    7  HPFS/NTFS
 /dev/sda3       956004352   976773119    10384384   17  Hidden HPFS/NTFS

---

### Post by oldfred on 2012-02-07
I do not know wubi enough to help. 

Does Windows boot ok? 

What did you use to resize Windows c: drive?
Windows normally wants to run chkdsk after a resize, did that run without any issues?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Your boot script for those who may be able to help:

  ```
                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => FreeDOS (eXtended FDisk) is installed in the MBR of /dev/sdb.

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
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,074,048   956,002,303   952,928,256   7 NTFS / exFAT / HPFS
/dev/sda3         956,004,352   976,773,119    20,768,768  17 Hidden NTFS / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
32 heads, 63 sectors/track, 3884 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63     7,830,143     7,830,081   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       679b9c4d-53cf-41d8-ab6b-49bbb06f46eb   ext4       
/dev/sda1        CC5AC88C5AC8752C                       ntfs       System
/dev/sda2        908ACCE98ACCCCC2                       ntfs       Toshiba 500GB
/dev/sda3        7E4CD3724CD32425                       ntfs       HDDRECOVERY
/dev/sdb1        5134-5666                              vfat       KINGSTON

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-32-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-32-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-32-generic
}
menuentry "Ubuntu, Linux 2.6.35-32-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-32-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-32-generic
}
menuentry "Ubuntu, Linux 2.6.35-30-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, Linux 2.6.35-30-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=908ACCE98ACCCCC2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set CC5AC88C5AC8752C
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 908ACCE98ACCCCC2
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 7E4CD3724CD32425
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

============================= sda2/Wubi/etc/fstab: =============================

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

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  14.726547241 = 15.812509696   boot/grub/grub.cfg                             1
   1.773437500 = 1.904214016    boot/initrd.img-2.6.35-22-generic              2
   2.679687500 = 2.877292544    boot/initrd.img-2.6.35-25-generic              2
  18.765625000 = 20.149436416   boot/initrd.img-2.6.35-27-generic              2
   3.522911072 = 3.782696960    boot/initrd.img-2.6.35-28-generic              2
   1.078125000 = 1.157627904    boot/initrd.img-2.6.35-30-generic              2
   1.085937500 = 1.166016512    boot/initrd.img-2.6.35-32-generic              2
  18.280040741 = 19.628044288   boot/vmlinuz-2.6.35-22-generic                 1
  18.303348541 = 19.653070848   boot/vmlinuz-2.6.35-25-generic                 1
  18.629047394 = 20.002787328   boot/vmlinuz-2.6.35-27-generic                 1
   3.242187500 = 3.481272320    boot/vmlinuz-2.6.35-28-generic                 2
  18.379051208 = 19.734355968   boot/vmlinuz-2.6.35-30-generic                 1
  18.472805023 = 19.835023360   boot/vmlinuz-2.6.35-32-generic                 1
   1.085937500 = 1.166016512    initrd.img                                     2
   1.078125000 = 1.157627904    initrd.img.old                                 2
  18.472805023 = 19.835023360   vmlinuz                                        1
  18.379051208 = 19.734355968   vmlinuz.old                                    1



```

---

### Post by BigFoot2012 on 2012-02-07
Windows 7 runs just fine. I used the disk management to create the partition and deleted it later that day. I even did a system restore to earlier in the day before I had created the partition and that did not work neither. I'll try this from wubi guide link you shared. Thanks a lot.

**How can I access my Wubi install and repair my install if it won't boot?**

 Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition: 

sudo mkdir /win
sudo mount /dev/sda1 /winReplace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein 

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdiskNow  the content of the virtual disk will be visible under /vdisk. 7.04  users will have to install ntfs-3g first and specify it as fstype to  gain r/w access.  
To check the filesystem you can use (make sure the root.disk is not mounted): 

sudo fsck /win/ubuntu/disks/root.disk

---

### Post by BigFoot2012 on 2012-02-07
It didn't work. I entered: sudo mount /dev/sda2 /win. And received: Mount is denied b/c the NTFS volume is already exclusively opened. The volume may be already mounted, or another software may use it which could be identified for example by the "fuser" command.

I just need someone who understands the boot script and could give me the correct commands to enter in the terminal. I tried "sda2" b/c that is where wubi is on my boot script and when I tried "sdb1" instead it says special device does not exist.

---

### Post by oldfred on 2012-02-07
It should be sda2.

Did you use liveCd to look at partition as then it is mounted and you have to unmount it.

To see what is mounted:
mount
To unmount (spelling is correct) by device:
umount /dev/sda2
or 
umount /media/sda2

---

### Post by BigFoot2012 on 2012-02-07
I didn't use a live cd or desktop cd because I can boot into Ubuntu when prompted with "Minimal BASH-like line editing is supported." Then enter... root (hd0,0), chainloader +1, boot. So I am currently trying to fix the issue using the terminal in Ubuntu. Thanks

---

### Post by BigFoot2012 on 2012-02-08
Here's how I solved it:

[www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

---

