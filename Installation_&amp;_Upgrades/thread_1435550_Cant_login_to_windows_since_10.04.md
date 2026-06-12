---
title: "Cant login to windows since 10.04"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by azzy101 on 2010-03-21
Hi, i upgraded to the 10.04 beta today . i upgraded from 9.10 64bit. I am on a dual boot system, Ubuntu is on my secondary hard-drive and windows xp is on my primary hard drive.


Since upgrading to the 10.04 beta i cannot login into XP, GRUB restarts when i select it. selecting Ubuntu works though.  during the upgrade process GRUB prompted me to select some options and to be quite honest i was not entirely sure what to select, regardless i tried three times to select options, twice it rejected me from selecting all of the ( what seemed to be) disks. until i tried selecting two out of the 5 names on the list it gave me.

Im not sure what to do now, and i am not sure what exactly i did wrong.

---

### Post by coffeecat on 2010-03-21
Let's get some information about your system. Have a look here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Use the link on that page to download the Boot Info Script. Then run it and post the contents of the resultant RESULTS.txt. Please enclose the results text in [noparse]```

```[/noparse] tags to make it readable. You can highlight the text in the reply box and click on the '#' to wrap it in code tags.

---

### Post by azzy101 on 2010-03-21
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1881763251 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1881761715 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
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
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,503,999 1,953,503,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,881,340,019 1,881,339,957   7 HPFS/NTFS
/dev/sdb2       1,881,340,020 2,930,272,064 1,048,932,045   5 Extended
/dev/sdb5       1,881,340,083 2,918,223,314 1,036,883,232  83 Linux
/dev/sdb6       2,918,223,378 2,930,272,064    12,048,687  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9CB84FA2B84F7A32                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D0AAFC95AAFC7974                       ntfs       Barracuda                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        9d06c47c-d244-4e69-b364-9f3b61e1f7ae   ext4                                     
/dev/sdb6        b7290014-05ab-4aa2-97d7-c552a9de33f5   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 9d06c47c-d244-4e69-b364-9f3b61e1f7ae
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
search --no-floppy --fs-uuid --set 9d06c47c-d244-4e69-b364-9f3b61e1f7ae
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9d06c47c-d244-4e69-b364-9f3b61e1f7ae
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=9d06c47c-d244-4e69-b364-9f3b61e1f7ae ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9d06c47c-d244-4e69-b364-9f3b61e1f7ae
    echo    Loading Linux 2.6.32-16-generic ...
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=9d06c47c-d244-4e69-b364-9f3b61e1f7ae ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9d06c47c-d244-4e69-b364-9f3b61e1f7ae
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=9d06c47c-d244-4e69-b364-9f3b61e1f7ae ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9d06c47c-d244-4e69-b364-9f3b61e1f7ae
    echo    Loading Linux 2.6.31-20-generic ...
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=9d06c47c-d244-4e69-b364-9f3b61e1f7ae ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9d06c47c-d244-4e69-b364-9f3b61e1f7ae
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9d06c47c-d244-4e69-b364-9f3b61e1f7ae
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9cb84fa2b84f7a32
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=9d06c47c-d244-4e69-b364-9f3b61e1f7ae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=b7290014-05ab-4aa2-97d7-c552a9de33f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 963.4GB: boot/grub/core.img
 963.6GB: boot/grub/grub.cfg
 967.4GB: boot/initrd.img-2.6.31-20-generic
 967.6GB: boot/initrd.img-2.6.32-16-generic
 966.0GB: boot/vmlinuz-2.6.31-20-generic
 967.2GB: boot/vmlinuz-2.6.32-16-generic
 967.6GB: initrd.img
 967.4GB: initrd.img.old
 967.2GB: vmlinuz
 966.0GB: vmlinuz.old
```

hope this helps

---

### Post by coffeecat on 2010-03-21
Somehow, you've managed to get grub to write grub stage 2 to the Windows C: partition (sda1), overwriting the Windows XP boot sector. You've also done the same to sdb1, but as that looks as though it might be a data partition, that won't matter. Have a look at your boot script information for sda1. Now compare that with the way it should be:

```

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /ntldr /ntdetect.com
```That should be easy to repair, but only if you have a Windows XP installation CD. That needs to be a proper Microsoft one, not a manufacturer's restore disc. If you do have one, you need to boot up with it, select "R" at the welcome screen, and run "FIXBOOT" from the command prompt. DO NOT run "FIXMBR". This will overwrite grub stage 1 in the mbr with the Windows MBR. Then nothing will boot and you will have to reinstall grub.

If you don't have access to a Windows install disc, post back and I'll see if I can find links for a freeware alternative.

---

### Post by azzy101 on 2010-03-21
i have my Windows Disk, thanks for the help - i'll try  FIXBOOT.

---

