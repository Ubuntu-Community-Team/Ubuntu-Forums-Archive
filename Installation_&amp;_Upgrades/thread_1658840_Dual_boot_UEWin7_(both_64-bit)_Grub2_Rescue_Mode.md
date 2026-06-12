---
title: "Dual boot UE/Win7 (both 64-bit) Grub2 Rescue Mode"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by Iecur on 2011-01-03
Well yes I just recent got a new computer and recently switched to Ubuntu on the last one I was using so I figured I'd go ahead and install it on here too.  I chose Ultimate Edition 2.8 [I'm hoping I can still get help here I'm sure they are plenty helpful but I've grown fond of these forums since I've gotten so much wonderful help here already(and if it is fine to post here should I be prefixing ubuntu, all variants, or other_os ?)].  I first installed Windows 7 on my main hard drive made three partitions and used the last one.    Then I installed UE on the first partition.  No problems yet.  Then I logged into Windows seeing as I'd forgotten to format the last partition.  I was figuring NTFS might be nice so that I could use it on both OSs.

After this I rebooted the computer and then I went to Rescue Mode on Grub2.  I checked on another computer to see what to do and I ended up here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) I read through that article and found the rescue mode section.  Followed the instructions:
ls
set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod linux
insmod normal
normal

I think I read that part right might not have but it seemed to work.  I was able to pick which OS to boot into.  Both seem to work perfectly fine.  But whenever I would need to reboot.  I keep getting the same error.

I checked out my /boot/grub/grub.cfg file and I noticed that when it looks for where to search for boot files it's looking on the wrong hard drive ?  Or at least that is what it looks like to me.  Here is my boot_info_script output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 155472512 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34       262,177       262,144 Microsoft Windows
/dev/sda2         264,192 1,818,068,991 1,817,804,800 Linux or Data
/dev/sda3   3,895,310,336 3,907,028,991    11,718,656 Linux Swap
/dev/sda4   1,818,068,992 3,895,308,287 2,077,239,296 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   260,829,183   260,827,136  83 Linux
/dev/sdc2         260,829,184   651,452,415   390,623,232   7 HPFS/NTFS
/dev/sdc3    *    651,452,416   651,657,215       204,800   7 HPFS/NTFS
/dev/sdc4         651,657,216   976,771,071   325,113,856   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        12A46057A4603EFB                       ntfs       gigante                       
/dev/sda3        37b843b2-d388-4cb5-b088-9e817112c456   swap                                     
/dev/sda4        2fb4cd9c-e3d8-4849-bede-7c2ed50f65c2   ext4                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        6660E07260E04A7F                       ntfs       1                             
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        b4440725-21f7-4e04-8be8-60a3e9d61fd7   ext4                                     
/dev/sdc2        C08A68A08A689526                       ntfs       virtual                       
/dev/sdc3        5680909780907F65                       ntfs       System Reserved               
/dev/sdc4        3AC498E5C498A4A3                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda4        /home                    ext4       (rw,commit=0)
/dev/sdc2        /media/virtual           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/gigante           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/Ultimate Edition 2.8 iso9660    (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/1                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set b4440725-21f7-4e04-8be8-60a3e9d61fd7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1920x1080x32,1280x1024x32,640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set b4440725-21f7-4e04-8be8-60a3e9d61fd7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
play 480 440 1
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set b4440725-21f7-4e04-8be8-60a3e9d61fd7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b4440725-21f7-4e04-8be8-60a3e9d61fd7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set b4440725-21f7-4e04-8be8-60a3e9d61fd7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b4440725-21f7-4e04-8be8-60a3e9d61fd7 ro single 
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set b4440725-21f7-4e04-8be8-60a3e9d61fd7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set b4440725-21f7-4e04-8be8-60a3e9d61fd7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos3)'
    search --no-floppy --fs-uuid --set 5680909780907f65
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc3 during installation
UUID=b4440725-21f7-4e04-8be8-60a3e9d61fd7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=2fb4cd9c-e3d8-4849-bede-7c2ed50f65c2 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=37b843b2-d388-4cb5-b088-9e817112c456 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


  79.6GB: boot/grub/core.img
  45.2GB: boot/grub/grub.cfg
  41.2GB: boot/initrd.img-2.6.35-22-generic
  79.5GB: boot/vmlinuz-2.6.35-22-generic
  41.2GB: initrd.img
  79.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```I don't really know much about this and just noticed the part that talks about core.img missing ?  I don' t really get what that's about but on the /boot/grub/grub.cfg section it says it's looking for linux and everything else in (hd2,Y) but in order to get out of rescue mode it shows that Linux is on  (hd0,msdos1 ).  
Also what decides the order of the hard drives ?  I plugged the hard drive I wanted to use as my primary one in the SATA slot 1, my other two hard drives on slots 2 and 3 and my optical drive in slot 4 on the motherboard.  However in BIOS they are shown in backwards order.  And I had to change the boot order seeing as my primary hard drive was showing up as the last one on the list and won't "boot" (using that term loosely seeing as if I did I'd just end up in rescue mode) it just tells me to put in something it can boot into and hit return.  Why is my primary drive sdc and last time I booted up it was sdd and there was no sdb...I'm tremendously confused.  I'm so exhausted lack of sleep and so much time being consumed into this I'm sure I'm missing out obvious things in that file so if someone would be kind enough to help me out...

Reading more of that Grub2 page I tried going to the command line once I was in Grub2 and tried to boot into UE but that failed I got some error.  I also tried to see if there was anything I could edit in the /etc/default/grub file and looking through /etc/grub.d/ dir but I couldn't quite figure out what was required to be changed in order for it to look in the correct spot.  I've tried reinstalling grub with no success.  I've tried reinstalling Windows and UE installed Windows first this time then when UE installed straight to rescue mode.  Is there really no way to change that part in the grub.cfg file ?  Is that not the issue ?  Help please!  Well I will try to be around to answer any questions that arise but for now I shall go get something to eat not even sure when I last ate...sorry if I seem a bit distressed.  I would just like to sit back be able to turn on my computer without having to enter that sequence every single time.

Again just to stress it I'm sorry for my big long run-on sentences and whatnot and thank you for any help you can provide.

---

