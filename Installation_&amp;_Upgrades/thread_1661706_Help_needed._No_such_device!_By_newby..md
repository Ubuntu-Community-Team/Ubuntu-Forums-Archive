---
title: "Help needed. No such device! By newby."
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by laforce on 2011-01-07
Hello to the Forum.
The situation is as follows: 
I have no knoledge of linux or whatsoever I mean I can use dos and have always used windows. 
So for some time I had both Win7 and Ubuntu. Yeserday I booted Ubuntu and started the updates. It asked to choos which hard drives I selected both hard drives that I have and restarted. After the bios chek I got the message No such device: xxxx-xxx-xxx-xx(some number). I think the program was GRUB2. And can not lounch no operation system - it looks like I have no hard drives :) although in the bios all looks ok.

Is this a disk formater or what. What should I do? What to read to get the nececcery knoledge to restore my previous state of the system@
10x in advance.

---

### Post by sikander3786 on 2011-01-07
Welcome to the forums :-)

Yes seems like you installed Grub to the wrong place and it also seems like you had installed Ubuntu inside Windows using Wubi.

Instead of guessing your setup, please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

It might be an easy fix to your problem. You haven't lost any data and it is just the boot loader that is causing problems.

---

### Post by Rubi1200 on 2011-01-07
> **sikander3786 said:**
> Welcome to the forums :-)

Yes seems like you installed Grub to the wrong place and it also seems like you had installed Ubuntu inside Windows using Wubi.

Instead of guessing your setup, please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

It might be an easy fix to your problem. You haven't lost any data and it is just the boot loader that is causing problems.
+1 to the boot script and the initial analysis.

This information is needed in order for us to give you the correct method of fixing the problem.

---

### Post by laforce on 2011-01-07
```

  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sda2         204,802,048   413,698,047   208,896,000   7 HPFS/NTFS
/dev/sda3         413,698,048   625,137,663   211,439,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       642,599       642,537   7 HPFS/NTFS
/dev/sdb2             642,600   163,830,869   163,188,270   7 HPFS/NTFS
/dev/sdb3         163,830,870   819,186,479   655,355,610   7 HPFS/NTFS
/dev/sdb4         819,186,480 1,953,520,064 1,134,333,585   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       dcc28291-a852-4e39-8daa-55e06426056a   ext4                                     
/dev/sda1        78BC4296BC424EB6                       ntfs       &#1053;&#1086;&#1074; &#1090;&#1086;&#1084;                 
/dev/sda2        0E88609C88608455                       ntfs       &#1053;&#1086;&#1074; &#1090;&#1086;&#1084;                 
/dev/sda3        FE7082627082218F                       ntfs       &#1053;&#1086;&#1074; &#1090;&#1086;&#1084;                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0E4AF7724AF754C5                       ntfs       System Reserved               
/dev/sdb2        A0DA9CC6DA9C99DC                       ntfs                                     
/dev/sdb3        B0863890863858D4                       ntfs                                     
/dev/sdb4        04A64F36A64F280E                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/A0DA9CC6DA9C99DC  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb4        /media/04A64F36A64F280E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/&#1053;&#1086;&#1074; &#1090;&#1086;&#1084;     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/&#1053;&#1086;&#1074; &#1090;&#1086;&#1084;_    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 78bc4296bc424eb6
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 78bc4296bc424eb6
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=bg
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
menuentry "Ubuntu, Linux 2.6.32-27-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 78bc4296bc424eb6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 78bc4296bc424eb6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 78bc4296bc424eb6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 78bc4296bc424eb6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 78bc4296bc424eb6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 78bc4296bc424eb6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 0e4af7724af754c5
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

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
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   8.9GB: boot/grub/core.img
   2.5GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.32-24-generic
    .8GB: boot/initrd.img-2.6.32-25-generic
    .9GB: boot/initrd.img-2.6.32-27-generic
   8.9GB: boot/vmlinuz-2.6.32-24-generic
    .7GB: boot/vmlinuz-2.6.32-25-generic
   9.0GB: boot/vmlinuz-2.6.32-27-generic
    .9GB: initrd.img
    .8GB: initrd.img.old
   9.0GB: vmlinuz
    .7GB: vmlinuz.old

```

So I done this.
 Will it be of any use to follow those steps: [http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore).

---

### Post by Rubi1200 on 2011-01-07
Hi laforce,
this is the actual script you posted.

We need you to run the script and post the output from the RESULTS.txt that is generated by it.

If you are still on the LiveCD this should not take more than a few minutes.

In the original link provided by sikander3786 there are instructions on how to execute the script to generate the output.

---

### Post by laforce on 2011-01-07
I've done it right tis time didn't I? (In the edited post above.)

---

### Post by Rubi1200 on 2011-01-07
> **laforce said:**
> I've done it right tis time didn't I? (In the edited post above.)
Yes, perfect!

Okay, so here is the problem. You have Wubi installed within Windows, but GRUB installed in the MBR of both drives (sda and sdb).

Wubi installs cannot be booted from the MBR.

The boot flag (indicated by an asterisk) is on sdb1. Is BIOS set to boot sdb as first device?

In any event, I assume you are also unable to boot Windows; correct?

The solution can be found in problem #1 in the Wubi Megathread (use either solution #1 or #2 depending on your situation):
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

It looks to me as if you will need to restore the Windows bootloader for both drives.

If you need more help or if anything is unclear, please ask first.

---

### Post by laforce on 2011-01-07
OK 10x very much. 
And write I am unable to boot anything! No choise screen just msg that some device is missing....
I will seriously study the megathread.
If I have any unclearties I will bother the forum again. 
Once more thank you for you time and cooperation.

---

