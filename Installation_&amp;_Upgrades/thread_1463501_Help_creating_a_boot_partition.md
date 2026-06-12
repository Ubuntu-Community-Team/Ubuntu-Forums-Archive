---
title: "Help creating a boot partition"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by Skari on 2010-04-27
I´ve decided to create a new thread because my old one had become rather complicated and now had a misleading title.

I have a laptop with Windows XP and because of a few programs I want to keep it on and dual boot with Ubuntu. I have created a boot partition at the beginning of the harddisk because I had broken the 137gb and can´t keep Ubuntu at the end and still make it bootable. 

The separate boot partition is at the beginning of the disk and mounted as /boot in the installation. 

The system still can´t boot into Ubuntu, but at least grub shows up with  a decent menu and I can choose Windows. When I try to choose Ubuntu it  says that it can´t find the specific drive. The UUID is the same as the boot partition

So what should I do now ? Should I change fstab and move some files to  the boot partition ? I´d rather not move the entire Ubuntu partition to the front.

Here is my boot info script
     Code:
                     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /grub.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01a0019f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *        208,845   272,847,959   272,639,115   7 HPFS/NTFS
/dev/sda2         272,847,960   312,576,704    39,728,745   5 Extended
/dev/sda5         272,848,023   310,825,619    37,977,597  83 Linux
/dev/sda6         310,825,683   312,576,704     1,751,022  82 Linux swap / Solaris
/dev/sda3                  63       208,844       208,782  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        7B5FB5D0515BCF91                       ntfs                                     
/dev/sda3        3da696e2-eb43-4e4d-b80e-f64c3869a774   ext2                                     
/dev/sda5        e2476a90-0f93-458c-b170-c7db2a3e9b37   ext4                                     
/dev/sda6        37ceb988-9ad9-485b-a400-41c7c91b3724   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda5        /media/e2476a90-0f93-458c-b170-c7db2a3e9b37 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda3        /media/3da696e2-eb43-4e4d-b80e-f64c3869a774 ext2       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda5        /mnt                     ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e2476a90-0f93-458c-b170-c7db2a3e9b37 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=3da696e2-eb43-4e4d-b80e-f64c3869a774 /boot           ext2    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=37ceb988-9ad9-485b-a400-41c7c91b3724 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

============================= sda3/grub/grub.cfg: =============================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set e2476a90-0f93-458c-b170-c7db2a3e9b37
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
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 3da696e2-eb43-4e4d-b80e-f64c3869a774
    linux    /vmlinuz-2.6.31-14-generic root=UUID=e2476a90-0f93-458c-b170-c7db2a3e9b37 ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 3da696e2-eb43-4e4d-b80e-f64c3869a774
    linux    /vmlinuz-2.6.31-14-generic root=UUID=e2476a90-0f93-458c-b170-c7db2a3e9b37 ro single 
    initrd    /initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7b5fb5d0515bcf91
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda3: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: vmlinuz-2.6.31-14-generic

---

### Post by oldfred on 2010-04-27
I would test removing the entire search line.

From the grub menu press e for edit and move down to the search line and delete the entire line, then try booting.

---

### Post by Skari on 2010-04-27
It worked ! Thank you :)

Now I only have to find out how to change the line in grub permanently.

---

### Post by Skari on 2010-04-27
All done. I just followed this thread :)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by oldfred on 2010-04-27
this has info:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

I just tend to create my own entries and put them into 40_custom and turn off some of the auto searching that grub does. But I think the above is a better way.

---

