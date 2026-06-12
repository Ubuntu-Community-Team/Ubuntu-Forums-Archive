---
title: "Grub2 ual boot problem with XP"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by drmathprog on 2011-04-02
I just installed a default install of Ubuntu 10.1 over Win XP.

When I reboot, I get a GRUB> prompt with no options or choices.
How do I get to the point where it displays the choice to boot into Ubuntu or Win XP?

---

### Post by wilee-nilee on 2011-04-02
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by drmathprog on 2011-04-02
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 71714223. But according to the info from 
                       fdisk, sdd5 starts at sector 900154143.
    Operating System:  
    Boot files/dirs:   

sdd6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   490,223,474   490,223,412   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc2              16,065   488,392,064   488,376,000   f W95 Ext d (LBA)
/dev/sdc5              16,128   488,392,064   488,375,937   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63       353,429       353,367  de Dell Utility
/dev/sdd2    *        353,430   450,253,754   449,900,325   7 HPFS/NTFS
/dev/sdd3         450,254,846 1,250,258,624   800,003,779   f W95 Ext d (LBA)
/dev/sdd5         900,154,143 1,250,258,624   350,104,482   7 HPFS/NTFS
/dev/sdd6         450,254,848   887,865,343   437,610,496  83 Linux
/dev/sdd7         887,867,392   900,153,343    12,285,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        12CC960FCC95ED6B                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C0D8362BD8361FD8                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        4CB5E28732EF8416                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        07D4-030A                              vfat       DellUtility                   
/dev/sdd2        1EA8699BA8697267                       ntfs       Windows                       
/dev/sdd3: PTTYPE="dos" 
/dev/sdd5        1EB287D01693A333                       ntfs       Program Files                 
/dev/sdd6        6c342214-b2ee-4bb1-a507-01321f66ee25   ext4                                     
/dev/sdd7        4d606fef-74aa-46b9-b3a4-015167e96850   swap                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd2        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd6        /media/6c342214-b2ee-4bb1-a507-01321f66ee25 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc5        /media/4CB5E28732EF8416  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

================================ sdd2/boot.ini: ================================

[boot loader] 
timeout=2 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 

=========================== sdd6/boot/grub/grub.cfg: ===========================

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
set root='(hd3,msdos6)'
search --no-floppy --fs-uuid --set 6c342214-b2ee-4bb1-a507-01321f66ee25
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos6)'
search --no-floppy --fs-uuid --set 6c342214-b2ee-4bb1-a507-01321f66ee25
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set 6c342214-b2ee-4bb1-a507-01321f66ee25
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6c342214-b2ee-4bb1-a507-01321f66ee25 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set 6c342214-b2ee-4bb1-a507-01321f66ee25
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6c342214-b2ee-4bb1-a507-01321f66ee25 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set 6c342214-b2ee-4bb1-a507-01321f66ee25
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set 6c342214-b2ee-4bb1-a507-01321f66ee25
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdd2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd3,msdos2)'
    search --no-floppy --fs-uuid --set 1ea8699ba8697267
    drivemap -s (hd0) ${root}
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

=============================== sdd6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd6 during installation
UUID=6c342214-b2ee-4bb1-a507-01321f66ee25 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd7 during installation
UUID=4d606fef-74aa-46b9-b3a4-015167e96850 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd6: Location of files loaded by Grub: ===================


 271.4GB: boot/grub/core.img
 370.2GB: boot/grub/grub.cfg
 231.3GB: boot/initrd.img-2.6.35-22-generic
 230.9GB: boot/vmlinuz-2.6.35-22-generic
 231.3GB: initrd.img
 230.9GB: vmlinuz
```

---

### Post by Hedgehog1 on 2011-04-03
> **drmathprog said:**
> I just installed a default install of Ubuntu 10.1 over Win XP.

When I reboot, I get a GRUB> prompt with no options or choices.
How do I get to the point where it displays the choice to boot into Ubuntu or Win XP?

I started looking over the script that **wilee-nilee** asked you to run.

I want to be clear on your goal:  You installed over XP - was this to end up with a:

* Ubuntu only PC

* Windows XP / Ubuntu Dual-Boot PC? 

Also - am I correct in guessing that the PC came with a 640 gig IDE drive and you have added two 250gig SATA drives?

***The Hedge***

:KS

---

### Post by drmathprog on 2011-04-03
It came with XP; I'm trying to create a dual boot machine.
The boot drive is a 640 GB drive which now has a win XP boot partition, a win pogram partition and an Ubununtu 10.1 partition.

There are three other 250GB hard drives; at the moment all are Ntfs formatted XP data drives

As I said, at the moment I boot into a GRUB > prompt that displays no OS to boot into.  I can boot only into Ubuntu using the LIve CD.

---

### Post by Hedgehog1 on 2011-04-03
Thanks for that extra data.

It appears you made severla install attempts. so we have two steps yo get you operational.  Both will be done from the LiveCD/LiveUSB.

First we need to remove the boot flag from dev/sda1.

It do the Menu to System >> Administration >> Gparted Partition Editor

Using the button in the upper right hand corner, select this drive:

> Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   490,223,474   490,223,412   7 HPFS/NTFS

The right click on the partition to get a menu and select 'Manage Flags':

[IMG]http://img855.imageshack.us/img855/6408/bootflaggparted.png[/IMG]

Uncheck the boot flag. Close the little window.  Press the 'check mark' button to make the change real.

Next, we load grub on the real boot drive:

In the Terminal (Menu to: Applications >> Accessories >> Terminal),  please run these two commands:


```
sudo mount /dev/sdd6 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sdd
```

You are done!

You can restart your PC, and you should see the grub menu and be able to boot into Ubuntu and Windows from it.


***The Hedge***

:KS

---

