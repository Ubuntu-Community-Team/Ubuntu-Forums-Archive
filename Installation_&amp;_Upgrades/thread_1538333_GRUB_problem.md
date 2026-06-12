---
title: "GRUB problem"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by Linux4Pedro on 2010-07-24
:DI installed ubuntu 10.04 LTS next to windows vista. During the install process I chose to import all windows files into ubuntu. When I boot my machine the GRUB screens lets me choose between ubuntu and Vista. I can boot into ubuntu with no problem. But when i choose the Vista option my machine restarts right before the login  screen comes on and it brings me back to the GRUB screen and i keep trying to boot Vista but keeps doing the same thing over and over .  I'm able to access all  my windows files and folders but a lot of them i try to open and a pop up message tells me that I'm unable to access the file or folder. If anyone out there has an answer to my problem please reply. It is very important because i work from home with Vista and need to be able to boot into Vista. Thanks ....:(

---

### Post by kansasnoob on 2010-07-25
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Linux4Pedro on 2010-07-26
```

        
        
             .inlinemsg {border:2px solid;margin-bottom:0;margin-top:8px;padding:0 0 5px;border-color:#dc881e;}.inlinemsg .inlinemsgheader {color:#333333;font-weight:bold;padding: 0.5em 0 0.5em 10px;background-color:fbf5d8;border:1px solid #E6E6E6}.inlinemsg .plainMail {padding:5px} Im having trouble booting Vista From GRUB after installing UBUNTU next to it. I posted this problem a couple days ago and got a reply to get a boot info script and this is the result.  Very Thankful Kansasnoob for your help. hope you or someone can find what's wrong. 



: RESULTS.txt
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   270,095,747   270,093,700   7 HPFS/NTFS
/dev/sda2         465,489,920   488,390,655    22,900,736   7 HPFS/NTFS
/dev/sda3         270,096,382   465,489,919   195,393,538   5 Extended
/dev/sda5         270,096,384   273,442,364     3,345,981  83 Linux
/dev/sda6         457,455,616   465,489,919     8,034,304  82 Linux swap / Solaris
/dev/sda7         273,442,816   449,873,919   176,431,104  83 Linux
/dev/sda8         449,875,968   457,451,519     7,575,552  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3377330D045E96CF                       ntfs                                     
/dev/sda2        FEF6023CF601F625                       ntfs       RECOVERY                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ed29624f-68b6-4b8c-b996-b8a645c55018   ext4                                     
/dev/sda6        50574281-077e-4a0f-af3b-c74f06ee3c01   swap                                     
/dev/sda7        7e59292f-e861-430e-a524-ed67f88bdf43   ext4                                     
/dev/sda8        aaf21d42-8be6-4eb6-bf86-54b5b66e9b76   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
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
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7e59292f-e861-430e-a524-ed67f88bdf43 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7e59292f-e861-430e-a524-ed67f88bdf43 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7e59292f-e861-430e-a524-ed67f88bdf43 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7e59292f-e861-430e-a524-ed67f88bdf43 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3377330d045e96cf
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set fef6023cf601f625
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=7e59292f-e861-430e-a524-ed67f88bdf43 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=aaf21d42-8be6-4eb6-bf86-54b5b66e9b76 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 174.6GB: boot/grub/core.img
 191.8GB: boot/grub/grub.cfg
 175.0GB: boot/initrd.img-2.6.32-21-generic
 175.6GB: boot/initrd.img-2.6.32-24-generic
 175.4GB: boot/vmlinuz-2.6.32-21-generic
 175.4GB: boot/vmlinuz-2.6.32-24-generic
 175.6GB: initrd.img
 175.0GB: initrd.img.old
 175.4GB: vmlinuz
 175.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  21 21 10 10 10 18 29 31  10 29 31 21 31 39 10 29  |!!....)1.)1!19.)|
00000010  31 18 29 31 10 29 31 21  31 39 18 18 18 18 18 18  |1.)1.)1!19......|
00000020  18 18 18 21 21 21 10 29  31 18 29 31 18 18 18 21  |...!!!.)1.)1...!|
00000030  21 21 10 29 31 18 29 31  10 29 31 21 21 21 18 18  |!!.)1.)1.)1!!!..|
00000040  18 18 18 18 18 18 18 21  21 21 10 39 4a 10 42 52  |.......!!!.9J.BR|
00000050  18 18 18 21 21 21 18 18  18 18 18 18 18 18 18 21  |...!!!.........!|
00000060  21 21 10 29 31 18 18 18  18 18 18 21 21 21 18 18  |!!.)1......!!!..|
00000070  18 18 18 18 18 18 18 21  21 21 18 18 18 18 18 18  |.......!!!......|
00000080  18 18 18 21 21 21 18 18  18 18 18 18 18 18 18 21  |...!!!.........!|
00000090  21 21 18 18 18 18 18 18  18 18 18 21 21 21 18 18  |!!.........!!!..|
000000a0  18 18 18 18 18 18 18 21  21 21 18 18 18 18 18 18  |.......!!!......|
000000b0  18 18 18 21 21 21 18 18  18 18 18 18 18 18 18 21  |...!!!.........!|
000000c0  21 21 18 18 18 18 18 18  18 18 18 21 21 21 18 18  |!!.........!!!..|
000000d0  18 18 18 18 18 18 18 21  21 21 18 18 18 18 18 18  |.......!!!......|
000000e0  18 18 18 21 21 21 18 18  18 18 18 18 18 18 18 21  |...!!!.........!|
000000f0  21 21 21 21 21 18 18 18  18 18 18 18 18 18 21 21  |!!!!!.........!!|
00000100  21 18 18 18 18 18 18 18  18 18 21 21 21 18 18 18  |!.........!!!...|
00000110  18 18 18 18 18 18 21 21  21 18 18 18 18 18 18 18  |......!!!.......|
00000120  18 18 21 21 21 18 18 18  18 18 18 18 18 18 21 21  |..!!!.........!!|
00000130  21 18 18 18 18 18 18 18  18 18 21 21 21 18 18 18  |!.........!!!...|
00000140  18 18 18 18 18 18 21 21  21 18 18 18 18 18 18 18  |......!!!.......|
00000150  18 18 21 21 21 18 18 18  18 18 18 18 18 18 21 21  |..!!!.........!!|
00000160  21 18 18 18 18 18 18 18  18 18 21 21 21 18 18 18  |!.........!!!...|
00000170  18 18 18 18 18 18 21 21  21 18 18 18 18 18 18 18  |......!!!.......|
00000180  18 18 21 21 21 18 18 18  18 18 18 18 18 18 21 21  |..!!!.........!!|
00000190  21 18 18 18 18 18 18 18  18 18 21 21 21 18 18 18  |!.........!!!...|
000001a0  18 18 18 18 18 18 21 21  21 18 18 18 18 18 18 18  |......!!!.......|
000001b0  18 18 21 21 21 18 18 18  18 18 18 18 18 18 00 fe  |..!!!...........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 3d 0e 33 00 00 fe  |..........=.3...|
000001d0  ff ff 05 fe ff ff 02 d0  2a 0b 00 a8 7a 00 00 00  |........*...z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb
```

---

### Post by Linux4Pedro on 2010-07-26
```
Inline Attachment Follows: RESULTS.txt
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   270,095,747   270,093,700   7 HPFS/NTFS
/dev/sda2         465,489,920   488,390,655    22,900,736   7 HPFS/NTFS
/dev/sda3         270,096,382   465,489,919   195,393,538   5 Extended
/dev/sda5         270,096,384   273,442,364     3,345,981  83 Linux
/dev/sda6         457,455,616   465,489,919     8,034,304  82 Linux swap / Solaris
/dev/sda7         273,442,816   449,873,919   176,431,104  83 Linux
/dev/sda8         449,875,968   457,451,519     7,575,552  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3377330D045E96CF                       ntfs                                     
/dev/sda2        FEF6023CF601F625                       ntfs       RECOVERY                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ed29624f-68b6-4b8c-b996-b8a645c55018   ext4                                     
/dev/sda6        50574281-077e-4a0f-af3b-c74f06ee3c01   swap                                     
/dev/sda7        7e59292f-e861-430e-a524-ed67f88bdf43   ext4                                     
/dev/sda8        aaf21d42-8be6-4eb6-bf86-54b5b66e9b76   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
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
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7e59292f-e861-430e-a524-ed67f88bdf43 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7e59292f-e861-430e-a524-ed67f88bdf43 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7e59292f-e861-430e-a524-ed67f88bdf43 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7e59292f-e861-430e-a524-ed67f88bdf43 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 7e59292f-e861-430e-a524-ed67f88bdf43
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3377330d045e96cf
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set fef6023cf601f625
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=7e59292f-e861-430e-a524-ed67f88bdf43 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=aaf21d42-8be6-4eb6-bf86-54b5b66e9b76 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 174.6GB: boot/grub/core.img
 191.8GB: boot/grub/grub.cfg
 175.0GB: boot/initrd.img-2.6.32-21-generic
 175.6GB: boot/initrd.img-2.6.32-24-generic
 175.4GB: boot/vmlinuz-2.6.32-21-generic
 175.4GB: boot/vmlinuz-2.6.32-24-generic
 175.6GB: initrd.img
 175.0GB: initrd.img.old
 175.4GB: vmlinuz
 175.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  21 21 10 10 10 18 29 31  10 29 31 21 31 39 10 29  |!!....)1.)1!19.)|
00000010  31 18 29 31 10 29 31 21  31 39 18 18 18 18 18 18  |1.)1.)1!19......|
00000020  18 18 18 21 21 21 10 29  31 18 29 31 18 18 18 21  |...!!!.)1.)1...!|
00000030  21 21 10 29 31 18 29 31  10 29 31 21 21 21 18 18  |!!.)1.)1.)1!!!..|
00000040  18 18 18 18 18 18 18 21  21 21 10 39 4a 10 42 52  |.......!!!.9J.BR|
00000050  18 18 18 21 21 21 18 18  18 18 18 18 18 18 18 21  |...!!!.........!|
00000060  21 21 10 29 31 18 18 18  18 18 18 21 21 21 18 18  |!!.)1......!!!..|
00000070  18 18 18 18 18 18 18 21  21 21 18 18 18 18 18 18  |.......!!!......|
00000080  18 18 18 21 21 21 18 18  18 18 18 18 18 18 18 21  |...!!!.........!|
00000090  21 21 18 18 18 18 18 18  18 18 18 21 21 21 18 18  |!!.........!!!..|
000000a0  18 18 18 18 18 18 18 21  21 21 18 18 18 18 18 18  |.......!!!......|
000000b0  18 18 18 21 21 21 18 18  18 18 18 18 18 18 18 21  |...!!!.........!|
000000c0  21 21 18 18 18 18 18 18  18 18 18 21 21 21 18 18  |!!.........!!!..|
000000d0  18 18 18 18 18 18 18 21  21 21 18 18 18 18 18 18  |.......!!!......|
000000e0  18 18 18 21 21 21 18 18  18 18 18 18 18 18 18 21  |...!!!.........!|
000000f0  21 21 21 21 21 18 18 18  18 18 18 18 18 18 21 21  |!!!!!.........!!|
00000100  21 18 18 18 18 18 18 18  18 18 21 21 21 18 18 18  |!.........!!!...|
00000110  18 18 18 18 18 18 21 21  21 18 18 18 18 18 18 18  |......!!!.......|
00000120  18 18 21 21 21 18 18 18  18 18 18 18 18 18 21 21  |..!!!.........!!|
00000130  21 18 18 18 18 18 18 18  18 18 21 21 21 18 18 18  |!.........!!!...|
00000140  18 18 18 18 18 18 21 21  21 18 18 18 18 18 18 18  |......!!!.......|
00000150  18 18 21 21 21 18 18 18  18 18 18 18 18 18 21 21  |..!!!.........!!|
00000160  21 18 18 18 18 18 18 18  18 18 21 21 21 18 18 18  |!.........!!!...|
00000170  18 18 18 18 18 18 21 21  21 18 18 18 18 18 18 18  |......!!!.......|
00000180  18 18 21 21 21 18 18 18  18 18 18 18 18 18 21 21  |..!!!.........!!|
00000190  21 18 18 18 18 18 18 18  18 18 21 21 21 18 18 18  |!.........!!!...|
000001a0  18 18 18 18 18 18 21 21  21 18 18 18 18 18 18 18  |......!!!.......|
000001b0  18 18 21 21 21 18 18 18  18 18 18 18 18 18 00 fe  |..!!!...........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 3d 0e 33 00 00 fe  |..........=.3...|
000001d0  ff ff 05 fe ff ff 02 d0  2a 0b 00 a8 7a 00 00 00  |........*...z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb
```

---

### Post by overdrank on 2010-07-26
Threads merged. The text goes between the code tags :)

---

### Post by Linux4Pedro on 2010-07-26
:p Thanks for the invitation. I'll check it out!

---

### Post by kansasnoob on 2010-07-26
I see you have "/bootmgr" on both /dev/sda1 and /dev/sda2:

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr


With Vista that's kind of odd but both should show up in the boot menu:

> menuentry "**Windows Vista (loader) (on /dev/sda1)**" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3377330d045e96cf
    chainloader +1
}
menuentry "**Windows Vista (loader) (on /dev/sda2)**" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set fef6023cf601f625
    chainloader +1
}

So, does booting either result in the same error?

---

### Post by Linux4Pedro on 2010-07-28
Yes, it does. My computer restarts a few seconds after I press ENTER on either one of the Vista options on GRUB.

---

### Post by Herman on 2010-07-28
I installed Ubuntu Lucid Lynx in a netbook for a friend of mine and Ubuntu worked fine but  instead of booting Windows XP it would keep on rebooting, similar to the symptoms you're reporting.
I found out the problem has something to do with the BIOS in some computers, at least in the particular instance I'm talking about, I'm not sure about how widespread it could be. I thought it was a peculiarity of the particular make and model of netbook I was working on.

Anyhow, in case it's any help, the solution was to run CHKDSK/R from a Windows7 CD. 

I'm not sure if that will fix your problem, but it wouldn't do any harm to try it, apart from maybe being a waste of your time if it doesn't fix the problem. A file system check is never a waste of time though, it's always a good idea to run file system checks frequently. :D

---

