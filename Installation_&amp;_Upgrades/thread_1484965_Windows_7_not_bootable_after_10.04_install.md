---
title: "Windows 7 not bootable after 10.04 install"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by tedlux on 2010-05-16
your help would be great thanks in advance 

```
ne                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 531160873 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 563788441 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 566139385 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda6 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 566141569 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 566144497 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 566139465 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc2 and 
                       looks at sector 566140289 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 566138705 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd2 and 
                       looks at sector 566140225 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd3 and 
                       looks at sector 562127745 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   123,090,029   123,089,967   7 HPFS/NTFS
/dev/sda2         123,090,030 1,953,503,999 1,830,413,970   f W95 Ext d (LBA)
/dev/sda5         123,090,093 1,038,297,014   915,206,922   7 HPFS/NTFS
/dev/sda6       1,038,297,078 1,953,503,999   915,206,922   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   937,697,984   937,697,922   7 HPFS/NTFS
/dev/sdb2         937,697,985 1,953,520,064 1,015,822,080   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   527,992,289   527,992,227   7 HPFS/NTFS
/dev/sdc2       1,054,908,225 1,953,520,064   898,611,840   7 HPFS/NTFS
/dev/sdc3         527,992,290 1,054,908,224   526,915,935   5 Extended
/dev/sdc5         527,992,353 1,035,260,729   507,268,377  83 Linux
/dev/sdc6       1,035,260,793 1,054,908,224    19,647,432  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdd2         204,796,620 1,142,430,344   937,633,725   7 HPFS/NTFS
/dev/sdd3       1,142,430,345 1,953,520,064   811,089,720   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F680C81E80C7E2EB                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        C44C81814C816F4C                       ntfs       DownLs                        
/dev/sda6        4C0C91820C91682A                       ntfs       Movies                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0048633948632D1A                       ntfs       Ebooks & Audio Learning       
/dev/sdb2        5A2C37992C376F5F                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        32ECD8A6ECD8659F                       ntfs       Local Disk                    
/dev/sdc2        8250592C50592865                       ntfs       MP3                           
/dev/sdc3: PTTYPE="dos" 
/dev/sdc5        cf80c32d-9121-492c-a385-e1d8b70fa703   ext4                                     
/dev/sdc6        b0a9e830-f723-45f1-b6bf-83900418bfa7   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        5A88CB8088CB58E1                       ntfs       Music Videos                  
/dev/sdd2        F8E4E405E4E3C44A                       ntfs                                     
/dev/sdd3        344801214800E388                       ntfs                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc5        /                        ext4       (rw,errors=remount-ro)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set cf80c32d-9121-492c-a385-e1d8b70fa703
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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set cf80c32d-9121-492c-a385-e1d8b70fa703
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
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set cf80c32d-9121-492c-a385-e1d8b70fa703
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cf80c32d-9121-492c-a385-e1d8b70fa703 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set cf80c32d-9121-492c-a385-e1d8b70fa703
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cf80c32d-9121-492c-a385-e1d8b70fa703 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set cf80c32d-9121-492c-a385-e1d8b70fa703
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=cf80c32d-9121-492c-a385-e1d8b70fa703 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set cf80c32d-9121-492c-a385-e1d8b70fa703
    echo    'Loading Linux 2.6.31-16-generic ...'
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=cf80c32d-9121-492c-a385-e1d8b70fa703 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set cf80c32d-9121-492c-a385-e1d8b70fa703
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set cf80c32d-9121-492c-a385-e1d8b70fa703
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f680c81e80c7e2eb
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=cf80c32d-9121-492c-a385-e1d8b70fa703 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=b0a9e830-f723-45f1-b6bf-83900418bfa7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 287.8GB: boot/grub/core.img
 287.8GB: boot/grub/grub.cfg
 271.9GB: boot/initrd.img-2.6.31-16-generic
 271.9GB: boot/initrd.img-2.6.32-22-generic
 270.6GB: boot/vmlinuz-2.6.31-16-generic
 271.7GB: boot/vmlinuz-2.6.32-22-generic
 271.9GB: initrd.img
 271.7GB: vmlinuz 
```

---

### Post by kansasnoob on 2010-05-16
The problem:

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  **[COLOR="Red"]Grub 2[/COLOR]**
    Boot sector info:  [B][COLOR="Red"]Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 531160873 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.[/COLOR][/B] No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM


The solution:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

My bug report (please comment there):

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

