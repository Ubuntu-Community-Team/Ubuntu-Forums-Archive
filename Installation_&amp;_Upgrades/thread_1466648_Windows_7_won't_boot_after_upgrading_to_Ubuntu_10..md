---
title: "Windows 7 won't boot after upgrading to Ubuntu 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by smalul on 2010-04-30
Hello

I have Windows XP, Windows 7 and Ubuntu installed, all installed in the same hard drive, different partitions:
Windows XP - sda1 (this partition has the boot flag), NTFS
Ubuntu - sda2, ext3
Windows 7 - sda3, NTFS
(sda4 is an extended partition)
While using Ubuntu 9.10, the grub2 menu first let me select between Ubuntu and Windows7, and if I selected Windows 7, I had the option to select between Windows 7 and Windows XP.

I've updated to Ubuntu 10.04 today, and now when I select the Windows 7 option in the grub2 menu, it does nothing.

The relevant part of my grub.cfg file:
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 879d6fcd-10b2-47b2-9400-e359869b1386
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=879d6fcd-10b2-47b2-9400-e359869b1386 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 879d6fcd-10b2-47b2-9400-e359869b1386
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=879d6fcd-10b2-47b2-9400-e359869b1386 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 879d6fcd-10b2-47b2-9400-e359869b1386
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 879d6fcd-10b2-47b2-9400-e359869b1386
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 42c4aa3dc4aa32d9
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```I've run sudo update-grub several times, but it didn't help.

I'm guessing the update from grub 1.97, which I was using in Ubuntu 9.10, to grub 1.98, which came with Ubuntu 10.04, has changed something, and possibly corrupted the Windows 7 boot loader.

What should I do to fix this problem? I need to be able to access Windows 7 and Windows XP.

Thank you.

---

### Post by kansasnoob on 2010-04-30
Please post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by smalul on 2010-04-30
Here are the results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 144695233 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 144629681 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 144580481 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   125,837,144   125,837,082   7 HPFS/NTFS
/dev/sda2         125,837,145   175,831,424    49,994,280  83 Linux
/dev/sda3         175,833,088   426,846,207   251,013,120   7 HPFS/NTFS
/dev/sda4         426,847,050   488,392,064    61,545,015   f W95 Ext d (LBA)
/dev/sda5         426,863,115   488,392,064    61,528,950   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        42C4AA3DC4AA32D9                       ntfs       WinXP                         
/dev/sda2        879d6fcd-10b2-47b2-9400-e359869b1386   ext3                                     
/dev/sda3        AA826DB6826D87A1                       ntfs       Windows7                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        A6A00BD8A00BADBD                       ntfs       Shared Partition              
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B208C13D08C100F9                       ntfs       Main Storage                  
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,errors=remount-ro)
/dev/sda5        /media/sda5              fuseblk    (rw,nosuid,nodev,allow_other,blksize=512)
/dev/sdb1        /media/sdb1              fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sda2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=879d6fcd-10b2-47b2-9400-e359869b1386 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=879d6fcd-10b2-47b2-9400-e359869b1386

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        879d6fcd-10b2-47b2-9400-e359869b1386
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=879d6fcd-10b2-47b2-9400-e359869b1386 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        879d6fcd-10b2-47b2-9400-e359869b1386
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=879d6fcd-10b2-47b2-9400-e359869b1386 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, memtest86+
uuid        879d6fcd-10b2-47b2-9400-e359869b1386
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 879d6fcd-10b2-47b2-9400-e359869b1386
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 879d6fcd-10b2-47b2-9400-e359869b1386
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 879d6fcd-10b2-47b2-9400-e359869b1386
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=879d6fcd-10b2-47b2-9400-e359869b1386 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 879d6fcd-10b2-47b2-9400-e359869b1386
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=879d6fcd-10b2-47b2-9400-e359869b1386 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 879d6fcd-10b2-47b2-9400-e359869b1386
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 879d6fcd-10b2-47b2-9400-e359869b1386
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 42c4aa3dc4aa32d9
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda2 during installation
UUID=879d6fcd-10b2-47b2-9400-e359869b1386  /               ext3         errors=remount-ro           0  1  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/mnt/2Gb.swap                              none            swap         sw                          0  0  
/dev/sda5                                  /media/sda5     ntfs         defaults                    0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,ro,umask=000  0  0  

=================== sda2: Location of files loaded by Grub: ===================


  74.0GB: boot/grub/core.img
  74.0GB: boot/grub/grub.cfg
  74.0GB: boot/grub/menu.lst
  74.0GB: boot/grub/stage2
  73.9GB: boot/initrd.img-2.6.32-21-generic
  74.0GB: boot/vmlinuz-2.6.32-21-generic
  73.9GB: initrd.img
  74.0GB: vmlinuz

---

### Post by kansasnoob on 2010-04-30
Somehow you installed grub to the boot sector of both the Win7 and XP partitions:

> sda1: __________________________________________________ _______________________

File system: ntfs
[B][COLOR="Red"]Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda1 and
looks at sector 144695233 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.[/COLOR][/B]
Operating System: Windows XP
Boot files/dirs: /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM


sda3: __________________________________________________ _______________________

File system: ntfs
[B][COLOR="Red"]Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda3 and
looks at sector 144580481 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.[/COLOR][/B]
Operating System: Windows 7
Boot files/dirs: /Windows/System32/winload.exe

Meierfra outlined a fix here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by smalul on 2010-04-30
Thank you very much - this solved my problem.
I repaired the Windows XP and Windows 7 partitions, and now I'm able to boot from them.

I also think I know how I caused the problem - during the upgrade, I was asked to select the partitions from which to boot (or something like that), and I selected sda1, sda2 and sda3. I guess I didn't understand the question correctly and I sure didn't know what it would do to the boot sectors of those partitions.

Thanks again

Edit:
If I'm already here. In the results I also saw this:
```
sda2: __________________________________________________   _______________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2  and 
                       looks at sector 144629681 of the same hard drive  for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg  /etc/fstab 
                       /boot/grub/core.img
```
Everything is working now, but should I try to fix the Ubuntu partition as well using testdisk?

---

### Post by kansasnoob on 2010-04-30
> **smalul said:**
> Thank you very much - this solved my problem.
I repaired the Windows XP and Windows 7 partitions, and now I'm able to boot from them.

I also think I know how I caused the problem - during the upgrade, I was asked to select the partitions from which to boot (or something like that), and I selected sda1, sda2 and sda3. I guess I didn't understand the question correctly and I sure didn't know what it would do to the boot sectors of those partitions.

Thanks again

Edit:
If I'm already here. In the results I also saw this:
```
sda2: __________________________________________________   _______________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2  and 
                       looks at sector 144629681 of the same hard drive  for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg  /etc/fstab 
                       /boot/grub/core.img
```
Everything is working now, but should I try to fix the Ubuntu partition as well using testdisk?

No! But there is one other thing. I notice that Ubuntu has both a menu.lst and a grub.cfg:

> Boot files/dirs:   **[COLOR="Red"]/boot/grub/menu.lst /boot/grub/grub.cfg[/COLOR]**  /etc/fstab 
                       /boot/grub/core.img

That's not a huge deal but if you find that kernel updates fail to show up in the boot menu you may want to fix that. First I'd have to know what packages are actually installed, so I'd need to see the output of:

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4

```

Note: I'll be away from the desk for a couple of hours so if you want to fix this now please just be patient :)

---

### Post by smalul on 2010-04-30
Thanks again.

The output of your command is:
```
grub-install (GNU GRUB 1.98-1ubuntu5)
Package: grub
State: not installed
Version: 0.97-29ubuntu60
Priority: optional
Package: grub-pc
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu5
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu5
Package: os-prober
State: installed
Automatically installed: yes
Version: 1.38
```

The reason I have a menu.lst file is probably because I originally installed Ubuntu 9.04, which used grub1, which used the menu.lst file. When I upgraded to Ubuntu 9.10, grub2 was installed (version 1.97), and this file became obsolete. 

I did not have any problem getting kernels updates in version 9.10 during the 6 months I was using it (between versions 9.04 and 10.04), so I'm hoping I won't have any problems now that I'm using version 10.04. I also uninstall any old kernel once a new version is released (after I check it works of course) using the Synaptic Package Manager, so I only have one real linux kernel at any given time.

If you post anything which could help me, I would appreciate it, but the most important thing is that you helped me solve my boot problem, so thank you again.

---

### Post by kansasnoob on 2010-04-30
Well, if it's working great I tend to think, "if it ain't broke, don't fix it":)

If you should ever run into trouble with grub not updating correctly just click on my forum username and send me a brief PM with a forum thread number and we'll worry about it then.

---

### Post by HazelIced on 2010-04-30
Can somebody help me out?
My Vista won't start.
I tried the testdisk thing, but doesn't seem to be working.
Here is what my RESULTS.TXT looks like

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 300637656 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 300542216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,980,889    20,980,827  27 Hidden HPFS/NTFS
/dev/sda2    *     20,981,760   166,782,975   145,801,216   7 HPFS/NTFS
/dev/sda3         166,786,830   211,399,334    44,612,505   7 HPFS/NTFS
/dev/sda4         211,399,335   312,576,704   101,177,370   5 Extended
/dev/sda5         211,399,398   219,785,264     8,385,867  82 Linux swap / Solaris
/dev/sda6         219,785,328   312,576,704    92,791,377  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        446496D76496CAD6                       ntfs       PQSERVICE                     
/dev/sda2        C4667CB6667CAAB6                       ntfs       ACER                          
/dev/sda3        F8361CB1361C72BC                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        67f95be3-f310-4f2c-a4a2-225247772326   swap                                     
/dev/sda6        3e66f56b-6950-4ee4-993c-e657677fd42f   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
if terminal_input console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal console
fi
if terminal_output console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal console
fi
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3e66f56b-6950-4ee4-993c-e657677fd42f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3e66f56b-6950-4ee4-993c-e657677fd42f ro vga=792 splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3e66f56b-6950-4ee4-993c-e657677fd42f
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=3e66f56b-6950-4ee4-993c-e657677fd42f ro vga=792 splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3e66f56b-6950-4ee4-993c-e657677fd42f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3e66f56b-6950-4ee4-993c-e657677fd42f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 446496d76496cad6
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c4667cb6667caab6
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
set gfxmode="640x480"
set gfxfont="Unifont Regular 16"
loadfont /boot/grub/themes/fonts/unifont.pf2
loadfont /boot/grub/themes/fonts/aqui.pf2
loadfont /boot/grub/themes/fonts/edges.pf2
loadfont /boot/grub/themes/fonts/lime.pf2
loadfont /boot/grub/themes/fonts/7x13B.pf2
loadfont /boot/grub/themes/fonts/smoothansi.pf2
loadfont /boot/grub/themes/fonts/Helvetica-Bold-14.pf2
insmod vbe
insmod png
insmod coreui
load_config /boot/burg/themes/ubuntu2/theme.txt
#./boot/burg/themes/ubuntu2/theme.txt
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sda6 during installation
UUID=3e66f56b-6950-4ee4-993c-e657677fd42f  /              ext3         errors=remount-ro      0  1  
# swap was on /dev/sda5 during installation
UUID=67f95be3-f310-4f2c-a4a2-225247772326  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0   0  
/dev/sda2                                  /media/ACER    ntfs         defaults               0  0  
/dev/sda3                                  /media/DATA    ntfs         defaults               0  0  

=================== sda6: Location of files loaded by Grub: ===================


 153.8GB: boot/grub/core.img
 153.9GB: boot/grub/grub.cfg
 153.9GB: boot/initrd.img-2.6.31-20-generic
 158.6GB: boot/initrd.img-2.6.32-21-generic
 153.9GB: boot/vmlinuz-2.6.31-20-generic
 130.5GB: boot/vmlinuz-2.6.32-21-generic
 158.6GB: initrd.img
 130.5GB: vmlinuz

```



Thanks for any help in advance!

---

### Post by wilee-nilee on 2010-04-30
> **HazelIced said:**
> Can somebody help me out?
My Vista won't start.
I tried the testdisk thing, but doesn't seem to be working.
Here is what my RESULTS.TXT looks like

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 300637656 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 300542216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,980,889    20,980,827  27 Hidden HPFS/NTFS
/dev/sda2    *     20,981,760   166,782,975   145,801,216   7 HPFS/NTFS
/dev/sda3         166,786,830   211,399,334    44,612,505   7 HPFS/NTFS
/dev/sda4         211,399,335   312,576,704   101,177,370   5 Extended
/dev/sda5         211,399,398   219,785,264     8,385,867  82 Linux swap / Solaris
/dev/sda6         219,785,328   312,576,704    92,791,377  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        446496D76496CAD6                       ntfs       PQSERVICE                     
/dev/sda2        C4667CB6667CAAB6                       ntfs       ACER                          
/dev/sda3        F8361CB1361C72BC                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        67f95be3-f310-4f2c-a4a2-225247772326   swap                                     
/dev/sda6        3e66f56b-6950-4ee4-993c-e657677fd42f   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
if terminal_input console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal console
fi
if terminal_output console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal console
fi
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3e66f56b-6950-4ee4-993c-e657677fd42f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3e66f56b-6950-4ee4-993c-e657677fd42f ro vga=792 splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3e66f56b-6950-4ee4-993c-e657677fd42f
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=3e66f56b-6950-4ee4-993c-e657677fd42f ro vga=792 splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3e66f56b-6950-4ee4-993c-e657677fd42f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3e66f56b-6950-4ee4-993c-e657677fd42f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 446496d76496cad6
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c4667cb6667caab6
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
set gfxmode="640x480"
set gfxfont="Unifont Regular 16"
loadfont /boot/grub/themes/fonts/unifont.pf2
loadfont /boot/grub/themes/fonts/aqui.pf2
loadfont /boot/grub/themes/fonts/edges.pf2
loadfont /boot/grub/themes/fonts/lime.pf2
loadfont /boot/grub/themes/fonts/7x13B.pf2
loadfont /boot/grub/themes/fonts/smoothansi.pf2
loadfont /boot/grub/themes/fonts/Helvetica-Bold-14.pf2
insmod vbe
insmod png
insmod coreui
load_config /boot/burg/themes/ubuntu2/theme.txt
#./boot/burg/themes/ubuntu2/theme.txt
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sda6 during installation
UUID=3e66f56b-6950-4ee4-993c-e657677fd42f  /              ext3         errors=remount-ro      0  1  
# swap was on /dev/sda5 during installation
UUID=67f95be3-f310-4f2c-a4a2-225247772326  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0   0  
/dev/sda2                                  /media/ACER    ntfs         defaults               0  0  
/dev/sda3                                  /media/DATA    ntfs         defaults               0  0  

=================== sda6: Location of files loaded by Grub: ===================


 153.8GB: boot/grub/core.img
 153.9GB: boot/grub/grub.cfg
 153.9GB: boot/initrd.img-2.6.31-20-generic
 158.6GB: boot/initrd.img-2.6.32-21-generic
 153.9GB: boot/vmlinuz-2.6.31-20-generic
 130.5GB: boot/vmlinuz-2.6.32-21-generic
 158.6GB: initrd.img
 130.5GB: vmlinuz

```



Thanks for any help in advance!

Your going to want to start a thread all your own to get responses.

---

### Post by jliss on 2010-05-23
Had the same problem as smalul for the exact same reason.  I know little about Unix (but am a quick learner) and did not correctly respond to the 10.04 update questions re grub.  Your repair reference saved the day for me.  Could not take your help without thanking you.  As this is my first post I hope it is an acceptable use of the forum.

---

