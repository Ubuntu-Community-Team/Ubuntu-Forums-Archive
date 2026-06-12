---
title: "GRUB RESCUE thing and Ubuntu's taken over (I'm an absolute retard , please help!!)"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by JETLogistics on 2010-03-22
I have little knowledge of Ubuntu, however, I installed it nicely on my downstairs desktop on 9.10....
I tried 10.4 on my laptop, as a secondary O/S alongside Windows 7....
After setting it all up it I restarted and tried to go back to Windows 7, and it's now saying "Unknown File System - Grub rescue".

I've not a clue what to do, nor how to get my luscious Win7 and precious electronic belongings back - I'm a Windows tech not Ubuntu, so I turn to you, the geniuses of the Ubuntu world for urgent help!

I managed to boot off the disc and now have followed the instructions for the Boot Info - This is what I got:











                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048    24,782,847       204,800   7 HPFS/NTFS
/dev/sda3          24,782,848   391,365,119   366,582,272   7 HPFS/NTFS
/dev/sda4         391,368,703   604,155,903   212,787,201   f W95 Ext d (LBA)
/dev/sda5         391,368,704   595,431,423   204,062,720  83 Linux
/dev/sda6         595,433,472   604,155,903     8,722,432  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2063 MB, 2063597056 bytes
255 heads, 63 sectors/track, 250 cylinders, total 4030463 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     4,030,462     4,030,400   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        8A122B28122B18A9                       ntfs       SYSTEM RESERVED               
/dev/sda3        A80230D50230AA68                       ntfs       Packard Bell                  
/dev/sda4: PTTYPE="dos" 
/dev/sda5        16bb0166-dedb-4607-ad8c-4a72a63a502f   ext4                                     
/dev/sda6        cdae64c4-9105-449b-a544-ed86eae4bd3f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        401A-E204                              vfat       JACOB'S PEN                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/16bb0166-dedb-4607-ad8c-4a72a63a502f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/JACOB'S PEN       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda3        /media/Packard Bell      fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/SYSTEM RESERVED   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
search --no-floppy --fs-uuid --set 16bb0166-dedb-4607-ad8c-4a72a63a502f
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
search --no-floppy --fs-uuid --set 16bb0166-dedb-4607-ad8c-4a72a63a502f
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
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 16bb0166-dedb-4607-ad8c-4a72a63a502f
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=16bb0166-dedb-4607-ad8c-4a72a63a502f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 16bb0166-dedb-4607-ad8c-4a72a63a502f
    echo    Loading Linux 2.6.32-16-generic ...
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=16bb0166-dedb-4607-ad8c-4a72a63a502f ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 16bb0166-dedb-4607-ad8c-4a72a63a502f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 16bb0166-dedb-4607-ad8c-4a72a63a502f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set daa41c49a41c2b11
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 8a122b28122b18a9
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a80230d50230aa68
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
# / was on /dev/sda6 during installation
UUID=16bb0166-dedb-4607-ad8c-4a72a63a502f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=cdae64c4-9105-449b-a544-ed86eae4bd3f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 202.6GB: boot/grub/core.img
 256.3GB: boot/grub/grub.cfg
 202.6GB: boot/initrd.img-2.6.32-16-generic
 202.6GB: boot/vmlinuz-2.6.32-16-generic
 202.6GB: initrd.img
 202.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 








I don't know what it means, what I do with it, nor how it can help you guys, but all I know is from the moment I hit power, my laptop is next to dead. I don't know what to do. Is there a way I can stop it automatically trying to boot up Ubuntu (which seems to be the problem), going back to nice, old-fashioned and I know my way around it Win7 and I can wipe the partition that it is supposedly running off?


Thanks a lot, from Jacob (JETLogistics)

---

### Post by Megafag on 2010-03-22
> **JETLogistics said:**
> .I can wipe the partition that it is supposedly running off?

Dont do that, that will make everything worse.

I suggest you recover all of your windows data using a live disk and an external hard drive, then re-install windows.

it is possible (maybe) that if you wipe ubuntu and put a fresh install in its place it might work.

However there is probably a better solution.

---

### Post by JETLogistics on 2010-03-22
Don't worry, I don't know how the hell I did it, and don't ask to explain steps coz I tried about 10 different things, but I fixed it! Thank you for your help, Megafag, I really appreciate it!

Case solved! :D

---

