---
title: "Problems booting with grub with multiple hard drives"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by ledimies on 2011-01-23
Hi,

I have 3 hard drives installed to my system, 1TB, 2TB and 500GB drives with the following configuration:

ledi@ledi-ubuntu:~$ sudo parted /dev/sda print
Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   62.9GB  62.8GB  primary   ntfs
 3      62.9GB  916GB   853GB   primary   ntfs
 4      916GB   1000GB  83.9GB  extended
 5      916GB   957GB   40.2GB  logical   ext4
 7      957GB   997GB   40.2GB  logical   ext4
 6      997GB   1000GB  3461MB  logical   linux-swap(v1)


ledi@ledi-ubuntu:~$ sudo parted /dev/sdb print
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      1049kB  40.0GB  40.0GB  ext4
 2      40.0GB  40.0GB  10.0MB                  primary  bios_grub
 5      40.0GB  80.0GB  40.0GB                  primary
 3      80.0GB  83.5GB  3500MB  linux-swap(v1)
 4      83.5GB  2000GB  1917GB                           lvm


ledi@ledi-ubuntu:~$ sudo parted /dev/sdc print
Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ntfs

I have Windows 7 and 2 Ubuntu installations in the 1TB disk. I recently installed the 2TB disk to my system and installed one more Ubuntu to that one.

My problem is that after installing Ubuntu to the 2TB drive, I no longer could boot to any of the OS's in the 1TB drive. Grub correctly detected all the installations, but whenever I try to select one of those, I get the following errors from Grub:

error: no such device: [long string of numbers and letters]
error: no such partition.
When selecting Linux, I see an additional line:
error: you need to load the kernel first.

I can boot to the Ubuntu installation in the 2TB drive. My problem reversed when I reinstalled grub to one of the Ubuntu installations in the 1TB drive. I can boot to any of the OS's in the 1TB drive, but not to the Ubuntu in the 2TB drive. The error message is the same as above.

I have no idea what am I doing wrong and I would be really grateful for any assistance.

---

### Post by aqualad on 2011-01-23
I've been doing very similar stuff tonight on a new installation, here are some tips:

1. Make sure that wherever you have your bootloaders, the partitions are given the bootable flag (do so in gparted)
2. If you are having issues with grub, try```
sudo apt-get purge grub-pc grub-common
sudo apt-get install grub-pc grub-common
```

You can then choose which devices to install grub to while it's reinstalling.
3. Try booting the R.I.P. (Recovery is Possible) iso to see if you can fix anything that way.

I dual boot with LVM and soft raid, so I just made a 100MB partition (sda1) and slapped grub on that and everything went from there.

Good luck

---

### Post by ledimies on 2011-01-23
After reading my initial post, I realized that I'm not describing the problem very well.

Grub is installing itself without any error messages and it detects the installed operating systems, so they appear to the selection list whenever I boot the computer. So I do see the Grub bootloader menu.

I can use the following command to reinstall grub to any of the Linux partitions: "sudo grub-install --root-directory=[mounted_root_fs_of_some_linux] /dev/sda". I always use /dev/sda as the install device.

If I install grub to the linux partition in sdb, I can boot to Linux installed to sdb, but I cannot boot to any of the operating system in sda. I do see the selection for those OS's in the Grub bootloader menu, but I get the error in my first message whenever I try to select any of them.

If I install grub to either one of the linux partitions in sda, my problem is reversed. I can boot to OS's in the sda drive, but not to the Linux in sdb.

As far as I know it should be possible with Grub to do what I'm trying to do. It remains a mystery to me why I get these error messages even though I get no errors while installing and configuring grub.

---

### Post by ledimies on 2011-01-23
Here is the output of boot info script in my system:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 78125056 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdc

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
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  yavdr 0.2.0 (based on Ubuntu 
                       10.04)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  yavdr 0.3.0 (based on Ubuntu 
                       10.04)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   122,882,047   122,675,200   7 HPFS/NTFS
/dev/sda3         122,882,048 1,789,679,615 1,666,797,568   7 HPFS/NTFS
/dev/sda4       1,789,681,662 1,953,523,711   163,842,050   5 Extended
/dev/sda5       1,789,681,664 1,868,214,914    78,533,251  83 Linux
/dev/sda6       1,946,763,264 1,953,523,711     6,760,448  82 Linux swap / Solaris
/dev/sda7       1,868,216,320 1,946,755,071    78,538,752  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048    78,125,055    78,123,008 Linux or Data
/dev/sdb2      78,125,056    78,144,587        19,532 Bios Boot Partition
/dev/sdb3     156,250,112   163,086,335     6,836,224 Linux Swap
/dev/sdb4     163,086,336 3,907,028,991 3,743,942,656 LVM
/dev/sdb5      78,145,536   156,250,111    78,104,576 Linux or Data

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,770,143   976,770,081   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0C26C76226C74C00                       ntfs       System Reserved               
/dev/sda2        7A5CDCA35CDC5B87                       ntfs                                     
/dev/sda3        1476E89C76E8803A                       ntfs       New Volume                    
/dev/sda4: PTTYPE="dos" 
/dev/sda5        cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf   ext4                                     
/dev/sda6        61e8fb53-6eaf-409e-afd8-aca5440fb267   swap                                     
/dev/sda7        644726ea-90d4-4b50-8cbd-4fe381e10def   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3af5b82e-175c-4050-bb2e-8dbcb630c7e1   ext4                                     
/dev/sdb3        d507fe05-74b7-4e86-8a5a-71c469b91523   swap                                     
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        88A00ABBA00AAFAC                       ntfs       Datra                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro   quiet noresume
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro   quiet noresume
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0c26c76226c74c00
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/50_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
if [ ${recordfail} = 1 ]; then
  set timeout=5
else
      set timeout=5
fi

### END /etc/grub.d/50_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=61e8fb53-6eaf-409e-afd8-aca5440fb267 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 916.3GB: boot/grub/core.img
 947.0GB: boot/grub/grub.cfg
 916.3GB: boot/initrd.img-2.6.32-22-generic
 916.4GB: boot/initrd.img-2.6.32-24-generic
 916.3GB: boot/vmlinuz-2.6.32-22-generic
 916.3GB: boot/vmlinuz-2.6.32-24-generic
 916.4GB: initrd.img
 916.3GB: initrd.img.old
 916.3GB: vmlinuz
 916.3GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 644726ea-90d4-4b50-8cbd-4fe381e10def
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 644726ea-90d4-4b50-8cbd-4fe381e10def
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 644726ea-90d4-4b50-8cbd-4fe381e10def
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=644726ea-90d4-4b50-8cbd-4fe381e10def ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 644726ea-90d4-4b50-8cbd-4fe381e10def
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=644726ea-90d4-4b50-8cbd-4fe381e10def ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 644726ea-90d4-4b50-8cbd-4fe381e10def
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 644726ea-90d4-4b50-8cbd-4fe381e10def
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0c26c76226c74c00
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro quiet noresume
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro quiet noresume
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3af5b82e-175c-4050-bb2e-8dbcb630c7e1
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=3af5b82e-175c-4050-bb2e-8dbcb630c7e1 ro vmalloc=256m quiet noresume nohz=off acpi_enforce_resources=lax
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3af5b82e-175c-4050-bb2e-8dbcb630c7e1
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=3af5b82e-175c-4050-bb2e-8dbcb630c7e1 ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3af5b82e-175c-4050-bb2e-8dbcb630c7e1
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=3af5b82e-175c-4050-bb2e-8dbcb630c7e1 ro vmalloc=256m quiet noresume nohz=off acpi_enforce_resources=lax
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3af5b82e-175c-4050-bb2e-8dbcb630c7e1
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=3af5b82e-175c-4050-bb2e-8dbcb630c7e1 ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=644726ea-90d4-4b50-8cbd-4fe381e10def /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=61e8fb53-6eaf-409e-afd8-aca5440fb267 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 963.1GB: boot/grub/core.img
 971.8GB: boot/grub/grub.cfg
 963.3GB: boot/initrd.img-2.6.32-27-generic-pae
 963.2GB: boot/vmlinuz-2.6.32-27-generic-pae
 963.3GB: initrd.img
 963.2GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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
search --no-floppy --fs-uuid --set 3af5b82e-175c-4050-bb2e-8dbcb630c7e1
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
search --no-floppy --fs-uuid --set 3af5b82e-175c-4050-bb2e-8dbcb630c7e1
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3af5b82e-175c-4050-bb2e-8dbcb630c7e1
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=3af5b82e-175c-4050-bb2e-8dbcb630c7e1 ro   vmalloc=256m quiet noresume nohz=off acpi_enforce_resources=lax
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3af5b82e-175c-4050-bb2e-8dbcb630c7e1
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=3af5b82e-175c-4050-bb2e-8dbcb630c7e1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3af5b82e-175c-4050-bb2e-8dbcb630c7e1
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=3af5b82e-175c-4050-bb2e-8dbcb630c7e1 ro   vmalloc=256m quiet noresume nohz=off acpi_enforce_resources=lax
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3af5b82e-175c-4050-bb2e-8dbcb630c7e1
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=3af5b82e-175c-4050-bb2e-8dbcb630c7e1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0c26c76226c74c00
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro quiet noresume
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro quiet noresume
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=cb9e3e02-3c5b-4575-84b5-51b0d70cb8bf ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 644726ea-90d4-4b50-8cbd-4fe381e10def
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=644726ea-90d4-4b50-8cbd-4fe381e10def ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 644726ea-90d4-4b50-8cbd-4fe381e10def
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=644726ea-90d4-4b50-8cbd-4fe381e10def ro single
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/50_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
if [ ${recordfail} = 1 ]; then
  set timeout=5
else
      set timeout=5
fi

### END /etc/grub.d/50_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=3af5b82e-175c-4050-bb2e-8dbcb630c7e1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=d507fe05-74b7-4e86-8a5a-71c469b91523 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  34.5GB: boot/grub/grub.cfg
  34.5GB: boot/initrd.img-2.6.32-25-generic
  34.6GB: boot/initrd.img-2.6.32-27-generic
  34.5GB: boot/vmlinuz-2.6.32-25-generic
  34.5GB: boot/vmlinuz-2.6.32-27-generic
  34.6GB: initrd.img
  34.5GB: initrd.img.old
  34.5GB: vmlinuz
  34.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 18 a8 04  00 00 00 00 2f 00 20 08  |............/. .|
00000200



```

---

### Post by kansasnoob on 2011-01-23
I'm personally a big believer in installing the controlling OS's grub2 to the MBR of all drives, eg:

```
sudo grub-install /dev/sda
sudo grub-install /dev/sdb
sudo grub-install /dev/sdc
```

Not everyone agrees with me but it's the lazy mans way out of device mapping errors :D

---

### Post by srs5694 on 2011-01-23
Your problem may be a bug in GRUB that prevents it from booting Windows when you've got a mixture of MBR and GPT disks (as you do have). The solution to this problem is to add the following line to /etc/default/grub:

```
GRUB_PRELOAD_MODULES="part_msdos"

```

I believe you've got to then re-run grub-mkconfig.

---

### Post by ledimies on 2011-01-23
> **srs5694 said:**
> Your problem may be a bug in GRUB that prevents it from booting Windows when you've got a mixture of MBR and GPT disks (as you do have). The solution to this problem is to add the following line to /etc/default/grub:

```
GRUB_PRELOAD_MODULES="part_msdos"

```I believe you've got to then re-run grub-mkconfig.

I believe you are talking about bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

My situation is currently the other way around, I'm booting from MBR disk and I can't get to operating systems in GPT disk.

I added the following line to /etc/default/grub and run update-grub:
```
GRUB_PRELOAD_MODULES="part_gpt"
```Now everything works for me again. Thanks for the tip!

---

