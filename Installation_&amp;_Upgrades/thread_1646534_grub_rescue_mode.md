---
title: "grub rescue mode"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by emerald_fire on 2010-12-16
Hi
I updated yesterday and now when I start my laptop it goes in to grub rescue mode. I have booted from a 'live cd' and thought I could repair grub from there. In gparted however the partition with ubuntu (sda1) is seen as unknown file system, in terminal when I list the partition table it shows up as FAT16 type. When I try a grub-install it gives this error message:
```
sudo grub-install /dev/sda1
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```I've also run the boot info script...
```

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
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
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    16,383,999    16,381,952   6 FAT16
/dev/sda2    *     16,386,048   172,675,063   156,289,016   7 HPFS/NTFS
/dev/sda3         172,675,072   312,580,095   139,905,024   f W95 Ext d (LBA)
/dev/sda5         172,677,120   312,580,079   139,902,960   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,915,775     3,915,744   6 FAT16


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.0 GB, 16039018496 bytes
75 heads, 40 sectors/track, 10442 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             40    31,326,207    31,326,168   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       f39d9a1f-1a91-485c-9834-3a96e0703dd9   ext4                                     
/dev/sda2        A6142853142828AF                       ntfs       VistaOS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        B29814CD981491C9                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C2F8-E4F2                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        C170-3FE6                              vfat       PAISLEY                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b29814cd981491c9
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b29814cd981491c9
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=7
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b29814cd981491c9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b29814cd981491c9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b29814cd981491c9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b29814cd981491c9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b29814cd981491c9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b29814cd981491c9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set a6142853142828af
    drivemap -s (hd0) ${root}
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

================= sda1/Wubi: Location of files loaded by Grub: =================


   2.4GB: boot/grub/core.img
   8.9GB: boot/grub/grub.cfg
   3.1GB: boot/initrd.img-2.6.32-24-generic
   8.6GB: boot/initrd.img-2.6.32-25-generic
   1.5GB: boot/initrd.img-2.6.32-26-generic
   2.9GB: boot/vmlinuz-2.6.32-24-generic
   3.9GB: boot/vmlinuz-2.6.32-25-generic
   2.9GB: boot/vmlinuz-2.6.32-26-generic
   1.5GB: initrd.img
   8.6GB: initrd.img.old
   2.9GB: vmlinuz
   3.9GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-12-16
sudo grub-install /dev/sda1
your command: this is wrong grub in the type of installation you have inside of windows=wubi never has grub installed, don't install or accept any grb-pc or grub common upgrades.

So to fix this at least getting the windows to boot you need a install dvd or a recovery cd and one command run in the recovery/repair terminal. Looks like Vista here is a link for a recovery ISO, burn a cd. Boot it and follow these instructions. Notice the W7 forum tutorial to getting to the command line the instructions are for as well.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following command:
**BootRec.exe /fixmbr**
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

So if you have a netbook and no cd possibility we can load a thumb with Ubuntu or if you have one or a disc there is a linux bootloader that can be used rather then the native MS bootloader, it is not grub.

Not really sure about /boot/grub/core.img being installed in the Ubuntu wubi boot, probably not a problem others will know better

---

### Post by garvinrick4 on 2010-12-16
Looks like you had a WUBI install (inside of Windows, a folder in C; drive) and used
a grub install for a partition install and kind of have made a mess of things. I will post
this to give you a bump to beginning of Forums and hope a WUBI guy shows up.
Put WUBI in your Title will help you find a user.

---

### Post by emerald_fire on 2010-12-16
thanks wilee-nilee and garvinrick4
good to know wubi has no grub, I guess this is the problem caused by the update.
won't make same mistake twice

---

### Post by garvinrick4 on 2010-12-16
> **emerald_fire said:**
> thanks wilee-nilee and garvinrick4
good to know wubi has no grub, I guess this is the problem caused by the update.
won't make same mistake twice Its wubildr places itself inside of Windows boot
manager to boot. (it does have a grub but it is a different install and fix than partition install.) 
You just made a mistake, no big deal, everyone does.
# This will bump it up to front again incase a user pops up that can fix you up.
 ## below is a link to save for WUBI users.

[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?")

---

### Post by bcbc on 2010-12-16
You need to reinstall the windows bootloader (or use lilo). Grub has been installed to the disk master boot record and doesn't work in this way with Wubi.

See *Rubi1200*s [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") Problem #1, Solution #1,#2 for everything you need.

PS: you just need the windows bootloader - you don't need to fix the bootsector or anything else

Edit: you may need to repair sda1 using testdisk. Do you remember what partition type it was before? If your Ubuntu install (root.disk) was bigger than 4GB it's likely type ntfs, not fat16.

---

### Post by emerald_fire on 2010-12-16
thankyou garvinrick4 i at least could start looking for answers in the right place :)

---

### Post by bcbc on 2010-12-16
Actually things look a little messed. According to the grub.cfg file, your wubi install was on sda5, not sda1. So not sure how that happened.

---

### Post by emerald_fire on 2010-12-16
cheers bcbc
I've begun looking at lilo and reading wubi guide/bug reports,  will check wubi thread too! 

never even knew to look for partition types etc before today, doubt FAT is correct, a friend thought it might be ext4, ntfs would make sense though.

---

### Post by emerald_fire on 2010-12-16
have windows back unscathed, heading back in for another try at ubuntu

---

