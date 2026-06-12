---
title: "Problem installing Ubuntu 10.10"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by netsurfer802 on 2011-01-10
I have an HP desktop that I've installed Ubuntu 10.10 successfully on before...then one day it just stopped working.

I've formatted the boot partition of my HP desktop with a Windows XP cd which I've done before successfully installing Ubuntu 10.10 in the past.  This time I tried installing Ubuntu 10.10 again but when I restarted it just froze before even getting to the Ubuntu splash screen for minutes at a time with a black screen...no errors or anything.

Ubuntu runs fine off the CD when I boot from it and click to try it out.   Should I check the memory or hard drive?  I actually tried to restart of the CD and wait for the option on checking memory ...but it just boots right to Ubuntu from the CD without giving that option on checking memory.  What should I do?

---

### Post by netsurfer802 on 2011-01-13
Wow...is there anybody out there??  Anyway, I'm still lost here.  Somebody told me about "Smart Data" to check out my system's hard-drive.  I've been trying to download the live version: [http://sourceforge.net/apps/trac/smartmontools/wiki/Download#ListofbootableCDs](http://sourceforge.net/apps/trac/smartmontools/wiki/Download#ListofbootableCDs) .  (I think I'm running into trouble installing a package while running in Live mode.  So, I thought creating a boot CD would be more useful.)

I'm confused when I get to the download for this because I end up downloading a file with a .deb extension...I'm only familliar file formats like .iso when I have to create a CD.  Can somebody enlighten me.

---

### Post by Quackers on 2011-01-13
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by netsurfer802 on 2011-01-13
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2014 MB, 2014641664 bytes
4 heads, 32 sectors/track, 30740 cylinders, total 3934847 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,934,846     3,934,815   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6ad6129e-95f3-4175-9b50-88b2fb8d754d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d100fbc1-8566-4c61-b2b1-900e0b280944   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1555-02B7                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/1555-02B7         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 6ad6129e-95f3-4175-9b50-88b2fb8d754d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 6ad6129e-95f3-4175-9b50-88b2fb8d754d
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6ad6129e-95f3-4175-9b50-88b2fb8d754d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6ad6129e-95f3-4175-9b50-88b2fb8d754d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6ad6129e-95f3-4175-9b50-88b2fb8d754d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6ad6129e-95f3-4175-9b50-88b2fb8d754d ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6ad6129e-95f3-4175-9b50-88b2fb8d754d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6ad6129e-95f3-4175-9b50-88b2fb8d754d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6ad6129e-95f3-4175-9b50-88b2fb8d754d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d100fbc1-8566-4c61-b2b1-900e0b280944 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  19.4GB: boot/grub/core.img
   8.7GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-22-generic
  19.4GB: boot/vmlinuz-2.6.35-22-generic
    .7GB: initrd.img
  19.4GB: vmlinuz
```

---

### Post by Quackers on 2011-01-13
I can't see anything wrong with the boot script output.
When you say it just froze on reboot, what does that mean exactly? Was there something on the screen? A pointer for instance. Or did the screen just go black?
Which graphics card are you using?

---

### Post by netsurfer802 on 2011-01-15
Thanks...well, I re-installed it and everything seems to be working.  The only thing I seemed to do different was choose to encrypt the home directory...what does that do anyway?  Anyway, Thanks!

---

### Post by dino99 on 2011-01-15
[https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory)

---

### Post by Quackers on 2011-01-15
Ah good news :-)

---

