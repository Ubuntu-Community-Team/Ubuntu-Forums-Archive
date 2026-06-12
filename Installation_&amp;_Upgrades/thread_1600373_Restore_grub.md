---
title: "Restore grub"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by dathui on 2010-10-18
I've installed Kubuntu 10.10 using Wubi and everything worked fine until a few hours ago thought a nifty bootloader would be fun so I tried to install burg. Mistake. Now I can't boot the machine, all I get is:
"error: no such device: 6706...-1945-...-.....
Entering rescue mode...
grub rescue>"

After some swearing and panic I've managed to get a bootable usb stick with Kubuntu 10.10 going and it starts fine, now I'm wondering how to either restore grub, i'd be happy with that, of if it's easier, configure grub properly, from the live usb-kubuntu.

---

### Post by ronparent on 2010-10-18
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by dathui on 2010-10-18
I tried to follow the reinstall way but I get this.

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda1
The file /mnt//boot/grub/stage1 not read correctly.

I have checked and there is a stage1 file at /mtn/boot/grub/stage1.

Pasting the results from the boot info script in case it helps
-----------------------------------------------------------------------------------------------

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/burg.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   502,259,711   502,052,864   7 HPFS/NTFS
/dev/sda3         502,259,712   625,139,711   122,880,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16001036288 bytes
32 heads, 63 sectors/track, 15501 cylinders, total 31252024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,250,015    31,249,953   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       670693f3-1946-4c5b-b6d8-c3909230e25a   ext4                                     
/dev/sda1        5EDA2E36DA2E0ABB                       ntfs                                     
/dev/sda2        C80A0DB10A0D9E16                       ntfs                                     
/dev/sda3        26D45351D45321FB                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3AF6-6C42                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2

======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set c80a0db10a0d9e16
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=773  quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set c80a0db10a0d9e16
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=773
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set c80a0db10a0d9e16
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=773  quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set c80a0db10a0d9e16
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=773
	initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5eda2e36da2e0abb
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

============================= sda2/Wubi/etc/fstab: =============================

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

================= sda2/Wubi: Location of files loaded by Grub: =================


   3.2GB: boot/grub/grub.cfg
   3.2GB: boot/initrd.img-2.6.32-25-generic
   7.1GB: boot/initrd.img-2.6.35-22-generic
   4.7GB: boot/vmlinuz-2.6.32-25-generic
   4.7GB: boot/vmlinuz-2.6.35-22-generic
   7.1GB: initrd.img
   3.2GB: initrd.img.old
   4.7GB: vmlinuz
   4.7GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Start Kubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg

---

### Post by bcbc on 2010-10-18
with wubi you require the windows bootloader - not grub (or burg). So, reinstall that first (either from windows discs) or you can use lilo as well:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

That should get you booting windows and you'll see the windows boot manager offering (K)Ubuntu. Now if burg removed grub.cfg you'll probably end up at a grub prompt. If not it should boot. And then you'll need to remove burg and reinstall grub-pc (if grub-pc is uninstalled with burg which I assume it is). If you do have to reinstall grub-pc do not install it's bootloader to /dev/sda (or anywhere if prompted)

For manually booting wubi from a grub prompt (not a grub rescue prompt):
```
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

---

### Post by dathui on 2010-10-18
> **bcbc said:**
> with wubi you require the windows bootloader - not grub (or burg). So, reinstall that first (either from windows discs) or you can use lilo as well:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

That should get you booting windows and you'll see the windows boot manager offering (K)Ubuntu. Now if burg removed grub.cfg you'll probably end up at a grub prompt. If not it should boot. And then you'll need to remove burg and reinstall grub-pc (if grub-pc is uninstalled with burg which I assume it is). If you do have to reinstall grub-pc do not install it's bootloader to /dev/sda (or anywhere if prompted)

For manually booting wubi from a grub prompt (not a grub rescue prompt):
```
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

The lilo part did it, now everything is back to normal, panic and more swearing averted :) thanks alot for the help.

---

### Post by bcbc on 2010-10-18
> **dathui said:**
> The lilo part did it, now everything is back to normal, panic and more swearing averted :) thanks alot for the help.

Great :) 

If you want to experiment with burg I recommend migrating your wubi install to a partition install first: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) (and also backing up data beforehand course)

---

