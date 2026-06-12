---
title: "Dual Boot Failure"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by just4u on 2010-03-08
Hello I'm quite new to linux so bear with me.  If I don't list all the info u need please understand I don't know the right questions to ask yet ;)

I have 2 harddrives - 1 IDE and 1 SATA,  I installed ubuntu on the SATA drive and kept my XP on the first drive.  The installation went fine or so I thought until reboot, all I got on my screen was 6 rows of (99) and had to reboot.  I used F8 for my booting menu and chose the SATA drive to boot from just to see if linux would load and it did, but I can't boot into my windows drive.

After reading and looking thru files unbuntu (fstab, grub.cfg) I noticed that grub didn't even find my windows installation.  It just shows the ubuntu install and a memory test.

I then installed the startup-manger hoping it would correct the problem but no, I then edited fstab and entered what I hoped was the correct info for my 1st harddrive then ran update-grub but that didn't work either.

I'm at a loss on what to do now any help would be appreicated.

I'm running ubuntu 9.10/grub2, don't really know what other info to include sry

   

             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/mapper/nvidia_dgccaddb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

nvidia_dgccaddb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

nvidia_dgccaddb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

nvidia_dgccaddb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, 
                       nvidia_dgccaddb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007703d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   577,054,799   577,054,737  83 Linux
/dev/sda2         577,054,800   586,099,394     9,044,595   5 Extended
/dev/sda5         577,054,863   586,099,394     9,044,532  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   307,194,929   307,194,867   7 HPFS/NTFS
/dev/sdb2         307,194,930   586,051,199   278,856,270   f W95 Ext d (LBA)
/dev/sdb5         307,194,993   586,051,199   278,856,207   7 HPFS/NTFS


Drive: nvidia_dgccaddb ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_dgccaddb: 300.1 GB, 300069027840 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072320 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_dgccaddb1   *             63   307,194,929   307,194,867   7 HPFS/NTFS
/dev/mapper/nvidia_dgccaddb2        307,194,930   586,051,199   278,856,270   f W95 Ext d (LBA)
/dev/mapper/nvidia_dgccaddb5        307,194,993   586,051,199   278,856,207   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/nvidia_dgccaddb1 BAC481B0C4817005                       ntfs                                     
/dev/mapper/nvidia_dgccaddb5 D0F4EA1AF4EA0298                       ntfs                                     
/dev/sda1        6622fd44-54a1-4abf-be0a-74ca66db14ed   ext4                                     
/dev/sda5        e459bb45-ee48-4a50-be42-3376300e535b   swap                                     
/dev/sdb1        BAC481B0C4817005                       ntfs                                     
/dev/sdb5        D0F4EA1AF4EA0298                       ntfs                                     
/dev/sdb                                                nvidia_raid_member                               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 6622fd44-54a1-4abf-be0a-74ca66db14ed
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
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
  set timeout=100
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
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6622fd44-54a1-4abf-be0a-74ca66db14ed
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=6622fd44-54a1-4abf-be0a-74ca66db14ed ro  vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6622fd44-54a1-4abf-be0a-74ca66db14ed
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=6622fd44-54a1-4abf-be0a-74ca66db14ed ro single  vga=795
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6622fd44-54a1-4abf-be0a-74ca66db14ed
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6622fd44-54a1-4abf-be0a-74ca66db14ed ro  vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6622fd44-54a1-4abf-be0a-74ca66db14ed
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6622fd44-54a1-4abf-be0a-74ca66db14ed ro single  vga=795
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=6622fd44-54a1-4abf-be0a-74ca66db14ed / ext4 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=e459bb45-ee48-4a50-be42-3376300e535b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

=================== sda1: Location of files loaded by Grub: ===================


   7.7GB: boot/grub/core.img
  19.5GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.31-14-generic
   1.0GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-20-generic
   1.0GB: initrd.img
    .9GB: initrd.img.old
    .5GB: vmlinuz
    .5GB: vmlinuz.old

========================== nvidia_dgccaddb1/boot.ini: ==========================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on nvidia_dgccaddb2



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/nvidia_dgccaddb2: No such file or directory
hexdump: /dev/mapper/nvidia_dgccaddb2: No such file or directory

---

### Post by oldfred on 2010-03-08
the device/mapper/nvidia are raid related. Since you have only one drive I assume you are not meaninng to run raid. Was this drive part of a raid set before?

Grub2 finds raid settings hidden on a drive and has issues. Do not run this if your really have raid set up somehow as it will destroy your raid.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

