---
title: "I'm sure the answer is here somewhere, but..."
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by subtle1976 on 2010-05-10
...I have no idea what everyone is talking about. I know that sounds ridiculous, but, being a novice user Ubuntu-speak makes my brain start sizzling. I've tried finding a Lonely Planet Ubuntu-ese Phrase Book, but there doesn't appear to be any on the market - perhaps the travel opportunities are even more limited than Aramaic.

Like many updaters on these pages, I have made the perhaps unwise move to Ubuntu 10.04 from 9.10. All went swimmingly until the Grub loader stopped and a command line for Grub rescue came up, telling me something was wrong with my pots. Now, my wife wants me to pot some basil we have in the garden and I initially went out to have a look whether our pots were broken, but then I realised - how could a *computer* know about my garden? Obviously it couldn't, so I knew something else was afoot. 

For the last three hours, I have been baffled by talk of Gnomes, Grubs, MBRs, SDAs and such. Please, can someone help in plain English? If necessary, I'll even take basic French (I've just learned all about the names of different cheeses in class - perhaps if the person who helps uses roquefort as a metaphor it might help.)

Here's what I can tell you: I'm running (or was running...) a dual boot configuration with OS X Tiger on one and Ubuntu 9.10 on the other. This morning I used the upgrade software option from 9.10 to upgrade to 10.04. When it asked me to indicate where to place Grub, I thought (foolishly as it turns out) that it should go into the same partition as 10.04, which is designated sda4. 

When I re-started, I got the aforementioned Grub/pots issue. From boot info script I was able to gain the following: 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 156438400 
    of the same hard drive for core.img, core.img is at this location on 
    /dev/sda and looks on partition #4 for /boot/grub.
 => Grub 0.97-os.1 is installed in the MBR of /dev/sdb and looks on the same 
    drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Grub 2's core.img
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 156718242 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2    *        409,640   156,438,399   156,028,760  af HFS
/dev/sda3         156,438,400   156,440,353         1,954  ef EFI (FAT-12/16/32)
/dev/sda4         156,440,354   306,750,900   150,310,547  83 Linux


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   156,438,399   156,028,760 HFS+
/dev/sda3     156,438,400   156,440,353         1,954 Bios Boot Partition
/dev/sda4     156,440,354   306,750,900   150,310,547 Linux or Data
/dev/sda5     306,750,901   312,581,774     5,830,874 Linux Swap

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,333,394     1,333,332   c W95 FAT32 (LBA)
/dev/sdb2           1,333,395     7,823,654     6,490,260   5 Extended
/dev/sdb5           1,333,458     7,422,029     6,088,572  83 Linux
/dev/sdb6           7,422,093     7,823,654       401,562  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3991-1105                              vfat       EFI                           
/dev/sda2        d6432769-b435-3d32-ac38-d9f22647fdb2   hfsplus    Mac OS X                      
/dev/sda4        dd2fe246-01bb-4bc7-b059-554091c62855   ext4                                     
/dev/sda5        7ae11f6c-8f68-45e6-9861-c3b9dc02311f   swap                                     
/dev/sdb1        B3DC-85AC                              vfat       Lexar                         
/dev/sdb5        9c85ee03-c258-428a-b36a-a029d93ce548   ext4                                     
/dev/sdb6        055438a9-4ad4-4da2-adaf-7e3fa64a66d4   swap                                     
/dev/sdc         EC5B-7856                              vfat       LEXAR                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc         /media/LEXAR             vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set dd2fe246-01bb-4bc7-b059-554091c62855
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
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set dd2fe246-01bb-4bc7-b059-554091c62855
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set dd2fe246-01bb-4bc7-b059-554091c62855
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=dd2fe246-01bb-4bc7-b059-554091c62855 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set dd2fe246-01bb-4bc7-b059-554091c62855
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=dd2fe246-01bb-4bc7-b059-554091c62855 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set dd2fe246-01bb-4bc7-b059-554091c62855
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=dd2fe246-01bb-4bc7-b059-554091c62855 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set dd2fe246-01bb-4bc7-b059-554091c62855
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=dd2fe246-01bb-4bc7-b059-554091c62855 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set dd2fe246-01bb-4bc7-b059-554091c62855
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set dd2fe246-01bb-4bc7-b059-554091c62855
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1883c7cdb7ef2586
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 1883c7cdb7ef2586 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1883c7cdb7ef2586
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 1883c7cdb7ef2586 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=dd2fe246-01bb-4bc7-b059-554091c62855 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7ae11f6c-8f68-45e6-9861-c3b9dc02311f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


  80.2GB: boot/grub/core.img
  80.3GB: boot/grub/grub.cfg
  87.6GB: boot/initrd.img-2.6.31-21-generic
  88.7GB: boot/initrd.img-2.6.32-22-generic
  81.6GB: boot/vmlinuz-2.6.31-21-generic
  87.6GB: boot/vmlinuz-2.6.32-22-generic
  88.7GB: initrd.img
  87.6GB: initrd.img.old
  87.6GB: vmlinuz
  81.6GB: vmlinuz.old

=========================== sdb1/boot/grub/menu.lst: ===========================

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 0
timeout 2
setgrubdevice # This is compulsory
#sgdgfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan


#title Inicio normal / Normal Boot 
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs

#title Soporte de accesibilidad / Accesibility Support -->
#configfile $(grub_device)/boot/grub/menu2.lst

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/sgd.lst

#title Normal boot. Kernel is aware of Boot device
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
#initrd $(grub_device)/initramfs

#title Normal boot. Selecting kernel and initrd files depending on grub_device
#kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs_$(grub_device_string)

#title Selecthd test
#configfile $(grub_device)/boot/grub/choose/selecthd.lst

#title findp test
#configfile $(grub_device)/boot/grub/choose/selectpart.lst
#title set SGD variables and boot SGD
#
#configfile $(grub_device)/boot/sgd/menu.lst

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set 9c85ee03-c258-428a-b36a-a029d93ce548
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 9c85ee03-c258-428a-b36a-a029d93ce548
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9c85ee03-c258-428a-b36a-a029d93ce548 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 9c85ee03-c258-428a-b36a-a029d93ce548
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9c85ee03-c258-428a-b36a-a029d93ce548 ro single 
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
menuentry "Mac OS X (on /dev/sda2)" {
    insmod hfsplus
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set c0ef3056154540e0
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid c0ef3056154540e0 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=9c85ee03-c258-428a-b36a-a029d93ce548 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=055438a9-4ad4-4da2-adaf-7e3fa64a66d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


   3.0GB: boot/grub/core.img
   3.0GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.31-14-generic
   3.1GB: boot/vmlinuz-2.6.31-14-generic
   1.5GB: initrd.img
   3.1GB: vmlinuz
All of your kind help and patience is appreciated. Now, to that basil...

---

### Post by subtle1976 on 2010-05-10
Alright, everybody. Relax. All solved. Pots all back in the garden.

---

