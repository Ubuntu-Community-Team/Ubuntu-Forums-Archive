---
title: "Triple Boot disaster following updates to Ubuntu"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by keentolearn on 2010-11-27
My System was triple-boot, Win XP, Ubuntu 9.04 & Ububuntu9.10. Over 2 weeks or so I upgraded U9.04 to U10.04 and then 3/4 days later U9.10 to U10.10. I used a method of updating used 4/5 times before without faults.I did not initially set the default system and selected which system was needed by using up/down arrow key. All versions were OK. Later I used my usual procedure to reset the default operating system to Win XP using terminal and command 

"gksu gedit /etc/default/grub" 

[Unfortunately on this occasion I forgot to take a copy of the original file, since I had used this method so many times before without a problem]
 
I changed the value of the XP entry so that the PC would boot up into XP ie menu position 4.

 I then used the command "sudo update-grub". 

I then re-booted and was horrified to see that only version U 1010 was available. No Windows XP, No U 1004.

I have used a script file from SourceForge and attach the results file hereto.

I have not done code entry before so apologies if not correctly stored in this document.

Hope this provides sufficient information to enable you to help.

Many thanks 

keentolearn

---------------------------------------------------------------------------
```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,199,154    51,199,092   7 HPFS/NTFS
/dev/sda2          51,199,155   390,716,864   339,517,710   f W95 Ext d (LBA)
/dev/sda5          51,199,218    81,529,874    30,330,657  83 Linux
/dev/sda6          81,529,938    91,136,744     9,606,807   7 HPFS/NTFS
/dev/sda7          91,136,808    93,193,064     2,056,257   7 HPFS/NTFS
/dev/sda8          93,193,128    97,289,639     4,096,512   7 HPFS/NTFS
/dev/sda9          97,289,703   300,062,069   202,772,367   7 HPFS/NTFS
/dev/sda10        300,062,133   390,716,864    90,654,732   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,126   625,137,344   625,121,219   f W95 Ext d (LBA)
/dev/sdb5              16,128     4,112,639     4,096,512   7 HPFS/NTFS
/dev/sdb6           4,112,703   106,446,689   102,333,987   7 HPFS/NTFS
/dev/sdb7         106,446,753   147,283,919    40,837,167   7 HPFS/NTFS
/dev/sdb8         147,283,983   290,455,199   143,171,217   7 HPFS/NTFS
/dev/sdb9         290,455,263   331,292,429    40,837,167   7 HPFS/NTFS
/dev/sdb10        331,292,493   597,007,529   265,715,037   7 HPFS/NTFS
/dev/sdb11        597,039,723   623,048,894    26,009,172  83 Linux
/dev/sdb12        623,048,958   625,137,344     2,088,387  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0480CBD980CBCF7C                       ntfs       XP + APPs                     
/dev/sda10       58962D2DEE634604                       ntfs       BACKUPS                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        43d55c4b-0c33-44c9-9217-cd3884b42e3f   ext4                                     
/dev/sda6        47C0A11CDE3D7DA4                       ntfs       RESERVED                      
/dev/sda7        A1716A80F40A5AB1                       ntfs       TEMP FILES                    
/dev/sda8        00E2DBDB78F5F690                       ntfs       RESERVED                      
/dev/sda9        1ACC5C3CE58C0D11                       ntfs       VIDEO DATA                    
/dev/sda: PTTYPE="dos" 
/dev/sdb10       D6D80ED4D80EB333                       ntfs       Video (D2)                    
/dev/sdb11       1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf   ext4                                     
/dev/sdb12       096fe465-3538-4549-9526-276cf83b9a88   swap                                     
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        E044017D44015824                       ntfs       Swap File (D2)                
/dev/sdb6        5AEC0415EC03EA59                       ntfs       Data (D2)                     
/dev/sdb7        965806B058068F65                       ntfs       Temp Disk Images (D2)         
/dev/sdb8        2E98096898092FBF                       ntfs       Backups (D2)                  
/dev/sdb9        221C0C211C0BEF1B                       ntfs       Reserved 2 (D2)               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptOut

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 43d55c4b-0c33-44c9-9217-cd3884b42e3f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 43d55c4b-0c33-44c9-9217-cd3884b42e3f
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 43d55c4b-0c33-44c9-9217-cd3884b42e3f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=43d55c4b-0c33-44c9-9217-cd3884b42e3f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 43d55c4b-0c33-44c9-9217-cd3884b42e3f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=43d55c4b-0c33-44c9-9217-cd3884b42e3f ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 43d55c4b-0c33-44c9-9217-cd3884b42e3f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 43d55c4b-0c33-44c9-9217-cd3884b42e3f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=43d55c4b-0c33-44c9-9217-cd3884b42e3f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb12 during installation
UUID=096fe465-3538-4549-9526-276cf83b9a88 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  35.4GB: boot/grub/core.img
  28.7GB: boot/grub/grub.cfg
  29.0GB: boot/initrd.img-2.6.35-22-generic
  35.4GB: boot/vmlinuz-2.6.35-22-generic
  29.0GB: initrd.img
  35.4GB: vmlinuz

========================== sdb11/boot/grub/grub.cfg: ==========================

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
set root='(hd1,11)'
search --no-floppy --fs-uuid --set 1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf
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
set root='(hd1,11)'
search --no-floppy --fs-uuid --set 1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set 1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set 1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set 1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set 1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set 1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set 1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set 1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set 1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0480cbd980cbcf7c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9a0d7a0d-d8c5-47d3-ad1b-16326eabc45e
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=9a0d7a0d-d8c5-47d3-ad1b-16326eabc45e ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9a0d7a0d-d8c5-47d3-ad1b-16326eabc45e
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=9a0d7a0d-d8c5-47d3-ad1b-16326eabc45e ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9a0d7a0d-d8c5-47d3-ad1b-16326eabc45e
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=9a0d7a0d-d8c5-47d3-ad1b-16326eabc45e ro quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9a0d7a0d-d8c5-47d3-ad1b-16326eabc45e
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=9a0d7a0d-d8c5-47d3-ad1b-16326eabc45e ro single
    initrd /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb11 during installation
UUID=1d209ceb-3e4f-4600-9eb2-a4ffe0cd54cf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb12 during installation
UUID=096fe465-3538-4549-9526-276cf83b9a88 none            swap    sw              0       0

=================== sdb11: Location of files loaded by Grub: ===================


 317.0GB: boot/grub/core.img
 316.9GB: boot/grub/grub.cfg
 317.0GB: boot/initrd.img-2.6.32-23-generic
 317.5GB: boot/initrd.img-2.6.32-24-generic
 317.6GB: boot/initrd.img-2.6.32-25-generic
 316.9GB: boot/vmlinuz-2.6.32-23-generic
 317.4GB: boot/vmlinuz-2.6.32-24-generic
 317.4GB: boot/vmlinuz-2.6.32-25-generic
 317.6GB: initrd.img
 317.5GB: initrd.img.old
 317.4GB: vmlinuz
 317.4GB: vmlinuz.old

```

---

### Post by oldfred on 2010-11-27
You are booting from sda5 which should be the 10.10. 

The grub.cfg in your other install in sdb11 shows both Ubuntus and the windows. Did you run the update-grub while on sdb11? But it does not look like you can get there except when you did the initial upgrade.

I would try rerunning the sudo update-grub and see what happens.

---

### Post by keentolearn on 2010-11-28
No, I did not touch sdb11 which is U10.04, I selected manually from menu and did not change default from there so did not use "sudo update-grub" on that system. Only used it on U10.10 on sda5. I decided not to put too  much down in initial post.

The only thing that concerns me about doing anything myself without checking with wiser/experienced parties is that U10.10 i snow my ONLY access to the internet to get help, I have no other way.

One other thing that I discovered is that I think that U10.04 may be running with Grub legacy from its original upgrade from U9.04 and I'm sure that I did see a "grub-legacy" folder on that partition.

I was wondering whether it would be worth removing the files on the U10.04 partition and re-install it again, hoping that I could get rid of any reference to Grub Legacy. Not to say that I understand the affects of my suggestion  in relation to re-booting 'calculations' carried out by its new system/version.

Just to check, the running of "sudo update-grub" in U 10.10 as I understand little of exactly what happens, I gather that it reads all relevant system/partition data and starts work afresh on a new setup. Is there much risk of this causing a disaster by losing the only system I have left.

Many thanks for your time and effort to assist me it is very much appreciated at this end, thanks

keentolearn

---

### Post by oldfred on 2010-11-28
While you should be able to use grub legacy to boot, grub2 & grub legacy do not seem to get along well. It is better to totally uninstall both and reinstall one. I would try that before reinstalling.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by keentolearn on 2010-11-28
Thank you for your reply. If I decide to remove both will I be able to access Win Xp. ie does the mbr of the Win XP position get rewritten on Grub's removal, so that Win XP re-appears. That is my continued "lack-of-confidence item" since I would like to have one system to do the web contacting. If the answer to that is that it will return the correct settings of the MBR to Boot Windows XP then I can fairly easily "correctly" re-install the two Ubuntu versions. I now realise that I could get onto the web via a live-disk session and should therefore be able to access this thread for any further advice. Sorry about asking all the questions but that is the way I learn and build confidence. I have plenty of ideas, it's just knowing which one's are right for the job.

Many thanks for your speedy help and comments.

keentolearn

---

### Post by oldfred on 2010-11-28
No, uninstalling Ubuntu will leave the grub in the MBR looking for the rest of grub that has been deleted.

You can install lilo from a Ubuntu liveCD that works just like windows in jumping to the PBR - partition boot sector. Or you can run fixMBR from a windows repair/XP install disk.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
FIXMBR  C:  #do not run if you still want grub in the MBR

---

### Post by keentolearn on 2010-11-28
Sorry for dragging this out a little, forgive me as I don't think I,ve ever attempted that before. So I will talk to myself, now. Run Live disk booting from that, and Remove U10.04 say re-format the partition to clear off all data etc. Then repeat process for second U10.10. Continue similar live-disk process and re-install both, one at a time after each other. Have I got that about right. I'm only a 68 year-old learner on Linux systems.

keentolearn

---

### Post by oldfred on 2010-11-28
If you are reinstalling to the same partitions you do not have to erase anything in advance. If you use manual install it lets you choose which partition is / (root) & what format; and it automatically finds swap. If you have a /home you should also specify it but do not format.

Just keep track of which partition is which, I have a bunch and have installed to the wrong one. Which every boot loader you want in charge, should be the one you install second as that will be the last one installed into the MBR. I would install the newest last as it has the newer version of grub2.

You do have good backups? Did you give up on trying to repair? We spend days trying to fix things. (But we will not tell you that you can reinstall in about an hour:))

---

### Post by keentolearn on 2010-11-28
Sorry for dragging this out a little, forgive me as I don't think I,ve ever attempted that before. So I will talk to myself, now. Run Live disk booting from that, and Remove U10.04 say re-format the partition to clear off all data etc. Then repeat process for second U10.10. Continue similar live-disk process and re-install both, one at a time after each other. Have I got that about right. I'm only a 68 year-old learner on Linux systems.

Sorry but I do not know what Lilo is although I think I have heard about it. Up until computers were invented Lilos were plastic air floats that you used for swimming practise, at least that is what they were calle din the UK. Ha Ha.

keentolearn

---

### Post by keentolearn on 2010-11-28
Very sorry about the reat + joke, pressed wrong buttons. Thought I was using quick reply but just found the little icon, better.

When you say "second one you install" above do you mean 1-XP already installed don't touch. 2 U1004 No1. 3.U1010 No2. ie that is the second one referred to. Is the boot menu with all 3 systems automatically produced by grub after/during this process, so that a menu will show XP, then XP +U1004 then Xp+U1004 +U1010. Or am I wrong

---

### Post by oldfred on 2010-11-28
You are correct.

If you install 10.04 as the first install, it should find windows and let you boot either. Then if you install 10.10 it will find all three and be the grub2 in the MBR. Then 10.10 will be the first choice in the menu.

If you choose to boot 10.04 and run sudo update-grub it will also find 10.10, but it then will be at the bottom of the list, but you will not normally see that menu since the default boot is grub2 to the grub install & menu from 10.10.

---

### Post by keentolearn on 2010-11-29
Up to this point I thought I was doing well, so thinking aloud, I am now a little confused. I thought that I had read in my magazine that U1004 and U1010 both were using Grub2. I then spotted a folder in the 1004 partition which was called Grub Legacy and another file called "upgrade-from-grub-legacy" (does not necessarily mean that they being used at this time though). I performed a clean install of U1004 [using magazine dvd from LinuxFormat UK]. Am I right in assuming that at that install stage Grub Legacy from the earlier U9.10 was installed in the mbr so the U1004 installation was automatically based on Grub Legacy. If I am correct, as a result when I installed U1004 it operated under Grub Legacy.

I would prefer to make the changes now to update U1004 so that it operates fully on Grub2 and Legacy version is 'removed' and replaced by Grub2. Since I assume that unless I write to the mbr with Grub2 I will perpetuate the problem of grub legacy for my next update re-install. If, having installed U1004 as you suggest,  can I then update it so that it removes Grub Legacy and installs Grub2 and removes the problem 'before' my re-install of the 2nd system U1010. 

Also can I set the default to "always-being-Win-XP". Where the two Ubuntu systems are positioned in the menu does not seem to be a problem, as long as I have sufficient time to arrow up/down and select the desired ubuntu version I am OK. It would again also mean that I could use the same process each time I do updating.

Another major problem which I have not mentioned is that my dear wife loves to use the computer also and in the last 4/5 weeks has been playing games on Ubuntu. She is far from a happy bunny because there are other craft things she needs to use also on XP. I therefore need to set the default operating system to XP in the boot menu asap otherwise my retired way of life may deteriorate very quickly! I'm sure you understand.

Many thanks yet again for your help

keentolearn

---

### Post by oldfred on 2010-11-29
If you do a new install of 10.10 you will be booting only with the newest grub2.

You can convert your install of 10.04 to grub2 and the best way is by drs305 where you uninstall both grub legacy & grub2 and then reinstall just grub2. You can do this while booted into 10.04, you do not have to chroot. See note in instructions.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You can edit the grub config file to set defaults, but it is easier just to use SUM.
Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Manual way:
find your windows entry in this and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by keentolearn on 2010-11-29
Thanks for that, just what I wanted to hear. Might take me a couple of days now to get sorted. I will let you know how I get on . Thanks again.

Keentolearn

---

### Post by keentolearn on 2011-01-06
First Happy New Year and hope that you had a very nice Christmas. Very sorry for the long delay. I decided that I could no longer go on with the existing situation without normal use of the PC and XP in particular. So I bit the bullet, looked up how to use fixmbr with Recovery Console and now am using PC with XP only. This is the first time that I can make enough time to make any further progress due to family at Xmas etc. I have now decided that I will only have one version of Ubuntu (ie DEV 10.10) and not 2 versions. I will also use the other partition for MY Documents (whatever Ubuntu calls it, since I have already forgotten, not having used Ubuntu seriously for many weeks.

I have installed the DOS Recovery Console to help prevent the same mistake in future and giving easy access to "fixmbr". MS Win XP shows this with a menu along with Win XP. Will the installation of Grub2 leave the menu as described or does it remove it and replace with its own menu system.

Thanks, your help is really appreciated. Once again sorry for the TOO-LONG delay in response.

Thanks keentolearn

I will contact you further, later for more accurate detailed help as I prepare to carry out the new installation.

Keentolearn[/QUOTE]

---

