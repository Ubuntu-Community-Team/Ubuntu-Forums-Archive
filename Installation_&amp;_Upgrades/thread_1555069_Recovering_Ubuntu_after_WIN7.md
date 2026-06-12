---
title: "Recovering Ubuntu after WIN7 ??"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by schoft on 2010-08-17
I tried to follow this tutorial ( [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record") ) but i'm getting stuck. It says I need to type in "mount | tail -1" in order to verify that i'm on the right HDD. But it replies by saying:

/dev/sda1 on /media/Lokaal station type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

Wich is my second HDD, just using it for storage. 

Here's a screenshot of my gparted:
[http://img186.imageshack.us/img186/7959/screenshotwx.png](http://img186.imageshack.us/img186/7959/screenshotwx.png)

---

### Post by Rubi1200 on 2010-08-17
Hi and welcome,
yes, if you are using a LiveCD things will be slower.

Also, since you are using the CD, please click on the link at the bottom of my post.

Follow the instructions there and post the results back here.

The results will give us a clearer overview of your setup and make offering solutions a lot easier.

:-)

---

### Post by schoft on 2010-08-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc922c922

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x36e1f639

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   114,527,384   114,527,322  83 Linux
/dev/sdb2    *    114,528,256   114,733,055       204,800   7 HPFS/NTFS
/dev/sdb3         114,733,056   299,804,671   185,071,616   7 HPFS/NTFS
/dev/sdb4         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sdb5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0010841710841636                       ntfs       Lokaal station                
/dev/sdb1        de76f14f-2988-4e21-a3fb-a491e19c7341   ext4                                     
/dev/sdb2        A288A40588A3D5D7                       ntfs       System Reserved               
/dev/sdb3        C262AA6962AA61C1                       ntfs                                     
/dev/sdb5        4d330b9d-fa13-4428-b8dc-5117cd064835   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/de76f14f-2988-4e21-a3fb-a491e19c7341 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb3        /media/C262AA6962AA61C1  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/Lokaal station    fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set de76f14f-2988-4e21-a3fb-a491e19c7341
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
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set de76f14f-2988-4e21-a3fb-a491e19c7341
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=de76f14f-2988-4e21-a3fb-a491e19c7341 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set de76f14f-2988-4e21-a3fb-a491e19c7341
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=de76f14f-2988-4e21-a3fb-a491e19c7341 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set de76f14f-2988-4e21-a3fb-a491e19c7341
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=de76f14f-2988-4e21-a3fb-a491e19c7341 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set de76f14f-2988-4e21-a3fb-a491e19c7341
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=de76f14f-2988-4e21-a3fb-a491e19c7341 ro single 
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=de76f14f-2988-4e21-a3fb-a491e19c7341 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4d330b9d-fa13-4428-b8dc-5117cd064835 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
  38.4GB: boot/initrd.img-2.6.31-21-generic
    .2GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: boot/vmlinuz-2.6.31-21-generic
  38.4GB: initrd.img
    .2GB: initrd.img.old
    .2GB: vmlinuz
    .2GB: vmlinuz.old
``` hmm

---

### Post by schoft on 2010-08-17
```
root@ubuntu:~# mount /dev/sdb1/ /mnt
root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sdb
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Auto-detection of a filesystem module failed.

root@ubuntu:~# mount | tail -1
/dev/sdb1 on /mnt type ext4 (rw)
root@ubuntu:~# ls /media/
C262AA6962AA61C1/                     Lokaal station/
de76f14f-2988-4e21-a3fb-a491e19c7341/ System Reserved/



```

---

### Post by schoft on 2010-08-17
```
root@ubuntu:~# sudo grub-install --root-directory=/media/de76f14f-2988-4e21-a3fb-a491e19c7341 /dev/sdb
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

---

### Post by schoft on 2010-08-17
```
root@ubuntu:~# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0010841710841636" LABEL="Lokaal station" TYPE="ntfs" 
/dev/sdb1: UUID="de76f14f-2988-4e21-a3fb-a491e19c7341" TYPE="ext4" 
/dev/sdb2: UUID="A288A40588A3D5D7" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdb3: UUID="C262AA6962AA61C1" TYPE="ntfs" 
/dev/sdb5: UUID="4d330b9d-fa13-4428-b8dc-5117cd064835" TYPE="swap" 
```

```
root@ubuntu:~# cat /etc/fstab 
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0
```

---

