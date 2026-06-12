---
title: "Double boot required to get to current grub"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by scyntax on 2010-05-08
When I boot my machine up, I first get the legacy grub, ver 1.97 beta,  that points to 9.10. I then have to shutdown and reboot. The second time  I do this, I get the grub I want, ver 1.98, which points to ver 10.4 of  ubuntu. I have to boot twice every time in order to get to the correct  grub. 10.4 lives on an external USB drive while 9.10 lives on the  internal drive. My hardware: Dell Inspiron e1505 with 2gb ram, internal  100gb sata drive and 120gb external USB drive. I realize the info below  is a lot of data to sift through, but I am hoping someone far smarter  than I am will be able to see where I am going wrong. Thank you very much for looking. Here are the results of boot script:
```

  

                Boot Info Script 0.55    dated February 15th, 2010                     

============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same  drive in 
    partition #7 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same  drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1  and 
                       looks at sector 272831 of the same hard drive for  
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter  Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________   _______________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________   _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sda6: __________________________________________________   _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________   _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sda8: __________________________________________________   _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________   _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sdb2: __________________________________________________   _______________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________   _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________   _______________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  __________________________________________________  ___

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   116,872,874   116,872,812   7 HPFS/NTFS
/dev/sda2         116,872,875   195,366,464    78,493,590   5 Extended
/dev/sda5         142,609,068   193,085,234    50,476,167  83 Linux
/dev/sda6         193,085,298   195,366,464     2,281,167  82 Linux swap  / Solaris
/dev/sda7         116,873,001   141,420,194    24,547,194  83 Linux
/dev/sda8         141,420,258   142,609,004     1,188,747  82 Linux swap  / Solaris


Drive: sdb ___________________  __________________________________________________  ___

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   224,761,855   224,759,808  83 Linux
/dev/sdb2         224,763,902   234,373,119     9,609,218   5 Extended
/dev/sdb5         224,763,904   234,373,119     9,609,216  82 Linux swap  / Solaris


Drive: sdc ___________________  __________________________________________________  ___

Disk /dev/sdc: 128 MB, 128188416 bytes
8 heads, 32 sectors/track, 978 cylinders, total 250368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32       250,367       250,336   6 FAT16


blkid -c /dev/null: __________________________________________________   __________

Device           UUID                                   TYPE       LABEL                          

/dev/sda1        4A6C77D56C77BA71                       ntfs                                      
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9dd5025e-3a64-406b-9e33-6674096d0193   ext4                                      
/dev/sda6        a4b491d6-85db-4492-99cb-b2101b1f6dfb   swap                                      
/dev/sda7        18dabb63-849d-4283-bbaf-5ebe18f4415e   ext4                                      
/dev/sda8        49493dfc-270b-4557-8201-35d701cd80e2   swap                                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c9a3959e-7aaf-47e0-962f-a43a50158da2   ext4                                      
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        1e28a480-da2e-46b1-b90c-5b96927e2170   swap                                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F0CC-3E36                              vfat       STI                            
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4        (rw,errors=remount-ro)
/dev/sdc1        /media/STI               vfat        (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,   shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/4A6C77D56C77BA71  fuseblk     (rw,nosuid,nodev,allow_other,blksize=4096,default_  permissions)


================================ sda1/boot.ini:  ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW  S 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro  soft Windows XP  Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 9dd5025e-3a64-406b-9e33-6674096d0193
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
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
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux    /boot/vmlinuz-2.6.31-21-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux    /boot/vmlinuz-2.6.31-21-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux    /boot/vmlinuz-2.6.31-20-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux    /boot/vmlinuz-2.6.31-20-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux    /boot/vmlinuz-2.6.31-16-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux    /boot/vmlinuz-2.6.31-16-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux    /boot/vmlinuz-2.6.31-15-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux    /boot/vmlinuz-2.6.31-15-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4a6c77d56c77ba71
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb2)" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 1e8cf4b88cf48c11
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9dd5025e-3a64-406b-9e33-6674096d0193 /               ext4     errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a4b491d6-85db-4492-99cb-b2101b1f6dfb none            swap    sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0        0

=================== sda5: Location of files loaded by Grub:  ===================


  85.7GB: boot/grub/core.img
  78.2GB: boot/grub/grub.cfg
  73.2GB: boot/initrd.img-2.6.31-14-generic
  73.2GB: boot/initrd.img-2.6.31-15-generic
  86.2GB: boot/initrd.img-2.6.31-16-generic
  87.2GB: boot/initrd.img-2.6.31-20-generic
  88.1GB: boot/initrd.img-2.6.31-21-generic
  73.2GB: boot/vmlinuz-2.6.31-14-generic
  73.2GB: boot/vmlinuz-2.6.31-15-generic
  73.8GB: boot/vmlinuz-2.6.31-16-generic
  78.6GB: boot/vmlinuz-2.6.31-20-generic
  88.1GB: boot/vmlinuz-2.6.31-21-generic
  88.1GB: initrd.img
  87.2GB: initrd.img.old
  88.1GB: vmlinuz
  78.6GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 18dabb63-849d-4283-bbaf-5ebe18f4415e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set  18dabb63-849d-4283-bbaf-5ebe18f4415e
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=18dabb63-849d-4283-bbaf-5ebe18f4415e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set  18dabb63-849d-4283-bbaf-5ebe18f4415e
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=18dabb63-849d-4283-bbaf-5ebe18f4415e ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4a6c77d56c77ba71
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-21-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792 quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode) (on  /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-21-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-20-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792 quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on  /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-20-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-16-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792 quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on  /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-16-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-15-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792 quiet splash
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on  /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-15-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792 quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on  /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=18dabb63-849d-4283-bbaf-5ebe18f4415e /               ext4     errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=49493dfc-270b-4557-8201-35d701cd80e2 none            swap    sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0        0

=================== sda7: Location of files loaded by Grub:  ===================


  68.7GB: boot/grub/core.img
  68.7GB: boot/grub/grub.cfg
  60.6GB: boot/initrd.img-2.6.31-14-generic
  62.2GB: boot/vmlinuz-2.6.31-14-generic
  60.6GB: initrd.img
  62.2GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env  recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c9a3959e-7aaf-47e0-962f-a43a50158da2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c9a3959e-7aaf-47e0-962f-a43a50158da2
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set  c9a3959e-7aaf-47e0-962f-a43a50158da2
    linux    /boot/vmlinuz-2.6.32-22-generic  root=UUID=c9a3959e-7aaf-47e0-962f-a43a50158da2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set  c9a3959e-7aaf-47e0-962f-a43a50158da2
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic  root=UUID=c9a3959e-7aaf-47e0-962f-a43a50158da2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set  c9a3959e-7aaf-47e0-962f-a43a50158da2
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=c9a3959e-7aaf-47e0-962f-a43a50158da2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set  c9a3959e-7aaf-47e0-962f-a43a50158da2
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=c9a3959e-7aaf-47e0-962f-a43a50158da2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set  c9a3959e-7aaf-47e0-962f-a43a50158da2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set  c9a3959e-7aaf-47e0-962f-a43a50158da2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4a6c77d56c77ba71
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-21-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792 quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode) (on  /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-21-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-20-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792 quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on  /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-20-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-16-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792 quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on  /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-16-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-15-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792 quiet splash
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on  /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-15-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro vga=792 quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on  /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  9dd5025e-3a64-406b-9e33-6674096d0193
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=9dd5025e-3a64-406b-9e33-6674096d0193 ro single vga=792
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set  18dabb63-849d-4283-bbaf-5ebe18f4415e
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=18dabb63-849d-4283-bbaf-5ebe18f4415e ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on  /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set  18dabb63-849d-4283-bbaf-5ebe18f4415e
    linux /boot/vmlinuz-2.6.31-14-generic  root=UUID=18dabb63-849d-4283-bbaf-5ebe18f4415e ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=c9a3959e-7aaf-47e0-962f-a43a50158da2 /               ext4     errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1e28a480-da2e-46b1-b90c-5b96927e2170 none            swap    sw               0       0

=================== sdb1: Location of files loaded by Grub:  ===================


  17.3GB: boot/grub/core.img
  47.8GB: boot/grub/grub.cfg
  17.3GB: boot/initrd.img-2.6.32-21-generic
  17.3GB: boot/initrd.img-2.6.32-22-generic
  17.3GB: boot/vmlinuz-2.6.32-21-generic
  17.3GB: boot/vmlinuz-2.6.32-22-generic
  17.3GB: initrd.img
  17.3GB: initrd.img.old
  17.3GB: vmlinuz
  17.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc  =======================

Unknown BootLoader  on sdb2

00000000  41 90 b9 5f 50 90 b9 5f  98 cb b9 5f 05 90 b9 5f   |A.._P.._..._..._|
00000010  14 90 b9 5f 23 90 b9 5f  3f cb b9 5f 5e cb b9 5f   |..._#.._?.._^.._|
00000020  7b cb b9 5f d8 8f b9 5f  e7 8f b9 5f f6 8f b9 5f   |{.._..._..._..._|
00000030  28 cb b9 5f 0a cc b9 5f  d0 e4 b9 5f 50 cc b9 5f   |(.._..._..._P.._|
00000040  a1 c8 b9 5f b5 c9 b9 5f  d2 c9 b9 5f d1 d3 b9 5f   |..._..._..._..._|
00000050  39 ca b9 5f 6f ca b9 5f  8f ca b9 5f fa ca b9 5f   |9.._o.._..._..._|
00000060  43 58 61 53 79 6e 63 68  00 90 90 90 3d ae b9 5f   |CXaSynch....=.._|
00000070  52 9b b9 5f 62 ae b9 5f  7c ae b9 5f f5 9d b9 5f   |R.._b.._|.._..._|
00000080  1d 9e b9 5f 09 9e b9 5f  f1 9b b9 5f 3a 9c b9 5f   |..._..._..._:.._|
00000090  a0 bb b9 5f c4 9d b9 5f  b4 bd b9 5f e1 9d b9 5f   |..._..._..._..._|
000000a0  ec a4 b9 5f 14 a5 b9 5f  00 a5 b9 5f ce bb b9 5f   |..._..._..._..._|
000000b0  84 a3 b9 5f 6a a3 b9 5f  de b2 b9 5f d9 ab b9 5f   |..._j.._..._..._|
000000c0  e8 ab b9 5f f7 ab b9 5f  f5 ce b4 5f 9c a4 b9 5f   |..._..._..._..._|
000000d0  7e a4 b9 5f 9e a3 b9 5f  0a a4 b9 5f 27 a4 b9 5f   |~.._..._..._'.._|
000000e0  5f a4 b9 5f 05 f1 b7 5f  05 f1 b7 5f 64 3a 5c 71   |_.._..._..._d:\q|
000000f0  78 70 5f 73 6c 70 5c 63  6f 6d 5c 63 6f 6d 31 78   |xp_slp\com\com1x|
00000100  5c 64 74 63 5c 64 74 63  5c 78 61 74 6d 5c 73 72   |\dtc\dtc\xatm\sr|
00000110  63 5c 78 61 72 6d 63 6f  6e 6e 2e 63 70 70 00 90   |c\xarmconn.cpp..|
00000120  43 58 61 52 6d 43 6f 6e  6e 5f 53 74 61 74 65 2f   |CXaRmConn_State/|
00000130  45 6e 74 65 72 5f 53 74  61 74 65 20 45 76 65 6e  |Enter_State  Even|
00000140  74 00 90 90 fa 95 be 3b  3f c5 d1 11 b3 a2 00 a0   |t......;?.......|
00000150  c9 08 33 65 f9 95 be 3b  3f c5 d1 11 b3 a2 00 a0   |..3e...;?.......|
00000160  c9 08 33 65 b2 ab b9 5f  d4 8c bc 5f 81 37 bc 5f   |..3e..._..._.7._|
00000170  7c ac b9 5f 97 ac b9 5f  c4 ac b9 5f 43 4f 70 65   ||.._..._..._COpe|
00000180  6e 54 61 73 6b 00 90 90  d7 c1 b9 5f 0a bc b9 5f   |nTask......_..._|
00000190  fc c1 b9 5f 16 c2 b9 5f  09 9e b9 5f d1 bd b9 5f   |..._..._..._..._|
000001a0  f2 bd b9 5f 65 bc b9 5f  b3 bc b9 5f 2d c6 b9 5f   |..._e.._..._-.._|
000001b0  b4 bd b9 5f 64 3a 5c 71  78 70 5f 73 6c 70 00 fe   |..._d:\qxp_slp..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a0 92 00 00 00   |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa   |..............U.|
00000200
```

---

### Post by frantid on 2010-05-08
scyntax,

thankyou for starting a new thread.

I think the best bet would just be to update your grub so that you still keep two copies.  That way if you ever boot without the external drive connected you won't get a grub error.

To make this easier so you don't have to double boot.  What you need to do is update the grub on your internal drive.  So boot off of your grub 1.97, get into Karmic and do:

sudo update-grub

this should put an entry in the grub lower in the menu, you will have to scroll down to see it.  Then you will be able to boot lucid directly without another reboot.

If you want something else or just will always have your external, let me know and we can do that too.

---

### Post by frantid on 2010-05-08
There are also tweaks we can do too remove some of the menu entries so you don't have to scroll so much.

---

### Post by oldfred on 2010-05-08
You have not said you cannot boot window (yet) but you have grub installed to the windows partition:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use windows cd/dvd to repair with fixboot command. Instructions are slightly different for XP and vista/7 but you want to get into the repair console and go to command line. If you also run fixmbr you will be able to directly boot windows, but will have to reinstall grub or grub2 to the MBR or drives Master Boot Record to boot Ubuntu.

XP:
FIXBOOT C:

Vista/7
BootRec.exe /FixBoot #updates PBR or partition boot sector

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

And you are missing the boot flag on sda1. 
You can use gparted or disk utility to set boot flag on the windows partition sda1.

set boot flag on for sda1 (off on others)
sudo sfdisk -A1 /dev/sda

-

---

### Post by scyntax on 2010-05-08
I am going to update the internal hdd grub as you suggest. I will always have the external USB attached since that is where 10.4 lives. I would also appreciate it if you would let me know how to eliminate some of the grub entries. Not sure why there are so many, but I would like get rid of some of them and also would like the option to boot into 10.4 as the first and automatic entry in grub. Thank you again for your help as I am a recent Linux convert and am still shaking a life-long attachment to Windows since the early days of DOS and internet access using Unix commands!

---

### Post by kansasnoob on 2010-05-08
**[COLOR="Red"]I didn't realize the Lucid drive was external! Listen to OldFred![/COLOR]**

One very obvious problem, you have grub2 installed to the Win XP partition:

> sda1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  **[COLOR="Red"]Grub 2[/COLOR]**
    Boot sector info:  [B][COLOR="Red"]Grub 2 is installed in the boot sector of sda1  and 
                       looks at sector 272831 of the same hard drive for  
                       core.img, but core.img can not be found at this 
                       location.[/COLOR][/B] No errors found in the Boot Parameter  Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

The fix for that is well explained here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

The other thing is you have two Karmics (nothing wrong with that) on sda5 and sda7, then you have Lucid on sdb1. I've done a lot of grub2 testing and Lucid's grub2 is far superior to Karmic's!

So IMO I'd hand boot off to Lucid by booting into it and first checking to be sure you're where you want to be with:

```
df
```

That will only show you what partition(s) are mounted, example:

```
lance@lance-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
**[COLOR="Red"]/dev/sda2[/COLOR]**              8649576   3439288   4770912  42% /
none                   1021800       348   1021452   1% /dev
none                   1026016       332   1025684   1% /dev/shm
none                   1026016        92   1025924   1% /var/run
none                   1026016         0   1026016   0% /var/lock
none                   1026016         0   1026016   0% /lib/init/rw
/dev/sda5              4617268    419124   3963604  10% /home

```

You can see there that /dev/sda2 is mounted, you want to be sure **/dev/sdb1** is mounted! As a double check you could run:

```
lsb_release -a
```

That should show you've mounted Ubuntu 10.04 LTS, if so just run:

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdb
```

```
sudo update-grub
```

Note: if either of the grub install commands returns errors use the command:

```
sudo grub-install --recheck /dev/sd**[COLOR="Red"]X[/COLOR]**
```

Of course replace the **[COLOR="Red"]X[/COLOR]** with the proper drive designation, eg: "a" or "b".

---

### Post by kansasnoob on 2010-05-08
> **oldfred said:**
> You have not said you cannot boot window (yet) but you have grub installed to the windows partition:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use windows cd/dvd to repair with fixboot command. Instructions are slightly different for XP and vista/7 but you want to get into the repair console and go to command line. If you also run fixmbr you will be able to directly boot windows, but will have to reinstall grub or grub2 to the MBR or drives Master Boot Record to boot Ubuntu.

XP:
FIXBOOT C:

Vista/7
BootRec.exe /FixBoot #updates PBR or partition boot sector

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

And you are missing the boot flag on sda1. 
You can use gparted or disk utility to set boot flag on the windows partition sda1.

set boot flag on for sda1 (off on others)
sudo sfdisk -A1 /dev/sda

-

Glad to see you :)

I'm obviously getting too tired, time for a break.

---

### Post by frantid on 2010-05-08
Hi oldfred and kansasnoob, I agree still need to fix xp.  I was just going after the grub side first.

---

### Post by frantid on 2010-05-08
scyntax,  here are the tweaks I was talking about.

I usually do #2 on this [list]("http://art.ubuntuforums.org/showthread.php?t=1287602") to limit kernel listings to just the last two.  The proper way would be to remove the kernels through synaptic.  I have the disk space so I don't mind the kernels being there, I just don't want to see them.  

I also turn off memtest and recovery mode as specified in the "Before you start" section, reduces clutter.  Those options can still be run, you will just have to enter the commands by hand -- it's not as hard as it sounds see here for illustrated [examples]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html"):

---

### Post by scyntax on 2010-05-09
The grub update worked as shown by kansasnoob. I know have only the latest grub and no longer have to double boot. Thanks to you and frantid for your generous help.

---

### Post by kansasnoob on 2010-05-10
> **scyntax said:**
> The grub update worked as shown by kansasnoob. I know have only the latest grub and no longer have to double boot. Thanks to you and frantid for your generous help.

Please post back again if you have any more problems.

---

