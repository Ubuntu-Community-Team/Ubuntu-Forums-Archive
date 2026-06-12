---
title: "unable to boot to Ubuntu on dual-boot Ubuntu/XP after recovering Windows bootloader"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by Gabby88 on 2010-07-18
Hello, I have Ubuntu 10.04 LTS and Windows XP installed on my laptop. Usually when booting, I get the GRUB 2 menu and I can boot into either Ubuntu or XP.

I was playing around with EasyBCD, then after trying to remove it I was unable to boot into Windows, I used a Windows 2000 CD recovery console to fix the MBR (using: fixboot and fixmbr).

Now Windows starts up when I power on, but I don't get the grub menu anymore with an Ubuntu option. If I boot from the Ubuntu Live CD and try to mount my Ubuntu partition (/dev/sda5) I get this error:

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

here is the        output of           Boot Info Script ([http://bootinfoscript.sourceforge.net/):]("http://bootinfoscript.sourceforge.net/%29:")
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 79.8 GB, 79826342400 bytes
255 heads, 63 sectors/track, 9705 cylinders, total 155910825 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,945,714    41,945,652   7 HPFS/NTFS
/dev/sda2          41,945,715    68,308,379    26,362,665   f W95 Ext d (LBA)
/dev/sda5          41,945,778    55,617,029    13,671,252  83 Linux
/dev/sda6          62,171,613    68,308,379     6,136,767  82 Linux swap / Solaris
/dev/sda3          68,308,380   155,894,759    87,586,380   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        347070AE70707906                       ntfs       SQ004101P01                   
/dev/sda2: PTTYPE="dos" 
/dev/sda3        52BCA5F6BCA5D4AF                       ntfs       E-40GB                        
/dev/sda5        b9096ceb-57b1-4760-bbf2-db1db48b94b8   ext4                                     
/dev/sda6        c0dfed21-1e62-40fd-81e6-fd659c34470a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         F4D4-8332                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /media/F4D4-8332         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

; This boot.ini was automatically generated by NeoSmart Technologies' BootGrabber.exe 
; Use EasyBCD from http://neosmart.net/dl.php?id=1 to manage your bootloader 
 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP on C:\" /fastdetect

```And this is how it looked before I used the Windows 2000 Recovery CD:
(Note: it says I have a Vista OS, this is because I was messing around with EasyBCD, it's really XP)
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 79.8 GB, 79826342400 bytes
255 heads, 63 sectors/track, 9705 cylinders, total 155910825 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,945,714    41,945,652   7 HPFS/NTFS
/dev/sda2          41,947,134    68,308,379    26,361,246   5 Extended
/dev/sda5          41,947,136    62,171,549    20,224,414  83 Linux
/dev/sda3          68,308,380   155,894,759    87,586,380  17 Hidden HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        347070AE70707906                       ntfs       SQ004101P01                   
/dev/sda2: PTTYPE="dos" 
/dev/sda3        52BCA5F6BCA5D4AF                       ntfs       E-40GB                        
/dev/sda5        11a032af-3834-46b0-9b30-7894b9e9b422   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

; This boot.ini was automatically generated by NeoSmart Technologies' BootGrabber.exe 
; Use EasyBCD from http://neosmart.net/dl.php?id=1 to manage your bootloader 
 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP on C:\" /fastdetect 

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
set default="8"
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
search --no-floppy --fs-uuid --set 11a032af-3834-46b0-9b30-7894b9e9b422
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
search --no-floppy --fs-uuid --set 11a032af-3834-46b0-9b30-7894b9e9b422
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 11a032af-3834-46b0-9b30-7894b9e9b422
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=11a032af-3834-46b0-9b30-7894b9e9b422 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 11a032af-3834-46b0-9b30-7894b9e9b422
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=11a032af-3834-46b0-9b30-7894b9e9b422 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 11a032af-3834-46b0-9b30-7894b9e9b422
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=11a032af-3834-46b0-9b30-7894b9e9b422 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 11a032af-3834-46b0-9b30-7894b9e9b422
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=11a032af-3834-46b0-9b30-7894b9e9b422 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 11a032af-3834-46b0-9b30-7894b9e9b422
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=11a032af-3834-46b0-9b30-7894b9e9b422 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 11a032af-3834-46b0-9b30-7894b9e9b422
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=11a032af-3834-46b0-9b30-7894b9e9b422 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 11a032af-3834-46b0-9b30-7894b9e9b422
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 11a032af-3834-46b0-9b30-7894b9e9b422
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 347070ae70707906
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=11a032af-3834-46b0-9b30-7894b9e9b422 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c0dfed21-1e62-40fd-81e6-fd659c34470a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  23.8GB: boot/grub/core.img
  28.8GB: boot/grub/grub.cfg
  23.9GB: boot/initrd.img-2.6.32-21-generic
  24.7GB: boot/initrd.img-2.6.32-22-generic
  25.1GB: boot/initrd.img-2.6.32-23-generic
  23.7GB: boot/vmlinuz-2.6.32-21-generic
  24.7GB: boot/vmlinuz-2.6.32-22-generic
  24.7GB: boot/vmlinuz-2.6.32-23-generic
  25.1GB: initrd.img
  24.7GB: initrd.img.old
  24.7GB: vmlinuz
  24.7GB: vmlinuz.old

```Please help me figure out how to restore grub so I can boot my Ubuntu system as well.
Thank you!

---

### Post by dino99 on 2010-07-18
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by oldfred on 2010-07-18
Some links that may help:

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

---

