---
title: "Unable to boot in windows 7 after ubuntu install"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by gaur.puneet on 2010-05-28
Yesterday I installed Ubuntu on my laptop running windows 7. I chose the option of running both OS side by side. Now at the time of boot up these are the options available :-

[LIST=1]
[*]Ubuntu, with Linux 2.6 32-22-generic
[*]Ubuntu, with Linux 2.6 32-22-generic (recovery mode )
[*]Ubuntu, with Linux 2.6 32-22-generic
[*]Ubuntu, with Linux 2.6 32-22-generic (recovery mode)
[*]Memory Test (memtest 86+)
[*]Memory Test (memtest 86+)
[*]Windows 7 (loader) (on /dev/sda1)
[/LIST]
I am confused with these options & when I select windows 7, again the same screen appears.
At the time of installation the screen friezed & I restarted the installation, Is the problem arising due to this? Please inform what should I do?
I am totally new to Ubuntu, please guide me on this.

---

### Post by wilee-nilee on 2010-05-28
I would post this script to begin with in code tags. [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You should also confirm if you shrunk the W7 partition with the W7 partition manager or if you let Ubuntu shrink W7.

---

### Post by gaur.puneet on 2010-05-28
deleted

---

### Post by gaur.puneet on 2010-05-28
I have not shrunk the window 7 partition.

---

### Post by wilee-nilee on 2010-05-28
> **gaur.puneet said:**
> I have not shrunk the window 7 partition.

Would you please go back to the script and use the code tags as I showed in my 1st post. ;) It is very hard to read otherwise.

[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end

---

### Post by gaur.puneet on 2010-05-28
```
               

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 125741144 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   100,012,178   100,012,116   7 HPFS/NTFS
/dev/sda2         100,014,078   312,576,704   212,562,627   5 Extended
/dev/sda5         153,597,528   312,576,704   158,979,177   7 HPFS/NTFS
/dev/sda6         100,014,080   151,289,855    51,275,776  83 Linux
/dev/sda7         151,291,904   153,595,903     2,304,000  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2098082D980803CE                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        C98365AB31088A12                       ntfs       Puneet                        
/dev/sda6        30495c9b-5aef-4572-9e75-868807c86e2d   ext4                                     
/dev/sda7        cd775b43-fa89-494a-9a0f-ca8e9fa66ef5   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/2098082D980803CE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/Puneet            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
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
search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
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
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=30495c9b-5aef-4572-9e75-868807c86e2d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=30495c9b-5aef-4572-9e75-868807c86e2d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=30495c9b-5aef-4572-9e75-868807c86e2d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=30495c9b-5aef-4572-9e75-868807c86e2d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2098082d980803ce
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=30495c9b-5aef-4572-9e75-868807c86e2d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=cd775b43-fa89-494a-9a0f-ca8e9fa66ef5 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  64.3GB: boot/grub/core.img
  55.6GB: boot/grub/grub.cfg
  64.3GB: boot/initrd.img-2.6.32-21-generic
  64.3GB: boot/initrd.img-2.6.32-22-generic
  64.3GB: boot/vmlinuz-2.6.32-21-generic
  64.3GB: boot/vmlinuz-2.6.32-22-generic
  64.3GB: initrd.img
  64.3GB: initrd.img.old
  64.3GB: vmlinuz
  64.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  41 42 52 52 52 51 41 55  55 55 55 41 46 46 46 46  |ABRRRQAUUUUAFFFF|
*
00000040  41 42 52 52 52 51 41 55  0d 0a 55 55 55 41 46 46  |ABRRRQAU..UUUAFF|
00000050  46 46 41 42 52 52 52 51  41 55 55 55 55 41 46 46  |FFABRRRQAUUUUAFF|
*
00000090  46 46 41 42 52 52 0d 0a  52 51 41 55 55 55 55 41  |FFABRR..RQAUUUUA|
000000a0  46 46 46 46 41 42 52 52  52 51 41 55 55 55 55 41  |FFFFABRRRQAUUUUA|
*
000000e0  46 46 46 46 0d 0a 41 42  52 52 52 51 41 55 55 55  |FFFF..ABRRRQAUUU|
000000f0  55 41 46 46 46 46 41 42  52 52 52 51 41 55 55 55  |UAFFFFABRRRQAUUU|
*
00000130  55 41 0d 0a 46 46 46 46  41 42 52 52 52 51 41 55  |UA..FFFFABRRRQAU|
00000140  55 55 55 41 46 46 46 46  41 42 52 52 52 51 41 55  |UUUAFFFFABRRRQAU|
00000150  55 55 55 41 46 46 46 46  41 46 72 56 66 2b 51 6e  |UUUAFFFFAFrVf+Qn|
00000160  64 2f 38 41 58 5a 2f 35  6d 71 74 57 74 56 2f 35  |d/8AXZ/5mqtWtV/5|
00000170  43 64 33 2f 41 4e 64 6e  2f 6d 61 71 31 30 34 72  |Cd3/ANdn/maq104r|
00000180  0d 0a 2b 50 55 39 58 2b  5a 45 50 68 51 55 55 55  |..+PU9X+ZEPhQUUU|
00000190  56 7a 46 68 52 52 52 51  41 55 55 55 55 41 46 46  |VzFhRRRQAUUUUAFF|
000001a0  46 46 41 42 52 52 52 51  41 55 55 55 55 41 46 46  |FFABRRRQAUUUUAFF|
000001b0  46 46 41 42 52 52 52 51  41 55 55 55 55 41 00 fe  |FFABRRRQAUUUUA..|
000001c0  ff ff 07 fe ff ff 5a 9e  31 03 69 d4 79 09 00 fe  |......Z.1.i.y...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 68 0e 03 00 00  |...........h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-05-29
You installed grub to the windows boot sector which has windows boot info in it.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Because you now have windows in the MBR you will boot windows once it is fixed. 

To reinstall grub to boot either Ubuntu or windows. The grub menu shows different kernels as they are updated so you do get more as new kernels are added.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

General grub2 info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
/etc/default/grub
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by fire.for.effect on 2010-05-29
**Oh boy, I'm about to need this!**

---

### Post by wilee-nilee on 2010-05-29
> **fire.for.effect said:**
> **Oh boy, I'm about to need this!**
If your having boot problems just don't try fixes that may seem similar to your problems look at my post for the link to the bootscript and start a new thread and post it in code tags as shown.;) If you know what your problem is and can read that bootscript fully then act accordingly, but if not you may make it a more difficult fix by just trying fixes.

---

### Post by gaur.puneet on 2010-05-29
Sorry for disturbing you again. I tried,but I am unable to solve the problem. I am herewith giving the code again please look into the same & advise.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 125741144 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   100,012,178   100,012,116   7 HPFS/NTFS
/dev/sda2         100,014,078   312,576,704   212,562,627   5 Extended
/dev/sda5         153,597,528   312,576,704   158,979,177   7 HPFS/NTFS
/dev/sda6         100,014,080   151,289,855    51,275,776  83 Linux
/dev/sda7         151,291,904   153,595,903     2,304,000  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2098082D980803CE                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        C98365AB31088A12                       ntfs       Puneet                        
/dev/sda6        30495c9b-5aef-4572-9e75-868807c86e2d   ext4                                     
/dev/sda7        cd775b43-fa89-494a-9a0f-ca8e9fa66ef5   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
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
search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
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
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=30495c9b-5aef-4572-9e75-868807c86e2d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=30495c9b-5aef-4572-9e75-868807c86e2d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=30495c9b-5aef-4572-9e75-868807c86e2d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=30495c9b-5aef-4572-9e75-868807c86e2d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 30495c9b-5aef-4572-9e75-868807c86e2d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2098082d980803ce
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=30495c9b-5aef-4572-9e75-868807c86e2d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=cd775b43-fa89-494a-9a0f-ca8e9fa66ef5 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  64.3GB: boot/grub/core.img
  55.6GB: boot/grub/grub.cfg
  64.3GB: boot/initrd.img-2.6.32-21-generic
  64.3GB: boot/initrd.img-2.6.32-22-generic
  64.3GB: boot/vmlinuz-2.6.32-21-generic
  64.3GB: boot/vmlinuz-2.6.32-22-generic
  64.3GB: initrd.img
  64.3GB: initrd.img.old
  64.3GB: vmlinuz
  64.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  41 42 52 52 52 51 41 55  55 55 55 41 46 46 46 46  |ABRRRQAUUUUAFFFF|
*
00000040  41 42 52 52 52 51 41 55  0d 0a 55 55 55 41 46 46  |ABRRRQAU..UUUAFF|
00000050  46 46 41 42 52 52 52 51  41 55 55 55 55 41 46 46  |FFABRRRQAUUUUAFF|
*
00000090  46 46 41 42 52 52 0d 0a  52 51 41 55 55 55 55 41  |FFABRR..RQAUUUUA|
000000a0  46 46 46 46 41 42 52 52  52 51 41 55 55 55 55 41  |FFFFABRRRQAUUUUA|
*
000000e0  46 46 46 46 0d 0a 41 42  52 52 52 51 41 55 55 55  |FFFF..ABRRRQAUUU|
000000f0  55 41 46 46 46 46 41 42  52 52 52 51 41 55 55 55  |UAFFFFABRRRQAUUU|
*
00000130  55 41 0d 0a 46 46 46 46  41 42 52 52 52 51 41 55  |UA..FFFFABRRRQAU|
00000140  55 55 55 41 46 46 46 46  41 42 52 52 52 51 41 55  |UUUAFFFFABRRRQAU|
00000150  55 55 55 41 46 46 46 46  41 46 72 56 66 2b 51 6e  |UUUAFFFFAFrVf+Qn|
00000160  64 2f 38 41 58 5a 2f 35  6d 71 74 57 74 56 2f 35  |d/8AXZ/5mqtWtV/5|
00000170  43 64 33 2f 41 4e 64 6e  2f 6d 61 71 31 30 34 72  |Cd3/ANdn/maq104r|
00000180  0d 0a 2b 50 55 39 58 2b  5a 45 50 68 51 55 55 55  |..+PU9X+ZEPhQUUU|
00000190  56 7a 46 68 52 52 52 51  41 55 55 55 55 41 46 46  |VzFhRRRQAUUUUAFF|
000001a0  46 46 41 42 52 52 52 51  41 55 55 55 55 41 46 46  |FFABRRRQAUUUUAFF|
000001b0  46 46 41 42 52 52 52 51  41 55 55 55 55 41 00 fe  |FFABRRRQAUUUUA..|
000001c0  ff ff 07 fe ff ff 5a 9e  31 03 69 d4 79 09 00 fe  |......Z.1.i.y...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 68 0e 03 00 00  |...........h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by gaur.puneet on 2010-05-29
Testdisk Log
```



Sat May 29 23:29:04 2010
Command line: TestDisk

TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.32-22-generic (#33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010)
Compiler: GCC 4.3 - May  6 2009 14:40:08
ext2fs lib: 1.41.4, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       312581808 sectors
/dev/sda: user_max   312581808 sectors
/dev/sda: native_max 10591920 sectors
/dev/sda: dco        312581808 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - ATA WDC WD1600BEVS-2

Partition table type (auto): Intel
/dev/sda: Device Configuration Overlay (DCO) present.
Disk /dev/sda - 160 GB / 149 GiB - ATA WDC WD1600BEVS-2
Partition table type: Intel

Interface Advanced
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
NTFS at 9561/1/1
get_geometry_from_list_part_aux head=255 nbr=3
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=3
 1 * HPFS - NTFS              0   1  1  6225 119 57  100012116
     NTFS, 51 GB / 47 GiB
 2 E extended              6225 150  4 19456 254 63  212562627
   X extended              6225 150  5  9417  91 18   51275777
 6 L Linux                 6225 150  6  9417  91 18   51275776
     EXT4 Large file Sparse superblock Recover, 26 GB / 24 GiB
   X extended              9417  91 19  9560 230 14    2306048
 7 L Linux Swap            9417 123 51  9560 230 14    2304000
     SWAP2 version 1, 1179 MB / 1125 MiB
 5 L HPFS - NTFS           9561   1  1 19456 254 63  158979177 [Puneet]
     NTFS, 81 GB / 75 GiB

ntfs_boot_sector
 1 * HPFS - NTFS              0   1  1  6225 119 57  100012116
     NTFS, 51 GB / 47 GiB
NTFS at 0/1/1
NTFS at 0/1/1
filesystem size           100012116
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               9599837
clusters_per_mft_record   -10
clusters_per_index_record 1
Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

TestDisk exited normally.

```

---

### Post by oldfred on 2010-05-29
You still have grub in the window boot sector, so the next choice is to try the windows tools. You need to run the fixboot command, I show all of them in case that does not work on its own.

Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r /f 
BootRec.exe /FixBoot  #updates PBR partition boot sector 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

---

### Post by wilee-nilee on 2010-05-29
Good deal I just noticed the last post, I was wondering if a reload and rebuild of the bcd was really the answer. oldfred I noticed that you have added a additional /f fix to the chkdsk, this makes sense is this a specific for this user or best overall? seems like a overall addition.

---

### Post by oldfred on 2010-05-29
I have not run chkdsk for so long I do not know. I have seen that you have to run with /r and I have seen you have to run with /f. The microsoft site did not help much.

Looking now I am changing it to:
chkdsk c: /f /r

I am not sure you can run together as I posted or you have to run twice. I have seen that you have to keep running until there are no errors.
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
**chkdsk** [*volume***:**][[*Path*] *FileName*] [**/f**] [**/v**] [**/r**] [**/x**] [**/i**] [**/c**] [**/l**[**:***size*]]

---

### Post by wilee-nilee on 2010-05-29
> **oldfred said:**
> I have not run chkdsk for so long I do not know. I have seen that you have to run with /r and I have seen you have to run with /f. The microsoft site did not help much.

Looking now I am changing it to:
chkdsk c: /f /r

I am not sure you can run together as I posted or you have to run twice. I have seen that you have to keep running until there are no errors.
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
**chkdsk** [*volume***:**][[*Path*] *FileName*] [**/f**] [**/v**] [**/r**] [**/x**] [**/i**] [**/c**] [**/l**[**:***size*]]

Thanks I am not sure either if the /r and /f can be run together or in what order I will look at the MS page again, I know as you suggest it is kind of vague.

This boot script I was unsure about in that I saw the mixture of XP and Vista bootloaders in sda1 and no bootrec, I also wondered about the extended between sda1 and the Ubuntu partition. Generally I don't advise people anyway, I just try to get the script posted in a readable manner.

I have a laptop I can bork for testing once I get my netbook fixed to confirm some areas, like using testdisk as I have never used it. I know it is a excellent tool with multiple uses and would like to have a better grasp of it's use. Thanks for all your hard work and the other daily help from others in this area, it has been very helpful to me and tons of users.

---

### Post by elbajonn on 2010-07-21
Hi!
Maybe someone could check my code also...

Code
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 192057080 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

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

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 192057080 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   165,260,654   165,260,592   7 HPFS/NTFS
/dev/sda2         165,260,655   220,556,384    55,295,730   5 Extended
/dev/sda5         191,253,888   220,556,384    29,302,497  83 Linux
/dev/sda6         190,852,263   191,253,824       401,562  82 Linux swap / Solaris
/dev/sda7         165,260,781   190,852,199    25,591,419   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D28C18948C187567                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0e60c5d0-5770-403d-b19d-f42f04a09cef   ext4                                     
/dev/sda6        7075fd62-fd73-4cb3-9f0c-a2101d18bd40   swap                                     
/dev/sda7        A59A-9863                              vfat       KAUST2                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 0e60c5d0-5770-403d-b19d-f42f04a09cef
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
search --no-floppy --fs-uuid --set 0e60c5d0-5770-403d-b19d-f42f04a09cef
set locale_dir=($root)/boot/grub/locale
set lang=et
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
	search --no-floppy --fs-uuid --set 0e60c5d0-5770-403d-b19d-f42f04a09cef
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0e60c5d0-5770-403d-b19d-f42f04a09cef ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e60c5d0-5770-403d-b19d-f42f04a09cef
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0e60c5d0-5770-403d-b19d-f42f04a09cef ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e60c5d0-5770-403d-b19d-f42f04a09cef
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=0e60c5d0-5770-403d-b19d-f42f04a09cef ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e60c5d0-5770-403d-b19d-f42f04a09cef
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=0e60c5d0-5770-403d-b19d-f42f04a09cef ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e60c5d0-5770-403d-b19d-f42f04a09cef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e60c5d0-5770-403d-b19d-f42f04a09cef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d28c18948c187567
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=0e60c5d0-5770-403d-b19d-f42f04a09cef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=eb9af654-a647-4061-bacd-965f3f553720 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  98.3GB: boot/grub/core.img
 102.7GB: boot/grub/grub.cfg
 104.2GB: boot/initrd.img-2.6.31-22-generic
 104.4GB: boot/initrd.img-2.6.32-23-generic
  99.5GB: boot/vmlinuz-2.6.31-22-generic
 104.4GB: boot/vmlinuz-2.6.32-23-generic
 104.4GB: initrd.img
 104.2GB: initrd.img.old
 104.4GB: vmlinuz
  99.5GB: vmlinuz.old
/code

---

### Post by oldfred on 2010-07-21
elbajonn generally it is better to start a new thread on boot issues. But yours is identical to the OP.

See post #7. You have grub installed to the windows partition sda1 where windows has essential boot info.

---

### Post by elbajonn on 2010-07-21
still no result
I've tried with 7 original disc, 7 on external hdd, 7 on usb stick

nada

---

### Post by oldfred on 2010-07-21
Are you not able to run testdisk either from Ubuntu or the Ubuntu liveCD?

---

### Post by elbajonn on 2010-07-22
testdisk runs
yesterday there wasn't backupBS choice, today there was...
but still, choosing win 7 loader from grub menu my laptop restarts
most strange thing is that I can't load any windows, nor from dvd or usb drive.
of course ubuntu boots up normally from usb drive ;)

---

### Post by oldfred on 2010-07-22
Testdisk also has a rebuild BS function and from a windows repair CD you can run fixboot.

---

### Post by elbajonn on 2010-07-23
but i'm unable to run repair cd

---

### Post by elbajonn on 2010-07-23
only blinking cursor
same thing happened before with win 7 discs, now the system just restarts...

---

### Post by oldfred on 2010-07-23
Are you sure you are booting  cddvd drive? If so then windows DVD is defective which is unlikely.

---

### Post by cllewis91592 on 2010-07-23
wow im seeing more and more problems with windows 7 and ubuntu.i think they hate each other.

---

### Post by elbajonn on 2010-07-23
> **oldfred said:**
> Are you sure you are booting  cddvd drive? If so then windows DVD is defective which is unlikely.

100% :D

I've tried 3 different copies already and also from usb drive
absolutely impossible

press any key to boot from cd/dvd... and that's it. freezes
win 7 rescue disc goes a bit further, after pressing any key comes up the bootmr is missing error...

---

### Post by oldfred on 2010-07-23
Did you install ISO to CD not just copy it. A copy is not bootable and your system will then go to the hard drive if that is next in boot order and error out.

A missing bootmgr is a windows error for a missing OS. Not a bootable CD or DVD, just a NTFS partition typically.

I prefer USB installs at they work quicker if USB2 and saves CDs, if your system will boot USB flash drives.

---

### Post by elbajonn on 2010-07-23
I have an idea, stop me if I'm completely wrong :)

if I move my present win 7 partition and create a ntfs partition in front of that...

---

### Post by elbajonn on 2010-07-23
> **oldfred said:**
> Did you install ISO to CD not just copy it. A copy is not bootable and your system will then go to the hard drive if that is next in boot order and error out.



but why win 7 dvd freezes after pressing any key? it is bootable, if goes already that far....

---

### Post by oldfred on 2010-07-23
Check for hardware issues. Reset memory, push in all connectors, check everything as it may be a hardware issue.

---

### Post by elbajonn on 2010-07-24
> **oldfred said:**
> Check for hardware issues. Reset memory, push in all connectors, check everything as it may be a hardware issue.

only thing I can think of is HDD, but several tests already made, have found nothing
or is there something I could try?

---

