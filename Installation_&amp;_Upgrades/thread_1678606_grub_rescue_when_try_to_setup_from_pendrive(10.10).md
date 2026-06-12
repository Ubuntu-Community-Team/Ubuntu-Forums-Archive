---
title: "grub rescue when try to setup from pendrive(10.10)"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by karolykarolykaroly on 2011-01-30
[FONT=Arial][COLOR=Black]I did a boot pendrive with 10.10, but when i try to boot from pendrive, there comes the grub rescue, and i have no idea, what i have to do. Here is my steps to make boot pendrive:
1.make 2 partitions in pendrive: -750 mb, ext2(label: ubuntu1010)  -remains mb(~7gb), ext3(label: casper-rw)
2.make folder for the files and mount the iso:[COLOR=#C20CB9][B][FONT=monospace]
[/FONT][/B][/COLOR][COLOR=#C20CB9]**sudo mkdir **[/COLOR][COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]ubuntu_iso[COLOR=#C20CB9][B][FONT=monospace]
[/FONT]sudo[/B][/COLOR] [COLOR=#C20CB9]**mount**[/COLOR] ubuntu-10[COLOR=#000000].10[/COLOR]-desktop-i386.iso [COLOR=#660033]-o[/COLOR] loop [COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]ubuntu_iso
3.attach the pendrive:[COLOR=#C20CB9][B][FONT=monospace]
[/FONT]sudo[/B][/COLOR] [COLOR=#C20CB9]**mkdir**[/COLOR] [COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]ubunt[/COLOR][/FONT][FONT=Arial][SIZE=2][COLOR=Black]u1010[FONT=monospace]****[/FONT][/COLOR][/SIZE][/FONT][FONT=Arial][COLOR=Black][COLOR=#C20CB9][B][FONT=monospace]
[/FONT]sudo[/B][/COLOR] [COLOR=#C20CB9]**mount**[/COLOR] [COLOR=#660033]-t[/COLOR] ext2 [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]sdb1 [COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]ubuntu1010
4.copy the cd content to pendrive:[COLOR=#C20CB9][B]
sudo[/B][/COLOR] [COLOR=#C20CB9]**cp**[/COLOR] [COLOR=#660033]-rf[/COLOR] [COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]ubuntu_iso[COLOR=#000000]**/***[/COLOR] [COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]ubuntu_iso[COLOR=#000000]**/**[/COLOR].disk [COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]ubuntu1010
5.untar the Super Grub Disk:[COLOR=#C20CB9][B]
tar[/B][/COLOR] xvzf super_grub_disk_english_usb_0.9763.tar.gz
6.this content copy to pendrive:[COLOR=#C20CB9][B]
sudo[/B][/COLOR] [COLOR=#C20CB9]**cp**[/COLOR] [COLOR=#660033]-r[/COLOR] boot [COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]ubuntu1010[COLOR=#000000]**/**[/COLOR]
7.setup the SGD to pendrive's MBR:[COLOR=#C20CB9][B]
sudo[/B][/COLOR] grub[COLOR=#C20CB9][B]
 >find[/B][/COLOR] [COLOR=#000000]**/**[/COLOR]boot[COLOR=#000000]**/**[/COLOR]grub[COLOR=#000000]**/**[/COLOR]menu.lst
 >root (hd1,0)
 >makeactive
 >setup (hd1,0)
 >quit
8.change the text in this folder: [COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]ubuntu1010[COLOR=#000000]**/**[/COLOR]boot[COLOR=#000000]**/**[/COLOR]grub[COLOR=#000000]**/**[/COLOR]menu.lst to this:
[/COLOR][/FONT][INDENT][FONT=Arial][COLOR=Black]# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#Thank you adrian15!
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
usbshift[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]default 0
#timeout 2
setgrubdevice # This is compulsory
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
#gfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title       Ubuntu Gutsy Gibbon in Persistent Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash –
initrd    $(grub_device)/casper/initrd.gz[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title       Super Grub Disk
configfile $(grub_device)/boot/sgd/menu.lst[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title      Ubuntu Gutsy Gibbon in Live CD Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash –
initrd   $(grub_device)/casper/initrd.gz[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title       Start Ubuntu in Safe Graphics Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper xforcevesa quiet splash –
initrd    $(grub_device)/casper/initrd.gz[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title        Install with Driver Update CD
kernel    $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed  boot=casper debian-installer/driver-update=true quiet splash –
initrd     $(grub_device)/casper/initrd.gz[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title        OEM Ubuntu Gutsy Gibbon Install (for manufacturers)
kernel    $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper oem-config/enable=true quiet splash –
initrd     $(grub_device)/casper/initrd.gz[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title        Check CD for Defects
kernel    $(grub_device)/casper/vmlinuz boot=casper integrity-check quiet splash –
initrd      $(grub_device)/casper/initrd.gz[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title        Memory Test
kernel    $(grub_device)/install/mt86plus  -[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title       Boot the First Hard Disk
root       (hd0)
chainloader +1[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title       Boot the Second Hard Disk
root      (hd1)
chainloader +1[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title Inicio normal / Normal Boot
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initramfs[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title Soporte de accesibilidad / Accesibility Support –>
configfile $(grub_device)/boot/grub/menu2.lst[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title Normal boot. Kernel is aware of Boot device
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0  ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash  boot_device=$(grub_device)
initrd $(grub_device)/initramfs[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title Normal boot. Selecting kernel and initrd files depending on grub_device
kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none  root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live  splash
initrd $(grub_device)/initramfs_$(grub_device_string)[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title Selecthd test
configfile $(grub_device)/boot/grub/choose/selecthd.lst[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title findp test
configfile $(grub_device)/boot/grub/choose/selectpart.lst[/COLOR][/FONT]
 [FONT=Arial][COLOR=Black]title set SGD variables and boot SGD
configfile $(grub_device)/boot/sgd/menu.lst[/COLOR][/FONT]
[/INDENT]sorry for the long thread

---

### Post by karolykarolykaroly on 2011-01-31
Boot info results:

              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

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

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97-os.1 is installed in the boot sector of sdb1 
                       and looks at sector 315743 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

/dev/sda lemez: 80.0 GB, 80026361856 bájt
255 fej, 63 szektor, 9729 cilinder, összesen 156301488 szektor
Egység: szektorok 1 * 512 = 512 bájt
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   150,159,359   150,157,312  83 Linux
/dev/sda2         150,161,406   156,301,311     6,139,906   5 Extended
/dev/sda5         150,161,408   156,301,311     6,139,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

/dev/sdb lemez: 8019 MB, 8019509248) bájt
255 fej, 63 szektor, 974 cilinder, összesen 15663104 szektor
Egység: szektorok 1 * 512 = 512 bájt
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,542,239     1,542,177  83 Linux
/dev/sdb2           1,542,240    15,647,309    14,105,070  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        246cee58-4056-4c54-be59-5d4887644b7b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3e133eee-7c60-4cdb-9321-e49068f0f06f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        081fea60-e640-4d43-9881-09c0a3e50ac0   ext2       ubuntu1010                    
/dev/sdb2        7d144a49-b9c4-4a8d-888a-aed1cb05df07   ext3       casper-rw                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/ubuntu1010_       ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb2        /media/casper-rw         ext3       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
set locale_dir=($root)/boot/grub/locale
set lang=hu
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=246cee58-4056-4c54-be59-5d4887644b7b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=246cee58-4056-4c54-be59-5d4887644b7b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=246cee58-4056-4c54-be59-5d4887644b7b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=246cee58-4056-4c54-be59-5d4887644b7b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=246cee58-4056-4c54-be59-5d4887644b7b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=246cee58-4056-4c54-be59-5d4887644b7b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=246cee58-4056-4c54-be59-5d4887644b7b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=246cee58-4056-4c54-be59-5d4887644b7b ro single 
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
    search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 246cee58-4056-4c54-be59-5d4887644b7b
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3e133eee-7c60-4cdb-9321-e49068f0f06f none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  43.1GB: boot/grub/core.img
  43.6GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.35-22-generic
   9.3GB: boot/initrd.img-2.6.35-23-generic
    .4GB: boot/initrd.img-2.6.35-24-generic
  57.3GB: boot/initrd.img-2.6.35-25-generic
  43.2GB: boot/vmlinuz-2.6.35-22-generic
  43.2GB: boot/vmlinuz-2.6.35-23-generic
  43.8GB: boot/vmlinuz-2.6.35-24-generic
  43.7GB: boot/vmlinuz-2.6.35-25-generic
  57.3GB: initrd.img
    .4GB: initrd.img.old
  43.7GB: vmlinuz
  43.8GB: vmlinuz.old

=========================== sdb1/boot/grub/menu.lst: ===========================

    # You can edit this file to add your own distribution
    # You can choose default to 0 to select first entry
    # which it is usually the entry for the default distro
    #
    #Thank you adrian15!
    #
    # You can also set timeout to something as 10
    #
    # This is the shortcut to call Super Grub Disk (commented)
    #title Super Grub Disk
    ## The two commands: setgrubdevice and usbshift are needed
    ## so that SGD works well.
    usbshift

    #configfile $(grub_device)/boot/sgd/menu.lst
    #
    # Just after default and timeout statements you have to put
    # setgrubdevice so that grub device is correctly set.

    default 0
    #timeout 2
    setgrubdevice # This is compulsory
    # The two commands: setgrubdevice and usbshift are needed
    # so that SGD works well.
    usbshift
    #gfxmenu /boot/grub/message
    foreground ffffff
    background 0c00ff
    color white/brown yellow/cyan

    title Ubuntu Gutsy Gibbon in Persistent Mode
    kernel $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash –
    initrd $(grub_device)/casper/initrd.gz

    title Super Grub Disk
    configfile $(grub_device)/boot/sgd/menu.lst

    title Ubuntu Gutsy Gibbon in Live CD Mode
    kernel $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash –
    initrd $(grub_device)/casper/initrd.gz

    title Start Ubuntu in Safe Graphics Mode
    kernel $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper xforcevesa quiet splash –
    initrd $(grub_device)/casper/initrd.gz

    title Install with Driver Update CD
    kernel $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true quiet splash –
    initrd $(grub_device)/casper/initrd.gz

    title OEM Ubuntu Gutsy Gibbon Install (for manufacturers)
    kernel $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper oem-config/enable=true quiet splash –
    initrd $(grub_device)/casper/initrd.gz

    title Check CD for Defects
    kernel $(grub_device)/casper/vmlinuz boot=casper integrity-check quiet splash –
    initrd $(grub_device)/casper/initrd.gz

    title Memory Test
    kernel $(grub_device)/install/mt86plus -

    title Boot the First Hard Disk
    root (hd0)
    chainloader +1

    title Boot the Second Hard Disk
    root (hd1)
    chainloader +1

    title Inicio normal / Normal Boot
    kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
    initrd $(grub_device)/initramfs

    title Soporte de accesibilidad / Accesibility Support –>
    configfile $(grub_device)/boot/grub/menu2.lst

    title Normal boot. Kernel is aware of Boot device
    kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
    initrd $(grub_device)/initramfs

    title Normal boot. Selecting kernel and initrd files depending on grub_device
    kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
    initrd $(grub_device)/initramfs_$(grub_device_string)

    title Selecthd test
    configfile $(grub_device)/boot/grub/choose/selecthd.lst

    title findp test
    configfile $(grub_device)/boot/grub/choose/selectpart.lst

    title set SGD variables and boot SGD
    configfile $(grub_device)/boot/sgd/menu.lst

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2

---

