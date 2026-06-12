---
title: "Boot failure after upgrading to Ubuntu 10.4"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by altruist77 on 2010-07-28
Hi,
    I am a novice in the use of Ubuntu. I am just trying to get acclimatized with it slowly. My lap top has a single physical hard drive with three partitions.
Partition C: windows 7
Partition D: Ubuntu 
Partition E: Data
Yesterday, I booted into Ubuntu and found that there was an update available for Ubuntu 10.4. I was very excited and clicked on the update.
The update was installing and in the process there was a window mentioning about Grub and I just clicked Okay to install. 
Later after the update was completed, I restarted the computer. The computer won't boot up. After the preliminary memory check, instead of giving me the boot up screen to chose between windows 7 and Ubuntu, I was presented with a screen and following commands
Error: no such device: 080a3315-8550-40d4-9f88-c814aec24172
grub rescue>:

I was dumbstruck as I have no background training in computers and don't know to play with the command prompt. 
After a whole day of searching on the internet for similar cases, I found that most of the similar problems were addressed through a series of command prompt scripts and some choices. 
I was unable to choose a right solution as no one mentioned the exact error as above. 
I did download bootscript info.
The results.txt was as follows
```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa76b87b2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   123,852,799   123,645,952   7 HPFS/NTFS
/dev/sda3         123,852,800   226,252,799   102,400,000   7 HPFS/NTFS
/dev/sda4         226,252,800   488,394,751   262,141,952   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4078 MB, 4078960640 bytes
16 heads, 32 sectors/track, 15560 cylinders, total 7966720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,966,719     7,966,688   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       080a3315-8550-40d4-9f88-c814aec24172   ext4                                     
/dev/sda1        98BA9834BA98113C                       ntfs       System Reserved               
/dev/sda2        18386F06386EE26C                       ntfs                                     
/dev/sda3        6224446724443FF1                       ntfs                                     
/dev/sda4        FA18C24E18C20A19                       ntfs                                     
/dev/sdb1        46A8-262C                              vfat       KINGSTON                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/18386F06386EE26C  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda4        /media/FA18C24E18C20A19  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 6224446724443ff1
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 6224446724443ff1
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 6224446724443ff1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 6224446724443ff1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 6224446724443ff1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 6224446724443ff1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 98ba9834ba98113c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


   4.1GB: boot/grub/core.img
   5.8GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.31-17-generic
   1.4GB: boot/initrd.img-2.6.32-24-generic
   2.5GB: boot/vmlinuz-2.6.31-17-generic
   1.5GB: boot/vmlinuz-2.6.32-24-generic
   1.4GB: initrd.img
    .9GB: initrd.img.old
   1.5GB: vmlinuz
   2.5GB: vmlinuz.old

```I request the experienced users and gurus on this forum to please help me restore my computer. This is my work computer and I am really stuck without it. I forgot to back up my data. Also, I don't have the windows 7 installation disc as I misplaced my installation disc.

Thank you
Sincerely
Arul

---

### Post by bcbc on 2010-07-28
The grub update failed to recognize that you have a wubi install, and replaced the windows bootloader with the grub bootloader.

You need to put the windows bootloader back, or you can just use lilo. To use lilo, boot from the live CD and run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by altruist77 on 2010-07-28
THank you BCBC,
                          The solution that you provided worked for me. Now my boot menu is back to the original options - Windows7 or Ubuntu.
When I choose Ubuntu, it fails to boot up. I will post the error messages in a seperate thread to avoid confusion.
Thank you
Arul

---

### Post by Neophyte Newbie on 2010-07-29
I'm also trying to learn Ubuntu but have gotten the "black screen" (no messages however) during upgrade from 9.10 to 10.04 on my Toshiba laptop - the colored ring around power on button turns RED (for the first time) instead of normal blue and laptop screeches to a halt. No err msg. Laptop is dedicated to Ubuntu - no other OSes installed.

(1) 9.10 was installed from "live CD" and ran swell. It was successfully re-installed after 10.04 crashed.
(2) 10.04 will run ONLY in "live CD" mode. Installing to HD causes crash described above.
(3) Kubuntu 10.04 causes same problem during install to HD.

To my untrained eye it seems strange that an upgrade to same machine would create a situation like this. Any ideas ?  Thanx.

Bewildered

---

### Post by bob12564 on 2010-09-11
Just happened to me, also using a Toshiba laptop.  I run dual boot with Windows XP and Windows still boots.  I saw some posts about the 2.6.32-24-generic kernel causing boot problems for some people and I tried selecting the next lower kernel from the grub bootup menu and that worked.  So the newer kernel seems to be the culprit.

Can any of the experienced Ubuntu users help us with this?  I know I'm not skilled enough to resolve this on my own.

---

### Post by bcbc on 2010-09-11
> **bob12564 said:**
> Just happened to me, also using a Toshiba laptop.  I run dual boot with Windows XP and Windows still boots.  I saw some posts about the 2.6.32-24-generic kernel causing boot problems for some people and I tried selecting the next lower kernel from the grub bootup menu and that worked.  So the newer kernel seems to be the culprit.

Can any of the experienced Ubuntu users help us with this?  I know I'm not skilled enough to resolve this on my own.

Yeah that's been happening but totally unrelated to this thread (except maybe the title :p ). Try this one instead [http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)

---

### Post by bob12564 on 2010-09-12
Thanks.  I followed the suggestion in that thread and it didn't help.  My problem may be different so I started a new thread.  The upgrade to 10.4 apparently never completed properly.  It failed after I received the message to restart.  The restart got me as far as the Ubuntu logo screen with the dots and then it went black and no more response.  Maybe I'll get some tips under the new thread.

---

