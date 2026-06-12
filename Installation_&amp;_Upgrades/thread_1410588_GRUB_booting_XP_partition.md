---
title: "GRUB booting XP partition"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by gamecraziness on 2010-02-18
Well, I installed Ubuntu on a partition on my hard drive (I had to make it with GParted). Anyways, everything works with the Ubuntu. However, when I try to boot the XP from GRUB, it just displays a blinking underscore in the top left corner.

BTW I mounted the partition in Ubuntu to check the contents, and they are all there. The partition is in NTFS.

Thanks in advance.

---

### Post by johnson.d on 2010-02-19
If you are using Ubuntu 9.10, you can probably verify the following lines in the /boot/grub/grub.cfg
The line 2 is important for windows to load as ntfs module is needed for grub to boot windows loaded on to an NTFS partition. The problem you are facing may be due to the absence of the line "insmod ntfs". You can add this line to the grub.cfg file similar to the following lines and try to boot windows again.

```
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set XXXXXXXXXXXX
drivemap -s (hd0) ${root}
chainloader +1
}
```

Please edit the partition names, uuid etc. to suit your case.

---

### Post by gamecraziness on 2010-02-19
> **johnson.d said:**
> If you are using Ubuntu 9.10, you can probably verify the following lines in the /boot/grub/grub.cfg
The line 2 is important for windows to load as ntfs module is needed for grub to boot windows loaded on to an NTFS partition. The problem you are facing may be due to the absence of the line "insmod ntfs". You can add this line to the grub.cfg file similar to the following lines and try to boot windows again.

```
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set XXXXXXXXXXXX
drivemap -s (hd0) ${root}
chainloader +1
}
```Please edit the partition names, uuid etc. to suit your case.
I actually do have that line, as well as all the other ones.

Also, is editing through GRUB the same as editing grub.cfg?

---

### Post by stlsaint on 2010-02-19
It is best to edit the corresponding files used to update grub and not edit grub directly in 9.10 using grub2. See [GRUB2]("https://help.ubuntu.com/community/Grub2") for details.

---

### Post by gamecraziness on 2010-02-19
OK thanks.

However, the problem is still there.

---

### Post by kansasnoob on 2010-02-19
It would be best to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Just off the top of my head I'm thinking of either trying the newest grub2 packages from Lucid or reverting to legacy grub.

Then again I may see something in your RESULTS.txt from the Boot Info Script that will change my mind :)

---

### Post by gamecraziness on 2010-02-19
> **kansasnoob said:**
> It would be best to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Just off the top of my head I'm thinking of either trying the newest grub2 packages from Lucid or reverting to legacy grub.

Then again I may see something in your RESULTS.txt from the Boot Info Script that will change my mind :)
Thanks. I'll try it out and post the results. :D

---

### Post by gamecraziness on 2010-03-08
Here are the results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f6e4f6d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    92,839,634    92,839,572   7 HPFS/NTFS
/dev/sda2         155,252,160   156,296,384     1,044,225  82 Linux swap / Solaris
/dev/sda3          92,839,635   155,252,159    62,412,525  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f51416f

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1CCC6C3ECC6C1474                       ntfs                                     
/dev/sda2        eefd7005-cb83-4b1e-8658-307387455e0d   swap                                     
/dev/sda3        d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f   ext3       /                             
/dev/sdf1        1A30E32D30E30F17                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro)
/dev/sdf1        /media/1A30E32D30E30F17  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root=(hd0,3)
search --no-floppy --fs-uuid --set d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f ro single 
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
    search --no-floppy --fs-uuid --set 1ccc6c3ecc6c1474
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=d427393d-d0bb-4c60-bbbc-69cb2ad4eb6f /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=eefd7005-cb83-4b1e-8658-307387455e0d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  51.5GB: boot/grub/core.img
  51.5GB: boot/grub/grub.cfg
  51.5GB: boot/initrd.img-2.6.31-14-generic
  51.5GB: boot/initrd.img-2.6.31-16-generic
  51.4GB: boot/vmlinuz-2.6.31-14-generic
  51.5GB: boot/vmlinuz-2.6.31-16-generic
  51.5GB: initrd.img
  51.5GB: initrd.img.old
  51.5GB: vmlinuz
  51.4GB: vmlinuz.old

================================ sdf1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

Thanks in advance!

---

### Post by oldfred on 2010-03-08
It looks like the windows you mounted is sdf1 and the windows you are booting is sda1. But I do not see anything that would prevent windows from booting. Was it ok before installing Ubuntu?

---

### Post by gamecraziness on 2010-03-08
Yes, it worked perfectly before.

---

### Post by gamecraziness on 2010-03-13
bump

---

### Post by oldfred on 2010-03-14
I would first try removing the search line from the windows boot stanza. 

If that does not work you need to run the XP repairs to see if that will fix XP even though it looks ok. If you run the fixboot command it will use the windows boot loader. You will then have to reinstall grub2.

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You could just reinstall the XP boot loader to test that it still boots before running all the windows repairs then reinstall grub to isolate the problem.

---

