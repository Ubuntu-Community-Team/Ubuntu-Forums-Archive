---
title: "get grub choice when i start the pc"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by roynoblin on 2010-04-19
i had to reinstall XP on this pc and now when i start it up i do not the grub choice screen.

it appears everything i need to use ubuntu is still on the HDD but how can i access it?
i was going to just reinstall but it will creat another partition and i do not want that.

i was able to use the cd and get info scrip results. can anyone see what i can change so i will be able to chose between xp and ubuntu?

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa243532b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   525,454,019   525,453,957   7 HPFS/NTFS
/dev/sda2         525,454,020 1,953,520,064 1,428,066,045   f W95 Ext d (LBA)
/dev/sda5         525,454,083 1,425,495,644   900,041,562   7 HPFS/NTFS
/dev/sda6       1,425,495,708 1,942,965,359   517,469,652  83 Linux
/dev/sda7       1,942,965,423 1,953,520,064    10,554,642  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000098ec

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AEC4A45CC4A42893                       ntfs                                     
/dev/sda5        4A3CEB323CEB17A9                       ntfs       partition 2                   
/dev/sda6        7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0   ext4                                     
/dev/sda7        2c02be14-f031-4e93-aae8-3fef03895a79   swap                                     
/dev/sdb1        E6C82634C8260381                       ntfs       external drive                

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/external drive    fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6        /media/7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda5        /media/partition 2       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/AEC4A45CC4A42893  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0
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
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set aec4a45cc4a42893
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=7bda59d8-9b94-4d1f-ba8b-6caf7a4b65f0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2c02be14-f031-4e93-aae8-3fef03895a79 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 747.2GB: boot/grub/core.img
 731.4GB: boot/grub/grub.cfg
 730.1GB: boot/initrd.img-2.6.31-14-generic
 730.6GB: boot/initrd.img-2.6.31-21-generic
 730.4GB: boot/vmlinuz-2.6.31-14-generic
 730.3GB: boot/vmlinuz-2.6.31-21-generic
 730.6GB: initrd.img
 730.1GB: initrd.img.old
 730.3GB: vmlinuz
 730.4GB: vmlinuz.old

---

### Post by drs305 on 2010-04-19
Use the instructions in this thread:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

The title pretty much says what it does.

---

### Post by roynoblin on 2010-04-19
drs305
thank you.thank you.thank you
:popcorn:

:guitar:

that link was great and did the trick. i have everything running again and lost no data
:):)
i have a extra xp that don't boot but the partition is 250G so it can stay as is

:):)

---

