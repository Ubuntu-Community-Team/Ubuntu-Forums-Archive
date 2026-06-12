---
title: "can't boot into ubuntu 10.4"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by zapout on 2010-09-28
hi guys
i was trying to dual boot window 7 and ubuntu 10.4, but i accidentally delete the system reserved partition of window 7 while installing ubuntu, and left with only ubuntu
so i did a fresh installation of window 7 and now only OS available to boot in is window 7.:(

both the OS'es are on different hard drives
*here is the boot script info  * 
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    67,835,903    67,629,056   7 HPFS/NTFS
/dev/sda3          67,835,904   524,287,999   456,452,096   7 HPFS/NTFS
/dev/sda4         524,290,048   976,769,023   452,478,976   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1         264,192   488,517,631   488,253,440 Linux or Data
/dev/sdb2     488,517,632   944,513,023   455,995,392 Linux or Data
/dev/sdb3     944,515,072   976,771,071    32,256,000 Linux or Data

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 7851 MB, 7851737088 bytes
3 heads, 16 sectors/track, 319488 cylinders, total 15335424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             80    15,335,423    15,335,344   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2E9C26009C25C367                       ntfs       System Reserved               
/dev/sda2        D8962F01962EE02C                       ntfs                                     
/dev/sda3        9A28BFDB28BFB49B                       ntfs       WD                            
/dev/sda4        C6D40023D40017F7                       ntfs       WD                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D6E213A5E213893F                       ntfs       Seagate                       
/dev/sdb2        30D039FBD039C83C                       ntfs       Seagate                       
/dev/sdb3        e4d93dff-0d49-4e11-8f52-04f17359268c   ext4                                     
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        C4D9-3665                              vfat       CORSAIR                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set e4d93dff-0d49-4e11-8f52-04f17359268c
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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set e4d93dff-0d49-4e11-8f52-04f17359268c
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
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set e4d93dff-0d49-4e11-8f52-04f17359268c
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e4d93dff-0d49-4e11-8f52-04f17359268c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set e4d93dff-0d49-4e11-8f52-04f17359268c
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e4d93dff-0d49-4e11-8f52-04f17359268c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set e4d93dff-0d49-4e11-8f52-04f17359268c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set e4d93dff-0d49-4e11-8f52-04f17359268c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3cb4b875b4b832ee
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb3       /               ext4    errors=remount-ro 0       1

=================== sdb3: Location of files loaded by Grub: ===================


 485.9GB: boot/grub/core.img
 485.9GB: boot/grub/grub.cfg
 486.4GB: boot/initrd.img-2.6.32-24-generic
 486.5GB: boot/vmlinuz-2.6.32-24-generic
 486.4GB: initrd.img
 486.5GB: vmlinuz

```^^i was using flash drive to live boot ubuntu

I'm new to linux, so please guys help me out to fix ubuntu:)
thanks

---

### Post by TeoBigusGeekus on 2010-09-28
You need to restore grub
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7")

---

### Post by zapout on 2010-09-28
^^ didn't work:confused:
only showing window 7 in boot menu

can u please give step by step instructions.

---

### Post by zapout on 2010-09-28
this one worked for me
[http://www.ohbuntu.blogspot.com/2009/11/repair-grub2-after-install-windows-7.html](http://www.ohbuntu.blogspot.com/2009/11/repair-grub2-after-install-windows-7.html)
but now I'm unable to boot into window 7:(

and ```
sudo update-grub
``` not working to restore window

window 7 is on the OS list but when i select to boot it, it show error
"there is no device X(x is the uuid of window 7 boot drive)
press any key to continue"

please help:(

---

### Post by zapout on 2010-09-28
here is the boot entry of window 7

```
insmod ntfs
set root=' (hd0,1)
search --no-floppy --fs-uuid --set 2e9c26009c25c367
chainloader +1
```

please guys help me out.
I'm not able to get it run dual boot:(

---

