---
title: "GRUB - No Windows"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by The Wookiee on 2010-04-10
I have two hard disks. An 80 GB and a 320GB. On the 80, I installed Windows 7. Recently, I installed Karmic on a new partition on my 320, and that was fine.

However, when I went into GRUB2, I noticed that Windows 7 was not on the list. Presumably, because it was on a different harddisk.

I can access the Windows partition on my harddisk (Titled by Ubuntu as "55 GB Filesystem") from Ubuntu. However, it would be quite lovely to be able to boot into Windows. Is there any way I can get it so GRUB finds it?

If anyone could help me with this, it would be much appreciated, thanks. :)

(Probably not much help but both OS's are 64-bit)

---

### Post by oldfred on 2010-04-10
It should have found it. Sometimes running this will find it.
sudo update-grub

If not there may be a problem with the windows.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by The Wookiee on 2010-04-10
Windows seems to be on there, alright.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=4b12a41b-22c4-4813-ba30-e71805331395)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/mapper/pdc_cdhbhffhd and looks for 
    (UUID=4b12a41b-22c4-4813-ba30-e71805331395)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_cdhbhffhd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

pdc_cdhbhffhd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000147a0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   108,546,047   108,339,200   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x72b7c10c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   604,156,454   604,156,392   7 HPFS/NTFS
/dev/sdb2         604,156,455   625,137,344    20,980,890   5 Extended
/dev/sdb5         604,156,518   624,141,314    19,984,797  83 Linux
/dev/sdb6         624,141,378   625,137,344       995,967  82 Linux swap / Solaris


Drive: pdc_cdhbhffhd ___________________ _____________________________________________________

Disk /dev/mapper/pdc_cdhbhffhd: 82.3 GB, 82348212224 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836352 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000147a0

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_cdhbhffhd1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/pdc_cdhbhffhd2            206,848   108,546,047   108,339,200   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/pdc_cdhbhffhd1 A8B48E65B48E363A                       ntfs       System Reserved               
/dev/mapper/pdc_cdhbhffhd2 1AC299D6C299B68B                       ntfs                                     
/dev/sda1        A8B48E65B48E363A                       ntfs       System Reserved               
/dev/sda2        1AC299D6C299B68B                       ntfs                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        56780F40780F1E7D                       ntfs       K9                            
/dev/sdb5        4b12a41b-22c4-4813-ba30-e71805331395   ext4                                     
/dev/sdb6        e7c096da-ac8a-4a55-9c0d-8382f4c81d32   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=josh)
/dev/sdb1        /media/K9                fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set 4b12a41b-22c4-4813-ba30-e71805331395
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 4b12a41b-22c4-4813-ba30-e71805331395
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=4b12a41b-22c4-4813-ba30-e71805331395 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 4b12a41b-22c4-4813-ba30-e71805331395
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=4b12a41b-22c4-4813-ba30-e71805331395 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 4b12a41b-22c4-4813-ba30-e71805331395
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4b12a41b-22c4-4813-ba30-e71805331395 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 4b12a41b-22c4-4813-ba30-e71805331395
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4b12a41b-22c4-4813-ba30-e71805331395 ro single 
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
if [ ${timeout} != -1 ]; then
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=4b12a41b-22c4-4813-ba30-e71805331395 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=e7c096da-ac8a-4a55-9c0d-8382f4c81d32 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 313.0GB: boot/grub/core.img
 313.0GB: boot/grub/grub.cfg
 312.0GB: boot/initrd.img-2.6.31-14-generic
 313.0GB: boot/initrd.img-2.6.31-20-generic
 311.7GB: boot/vmlinuz-2.6.31-14-generic
 312.5GB: boot/vmlinuz-2.6.31-20-generic
 313.0GB: initrd.img
 312.0GB: initrd.img.old
 312.5GB: vmlinuz
 311.7GB: vmlinuz.old
```

---

### Post by oldfred on 2010-04-10
You have two totally different hard drives yet it is showing you running raid?
/dev/mapper/pdc_cdhbhffhd

---

### Post by The Wookiee on 2010-04-10
Yeah, I really have no idea. I don't think I ever told it to do anything with RAID.

Any ideas?

---

### Post by The Wookiee on 2010-04-11
After a bit more hunting, I finally found a solution.
[http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

I managed to find an adjustment that worked for me, based off his idea and the comments of other people with a very similar situation.

```
#! /bin/sh -e
echo "Adding Windows" >&2
cat << EOF
menuentry "Windows 7" {
insmod ntfs
insmod chain
insmod drivemap
set root=(hd0,1)
drivemap -s (hd0) (hd1)
chainloader +1
}
EOF
```

Thank you for your help, Oldfred. :)

---

