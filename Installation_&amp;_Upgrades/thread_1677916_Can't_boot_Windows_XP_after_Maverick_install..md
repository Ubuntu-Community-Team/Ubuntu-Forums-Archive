---
title: "Can't boot Windows XP after Maverick install."
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by lmp90 on 2011-01-29
I installed Ubuntu 10.10 using Wubi installer selecting 10GB install and now I can't boot into Windows XP. When I restart it loads GNU GRUB. It has the says:
```
[CENTER]GNU GRUB version 1.98+20100845ubun+u2
[/CENTER]
Ubuntu, Linux 2.6.35-25-generic
Ubuntu, Linux 2.6.35-25-generic (Recovery Mode)
Ubuntu, Linux 2.6.35-22-generic
Ubuntu, Linux 2.6.35-22-generic (Recovery Mode)
Windows NT/2000/XP (Loader) (on /dev/sda1)
```When I try to boot into Windows it says
```
error: unknown command: 'drivemap'
``` and returns to the GRUB boot menu. Is there any way to restore Windows XP? Also, my HD seems to be reduced from 100GB to 9.4GB. Any help would be appreciated.

---

### Post by sikander3786 on 2011-01-29
Welcome to the forums :-)

You've installed Grub in the MBR of your HDD by mistake which has replaced your Windows bootloader. Please see problem # 1 here.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Once your issue is fixed, don't forget to apply Permanent Fix from that page as that would save you troubles later.

---

### Post by Rubi1200 on 2011-01-29
Are you able to boot Ubuntu normally?

If yes, this is what I would like you to do please:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by lmp90 on 2011-01-29
I tried doing that. I bought a new Windows XP Installation CD, booted it into Recovery/Repair Mode and typed commands:
```
fixboot
fixmbr
exit
```
Rebooted into the GNU GRUB bootloader and tried to boot Windows:
```
error: unknown command: 'drivemap'
```
It still won't work!!!

---

### Post by lmp90 on 2011-01-29
I ran the script and got this in RESULTS.TXT

              ```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   195,350,399   195,350,337   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4136 MB, 4136632320 bytes
32 heads, 63 sectors/track, 4007 cylinders, total 8079360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     8,078,111     8,078,049   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       c08a677d-e003-4536-879e-2f5eb710d747   ext4                                     
/dev/sda1        A87CC4DF7CC4AA00                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9C8F-AC98                              vfat       MASSSTORAGE                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sr0         /media/GRTMPFPP_EN       iso9660    (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/MASSSTORAGE       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\wubildr.mbr 
[operating systems] 
C:\wubildr.mbr="Ubuntu Netbook" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=Z73E9L /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=Z73E9L-BAK 

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-25-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a87cc4df7cc4aa00
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a87cc4df7cc4aa00
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a87cc4df7cc4aa00
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a87cc4df7cc4aa00
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a87cc4df7cc4aa00
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

================= sda1/Wubi: Location of files loaded by Grub: =================


   2.3GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
   1.1GB: boot/initrd.img-2.6.35-25-generic
   6.8GB: boot/vmlinuz-2.6.35-22-generic
   6.8GB: boot/vmlinuz-2.6.35-25-generic
   1.1GB: initrd.img
   1.2GB: initrd.img.old
   6.8GB: vmlinuz
   6.8GB: vmlinuz.old
```

---

### Post by Rubi1200 on 2011-01-29
If Ubuntu is booting normally, and the results seem to indicate that it does, then the problem is on the Windows side.

Right now, the only thing I can think of is that it might have to do with the backup utility you have in Windows (but that is just a guess really).

I have to go now, but will ask some others to take a look and offer advice.

Will look back in on this tomorrow.

Good luck!

---

### Post by wilee-nilee on 2011-01-29
> **lmp90 said:**
> I tried doing that. I bought a new Windows XP Installation CD, booted it into Recovery/Repair Mode and typed commands:
```
fixboot
fixmbr
exit
```
**Rebooted into the GNU GRUB bootloader and tried to boot Windows:**
```
error: unknown command: 'drivemap'
```
It still won't work!!!

This is confusing, the bootloader you should be seeing now as the script confirms is the MS gui screen for a choice of XP or Ubuntu, is this correct?

If you choose the Ubuntu from there you get a pseudo grub screen there that may show windows is this where you are trying to access XP?

---

### Post by bcbc on 2011-01-29
You made the mistake of setting the timeout to zero and making Ubuntu the default OS to boot.

Windows boot manager is part of windows, and everytime you boot windows it waits for zero seconds before booting Ubuntu instead.

So you can fix this from ubuntu, by editing the /host/boot.ini file. BUT be very careful - if you mess up, nothing will boot.

So copy it first:
cp /host/boot.ini /host/boot.ini.backup

Then DON"T hit enter on any lines. Just change the 0 to 30 and save. Because the line ending control codes on linux are often different to windows and if you mess it up, neither windows or Ubuntu will boot.

FYI - this is what boot.ini looks like:
> [boot loader] 
[COLOR="Red"]timeout=0 
default=C:\wubildr.mbr [/COLOR]
[operating systems] 
C:\wubildr.mbr="Ubuntu Netbook" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=Z73E9L /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=Z73E9L-BAK 

---

