---
title: "can't boot my ubunut 10.04 or win 7!!!"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by Eng.Khalid on 2010-08-24
Dear all 

I was using win7 & ubuntu 10.04 and the system was stable until some problem caused me to reinstall win7 
after that I couldn't boot ubuntu 10.04 so I tried to fix that using some command handle with grub

after that I can't access win7 or ubuntu ??? what can I do this is my bootstrap info :

```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
251 heads, 63 sectors/track, 30885 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *        206,848    71,682,047    71,475,200   7 HPFS/NTFS
/dev/sda2          71,682,048   378,882,047   307,200,000   7 HPFS/NTFS
/dev/sda3         378,884,094   470,702,079    91,817,986   5 Extended
/dev/sda5         378,884,096   379,858,943       974,848  83 Linux
/dev/sda6         379,860,992   389,623,807     9,762,816  83 Linux
/dev/sda7         389,625,856   395,483,135     5,857,280  83 Linux
/dev/sda8         395,485,184   469,702,655    74,217,472  83 Linux
/dev/sda9         469,704,704   470,702,079       997,376  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3A88E31F88E2D901                       ntfs                                     
/dev/sda2        32E889A0E88962C9                       ntfs       Data                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ce91a9df-df03-443b-90db-f9556fad0381   ext4                                     
/dev/sda6        53ad1038-a761-4de7-9dc3-26f2fb6b7b9a   ext4                                     
/dev/sda7        f0d96e3a-8b72-484d-a0d2-4d9e90ef8da6   ext4                                     
/dev/sda8        43623e19-971e-4c1c-a60c-44819628c187   ext4                                     
/dev/sda9        0ef577ef-bcbb-4793-b3e2-5bbd5fc18807   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc         585E-AC4C                              vfat       USB                           
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/ce91a9df-df03-443b-90db-f9556fad0381 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/sda5              ext4       (rw)
/dev/sdc         /media/USB               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


============================= sda5/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 53ad1038-a761-4de7-9dc3-26f2fb6b7b9a
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
search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
set locale_dir=($root)/grub/locale
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
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    linux    /vmlinuz-2.6.32-24-generic root=UUID=53ad1038-a761-4de7-9dc3-26f2fb6b7b9a ro   quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=53ad1038-a761-4de7-9dc3-26f2fb6b7b9a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    linux    /vmlinuz-2.6.32-21-generic root=UUID=53ad1038-a761-4de7-9dc3-26f2fb6b7b9a ro   quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=UUID=53ad1038-a761-4de7-9dc3-26f2fb6b7b9a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0aca7b7aca7772e
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda5: Location of files loaded by Grub: ===================


 194.2GB: boot/grub/core.img
 194.1GB: grub/core.img
 194.1GB: grub/grub.cfg
 194.0GB: initrd.img-2.6.32-21-generic
 194.0GB: initrd.img-2.6.32-24-generic
 194.0GB: vmlinuz-2.6.32-21-generic
 194.0GB: vmlinuz-2.6.32-24-generic

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=53ad1038-a761-4de7-9dc3-26f2fb6b7b9a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=ce91a9df-df03-443b-90db-f9556fad0381 /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=43623e19-971e-4c1c-a60c-44819628c187 /home           ext4    defaults        0       2
# /var was on /dev/sda7 during installation
UUID=f0d96e3a-8b72-484d-a0d2-4d9e90ef8da6 /var            ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=0ef577ef-bcbb-4793-b3e2-5bbd5fc18807 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 198.1GB: boot/grub/core.img

=========================== sdc/boot/grub/grub.cfg: ===========================

# Super Grub Disk Main Configuration file
# Copyright (C) 2009  Adrian Gibanel Lopez.
#
# Super Grub Disk is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# Super Grub Disk is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

insmod biosdisk
insmod part_acorn
insmod part_amiga
insmod part_apple
insmod part_gpt
insmod part_msdos
insmod part_sun

# Prepare environment variables needed by some scripts

source /boot/grub/prepare-supergrub-environment.lua

# Define a function for updating paths when device names change.
# search.mod is required for update-paths, and must be loaded before device
# names change because $prefix will be invalid.
# prepare-supergrub-environment.lua also needs to be run before update-paths
# because update-paths uses $prefix_uuid and $prefix_path.

insmod search

function update_paths {
  search --fs-uuid --set=prefix_device $prefix_uuid
  prefix="(${prefix_device})${prefix_path}"
  script_prefix="(${prefix_device})${script_path}"
}

# Timeout for menu
#set timeout=10

# Set default boot entry as Entry 0
set default=0

# Entry 0 - Load osdetect lua script as a new menu
menuentry "Detect any OS" {
 configfile $script_prefix/osdetect.lua
}

# Entry 1 - Load cfgdetect lua script as a new menu
menuentry "Detect any GRUB2 configuration file (grub.cfg)" {
 configfile $script_prefix/cfgdetect.lua
}

# Entry 2 - Load grubdetect lua script as a new menu
menuentry "Detect any GRUB2 installation (even if mbr is overwritten)" {
  configfile $script_prefix/grubdetect.lua
}

# Entry 3 - Load isodetect lua script as a new menu
menuentry "Detect loop bootable isos (in /boot-isos or /boot/boot-isos)" {
  configfile $script_prefix/isodetect.lua
}

# Entry 4
menuentry "Enable GRUB2's LVM support" {
  insmod lvm
}

# Entry 5
menuentry "Enable GRUB2's RAID support" {
  insmod raid
  insmod mdraid
  insmod raid5rec
  insmod raid6rec
  insmod dm_nv
}

# Entry 6
menuentry "Enable GRUB2's PATA support (to work around BIOS bugs/limitations)" {
  insmod ata
  update_paths
}

# Entry 7
menuentry "Enable GRUB2's USB support *experimental*" {
  insmod ohci
  insmod uhci
  insmod usbms
  update_paths
}

# Entry 8
menuentry "Enable serial terminal" {
  serial
  terminal_input console serial
  terminal_output console serial
}

# Entry 9
menuentry "List devices/partitions" {
  # Set pager=1 so ls output doesn't scroll past the top of the screen
  # but restore $pager to its previous value when finished
  set oldpager="${pager}"
  set pager=1

  ls -l

  set pager="${oldpager}"
  unset oldpager
}

==================== sdc: Location of files loaded by Grub: ====================


    ??GB: boot/grub/grub.cfg
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by Rubi1200 on 2010-08-24
> **Eng.Khalid said:**
> Dear all 

I was using win7 & ubuntu 10.04 and the system was stable until some problem caused me to reinstall win7 
after that I couldn't boot ubuntu 10.04 so I tried to fix that using some command handle with grub

after that I can't access win7 or ubuntu ??? what can I do this is my bootstrap info :

```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

[COLOR=Red]sda5[/COLOR]: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs: [COLOR=Red]  /grub/grub.cfg /grub/core.img /boot/grub/core.img
[/COLOR] 
sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
251 heads, 63 sectors/track, 30885 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *        206,848    71,682,047    71,475,200   7 HPFS/NTFS
/dev/sda2          71,682,048   378,882,047   307,200,000   7 HPFS/NTFS
/dev/sda3         378,884,094   470,702,079    91,817,986   5 Extended
/dev/sda5         378,884,096   379,858,943       974,848  83 Linux
/dev/sda6         379,860,992   389,623,807     9,762,816  83 Linux
/dev/sda7         389,625,856   395,483,135     5,857,280  83 Linux
/dev/sda8         395,485,184   469,702,655    74,217,472  83 Linux
/dev/sda9         469,704,704   470,702,079       997,376  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3A88E31F88E2D901                       ntfs                                     
/dev/sda2        32E889A0E88962C9                       ntfs       Data                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ce91a9df-df03-443b-90db-f9556fad0381   ext4                                     
/dev/sda6        53ad1038-a761-4de7-9dc3-26f2fb6b7b9a   ext4                                     
/dev/sda7        f0d96e3a-8b72-484d-a0d2-4d9e90ef8da6   ext4                                     
/dev/sda8        43623e19-971e-4c1c-a60c-44819628c187   ext4                                     
/dev/sda9        0ef577ef-bcbb-4793-b3e2-5bbd5fc18807   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc         585E-AC4C                              vfat       USB                           
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/ce91a9df-df03-443b-90db-f9556fad0381 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/sda5              ext4       (rw)
/dev/sdc         /media/USB               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


============================= sda5/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 53ad1038-a761-4de7-9dc3-26f2fb6b7b9a
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
search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
set locale_dir=($root)/grub/locale
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
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    linux    /vmlinuz-2.6.32-24-generic root=UUID=53ad1038-a761-4de7-9dc3-26f2fb6b7b9a ro   quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=53ad1038-a761-4de7-9dc3-26f2fb6b7b9a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    linux    /vmlinuz-2.6.32-21-generic root=UUID=53ad1038-a761-4de7-9dc3-26f2fb6b7b9a ro   quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=UUID=53ad1038-a761-4de7-9dc3-26f2fb6b7b9a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ce91a9df-df03-443b-90db-f9556fad0381
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f0aca7b7aca7772e
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda5: Location of files loaded by Grub: ===================


 194.2GB: boot/grub/core.img
 194.1GB: grub/core.img
 194.1GB: grub/grub.cfg
 194.0GB: initrd.img-2.6.32-21-generic
 194.0GB: initrd.img-2.6.32-24-generic
 194.0GB: vmlinuz-2.6.32-21-generic
 194.0GB: vmlinuz-2.6.32-24-generic

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=53ad1038-a761-4de7-9dc3-26f2fb6b7b9a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=ce91a9df-df03-443b-90db-f9556fad0381 /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=43623e19-971e-4c1c-a60c-44819628c187 /home           ext4    defaults        0       2
# /var was on /dev/sda7 during installation
UUID=f0d96e3a-8b72-484d-a0d2-4d9e90ef8da6 /var            ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=0ef577ef-bcbb-4793-b3e2-5bbd5fc18807 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 198.1GB: boot/grub/core.img

=========================== sdc/boot/grub/grub.cfg: ===========================

# Super Grub Disk Main Configuration file
# Copyright (C) 2009  Adrian Gibanel Lopez.
#
# Super Grub Disk is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# Super Grub Disk is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

insmod biosdisk
insmod part_acorn
insmod part_amiga
insmod part_apple
insmod part_gpt
insmod part_msdos
insmod part_sun

# Prepare environment variables needed by some scripts

source /boot/grub/prepare-supergrub-environment.lua

# Define a function for updating paths when device names change.
# search.mod is required for update-paths, and must be loaded before device
# names change because $prefix will be invalid.
# prepare-supergrub-environment.lua also needs to be run before update-paths
# because update-paths uses $prefix_uuid and $prefix_path.

insmod search

function update_paths {
  search --fs-uuid --set=prefix_device $prefix_uuid
  prefix="(${prefix_device})${prefix_path}"
  script_prefix="(${prefix_device})${script_path}"
}

# Timeout for menu
#set timeout=10

# Set default boot entry as Entry 0
set default=0

# Entry 0 - Load osdetect lua script as a new menu
menuentry "Detect any OS" {
 configfile $script_prefix/osdetect.lua
}

# Entry 1 - Load cfgdetect lua script as a new menu
menuentry "Detect any GRUB2 configuration file (grub.cfg)" {
 configfile $script_prefix/cfgdetect.lua
}

# Entry 2 - Load grubdetect lua script as a new menu
menuentry "Detect any GRUB2 installation (even if mbr is overwritten)" {
  configfile $script_prefix/grubdetect.lua
}

# Entry 3 - Load isodetect lua script as a new menu
menuentry "Detect loop bootable isos (in /boot-isos or /boot/boot-isos)" {
  configfile $script_prefix/isodetect.lua
}

# Entry 4
menuentry "Enable GRUB2's LVM support" {
  insmod lvm
}

# Entry 5
menuentry "Enable GRUB2's RAID support" {
  insmod raid
  insmod mdraid
  insmod raid5rec
  insmod raid6rec
  insmod dm_nv
}

# Entry 6
menuentry "Enable GRUB2's PATA support (to work around BIOS bugs/limitations)" {
  insmod ata
  update_paths
}

# Entry 7
menuentry "Enable GRUB2's USB support *experimental*" {
  insmod ohci
  insmod uhci
  insmod usbms
  update_paths
}

# Entry 8
menuentry "Enable serial terminal" {
  serial
  terminal_input console serial
  terminal_output console serial
}

# Entry 9
menuentry "List devices/partitions" {
  # Set pager=1 so ls output doesn't scroll past the top of the screen
  # but restore $pager to its previous value when finished
  set oldpager="${pager}"
  set pager=1

  ls -l

  set pager="${oldpager}"
  unset oldpager
}

==================== sdc: Location of files loaded by Grub: ====================


    ??GB: boot/grub/grub.cfg
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

Looks like whatever you did, the boot files ended up on sda5. But Ubuntu is on sda6.

Here is the fix:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

What you need to do is mount sda6 and reinstall GRUB to the MBR of sda.

Follow the instructions in the link (all of them) and things should be back to normal.

If you have any questions, feel free to ask.

---

### Post by Eng.Khalid on 2010-08-24
I tried this & this which make me can't access win7 I'll try it again but when I'll reboot my laptop the grub command line will appear I don't know what to write on it ??


```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 

```

---

### Post by Rubi1200 on 2010-08-24
> **Eng.Khalid said:**
> I tried this & this which make me can't access win7 I'll try it again but when I'll reboot my laptop the grub command line will appear I don't know what to write on it ??


```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 

```
The commands worked: > installation finished. No error reported.

But this command ```
sudo update-grub
``` needs to be run from within Ubuntu NOT the LiveCD.

Reboot the computer, taking the CD out, and you should be back in Ubuntu. Then run the command and then try and get into Windows (it should work).

Let me know what happens please.

---

### Post by Eng.Khalid on 2010-08-24
when I reboot & taking off the cd the GNU grub command line appear 
and can't enter any of my o.s

******

may this information help you 

first I was have win 7 then I've installed ubuntu using advanced option

sda5 is boot partion 
sda6 is root partion 
& I made another partions for /home , /var & swap

---

### Post by Rubi1200 on 2010-08-24
Ok, my mistake; I should have looked at fstab. Sorry! :(

In that case, I think you need to do this again. But, this time use Method 3 (CHROOT) because that has instructions for when you have a separate /boot partition.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Let me know please.

---

### Post by Eng.Khalid on 2010-08-24
thank u veeeeeeeeery much Rubi it works but the problem that now I can only boot ubuntu but I can't boot win7 ???

but anyway now is much better that nothing :D 
so can u help me to make them both to work correctly ??

---

### Post by Rubi1200 on 2010-08-24
> **Eng.Khalid said:**
> thank u veeeeeeeeery much Rubi it works but the problem that now I can only boot ubuntu but I can't boot win7 ???

but anyway now is much better that nothing :D 
so can u help me to make them both to work correctly ??
In Ubuntu go to the terminal and run ```
sudo update-grub
```
It should recognize Windows and let you boot into it.

---

### Post by Eng.Khalid on 2010-08-24
Really I'm thankful ... 
no words gives you what do u deserve 

every thing gonna be ok :D

---

### Post by Rubi1200 on 2010-08-24
You can boot into Windows and Ubuntu now?

If yes, excellent!!!

And, you are more than welcome :D

Mark this thread Solved by using the Thread Tools near the top of the page please. That way other users who have had similar problems can also find a solution.

Good luck and enjoy!

---

### Post by Eng.Khalid on 2010-08-24
done :D

I've make it as solved 

now I can boot win7 or Ubuntu

---

