---
title: "Dual boot Problem"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by fattony2045 on 2010-05-08
Hi all,

Yesterday upgraded ubuntu from 9.10 to 10.4, I have Windows 7 installed, but now I can't boot in windows.

Thanks for your help.

Here are my results :

  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 59296992 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 59296992 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb6 and 
                       looks at sector 59296992 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb7 and 
                       looks at sector 59296992 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb4 and 
                       looks at sector 59296992 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   312,578,047   312,576,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848    51,202,047    50,995,200   7 HPFS/NTFS
/dev/sdb3          51,215,220   112,631,714    61,416,495   5 Extended
/dev/sdb5          51,215,283    59,006,744     7,791,462  82 Linux swap / Solaris
/dev/sdb6          59,006,808    78,541,784    19,534,977  83 Linux
/dev/sdb7          78,541,848   112,631,714    34,089,867  83 Linux
/dev/sdb4         112,642,048   312,578,047   199,936,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9AF8E8AFF8E88AB9                       ntfs       Respaldos                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        166203D96203BD0D                       ntfs       System Reserved               
/dev/sdb2        62A82EF3A82EC57F                       ntfs       Windows 7                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb4        98F637A5F6378314                       ntfs       Pirasoft                      
/dev/sdb5        a1201600-afda-4564-aade-fc9c204a338b   swap                                     
/dev/sdb6        06240600-98fa-46b5-b134-4e605d2fe847   ext4       Files /                       
/dev/sdb7        a7587c4c-6e7a-4946-a6e4-e83a21164f3f   ext4       Files /home                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb7        /home                    ext4       (rw)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 06240600-98fa-46b5-b134-4e605d2fe847
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
search --no-floppy --fs-uuid --set 06240600-98fa-46b5-b134-4e605d2fe847
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
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 06240600-98fa-46b5-b134-4e605d2fe847
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=06240600-98fa-46b5-b134-4e605d2fe847 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 06240600-98fa-46b5-b134-4e605d2fe847
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=06240600-98fa-46b5-b134-4e605d2fe847 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 06240600-98fa-46b5-b134-4e605d2fe847
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=06240600-98fa-46b5-b134-4e605d2fe847 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 06240600-98fa-46b5-b134-4e605d2fe847
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=06240600-98fa-46b5-b134-4e605d2fe847 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 06240600-98fa-46b5-b134-4e605d2fe847
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 06240600-98fa-46b5-b134-4e605d2fe847
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 166203d96203bd0d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=06240600-98fa-46b5-b134-4e605d2fe847 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=a7587c4c-6e7a-4946-a6e4-e83a21164f3f /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a1201600-afda-4564-aade-fc9c204a338b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  30.3GB: boot/grub/core.img
  30.5GB: boot/grub/grub.cfg
  36.7GB: boot/initrd.img-2.6.31-21-generic
  37.8GB: boot/initrd.img-2.6.32-22-generic
  34.5GB: boot/vmlinuz-2.6.31-21-generic
  34.5GB: boot/vmlinuz-2.6.32-22-generic
  37.8GB: initrd.img
  36.7GB: initrd.img.old
  34.5GB: vmlinuz
  34.5GB: vmlinuz.old

---

### Post by frantid on 2010-05-08
Did you get hit with this [http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)  If you did can you please add your comments to the bug in launchpad, filed by kansasnoob.

As in that thread, grub has been installed in all the major partitions.  Hopefully you can restore win7's boot partition by following 

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Otherwise you will need to boot off the win7 dvd and fixboot.

---

### Post by kansasnoob on 2010-05-08
> **frantid said:**
> Did you get hit with this [http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)  If you did can you please add your comments to the bug in launchpad, filed by kansasnoob.

As in that thread, grub has been installed in all the major partitions.  Hopefully you can restore win7's boot partition by following 

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Otherwise you will need to boot off the win7 dvd and fixboot.

+1! If you follow this carefully:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

That should fix it.

---

### Post by fattony2045 on 2010-05-08
YEESSSS !!

That work, follow the instructions carefully, and everything work well. 

What I did last was  boot off the win7 dvd, go to command prompt and run the command Bootrec /fixboot and finally I can use Ubuntu and Windows.

Thank you very much. :p

---

