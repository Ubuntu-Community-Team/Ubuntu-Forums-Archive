---
title: "Dual boot won't boot after flash key installation"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by Fran7842 on 2010-12-10
I have an approximately eight-year-old HP Pavilion 061 with 2 gigabytes of RAM, a DVD-burner and CD-ROM drive, and Windows 7 Home Premium. It has a 160 GB hard drive installed: Windows 7 takes up 100 GB, a factory settings recovery partition (which will restore the computer to its original Windows XP Home edition) takes up about 8 GB.  An installation of Ubuntu 10.04 Lucid Lynx LTS takes up about 40 GB.
 
The computer was working fine until today.  I inserted a USB key, booted into my 10.04 CD-ROM, and installed Ubuntu onto my 32 GB USB flash key.  It worked fine, until I attempted to re boot.  It could not boot from the flash key.  When removing the flash key, I get an error that a device with a string of random looking digits cannot be found followed by the Grub Error console command line.

OS Name Microsoft Windows 7 Home Premium
Version 6.1.7600 Build 7600
Other OS Description Not Available
OS Manufacturer Microsoft Corporation
System Name J_MAC7
System Manufacturer HP Pavilion 061
System Model PS563AA-ABA a1010n
System Type X86-based PC
Processor Intel(R) Celeron(R) CPU 2.93GHz, 2933 Mhz, 1 Core(s), 1 Logical Processor(s)
BIOS Version/Date Phoenix Technologies, LTD 3.05, 3/9/2005
SMBIOS Version 2.4
Windows Directory C:\Windows
System Directory C:\Windows\system32
Boot Device \Device\HarddiskVolume1
Locale United States
Hardware Abstraction Layer Version = "6.1.7600.16385"
User Name J_Mac7\John
Time Zone Eastern Daylight Time
Installed Physical Memory (RAM) 2.00 GB
Total Physical Memory 1.99 GB
Available Physical Memory 1.17 GB
Total Virtual Memory 2.99 GB
Available Virtual Memory 1.97 GB
Page File Space 1.00 GB
Page File C:\pagefile.sys

---

### Post by Rubi1200 on 2010-12-10
Hi and welcome to the forums :)

Please use a LiveCD/USB to boot the laptop and choose to try not install Ubuntu.

From the live desktop, post the results of the boot info script linked at the bottom of my post.

Thanks.

---

### Post by Fran7842 on 2010-12-10
Thanks for the help.  Below are the results of the file:

Would it help you to know that, when I installed ubuntu on the flash drive, I set the option to require a passphrase to log on and decrypt my home folder?


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    15,951,599    15,951,537   c W95 FAT32 (LBA)
/dev/sda2          15,951,661   312,576,704   296,625,044   f W95 Ext d (LBA)
/dev/sda5          15,951,663   226,123,692   210,172,030   7 HPFS/NTFS
/dev/sda6         226,131,003   312,576,704    86,445,702  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 32.1 GB, 32078036992 bytes
255 heads, 63 sectors/track, 3899 cylinders, total 62652416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1               2,048    59,979,775    59,977,728  83 Linux
/dev/sdf2          59,981,822    62,650,367     2,668,546   5 Extended
/dev/sdf5          59,981,824    62,650,367     2,668,544  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7270-48C2                              vfat       HP_RECOVERY                   
/dev/sda2: PTTYPE="dos" 
/dev/sda5        50588C00588BE2D8                       ntfs                                     
/dev/sda6        2806ba1a-4a4a-424e-ad95-60f67823bf66   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        1f64827d-b4a9-4e87-8669-67afb3ca2926   ext4                                     
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        9dadc0ff-4fda-484d-9607-7e309faa472b   swap                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/1f64827d-b4a9-4e87-8669-67afb3ca2926 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7270-48c2
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1

=================== sda6: Location of files loaded by Grub: ===================


 143.8GB: boot/grub/core.img
 118.3GB: boot/grub/grub.cfg
 115.9GB: boot/initrd.img-2.6.32-21-generic
 143.9GB: boot/initrd.img-2.6.32-23-generic
 144.0GB: boot/initrd.img-2.6.32-24-generic
 144.0GB: boot/initrd.img-2.6.32-25-generic
 143.9GB: boot/initrd.img-2.6.32-26-generic
 143.8GB: boot/vmlinuz-2.6.32-21-generic
 143.9GB: boot/vmlinuz-2.6.32-23-generic
 144.0GB: boot/vmlinuz-2.6.32-24-generic
 144.0GB: boot/vmlinuz-2.6.32-25-generic
 144.0GB: boot/vmlinuz-2.6.32-26-generic
 143.9GB: initrd.img
 144.0GB: initrd.img.old
 144.0GB: vmlinuz
 144.0GB: vmlinuz.old

=========================== sdf1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 1f64827d-b4a9-4e87-8669-67afb3ca2926
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 1f64827d-b4a9-4e87-8669-67afb3ca2926
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1f64827d-b4a9-4e87-8669-67afb3ca2926
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1f64827d-b4a9-4e87-8669-67afb3ca2926 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1f64827d-b4a9-4e87-8669-67afb3ca2926
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1f64827d-b4a9-4e87-8669-67afb3ca2926 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1f64827d-b4a9-4e87-8669-67afb3ca2926
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1f64827d-b4a9-4e87-8669-67afb3ca2926
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7270-48c2
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2806ba1a-4a4a-424e-ad95-60f67823bf66
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=2806ba1a-4a4a-424e-ad95-60f67823bf66 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdf1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=9dadc0ff-4fda-484d-9607-7e309faa472b none            swap    sw              0       0

=================== sdf1: Location of files loaded by Grub: ===================


  28.0GB: boot/grub/core.img
   9.0GB: boot/grub/grub.cfg
  28.1GB: boot/initrd.img-2.6.32-21-generic
  28.0GB: boot/vmlinuz-2.6.32-21-generic
  28.1GB: initrd.img
  28.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdf2

00000000  a7 8b 4b 22 3e 53 43 83  c2 24 cf 30 d8 0f ae 70  |..K">SC..$.0...p|
00000010  d4 79 d1 a3 22 31 08 b5  c3 dc ff e9 0e 87 74 78  |.y.."1........tx|
00000020  07 3f f2 6f 0e fa 71 85  bb a1 38 73 75 aa 87 c0  |.?.o..q...8su...|
00000030  c9 ab dc 85 8e b8 8e bc  6c 3a 7b 5d 15 3d ea 3f  |........l:{].=.?|
00000040  c3 90 c0 e8 db ce e9 f9  af 22 f9 12 5a 7d 9d 9a  |........."..Z}..|
00000050  01 3d 3b 98 6b 11 ba cc  79 23 33 34 8f 7d 15 ff  |.=;.k...y#34.}..|
00000060  fa 93 1c be 84 c0 0e 89  be 78 9b e9 26 69 24 d9  |.........x..&i$.|
00000070  23 c7 79 cb 0c c1 b1 4d  81 87 c1 94 3e 73 5d f3  |#.y....M....>s].|
00000080  f1 7f 31 4b 5c 3f 6a bc  bb c7 58 70 e9 df 91 eb  |..1K\?j...Xp....|
00000090  0a 58 8c fe 38 8e 16 39  f4 cb 87 c4 38 ac 75 79  |.X..8..9....8.uy|
000000a0  93 6e bf cf 7d 55 e5 cb  d3 2f 2c 7e dc 8f 76 97  |.n..}U.../,~..v.|
000000b0  e6 9e bf 3f c2 2c 33 70  d6 a3 df e6 5e a2 a6 63  |...?.,3p....^..c|
000000c0  92 4f dc 82 2d 35 82 8d  85 0d 27 a7 7f b5 cb 88  |.O..-5....'.....|
000000d0  88 ef 0c 39 a8 10 be 51  f6 d4 1f f7 66 be 0f 15  |...9...Q....f...|
000000e0  a0 e8 47 09 1d a0 32 b4  ae b4 62 e7 14 02 cd c3  |..G...2...b.....|
000000f0  38 24 03 76 7d 94 e2 ca  81 36 2e 4a 2c ce c0 26  |8$.v}....6.J,..&|
00000100  67 11 0d c9 21 b2 1c e0  90 e5 54 b3 cf 32 6e 40  |g...!.....T..2n@|
00000110  53 cf 3b 24 e7 3d 61 7c  76 ed fb 9e d2 70 c9 f3  |S.;$.=a|v....p..|
00000120  a7 00 1e 87 f7 6f 85 ac  32 d3 6e 38 66 6e ab fa  |.....o..2.n8fn..|
00000130  7f 3d ff cd 3d 0f fa f1  fa 73 2d 7f 95 1f 17 80  |.=..=....s-.....|
00000140  70 f7 66 9f fd a7 d6 18  ff 3c b9 f0 06 78 03 01  |p.f......<...x..|
00000150  cc 2b 68 f9 4d 18 78 eb  ae 25 e5 f5 79 d0 1e 8d  |.+h.M.x..%..y...|
00000160  eb ce 98 3b ba ba 53 f9  c6 c7 d4 d1 32 b2 67 56  |...;..S.....2.gV|
00000170  6c 2f bf 8a f5 c8 bb b6  3d d9 ca f3 c7 db 08 51  |l/......=......Q|
00000180  dc b4 a9 c8 44 d0 14 b6  eb 5c f2 32 74 8c 38 f2  |....D....\.2t.8.|
00000190  00 36 86 43 83 ce 67 0c  88 b6 f7 1e fc 7f 92 37  |.6.C..g........7|
000001a0  7b b8 b1 35 26 8b b4 6d  fd 72 66 d4 cb c5 0d 1b  |{..5&..m.rf.....|
000001b0  18 65 6b 54 e3 27 d8 47  21 be 45 db b7 b6 00 fe  |.ekT.'.G!.E.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b8 28 00 00 00  |............(...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

