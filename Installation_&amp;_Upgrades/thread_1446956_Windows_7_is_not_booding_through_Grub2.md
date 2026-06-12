---
title: "Windows 7 is not booding through Grub2"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by harti on 2010-04-04
I have windows 7 in RAID 0 and installed Ubuntu 9.10 to another Sata drive.
Ubuntu is working fine but if I try to boot windows in the Grub2 loader it goes do error and lets my to restart. 
I have finish the windows system recovery and setup repair several times and it won't find any problems. 
I can't get to windows loader.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/mapper/pdc_chfbjcefbd and looks for 
    (UUID=c859191e-3279-4ecc-a569-4dfc8e1789b3)/boot/grub.

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

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

pdc_chfbjcefbd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

pdc_chfbjcefbd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1010100f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   195,318,269   195,318,207  83 Linux
/dev/sdb2         195,318,270   625,137,344   429,819,075   5 Extended
/dev/sdb5         195,318,333   607,626,494   412,308,162  83 Linux
/dev/sdb6         607,626,558   625,137,344    17,510,787  82 Linux swap / Solaris


Drive: pdc_chfbjcefbd ___________________ _____________________________________________________

Disk /dev/mapper/pdc_chfbjcefbd: 2000.3 GB, 2000275505152 bytes
255 heads, 63 sectors/track, 243186 cylinders, total 3906788096 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1339951b

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_chfbjcefbd1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/pdc_chfbjcefbd2            206,848 3,906,785,279 3,906,578,432   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/pdc_chfbjcefbd1 D61E09DC1E09B691                       ntfs       System Reserved               
/dev/mapper/pdc_chfbjcefbd2 3ED40C10D40BC95B                       ntfs                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        06735678-17b8-4bee-9328-30444111e810   ext4                                     
/dev/sdb5        c859191e-3279-4ecc-a569-4dfc8e1789b3   ext4                                     
/dev/sdb6        73413913-d9fb-484f-ae1c-2683b0f2c399   swap                                     
/dev/sdc                                                promise_fasttrack_raid_member                               

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_chfbjcefbd
pdc_chfbjcefbd1
pdc_chfbjcefbd2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/mapper/pdc_chfbjcefbd2 /media/3ED40C10D40BC95B  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/mapper/pdc_chfbjcefbd1 /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
search --no-floppy --fs-uuid --set c859191e-3279-4ecc-a569-4dfc8e1789b3
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set c859191e-3279-4ecc-a569-4dfc8e1789b3
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=c859191e-3279-4ecc-a569-4dfc8e1789b3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set c859191e-3279-4ecc-a569-4dfc8e1789b3
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=c859191e-3279-4ecc-a569-4dfc8e1789b3 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set c859191e-3279-4ecc-a569-4dfc8e1789b3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c859191e-3279-4ecc-a569-4dfc8e1789b3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set c859191e-3279-4ecc-a569-4dfc8e1789b3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c859191e-3279-4ecc-a569-4dfc8e1789b3 ro single 
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
menuentry "Windows 7 (loader) (on /dev/mapper/pdc_chfbjcefbd1)" {
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=c859191e-3279-4ecc-a569-4dfc8e1789b3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=73413913-d9fb-484f-ae1c-2683b0f2c399 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 105.6GB: boot/grub/core.img
 100.3GB: boot/grub/grub.cfg
 100.6GB: boot/initrd.img-2.6.31-14-generic
 100.8GB: boot/initrd.img-2.6.31-20-generic
 100.5GB: boot/vmlinuz-2.6.31-14-generic
 100.7GB: boot/vmlinuz-2.6.31-20-generic
 100.8GB: initrd.img
 100.6GB: initrd.img.old
 100.7GB: vmlinuz
 100.5GB: vmlinuz.old
```

---

### Post by oldfred on 2010-04-04
I do not know raid, but I know it confuses things. I thought the desktop liveCD version would not work with raid only the server or the text based installer that had additional support for raid.

Your windows boot stanza is incomplete so grub did not find it correctly. I do not know the correct lines for a raid version but wonder if a pure chainboot to sda might work. Add to /etc/grub.d/40_custom and run sudo update-grub..

Satndard windows:
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
insmod fat
set root=(hd0,1)
search --no-floppy --fs-uuid --set 800e-1b1c
chainloader +1
}

Chainboot to sda to MBR not partition
# Entry N - Chainload another bootloader
menuentry "Chainload my OS" {
    set root=(hd0)
    chainloader +1
}

---

