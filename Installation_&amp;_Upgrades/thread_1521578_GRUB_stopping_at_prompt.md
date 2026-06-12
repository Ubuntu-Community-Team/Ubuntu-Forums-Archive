---
title: "GRUB stopping at prompt"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Dara Javaherian on 2010-07-01
When I start up, GRUB appears to be loading, then it goes into a simple GRUB prompt. Like this:

grub>

This happened after I deleted a partition. I'm on a live CD sending this. Could anybody help me?

---

### Post by Dara Javaherian on 2010-07-01
Could anybody help me? I tried update-grub but it didn't work for some reason.

---

### Post by Dara Javaherian on 2010-07-01
Ok, so I ran the following commands:

```

sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install  --root-directory=/mnt /dev/sda
sudo umount /mnt

```Now I can load up my Linux partition, However, my Windows XP partition will not load up. When I select it from the GRUB bootloader, a black screen comes up. Is there anything I can do to fix this?

P.S.  This is the output of fdisk -l:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10836    87040138+   7  HPFS/NTFS
/dev/sda2           10837       14593    30178072    f  W95 Ext'd (LBA)
/dev/sda5           10837       14472    29206138+  83  Linux
/dev/sda6           14473       14593      971901   82  Linux swap / Solaris

```


Could someone please help? :confused::confused:

---

### Post by Sanjeevtrip on 2010-07-01
Can you past the grub menu.lst(it has the example entry), 
check if the boot loaders for windows is put correctly

# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1

---

### Post by Dara Javaherian on 2010-07-01
> **Sanjeevtrip said:**
> Can you past the grub menu.lst(it has the example entry), 
check if the boot loaders for windows is put correctly

# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1

Where would I find that? I don't know if I'm using GRUB or GRUB2

---

### Post by confused57 on 2010-07-01
Someone should be able to help you if you can post the output of the bootinfo script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Dara Javaherian on 2010-07-01
Ok, I found it. Here it is; in all it's glory:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3cd9f74a-8524-421a-b31d-52de2d90d54c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Chainload into GRUB 2
root        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Dara Javaherian on 2010-07-01
> **confused57 said:**
> Someone should be able to help you if you can post the output of the bootinfo script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Great! Here you go!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 215384715 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 215450003 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   174,080,339   174,080,277   7 HPFS/NTFS
/dev/sda2         174,080,401   234,436,544    60,356,144   f W95 Ext d (LBA)
/dev/sda5         174,080,403   232,492,679    58,412,277  83 Linux
/dev/sda6         232,492,743   234,436,544     1,943,802  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E44CC4364CC404F0                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3cd9f74a-8524-421a-b31d-52de2d90d54c   ext3                                     
/dev/sda6        e94ab028-df00-4b14-a9c8-b98aa6246b28   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)
/dev/sr0         /media/Ubuntu 10.04 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3cd9f74a-8524-421a-b31d-52de2d90d54c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Chainload into GRUB 2
root        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        3cd9f74a-8524-421a-b31d-52de2d90d54c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 3cd9f74a-8524-421a-b31d-52de2d90d54c
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
search --no-floppy --fs-uuid --set 3cd9f74a-8524-421a-b31d-52de2d90d54c
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
    search --no-floppy --fs-uuid --set 3cd9f74a-8524-421a-b31d-52de2d90d54c
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3cd9f74a-8524-421a-b31d-52de2d90d54c
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3cd9f74a-8524-421a-b31d-52de2d90d54c
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3cd9f74a-8524-421a-b31d-52de2d90d54c
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3cd9f74a-8524-421a-b31d-52de2d90d54c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3cd9f74a-8524-421a-b31d-52de2d90d54c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e44cc4364cc404f0
    drivemap -s (hd0) ${root}
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
UUID=3cd9f74a-8524-421a-b31d-52de2d90d54c /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e94ab028-df00-4b14-a9c8-b98aa6246b28 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 110.2GB: boot/grub/core.img
 110.3GB: boot/grub/grub.cfg
 110.2GB: boot/grub/menu.lst
 110.2GB: boot/initrd.img-2.6.32-21-generic
 110.2GB: boot/initrd.img-2.6.32-23-generic
 110.2GB: boot/vmlinuz-2.6.32-21-generic
 110.2GB: boot/vmlinuz-2.6.32-23-generic
 110.2GB: initrd.img
 110.2GB: initrd.img.old
 110.2GB: vmlinuz
 110.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  cd 20 f3 3c 01 82 8e 23  ca 0b 19 ab 1d 2e 5a f1  |. .<...#......Z.|
00000010  3c 7a ad 4c 3a ac b8 53  e6 cd 5d 2f 48 66 68 50  |<z.L:..S..]/HfhP|
00000020  b2 0e 26 17 0e 11 cc 22  17 e2 98 09 f5 bc 42 ba  |..&...."......B.|
00000030  33 df c5 ca 81 ce a6 c1  a8 b4 62 71 c8 d7 eb c2  |3.........bq....|
00000040  4a 2f 0c 9d e4 61 8d 84  fe 26 79 f1 df fc 77 de  |J/...a...&y...w.|
00000050  6c 4d ef ea 4f 3b 1c 9d  08 46 08 29 00 bf fb d7  |lM..O;...F.)....|
00000060  9d 55 00 aa b8 e1 2d 58  f1 47 07 fe 56 ac 0b 4f  |.U....-X.G..V..O|
00000070  e4 46 66 58 9d 11 3f af  18 80 55 91 40 b8 72 11  |.FfX..?...U.@.r.|
00000080  7a b4 c6 b1 ce 92 78 47  92 b0 78 5f 09 50 6d 4c  |z.....xG..x_.PmL|
00000090  6e 44 ad 9e cd bc 68 2f  14 26 ce 1d 71 81 7a 7a  |nD....h/.&..q.zz|
000000a0  0c c3 b3 ed 42 1a 35 91  8d 17 93 73 5a 23 6a 33  |....B.5....sZ#j3|
000000b0  6a 5e 73 e1 9e 1d ff fd  e7 eb 9f 26 bf 45 cb 9b  |j^s........&.E..|
000000c0  78 bd d2 78 07 7c 9d 19  e9 75 63 e8 29 00 a8 52  |x..x.|...uc.)..R|
000000d0  25 7b 38 ac a8 e4 8d 5e  f6 31 5d 61 f5 5f 80 61  |%{8....^.1]a._.a|
000000e0  b2 ca 40 28 ef 14 6f 41  5e e5 5e e0 f6 27 18 d2  |..@(..oA^.^..'..|
000000f0  7f 35 b4 2e 15 d5 75 a1  4f 81 24 68 4c 14 04 e8  |.5....u.O.$hL...|
00000100  d8 39 14 0a 83 21 17 58  23 22 22 27 49 5c 8c 9a  |.9...!.X#""'I\..|
00000110  0c fb f1 cf 7f bd fb c8  c7 3f 7b e3 bb 03 3e ff  |.........?{...>.|
00000120  7f c0 12 28 e4 eb 4d 8d  73 da c0 d7 c1 67 55 ef  |...(..M.s....gU.|
00000130  10 6e f1 25 68 8c 55 df  25 09 49 41 c1 47 f0 31  |.n.%h.U.%.IA.G.1|
00000140  2f ae 73 e0 78 0e 5b 00  ef 79 a0 58 67 f5 32 cf  |/.s.x.[..y.Xg.2.|
00000150  e7 0b 07 35 28 c8 58 ee  b2 7f 40 a8 d5 a4 f5 10  |...5(.X...@.....|
00000160  cc 70 4e 2a f0 ad 9d 40  40 d3 b2 82 58 39 18 b0  |.pN*...@@...X9..|
00000170  c9 f4 a4 69 52 04 62 37  30 da b0 ce 20 18 8b 24  |...iR.b70... ..$|
00000180  d6 c6 2b 80 a4 e4 aa d9  a3 2a 2c 1a ab 5e 24 13  |..+......*,..^$.|
00000190  be 96 38 37 a3 38 f7 bf  5d e7 ff f1 37 8d 1e fd  |..87.8..]...7...|
000001a0  e4 ef 17 b5 cf 72 49 d2  30 35 58 ea 3a 5c 5e 25  |.....rI.05X.:\^%|
000001b0  a8 1f 51 15 8e 71 b2 41  47 ec 4a 8d 72 14 00 fe  |..Q..q.AG.J.r...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 f5 4c 7b 03 00 fe  |...........L{...|
000001d0  ff ff 05 fe ff ff f7 4c  7b 03 39 a9 1d 00 00 00  |.......L{.9.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo0/sda1: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

I'm suspicious of sda2. In theory, it doesn't exist.

---

### Post by confused57 on 2010-07-01
It looks like you upgraded and kept grub-legacy, you could just comment out the Windows example located above ###BEGIN AUTOMAGIC KERNELS LIST:

---

### Post by Sanjeevtrip on 2010-07-01
it seems your windows boot entry is missing,
try this on your grub prompt, type whats after the grub>
and after tying boot, you should get windows booted, if it works , thats what you need to enter in the menu.lst, the same file what you pasted

hope that works


grub> root  (hd0,0)
grub> makeactive
grub> chainloader    +1
grub> boot

if the above works put this in your menu.lst

title        Windows 
root        (hd0,0)
makeactive
chainloader    +1

---

### Post by Dara Javaherian on 2010-07-01
> **confused57 said:**
> It looks like you upgraded and kept grub-legacy, you could just comment out the Windows example located above ###BEGIN AUTOMAGIC KERNELS LIST:

Like this?
```

#
# examples
#
## title        Windows 95/98/NT/2000
## root        (hd0,0)
## makeactive
## chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```

---

### Post by confused57 on 2010-07-01
It looks like you have grub-legacy, maybe from an upgrade to 10.04.  You could just comment out the example Window's entry in your menu.lst:
```
# examples
#
title        Windows XP
root        (hd0,0)
makeactive
chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```

Or you can put it at the very end of your menu.lst, after the line ###END AUTOMAGIC KERNELS LIST.

May not be a bad idea to back up your menu.lst, before editing:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

Added:  My previous post was an accident, pressed "Enter" before I was finished, didn't know it had been recorded.  
Looks like you're in good hands with Sanjeevtrip, who gave you the correct info previously.

---

### Post by Dara Javaherian on 2010-07-01
> **confused57 said:**
> It looks like you have grub-legacy, maybe from an upgrade to 10.04.  You could just comment out the example Window's entry in your menu.lst:
```
# examples
#
title        Windows XP
root        (hd0,0)
makeactive
chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```Or you can put it at the very end of your menu.lst, after the line ###END AUTOMAGIC KERNELS LIST.

May not be a bad idea to back up your menu.lst, before editing:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```Added:  My previous post was an accident, pressed "Enter" before I was finished, didn't know it had been recorded.  
Looks like you're in good hands with Sanjeevtrip, who gave you the correct info previously.

:( I did as you and Sanjeevtrip said, but with no luck :(

---

### Post by confused57 on 2010-07-01
Your Windows won't currently boot because the bootinfo script shows grub2 is installed to the boot sector of your Windows partition(sda1).  What you'll need to do is use Testdisk to repair your boot sector:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use a Windows XP install cd & run fixboot, as the instructions mention in the above link.

---

### Post by Dara Javaherian on 2010-07-01
> **confused57 said:**
> Your Windows won't currently boot because the bootinfo script shows grub2 is installed to the boot sector of your Windows partition(sda1).  What you'll need to do is use Testdisk to repair your boot sector:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use a Windows XP install cd & run fixboot, as the instructions mention in the above link.

Excellent! Thank you both so much! My problem is solved :D

---

