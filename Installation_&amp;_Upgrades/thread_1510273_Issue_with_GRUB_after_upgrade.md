---
title: "Issue with GRUB after upgrade"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by PyroFX on 2010-06-15
I upgraded to 10.04 last night. This morning, however, when I tried to choose Windows XP from the GRUB menu, the screen went to black like it normally would, but would then return to the GRUB menu again.

Any suggestions?

---

### Post by PyroFX on 2010-06-27
I am still having the same problem and cannot find anything through searching. 

Also, my computer screen doesn't just go black, my computer actually restarts.

not sure if it is useful, but sudo fdisk -l returns: 

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48a648a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41a941a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12209    98068761    7  HPFS/NTFS
/dev/sdb2           12210       19457    58219560    5  Extended
/dev/sdb5           12210       19155    55793713+  83  Linux
/dev/sdb6           19156       19457     2425783+  82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9ec90800

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS
zach@Studio:~$

---

### Post by wilee-nilee on 2010-06-27
Post the bootscript in my signature in code tags as described.

---

### Post by PyroFX on 2010-06-27
Your script gives me the following:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 196456752 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 196445104 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 196432368 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   196,137,584   196,137,522   7 HPFS/NTFS
/dev/sdb2         196,137,585   312,576,704   116,439,120   5 Extended
/dev/sdb5         196,137,648   307,725,074   111,587,427  83 Linux
/dev/sdb6         307,725,138   312,576,704     4,851,567  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        CE7CDCE87CDCCC79                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        DA1CB4981CB4715D                       ntfs       Main                          
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        8d537bf0-6391-450a-89f5-dc7424bd6fa3   ext4                                     
/dev/sdb6        45c557a6-30a3-4761-84fb-b73a7bf102dc   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        55D123D9E79ABF54                       ntfs       Vault 2.0                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/Main              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1        /media/Vault 2.0         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8d537bf0-6391-450a-89f5-dc7424bd6fa3
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8d537bf0-6391-450a-89f5-dc7424bd6fa3
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8d537bf0-6391-450a-89f5-dc7424bd6fa3
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=8d537bf0-6391-450a-89f5-dc7424bd6fa3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8d537bf0-6391-450a-89f5-dc7424bd6fa3
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=8d537bf0-6391-450a-89f5-dc7424bd6fa3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8d537bf0-6391-450a-89f5-dc7424bd6fa3
    linux    /boot/vmlinuz-2.6.31-22-generic-pae root=UUID=8d537bf0-6391-450a-89f5-dc7424bd6fa3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8d537bf0-6391-450a-89f5-dc7424bd6fa3
    echo    'Loading Linux 2.6.31-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-22-generic-pae root=UUID=8d537bf0-6391-450a-89f5-dc7424bd6fa3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8d537bf0-6391-450a-89f5-dc7424bd6fa3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8d537bf0-6391-450a-89f5-dc7424bd6fa3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set da1cb4981cb4715d
    drivemap -s (hd0) ${root}
    chainloader +1
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
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb5 :
UUID=8d537bf0-6391-450a-89f5-dc7424bd6fa3 / ext4 errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=45c557a6-30a3-4761-84fb-b73a7bf102dc none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/Main ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb5: Location of files loaded by Grub: ===================


 100.5GB: boot/grub/core.img
 102.9GB: boot/grub/grub.cfg
 101.4GB: boot/initrd.img-2.6.31-22-generic-pae
 109.3GB: boot/initrd.img-2.6.32-22-generic-pae
 101.5GB: boot/vmlinuz-2.6.31-22-generic-pae
 101.3GB: boot/vmlinuz-2.6.32-22-generic-pae
 109.3GB: initrd.img
 101.4GB: initrd.img.old
 101.3GB: vmlinuz
 101.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 

```

---

### Post by wilee-nilee on 2010-06-27
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  **Grub 2 is installed in the boot sector of sdb1 and **
                       looks at sector 196445104 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

So you have grub in this partition and several others, including sda1 and sdd1, use this link to get sdb1 cleaned. The others appear to be data HD so they can be removed manually or with the link but I would start with the sdb1 as it is the XP boot partition and main partition.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

