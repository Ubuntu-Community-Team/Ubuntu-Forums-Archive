---
title: "Ubuntu 10.10 dual boot problem"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by mikeb3809 on 2011-03-25
I installed ubuntu on top of win xp which went ok, however I had set aside a separate drive for Ubuntu. This drive is a 20 gig drive & when I installed I selected to divide drive in two partition. YUK!! Now I can access only 9.3 gig plus the swap space. I am running out of room on the 9.3 drive and need the rest of the drive. I cannot access it by win or ubuntu. How can I regain the lost space? I heard about parted but can't find it on the system. I can see the partition when I use "disk utility" but it won't let me combine the partitions. The win drive is a 40 gig drive, so I have two different physical drives.

If I have to repartition will I lose the system I have already installed? I'm a very unhappy, confused camper. Thanks for any help.
Michael :o

---

### Post by Hedgehog1 on 2011-03-25
Gparted is loaded on the LiveCD/LiveUSB.  That tool will allow you to resize your partitions on the 20 gig drive to reclaim all your space.

To resize the partitons, you will need to boot from the LiveCD/LiveUSB, and select the 'TRY' option.  You cannot modifiy the partitions while they are in use.

If you would like some guidance as to what partitons can be removed on the 20 gig drive so the others can be expanded, please do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by mikeb3809 on 2011-03-25
OK hedge, here's what I got back. Hope it means something to you, it is all Greek to me.:p
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Windows Vista/7
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    15,583,049    15,582,987   b W95 FAT32
/dev/sda2          15,583,050    78,236,549    62,653,500   f W95 Ext d (LBA)
/dev/sda5          15,583,113    30,105,809    14,522,697   b W95 FAT32
/dev/sda6          30,105,873    44,869,544    14,763,672   b W95 FAT32
/dev/sda7          44,869,608    62,043,029    17,173,422   b W95 FAT32
/dev/sda8          62,043,093    78,236,549    16,193,457   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders, total 40088160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    19,218,443    19,216,396  83 Linux
/dev/sdb2          19,220,478    40,087,551    20,867,074   5 Extended
/dev/sdb5          38,328,320    40,087,551     1,759,232  82 Linux swap / Solaris
/dev/sdb6          19,220,480    37,412,863    18,192,384  83 Linux
/dev/sdb7          37,414,912    38,316,031       901,120  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    62,524,979    62,524,917   c W95 FAT32 (LBA)
/dev/sdd2          62,524,980   625,137,344   562,612,365   f W95 Ext d (LBA)
/dev/sdd5          62,525,043   625,137,344   562,612,302   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3C4C-1F03                              vfat       SYSTEM                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4EAE-6E56                              vfat       E_PROGRAM1                    
/dev/sda6        449E-139E                              vfat       F_PERSONAL                    
/dev/sda7        2443-467E                              vfat       G_MISC                        
/dev/sda8        7024-3D9E                              vfat       H_INTERNET                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e518df1f-0f9e-4289-b6fd-357b4a849c2b   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        da5961ac-b76b-43da-8a7d-99cdb5eead35   swap                                     
/dev/sdb6        d6c6b1f4-34f2-4339-be31-c0cfbdd5d361   ext4                                     
/dev/sdb7        55f8bc9e-4279-41be-90c6-19e37c119cfd   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdd1                                               vfat       CLASS_ PRES                   
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5                                               vfat       PHOTO_ARCH                    
/dev/sdd: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdd1        /media/CLASS_ PRES       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdd5        /media/PHOTO_ARCH        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda6        /media/F_PERSONAL        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda5        /media/E_PROGRAM1        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e518df1f-0f9e-4289-b6fd-357b4a849c2b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e518df1f-0f9e-4289-b6fd-357b4a849c2b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=e518df1f-0f9e-4289-b6fd-357b4a849c2b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=e518df1f-0f9e-4289-b6fd-357b4a849c2b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e518df1f-0f9e-4289-b6fd-357b4a849c2b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e518df1f-0f9e-4289-b6fd-357b4a849c2b ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3c4c-1f03
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=d6c6b1f4-34f2-4339-be31-c0cfbdd5d361 ro quiet splash
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=d6c6b1f4-34f2-4339-be31-c0cfbdd5d361 ro single
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d6c6b1f4-34f2-4339-be31-c0cfbdd5d361 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d6c6b1f4-34f2-4339-be31-c0cfbdd5d361 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=da5961ac-b76b-43da-8a7d-99cdb5eead35 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/core.img
   5.8GB: boot/grub/grub.cfg
   9.7GB: boot/initrd.img-2.6.35-22-generic
   1.9GB: boot/initrd.img-2.6.35-27-generic
   6.4GB: boot/initrd.img-2.6.35-28-generic
   1.6GB: boot/vmlinuz-2.6.35-22-generic
   1.7GB: boot/vmlinuz-2.6.35-27-generic
   4.3GB: boot/vmlinuz-2.6.35-28-generic
   6.4GB: initrd.img
   1.9GB: initrd.img.old
   4.3GB: vmlinuz
   1.7GB: vmlinuz.old

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=d6c6b1f4-34f2-4339-be31-c0cfbdd5d361 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=d6c6b1f4-34f2-4339-be31-c0cfbdd5d361 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d6c6b1f4-34f2-4339-be31-c0cfbdd5d361 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d6c6b1f4-34f2-4339-be31-c0cfbdd5d361 ro single 
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set d6c6b1f4-34f2-4339-be31-c0cfbdd5d361
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3c4c-1f03
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e518df1f-0f9e-4289-b6fd-357b4a849c2b ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set e518df1f-0f9e-4289-b6fd-357b4a849c2b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e518df1f-0f9e-4289-b6fd-357b4a849c2b ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=d6c6b1f4-34f2-4339-be31-c0cfbdd5d361 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=55f8bc9e-4279-41be-90c6-19e37c119cfd none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  10.4GB: boot/grub/core.img
  10.0GB: boot/grub/grub.cfg
  11.0GB: boot/initrd.img-2.6.35-22-generic
  11.0GB: boot/initrd.img-2.6.35-27-generic
  10.8GB: boot/vmlinuz-2.6.35-22-generic
  10.8GB: boot/vmlinuz-2.6.35-27-generic
  11.0GB: initrd.img
  11.0GB: initrd.img.old
  10.8GB: vmlinuz
  10.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc  
```

---

### Post by Rubi1200 on 2011-03-25
Hi mikeb3809,

Hedgehog1 aka The Hedge asked me to drop by and help out a bit.

First I have some questions that will hopefully clarify a few things:

1. there are remnants of a Wubi install; can I assume you used to have Wubi and subsequently uninstalled it?

2. is sdb, the 20GB drive, an external drive or secondary HD?

3. how is BIOS currently set as regards boot device priority?

So, to your original question:

it appears you have 2 Ubuntu installs on sdb; was this planned or done inadvertently?

My suggestion would be to delete one of the installs, freeing up space for the other.

You also need to determine which Ubuntu you installed last and whether it controls the boot process (something else that would be good to tell us before you continue).

As  Hedgehog1 already said, deleting/moving/resizing partitions should be done from the LiveCD.

But, first, before you start please make backups of all important data.

If you want to wait for some other opinions, please feel free.

Thanks.

---

### Post by mikeb3809 on 2011-03-25
> **Rubi1200 said:**
> Hi mikeb3809,

Hedgehog1 aka The Hedge asked me to drop by and help out a bit.

First I have some questions that will hopefully clarify a few things:

1. there are remnants of a Wubi install; can I assume you used to have Wubi and subsequently uninstalled it?

2. is sdb, the 20GB drive, an external drive or secondary HD?

3. how is BIOS currently set as regards boot device priority?

So, to your original question:

it appears you have 2 Ubuntu installs on sdb; was this planned or done inadvertently?

My suggestion would be to delete one of the installs, freeing up space for the other.

You also need to determine which Ubuntu you installed last and whether it controls the boot process (something else that would be good to tell us before you continue).

As  Hedgehog1 already said, deleting/moving/resizing partitions should be done from the LiveCD.

But, first, before you start please make backups of all important data.

If you want to wait for some other opinions, please feel free.

Thanks.

Rubi1200
thanx for the response. To start, I am very ignorant insofar as LINUX is concerned. I just installed first time in Nov or Dec, using part of a DOS drive for the install. I decided recently to clean all win stuff from sdb  & use whole HD for linux. Then I reinstalled, both times I installed the same version, 10.10 Ubuntu from same CD. 

2.The drive I used /dev/sdb1, is an internal drive. While reinstalling, I selected to partition drive, being used to doing that in windoze. I didn't realize I was going to lose the 2nd partition. 

1. I have no clue as to what WUBI is or does. Don't know if I uninstalled it. 

3. boot priority: cd, floppy, HD, then external HD.

When I boot, the menu has 3 different choices for ubuntu and one for Win XP. two choices for ubuntu on top then win xp and next ubuntuThe first two choices don't work properly so I use the third  prompt: 2.6.35-22 on /dev/sdb1 . Do you need to know what the first two choices say? They are different from last option tho they are both the same.

Seems to me I used to have v. 11 after the first install was updated from v 10.10. I thought when I reinstalled & repartitioned it would delete the first install. I am at a loss. Would I be better to clean the HD & start from scratch. This version I'm using now seems flakey, things keep changing for no reason. i.e. my cursor changes back to normal size, my colors change, the volume control disappeared from top panel. I have no data in this drive to back up as I place all documents on my dos drive. as long as I don't change that I'm cool. 

How can I clean all off the drive and start with a clean install using the entire drive for ubuntu? I have no idea how to remove one version leaving another on drive.:confused:

If I had any hair left, I'd be pulling it out! :P I appreciate the help you guys are giving me. I hope I answered your request properly. If you need more, let me know. 

Thanks loads
Michael

---

### Post by mikeb3809 on 2011-03-25
Having now read some of the exellent info you showed on wubi, I think I can answer your first question. I did originally used the live cd in windows to see what/how ubuntu worked. After using it, I decided to do a permanent install of Ubuntu. I hope this answers your question. I am learning more about various aspects of linux than I ever expected. I guess it helps to not be daring & trying things when you haven't a clue (or in GB clew:P). If i ever had a clue, I seem to have lost it. If you find one, please email it back to me.

BTW, i have bookmarked the exellent info available and will spend some time reading it all. I do need to back up my bookmarks before doing any changing on my system so I don't lose the latest sites I've accumulated.

Thanks again, very, very much! This site is wondermous! & of course it is the people on it who make it so.

Michael :D

PS:  To clarify a little; [COLOR=Red]I think[/COLOR] the first time I installed Ubuntu 10.10, I installed from within win XP. 2nd time I definitely booted on Unix cd & installed from there. Don't know if that matters. Also did sudo fdisk -l and printed results in a txt file. Would it help to post that? Let me know if so.
Michael

More stuff I remembered:
I installed kde on top of gnome. It never worked right so I tried to remove it. Don't know if it worked on the uninstall. Also when I checked with tweak I have 3 different kernels; I have 2.6.35-27; 28; & am currently using 22. I'm afraid to use tweak or synaptic to remove any of those. I'm way over my head, I think.

---

### Post by Hedgehog1 on 2011-03-25
Michael,

Based on what you have installed and un-installed, I wonder if you would be willing to make a clean slate of Ubuntu on the 20 gig drive?

The idea is that you would create a 3 partition install with your data in a partiton for '/home', so future installs/upgrades/reinstalls are less painful?  ***This is a great learning experience. ***

The idea is that would save any data from your Ubuntu install onto another drive (or to a USB stick), and then get a 'do-over', but this time YOU will be in control of the install.

Once you save your data, you would use gparted to remove all the partitions on the 20 gig drive, and then create three new ones.

They would be:

/dev/sdb1 ext4 5 gigs '/'
/dev/sdb2 Linux Swap 2 gigs
/dev/sdb3 ext4 23 gigs (the rest of the drive) '/home'

Here a a picture of the three partitions. They are part of dual boot in these pictures (only set I had on hand), so you need to translate the sda5=sdb1, sda6=sdb2 & sda7=sdb3:

[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]
 
Once your three partitions are laid out, you will start the install and eventually get to this screen:

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

Remeber, you need to translate the sda5=sdb1, sda6=sdb2 & sda7=sdb3. Now you will 'map' the three partitions on /dev/sdb.

First, make /dev/sdb1 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-25
Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

The last partition to setup is the '/home' one:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]

***The Hedge***

:KS

---

### Post by mikeb3809 on 2011-03-26
Thanks, hedge, I'll go ahead and do a clean install of ubuntu, setting up with 3 partitions. Will that small a partition be ok for root? I guess I could get a new HD as inexpensive as they are now. If I install a new drive, will install do the format once I have it partitioned? I can get a 500 gig drive to use just for ubuntu. how large a root partition should I allow? 

You guys are really great for giving this time to us. I have been through a couple of threads so far & will read more once I have this reinstall done. I like the idea of a separate /home partition. I read about that in some other threads & it makes sense to me. I've also visited several web sites recommended by different threads and have bookmarked them.

take care
Michael :-)

---

### Post by Hedgehog1 on 2011-03-26
> **mikeb3809 said:**
> Thanks, hedge, I'll go ahead and do a clean install of ubuntu, setting up with 3 partitions. Will that small a partition be ok for root? I guess I could get a new HD as inexpensive as they are now. If I install a new drive, will install do the format once I have it partitioned? I can get a 500 gig drive to use just for ubuntu. how large a root partition should I allow? 

You guys are really great for giving this time to us. I have been through a couple of threads so far & will read more once I have this reinstall done. I like the idea of a separate /home partition. I read about that in some other threads & it makes sense to me. I've also visited several web sites recommended by different threads and have bookmarked them.

take care
Michael :-)

The 5 gigs are enough, but you can make it a bit larger if you want.  All your documents will be in '/home'.

I expect you will copy & enlarge these partitions on a new drive someday.  We will show you how when you are ready.

***The Hedge***

:KS

---

### Post by mikeb380 on 2011-04-02
Hi hedge

I reinstalled 10.10 & it failed. Then I tried again and again it failed. I followed your advice & did a 5 gig / & a 14 gig /home. I submitted a bug report on this and then I d/l a new ISO, burned a new cd, and reinstalled. This time it went smoothly. Then I partitioned for a 5 gig / & a 14 gig /home. swap took about 2 gig. When I started installing new software, my / partition started filling up and I ended with 0 space left. I couldn't even uninstall to make more rooml meanwhile the /home ended with about 11 gig available. "Methinks, something is fishy in Denmark" to quote the bard, which at this point I hate to need. I received a new 500 gig drive today & had another on hand. Since I have been having problems with Windoze as well as this with Ubuntu, I am going to move Win over to one new drive & use the other to do a clean install of Ubuntu. I d/l a copy of Clonezilla & burned a cd; have you any hints on using this to copy win over to the new drive? I really don't want to reinstall at this point as I have too much software there to have to reinstall that as well as Ubuntu. Is clonezilla a good prog to use, or is there something better/easier? I've never used it before so am uncertain as to how to proceed except I know one has to boot from that cd & go from there.

BTW. it took me three times before I got parted to work properly. Not sure whether it was me or the disk I was using. The last install it went well. As I said before, I would be pulling my hair out if I had any left to pull. :lolflag:

Awaiting your help again, just want to say that I think I would not have dome so well without your help earlier. I want to thank you for the time you took to explain & to build the screen prints you used. You are fantastic!

Thanks so much for what you do.

Michael :):guitar:
I'm told the devil is in the details & I am finding it so, but am enjoying this. I hope all this helps someone else.

M

---

### Post by Hedgehog1 on 2011-04-02
Sorry I didn't see this earlier.  Thought the thread was done!

> ...Since I have been having problems with Windoze as well as this with Ubuntu, I am going to move Win over to one new drive & use the other to do a clean install of Ubuntu...

Issues with windows too?  That is useful info.  Replacing the hard drive with a newer & bigger one seems a reasonable first step.

There are easy and hard ways to copy data from one drive to another.

Easy: **dd** or **ddresue** - these both dupe the smaller drive onto the larger drive.  When done, remove the smaller drive and reboot. Windows is there.  You can extend partitions to fill the extra space.  *However, your current partition layout is duplicated on the new drive.*

Harder: Use Clonezilla to move and reorganize partitions on the new drive.  Make sure you create the MBR partition MAP on the new drive **before** you copy the first partition to it.  Move ONLY the windows partitions and reinstall Ubuntu something like this:

> /dev/sda1 ntfs Windows boot
/dev/sda2 ntfs Windows
/dev/sda3 ntfs Shared data storage for both Windows and Ubuntu
/dev/sda4 Extended Partition
__/dev/sda5 ext4 '/'
__/dev/sda6 ext4 '/home'
__/dev/sda7 Linux Swap

Only the first two partitions are copied from the old drive; the rest are created using Windows Disk Management (If ntfs) or Gparted (if ext4 or Linux Swap).

Set some time aside when you do this - and expect to do it twice to get it right.  *Next time it will go easier*.

***The Hedge***

:KS

---

