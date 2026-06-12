---
title: "Installed WinXP, Ubuntu will not boot"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by outleradam on 2010-04-21
I installed Windows XP home edition on a separate hard disk without locking write access on my two Ubuntu hard disks.  It removed my boot loader and windows XP inexplicit failed to install.  This left me without an operating system.

While troubleshooting I performed many many things including removing and repartitioning, then recovering data without success.   I tried to use grub from a recovery CD.  I tried to use grub-install from a terminal.   I tried many many things.  I had _**alot**_ of problems and wasted alot of time.  I finally installed Ubuntu from an installation CD.  I now have ubuntu installed on SDC.  I need to rewrite the boot loader and the /boot/ dir onto  my Ubuntu drive so that my filesystem reads correctly.  I could use some help on this.  Please!

I have 3 hard disks 
Ubuntu(ext4 on SDA1 swap on SDA2) 
Backup(SDB ext3 on SDB1, extended on SDB2, and Unallocated SDB )  
Extra (SDC ext4 dummy installation of Ubuntu for the bootloader on SDC1,  Extended on SDC2, and 5 gigs Free on SDC)

I'm currently booted onto my previous kernel on SDA1.  Grub is on SDC1.  My Filesystem is rooted ( / ) on SDC1.  I need my filesystem to be the standard root ( / ) on SDA1.

My goal is to reinstall grub or grub-pc (or whatever Ubuntu 10.04 comes with) on SDA1.  I need it to root my filesystem on SDA1.    How can I put things right after this WinXP catastrophe?

---

### Post by oldfred on 2010-04-21
With lots of drives and possibly versions, let's document the boot process:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

New install of Karmic should be grub2 (1.97) upgrades kept grub legacy (0.97).

---

### Post by wilee-nilee on 2010-04-21
At least for me this is confusing, can you say what exactly is on your computer and in what order, did you install it. The history, that it seems has no relevance makes it hard to understand. You might also post this boot script as it is quite helpful.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

And you have one of the wisest ;) helpers here above me in every way.

---

### Post by outleradam on 2010-04-21
^^ I don't understand what you mean.  It seems that you don't understand what I'm saying.  I installed 10.04, installed alot of software, tried to install winXP on another disk, it screwed things up, I tried alot of things, now I'm grubbing from SDB (I thought it was SDC though) and kerneling from SDA

The SDA grub 2 and/or other boot files are messed up.

btw.. I messed up when I said my filesystem is mounted in the wrong  place.  I was clicking on the newly created "filesystem" hard disk. 

I still need to reinstall grub and boot from SDA, it will not boot, it  just goes to a black screen.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 17057024 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 4874418 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   601,409,535   601,407,488  83 Linux
/dev/sda2         601,411,584   625,141,743    23,730,160  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   381,672,269   381,672,207  83 Linux
/dev/sdb2         381,672,332   390,716,864     9,044,533   5 Extended
Empty Partition


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   224,827,391   224,825,344  83 Linux
/dev/sdc2         224,829,439   234,440,703     9,611,265   5 Extended
/dev/sdc5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        859512c6-3aee-431f-b973-11d1380b400a   ext4                                     
/dev/sda2        3f85add8-ddca-476b-954f-37659347dbda   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        be50b68b-01b4-4a1b-8da7-06f22fd7c215   ext3       backup                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8f0de3dc-af33-47c2-9733-03b50ef4b63d   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        6f3ebebe-eadb-41df-a0d6-288f64cce679   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/8f0de3dc-af33-47c2-9733-03b50ef4b63d ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    echo    'Loading Linux 2.6.32-19-generic ...'
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=859512c6-3aee-431f-b973-11d1380b400a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3f85add8-ddca-476b-954f-37659347dbda none            swap    sw              0       0

//192.168.1.1/public /home/mythtv/NAS cifs credentials=/home/adam/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

=================== sda1: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/core.img
  28.0GB: boot/grub/grub.cfg
   8.7GB: boot/grub/stage2
   8.7GB: boot/initrd.img-2.6.32-19-generic
   9.7GB: boot/initrd.img-2.6.32-21-generic
   8.7GB: boot/vmlinuz-2.6.32-19-generic
    .7GB: boot/vmlinuz-2.6.32-21-generic
   9.7GB: initrd.img
   8.7GB: initrd.img.old
    .7GB: vmlinuz
   8.7GB: vmlinuz.old

=================== sdb1: Location of files loaded by Grub: ===================


 141.0GB: boot/grub/core.img

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
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
    set root='(hd2,1)'
```

How can I reinstall grub and other boot files to SDA1?

---

### Post by outleradam on 2010-04-21
I just did 
```
sudo grub-install sda
```
and now the RESULTS1.txt says this
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda1 and looks 
                       at sector 17057024 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 4874418 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   601,409,535   601,407,488  83 Linux
/dev/sda2         601,411,584   625,141,743    23,730,160  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   381,672,269   381,672,207  83 Linux
/dev/sdb2         381,672,332   390,716,864     9,044,533   5 Extended
Empty Partition


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   224,827,391   224,825,344  83 Linux
/dev/sdc2         224,829,439   234,440,703     9,611,265   5 Extended
/dev/sdc5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        859512c6-3aee-431f-b973-11d1380b400a   ext4                                     
/dev/sda2        3f85add8-ddca-476b-954f-37659347dbda   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        be50b68b-01b4-4a1b-8da7-06f22fd7c215   ext3       backup                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8f0de3dc-af33-47c2-9733-03b50ef4b63d   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        6f3ebebe-eadb-41df-a0d6-288f64cce679   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    echo    'Loading Linux 2.6.32-19-generic ...'
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=859512c6-3aee-431f-b973-11d1380b400a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3f85add8-ddca-476b-954f-37659347dbda none            swap    sw              0       0

//192.168.1.1/public /home/mythtv/NAS cifs credentials=/home/adam/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

=================== sda1: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/core.img
  28.0GB: boot/grub/grub.cfg
   8.7GB: boot/grub/stage2
   8.7GB: boot/initrd.img-2.6.32-19-generic
   9.7GB: boot/initrd.img-2.6.32-21-generic
   8.7GB: boot/vmlinuz-2.6.32-19-generic
    .7GB: boot/vmlinuz-2.6.32-21-generic
   9.7GB: initrd.img
   8.7GB: initrd.img.old
    .7GB: vmlinuz
   8.7GB: vmlinuz.old

=================== sdb1: Location of files loaded by Grub: ===================


 141.0GB: boot/grub/core.img

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
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
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    echo    Loading Linux 2.6.32-16-generic ...
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro quiet splash
    initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single
    initrd /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=6f3ebebe-eadb-41df-a0d6-288f64cce679 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 111.8GB: boot/grub/core.img
  58.1GB: boot/grub/grub.cfg
 111.8GB: boot/initrd.img-2.6.32-16-generic
 111.8GB: boot/vmlinuz-2.6.32-16-generic
 111.8GB: initrd.img
 111.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  93 9d 92 4f 85 5d 18 21  a0 41 a0 f6 6f 85 a8 ca  |...O.].!.A..o...|
00000010  03 70 c7 17 e0 fa 28 76  14 8c 40 83 0f 0f a1 c3  |.p....(v..@.....|
00000020  31 f4 87 ae f2 92 07 8b  42 cf 0a b1 c2 87 07 c1  |1.......B.......|
00000030  b8 c4 a0 df f1 3b d0 e2  18 7f 94 49 83 89 d7 fb  |.....;.....I....|
00000040  1e b3 23 43 d6 e1 f4 e3  0b 87 8e 85 4a a7 2c 4c  |..#C........J.,L|
00000050  78 88 73 5e 31 41 4a 33  92 2a be a2 87 60 c1 48  |x.s^1AJ3.*...`.H|
00000060  59 33 e8 1f 1b d4 6c 60  a9 52 4f aa 6a f8 a5 92  |Y3....l`.RO.j...|
00000070  27 47 5d 0e 21 4b 88 35  85 cd 1b 3d d3 9a 2c 2a  |'G].!K.5...=..,*|
00000080  b4 f3 b5 d0 d1 ed 98 a4  34 4b 51 af bd 91 69 c4  |........4KQ...i.|
00000090  2f 0a b5 dd d5 ca 24 ea  5a 84 73 50 62 80 44 00  |/.....$.Z.sPb.D.|
000000a0  48 30 96 a0 0c c5 06 b8  41 40 22 a3 af 30 68 05  |H0......A@"..0h.|
000000b0  62 92 08 a0 0e 1e 06 ae  f4 a4 15 81 dc d1 91 de  |b...............|
000000c0  9d f3 91 68 06 b4 7e 72  2c 59 f1 b4 49 00 d0 2a  |...h..~r,Y..I..*|
000000d0  1d 04 40 36 05 a0 28 e9  a0 b0 43 ff be 1a 69 2d  |..@6..(...C...i-|
000000e0  22 62 10 04 ef 97 ff 8b  09 fc b1 ee 24 7d 21 03  |"b..........$}!.|
000000f0  4b 48 23 00 24 65 12 38  ed 10 53 8d 42 d8 90 27  |KH#.$e.8..S.B..'|
00000100  c3 96 0f 52 ec 0f 61 73  de 1e 92 42 83 07 90 6f  |...R..as...B...o|
00000110  c3 ee 94 14 6d e1 0a 44  bf 75 c2 c5 05 fe a8 d8  |....m..D.u......|
00000120  da d9 13 95 0f 27 a2 68  19 1d bf 0b c5 21 a1 20  |.....'.h.....!. |
00000130  6e 60 bb f1 97 64 1b a1  d3 b3 12 be f6 1d ab 07  |n`...d..........|
00000140  52 36 ed 23 0a 0b c7 e5  39 08 55 34 1c a4 62 2f  |R6.#....9.U4..b/|
00000150  19 83 39 45 00 e6 49 03  04 06 40 00 00 01 11 32  |..9E..I...@....2|
00000160  1c 3c 25 3f 1d 1a d6 75  0e 21 05 15 2b 81 a5 46  |.<%?...u.!..+..F|
00000170  59 80 72 8c bc 42 11 c7  06 1f 42 e1 f7 96 64 4e  |Y.r..B....B...dN|
00000180  36 03 e0 6e 8a a9 22 ad  41 7e e8 75 0e 03 76 75  |6..n..".A~.u..vu|
00000190  15 3a 0a 20 59 90 7b a2  88 42 eb 0d 63 a9 4c d1  |.:. Y.{..B..c.L.|
000001a0  9c 42 8c a8 cb c6 2c a2  46 c7 0a bc d0 c5 58 56  |.B....,.F.....XV|
000001b0  d1 87 18 64 6d 14 4e 87  dc 4c 46 68 90 3a 00 00  |...dm.N..LFh.:..|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  a7 23 3f 44 62 9f 02 70  f2 00 5c a5 f6 28 35 b3  |.#?Db..p..\..(5.|
00000010  97 a1 d8 83 f4 db 2e e6  ec ec 49 3a 99 09 ab 3a  |..........I:...:|
00000020  cb 8c c2 a1 56 cf e8 f1  6e 46 0e b9 5b d4 81 f1  |....V...nF..[...|
00000030  f7 e8 92 63 56 e9 6c 72  18 53 ab ef 06 9a a5 c8  |...cV.lr.S......|
00000040  2d 04 81 11 4e e7 ac 70  45 8e 84 ff 86 6b 71 b3  |-...N..pE....kq.|
00000050  d9 c6 6c 42 3c dd 15 68  05 d8 08 5a 74 89 f6 86  |..lB<..h...Zt...|
00000060  8a 6f ea 67 aa 38 68 17  4c 2c a5 87 17 4f 1d 8f  |.o.g.8h.L,...O..|
00000070  54 5e a2 22 7e 0f d4 b7  77 55 56 54 d1 45 96 2c  |T^."~...wUVT.E.,|
00000080  b7 b9 cf 4b 0c a6 7c 42  d9 b4 4b 9e 36 9c 7c 18  |...K..|B..K.6.|.|
00000090  86 d7 ca 44 19 a2 a5 33  55 10 cb 78 17 1f 37 dc  |...D...3U..x..7.|
000000a0  32 ae f9 69 0a d6 29 be  76 15 f5 ad da fd ae f2  |2..i..).v.......|
000000b0  16 6e 20 14 ad b9 89 38  87 c6 dd 16 fe 89 e4 8c  |.n ....8........|
000000c0  12 77 45 b0 de 8b e1 42  3c 3d 85 06 06 3a 25 da  |.wE....B<=...:%.|
000000d0  d4 19 11 8c f2 18 f0 0b  cd 5a 4f fa f6 8e 2e f3  |.........ZO.....|
000000e0  c2 4a 17 27 79 a6 f8 de  6b c0 13 7a 92 4e d3 15  |.J.'y...k..z.N..|
000000f0  5c 29 84 03 09 8c c4 67  07 51 5d d0 e0 7e da 27  |\).....g.Q]..~.'|
00000100  f2 43 39 1c 7c f0 76 64  15 3f ca 27 e1 50 56 7d  |.C9.|.vd.?.'.PV}|
00000110  57 77 de 68 65 3d 13 c2  25 85 3e 45 a0 e8 96 d4  |Ww.he=..%.>E....|
00000120  3f a2 58 e9 5b ed fa e2  5a 44 e4 6e c0 f7 ce c1  |?.X.[...ZD.n....|
00000130  3c b8 14 d2 0b bd 4f 79  13 c3 47 b1 f8 6c dc e6  |<.....Oy..G..l..|
00000140  1c 65 c8 4b 30 d7 c8 62  83 65 22 5b 0e 4a 16 d6  |.e.K0..b.e"[.J..|
00000150  0e 9f 3f 3e 40 2b 1c 18  3b 7a 48 3f 29 6c b4 67  |..?>@+..;zH?)l.g|
00000160  bc ff 61 bd c7 d7 df c6  ce 20 3d 6c 07 74 e6 5c  |..a...... =l.t.\|
00000170  de 40 76 31 19 41 bb 52  ff 5f 3e 60 c6 46 56 12  |.@v1.A.R._>`.FV.|
00000180  49 9a 79 d8 c0 3e 11 b2  b9 5a 33 cf fb 8f 8c e0  |I.y..>...Z3.....|
00000190  64 b0 81 5b 81 5c d5 dc  f3 98 a2 24 6a d6 52 0d  |d..[.\.....$j.R.|
000001a0  db 5d f2 2f 63 27 7b f8  9a ff 9e ae 0e a0 bd df  |.]./c'{.........|
000001b0  0f 8d 78 dc 61 90 0f 05  da cf 36 2d 05 31 00 fe  |..x.a.....6-.1..|
000001c0  ff ff 82 fe ff ff 01 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

What does that mean under SDA1?  How can I reinstall stage2?

---

### Post by oldfred on 2010-04-21
I am also trying to find out if grub has a bug or if users are just checking all the boxes on the grub install screen with Lucid. Did you check all the boxes? You have grub installed to many of the partitions.

You have Lucid which is still beta. Your grub in sda says it is booting from sda1. You seem to have a partial install in sdb1 and another copy of lucid in sdc1. Your sda1 also has one file left over from grub legacy.
   8.7GB: boot/grub/stage2

Are you able to boot from either sda or sdb or only the liveCd.

To reinstall, follow directions for grub2:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Even though the script says it is booting from the first partition on the same drive, my system has lucid in sdc7 and grub in sda and it says same drive partition 7 which I know is wrong since I only have 3 partitions in sda, but my boot works. So I am not 100% sure your boot is correct. The reinstall should tell us, if it works.

It also may not be a grub issue. Have you tried holding down the shift key to see if you get a menu? You may be past grub as if it only sees one system it will not show the menu. Then your issue may be video.

---

### Post by outleradam on 2010-04-21
I found another site which provided some information and I modified their technique because I had already installed grub-pc.  I ran the following:
```
dpkg-reconfigure grub-pc
```
and it left me only needing a new core.img file.   



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 17055296 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 4874418 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   601,409,535   601,407,488  83 Linux
/dev/sda2         601,411,584   625,141,743    23,730,160  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   381,672,269   381,672,207  83 Linux
/dev/sdb2         381,672,332   390,716,864     9,044,533   5 Extended
Empty Partition


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   224,827,391   224,825,344  83 Linux
/dev/sdc2         224,829,439   234,440,703     9,611,265   5 Extended
/dev/sdc5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        859512c6-3aee-431f-b973-11d1380b400a   ext4                                     
/dev/sda2        3f85add8-ddca-476b-954f-37659347dbda   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        be50b68b-01b4-4a1b-8da7-06f22fd7c215   ext3       backup                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8f0de3dc-af33-47c2-9733-03b50ef4b63d   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        6f3ebebe-eadb-41df-a0d6-288f64cce679   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro   
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro   
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    echo    'Loading Linux 2.6.32-19-generic ...'
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-16-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux /boot/vmlinuz-2.6.32-16-generic root=UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d ro quiet splash
    initrd /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux /boot/vmlinuz-2.6.32-16-generic root=UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d ro single
    initrd /boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=859512c6-3aee-431f-b973-11d1380b400a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3f85add8-ddca-476b-954f-37659347dbda none            swap    sw              0       0

//192.168.1.1/public /home/mythtv/NAS cifs credentials=/home/adam/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

=================== sda1: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/core.img
 120.3GB: boot/grub/grub.cfg
   8.7GB: boot/grub/stage2
   8.7GB: boot/initrd.img-2.6.32-19-generic
   9.7GB: boot/initrd.img-2.6.32-21-generic
   8.7GB: boot/vmlinuz-2.6.32-19-generic
    .7GB: boot/vmlinuz-2.6.32-21-generic
   9.7GB: initrd.img
   8.7GB: initrd.img.old
    .7GB: vmlinuz
   8.7GB: vmlinuz.old

=================== sdb1: Location of files loaded by Grub: ===================


 141.0GB: boot/grub/core.img

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
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
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    echo    Loading Linux 2.6.32-16-generic ...
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro quiet splash
    initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single
    initrd /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=6f3ebebe-eadb-41df-a0d6-288f64cce679 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 111.8GB: boot/grub/core.img
  58.1GB: boot/grub/grub.cfg
 111.8GB: boot/initrd.img-2.6.32-16-generic
 111.8GB: boot/vmlinuz-2.6.32-16-generic
 111.8GB: initrd.img
 111.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  93 9d 92 4f 85 5d 18 21  a0 41 a0 f6 6f 85 a8 ca  |...O.].!.A..o...|
00000010  03 70 c7 17 e0 fa 28 76  14 8c 40 83 0f 0f a1 c3  |.p....(v..@.....|
00000020  31 f4 87 ae f2 92 07 8b  42 cf 0a b1 c2 87 07 c1  |1.......B.......|
00000030  b8 c4 a0 df f1 3b d0 e2  18 7f 94 49 83 89 d7 fb  |.....;.....I....|
00000040  1e b3 23 43 d6 e1 f4 e3  0b 87 8e 85 4a a7 2c 4c  |..#C........J.,L|
00000050  78 88 73 5e 31 41 4a 33  92 2a be a2 87 60 c1 48  |x.s^1AJ3.*...`.H|
00000060  59 33 e8 1f 1b d4 6c 60  a9 52 4f aa 6a f8 a5 92  |Y3....l`.RO.j...|
00000070  27 47 5d 0e 21 4b 88 35  85 cd 1b 3d d3 9a 2c 2a  |'G].!K.5...=..,*|
00000080  b4 f3 b5 d0 d1 ed 98 a4  34 4b 51 af bd 91 69 c4  |........4KQ...i.|
00000090  2f 0a b5 dd d5 ca 24 ea  5a 84 73 50 62 80 44 00  |/.....$.Z.sPb.D.|
000000a0  48 30 96 a0 0c c5 06 b8  41 40 22 a3 af 30 68 05  |H0......A@"..0h.|
000000b0  62 92 08 a0 0e 1e 06 ae  f4 a4 15 81 dc d1 91 de  |b...............|
000000c0  9d f3 91 68 06 b4 7e 72  2c 59 f1 b4 49 00 d0 2a  |...h..~r,Y..I..*|
000000d0  1d 04 40 36 05 a0 28 e9  a0 b0 43 ff be 1a 69 2d  |..@6..(...C...i-|
000000e0  22 62 10 04 ef 97 ff 8b  09 fc b1 ee 24 7d 21 03  |"b..........$}!.|
000000f0  4b 48 23 00 24 65 12 38  ed 10 53 8d 42 d8 90 27  |KH#.$e.8..S.B..'|
00000100  c3 96 0f 52 ec 0f 61 73  de 1e 92 42 83 07 90 6f  |...R..as...B...o|
00000110  c3 ee 94 14 6d e1 0a 44  bf 75 c2 c5 05 fe a8 d8  |....m..D.u......|
00000120  da d9 13 95 0f 27 a2 68  19 1d bf 0b c5 21 a1 20  |.....'.h.....!. |
00000130  6e 60 bb f1 97 64 1b a1  d3 b3 12 be f6 1d ab 07  |n`...d..........|
00000140  52 36 ed 23 0a 0b c7 e5  39 08 55 34 1c a4 62 2f  |R6.#....9.U4..b/|
00000150  19 83 39 45 00 e6 49 03  04 06 40 00 00 01 11 32  |..9E..I...@....2|
00000160  1c 3c 25 3f 1d 1a d6 75  0e 21 05 15 2b 81 a5 46  |.<%?...u.!..+..F|
00000170  59 80 72 8c bc 42 11 c7  06 1f 42 e1 f7 96 64 4e  |Y.r..B....B...dN|
00000180  36 03 e0 6e 8a a9 22 ad  41 7e e8 75 0e 03 76 75  |6..n..".A~.u..vu|
00000190  15 3a 0a 20 59 90 7b a2  88 42 eb 0d 63 a9 4c d1  |.:. Y.{..B..c.L.|
000001a0  9c 42 8c a8 cb c6 2c a2  46 c7 0a bc d0 c5 58 56  |.B....,.F.....XV|
000001b0  d1 87 18 64 6d 14 4e 87  dc 4c 46 68 90 3a 00 00  |...dm.N..LFh.:..|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  a7 23 3f 44 62 9f 02 70  f2 00 5c a5 f6 28 35 b3  |.#?Db..p..\..(5.|
00000010  97 a1 d8 83 f4 db 2e e6  ec ec 49 3a 99 09 ab 3a  |..........I:...:|
00000020  cb 8c c2 a1 56 cf e8 f1  6e 46 0e b9 5b d4 81 f1  |....V...nF..[...|
00000030  f7 e8 92 63 56 e9 6c 72  18 53 ab ef 06 9a a5 c8  |...cV.lr.S......|
00000040  2d 04 81 11 4e e7 ac 70  45 8e 84 ff 86 6b 71 b3  |-...N..pE....kq.|
00000050  d9 c6 6c 42 3c dd 15 68  05 d8 08 5a 74 89 f6 86  |..lB<..h...Zt...|
00000060  8a 6f ea 67 aa 38 68 17  4c 2c a5 87 17 4f 1d 8f  |.o.g.8h.L,...O..|
00000070  54 5e a2 22 7e 0f d4 b7  77 55 56 54 d1 45 96 2c  |T^."~...wUVT.E.,|
00000080  b7 b9 cf 4b 0c a6 7c 42  d9 b4 4b 9e 36 9c 7c 18  |...K..|B..K.6.|.|
00000090  86 d7 ca 44 19 a2 a5 33  55 10 cb 78 17 1f 37 dc  |...D...3U..x..7.|
000000a0  32 ae f9 69 0a d6 29 be  76 15 f5 ad da fd ae f2  |2..i..).v.......|
000000b0  16 6e 20 14 ad b9 89 38  87 c6 dd 16 fe 89 e4 8c  |.n ....8........|
000000c0  12 77 45 b0 de 8b e1 42  3c 3d 85 06 06 3a 25 da  |.wE....B<=...:%.|
000000d0  d4 19 11 8c f2 18 f0 0b  cd 5a 4f fa f6 8e 2e f3  |.........ZO.....|
000000e0  c2 4a 17 27 79 a6 f8 de  6b c0 13 7a 92 4e d3 15  |.J.'y...k..z.N..|
000000f0  5c 29 84 03 09 8c c4 67  07 51 5d d0 e0 7e da 27  |\).....g.Q]..~.'|
00000100  f2 43 39 1c 7c f0 76 64  15 3f ca 27 e1 50 56 7d  |.C9.|.vd.?.'.PV}|
00000110  57 77 de 68 65 3d 13 c2  25 85 3e 45 a0 e8 96 d4  |Ww.he=..%.>E....|
00000120  3f a2 58 e9 5b ed fa e2  5a 44 e4 6e c0 f7 ce c1  |?.X.[...ZD.n....|
00000130  3c b8 14 d2 0b bd 4f 79  13 c3 47 b1 f8 6c dc e6  |<.....Oy..G..l..|
00000140  1c 65 c8 4b 30 d7 c8 62  83 65 22 5b 0e 4a 16 d6  |.e.K0..b.e"[.J..|
00000150  0e 9f 3f 3e 40 2b 1c 18  3b 7a 48 3f 29 6c b4 67  |..?>@+..;zH?)l.g|
00000160  bc ff 61 bd c7 d7 df c6  ce 20 3d 6c 07 74 e6 5c  |..a...... =l.t.\|
00000170  de 40 76 31 19 41 bb 52  ff 5f 3e 60 c6 46 56 12  |.@v1.A.R._>`.FV.|
00000180  49 9a 79 d8 c0 3e 11 b2  b9 5a 33 cf fb 8f 8c e0  |I.y..>...Z3.....|
00000190  64 b0 81 5b 81 5c d5 dc  f3 98 a2 24 6a d6 52 0d  |d..[.\.....$j.R.|
000001a0  db 5d f2 2f 63 27 7b f8  9a ff 9e ae 0e a0 bd df  |.]./c'{.........|
000001b0  0f 8d 78 dc 61 90 0f 05  da cf 36 2d 05 31 00 fe  |..x.a.....6-.1..|
000001c0  ff ff 82 fe ff ff 01 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 17055296 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 4874418 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   601,409,535   601,407,488  83 Linux
/dev/sda2         601,411,584   625,141,743    23,730,160  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   381,672,269   381,672,207  83 Linux
/dev/sdb2         381,672,332   390,716,864     9,044,533   5 Extended
Empty Partition


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   224,827,391   224,825,344  83 Linux
/dev/sdc2         224,829,439   234,440,703     9,611,265   5 Extended
/dev/sdc5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        859512c6-3aee-431f-b973-11d1380b400a   ext4                                     
/dev/sda2        3f85add8-ddca-476b-954f-37659347dbda   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        be50b68b-01b4-4a1b-8da7-06f22fd7c215   ext3       backup                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8f0de3dc-af33-47c2-9733-03b50ef4b63d   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        6f3ebebe-eadb-41df-a0d6-288f64cce679   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro   
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro   
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    echo    'Loading Linux 2.6.32-19-generic ...'
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-16-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux /boot/vmlinuz-2.6.32-16-generic root=UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d ro quiet splash
    initrd /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux /boot/vmlinuz-2.6.32-16-generic root=UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d ro single
    initrd /boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=859512c6-3aee-431f-b973-11d1380b400a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3f85add8-ddca-476b-954f-37659347dbda none            swap    sw              0       0

//192.168.1.1/public /home/mythtv/NAS cifs credentials=/home/adam/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

=================== sda1: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/core.img
 120.3GB: boot/grub/grub.cfg
   8.7GB: boot/grub/stage2
   8.7GB: boot/initrd.img-2.6.32-19-generic
   9.7GB: boot/initrd.img-2.6.32-21-generic
   8.7GB: boot/vmlinuz-2.6.32-19-generic
    .7GB: boot/vmlinuz-2.6.32-21-generic
   9.7GB: initrd.img
   8.7GB: initrd.img.old
    .7GB: vmlinuz
   8.7GB: vmlinuz.old

=================== sdb1: Location of files loaded by Grub: ===================


 141.0GB: boot/grub/core.img

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
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
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    echo    Loading Linux 2.6.32-16-generic ...
    linux    /boot/vmlinuz-2.6.32-16-generic root=UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 8f0de3dc-af33-47c2-9733-03b50ef4b63d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro quiet splash
    initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 859512c6-3aee-431f-b973-11d1380b400a
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=859512c6-3aee-431f-b973-11d1380b400a ro single
    initrd /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=8f0de3dc-af33-47c2-9733-03b50ef4b63d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=6f3ebebe-eadb-41df-a0d6-288f64cce679 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 111.8GB: boot/grub/core.img
  58.1GB: boot/grub/grub.cfg
 111.8GB: boot/initrd.img-2.6.32-16-generic
 111.8GB: boot/vmlinuz-2.6.32-16-generic
 111.8GB: initrd.img
 111.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  93 9d 92 4f 85 5d 18 21  a0 41 a0 f6 6f 85 a8 ca  |...O.].!.A..o...|
00000010  03 70 c7 17 e0 fa 28 76  14 8c 40 83 0f 0f a1 c3  |.p....(v..@.....|
00000020  31 f4 87 ae f2 92 07 8b  42 cf 0a b1 c2 87 07 c1  |1.......B.......|
00000030  b8 c4 a0 df f1 3b d0 e2  18 7f 94 49 83 89 d7 fb  |.....;.....I....|
00000040  1e b3 23 43 d6 e1 f4 e3  0b 87 8e 85 4a a7 2c 4c  |..#C........J.,L|
00000050  78 88 73 5e 31 41 4a 33  92 2a be a2 87 60 c1 48  |x.s^1AJ3.*...`.H|
00000060  59 33 e8 1f 1b d4 6c 60  a9 52 4f aa 6a f8 a5 92  |Y3....l`.RO.j...|
00000070  27 47 5d 0e 21 4b 88 35  85 cd 1b 3d d3 9a 2c 2a  |'G].!K.5...=..,*|
00000080  b4 f3 b5 d0 d1 ed 98 a4  34 4b 51 af bd 91 69 c4  |........4KQ...i.|
00000090  2f 0a b5 dd d5 ca 24 ea  5a 84 73 50 62 80 44 00  |/.....$.Z.sPb.D.|
000000a0  48 30 96 a0 0c c5 06 b8  41 40 22 a3 af 30 68 05  |H0......A@"..0h.|
000000b0  62 92 08 a0 0e 1e 06 ae  f4 a4 15 81 dc d1 91 de  |b...............|
000000c0  9d f3 91 68 06 b4 7e 72  2c 59 f1 b4 49 00 d0 2a  |...h..~r,Y..I..*|
000000d0  1d 04 40 36 05 a0 28 e9  a0 b0 43 ff be 1a 69 2d  |..@6..(...C...i-|
000000e0  22 62 10 04 ef 97 ff 8b  09 fc b1 ee 24 7d 21 03  |"b..........$}!.|
000000f0  4b 48 23 00 24 65 12 38  ed 10 53 8d 42 d8 90 27  |KH#.$e.8..S.B..'|
00000100  c3 96 0f 52 ec 0f 61 73  de 1e 92 42 83 07 90 6f  |...R..as...B...o|
00000110  c3 ee 94 14 6d e1 0a 44  bf 75 c2 c5 05 fe a8 d8  |....m..D.u......|
00000120  da d9 13 95 0f 27 a2 68  19 1d bf 0b c5 21 a1 20  |.....'.h.....!. |
00000130  6e 60 bb f1 97 64 1b a1  d3 b3 12 be f6 1d ab 07  |n`...d..........|
00000140  52 36 ed 23 0a 0b c7 e5  39 08 55 34 1c a4 62 2f  |R6.#....9.U4..b/|
00000150  19 83 39 45 00 e6 49 03  04 06 40 00 00 01 11 32  |..9E..I...@....2|
00000160  1c 3c 25 3f 1d 1a d6 75  0e 21 05 15 2b 81 a5 46  |.<%?...u.!..+..F|
00000170  59 80 72 8c bc 42 11 c7  06 1f 42 e1 f7 96 64 4e  |Y.r..B....B...dN|
00000180  36 03 e0 6e 8a a9 22 ad  41 7e e8 75 0e 03 76 75  |6..n..".A~.u..vu|
00000190  15 3a 0a 20 59 90 7b a2  88 42 eb 0d 63 a9 4c d1  |.:. Y.{..B..c.L.|
000001a0  9c 42 8c a8 cb c6 2c a2  46 c7 0a bc d0 c5 58 56  |.B....,.F.....XV|
000001b0  d1 87 18 64 6d 14 4e 87  dc 4c 46 68 90 3a 00 00  |...dm.N..LFh.:..|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  a7 23 3f 44 62 9f 02 70  f2 00 5c a5 f6 28 35 b3  |.#?Db..p..\..(5.|
00000010  97 a1 d8 83 f4 db 2e e6  ec ec 49 3a 99 09 ab 3a  |..........I:...:|
00000020  cb 8c c2 a1 56 cf e8 f1  6e 46 0e b9 5b d4 81 f1  |....V...nF..[...|
00000030  f7 e8 92 63 56 e9 6c 72  18 53 ab ef 06 9a a5 c8  |...cV.lr.S......|
00000040  2d 04 81 11 4e e7 ac 70  45 8e 84 ff 86 6b 71 b3  |-...N..pE....kq.|
00000050  d9 c6 6c 42 3c dd 15 68  05 d8 08 5a 74 89 f6 86  |..lB<..h...Zt...|
00000060  8a 6f ea 67 aa 38 68 17  4c 2c a5 87 17 4f 1d 8f  |.o.g.8h.L,...O..|
00000070  54 5e a2 22 7e 0f d4 b7  77 55 56 54 d1 45 96 2c  |T^."~...wUVT.E.,|
00000080  b7 b9 cf 4b 0c a6 7c 42  d9 b4 4b 9e 36 9c 7c 18  |...K..|B..K.6.|.|
00000090  86 d7 ca 44 19 a2 a5 33  55 10 cb 78 17 1f 37 dc  |...D...3U..x..7.|
000000a0  32 ae f9 69 0a d6 29 be  76 15 f5 ad da fd ae f2  |2..i..).v.......|
000000b0  16 6e 20 14 ad b9 89 38  87 c6 dd 16 fe 89 e4 8c  |.n ....8........|
000000c0  12 77 45 b0 de 8b e1 42  3c 3d 85 06 06 3a 25 da  |.wE....B<=...:%.|
000000d0  d4 19 11 8c f2 18 f0 0b  cd 5a 4f fa f6 8e 2e f3  |.........ZO.....|
000000e0  c2 4a 17 27 79 a6 f8 de  6b c0 13 7a 92 4e d3 15  |.J.'y...k..z.N..|
000000f0  5c 29 84 03 09 8c c4 67  07 51 5d d0 e0 7e da 27  |\).....g.Q]..~.'|
00000100  f2 43 39 1c 7c f0 76 64  15 3f ca 27 e1 50 56 7d  |.C9.|.vd.?.'.PV}|
00000110  57 77 de 68 65 3d 13 c2  25 85 3e 45 a0 e8 96 d4  |Ww.he=..%.>E....|
00000120  3f a2 58 e9 5b ed fa e2  5a 44 e4 6e c0 f7 ce c1  |?.X.[...ZD.n....|
00000130  3c b8 14 d2 0b bd 4f 79  13 c3 47 b1 f8 6c dc e6  |<.....Oy..G..l..|
00000140  1c 65 c8 4b 30 d7 c8 62  83 65 22 5b 0e 4a 16 d6  |.e.K0..b.e"[.J..|
00000150  0e 9f 3f 3e 40 2b 1c 18  3b 7a 48 3f 29 6c b4 67  |..?>@+..;zH?)l.g|
00000160  bc ff 61 bd c7 d7 df c6  ce 20 3d 6c 07 74 e6 5c  |..a...... =l.t.\|
00000170  de 40 76 31 19 41 bb 52  ff 5f 3e 60 c6 46 56 12  |.@v1.A.R._>`.FV.|
00000180  49 9a 79 d8 c0 3e 11 b2  b9 5a 33 cf fb 8f 8c e0  |I.y..>...Z3.....|
00000190  64 b0 81 5b 81 5c d5 dc  f3 98 a2 24 6a d6 52 0d  |d..[.\.....$j.R.|
000001a0  db 5d f2 2f 63 27 7b f8  9a ff 9e ae 0e a0 bd df  |.]./c'{.........|
000001b0  0f 8d 78 dc 61 90 0f 05  da cf 36 2d 05 31 00 fe  |..x.a.....6-.1..|
000001c0  ff ff 82 fe ff ff 01 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I'll read some more, but if anyone knows how to reinstall core.img, that would be great!

---

### Post by outleradam on 2010-04-21
> **oldfred said:**
> I am also trying to find out if grub has a bug or if users are just checking all the boxes on the grub install screen with Lucid. Did you check all the boxes? You have grub installed to many of the partitions.

You have Lucid which is still beta. Your grub in sda says it is booting from sda1. You seem to have a partial install in sdb1 and another copy of lucid in sdc1. Your sda1 also has one file left over from grub legacy.
   8.7GB: boot/grub/stage2

Are you able to boot from either sda or sdb or only the liveCd.

To reinstall, follow directions for grub2:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Even though the script says it is booting from the first partition on the same drive, my system has lucid in sdc7 and grub in sda and it says same drive partition 7 which I know is wrong since I only have 3 partitions in sda, but my boot works. So I am not 100% sure your boot is correct. The reinstall should tell us, if it works.

It also may not be a grub issue. Have you tried holding down the shift key to see if you get a menu? You may be past grub as if it only sees one system it will not show the menu. Then your issue may be video.
Thank you oldfred.   I am now only having a problem with restoring core.img.  

This restored grub
```
sudo apt-get install grub-pc
``` 
Now I need to reinstall core.img

---

### Post by oldfred on 2010-04-21
You have copies of core.img in sda1, sdb1 & sdc1 per script. Are these different versions i.e. 1.97 Karmic vs 1.98 Lucid?

To totally reinstall grub2 you would have to chroot into your system.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

---

### Post by presence1960 on 2010-04-21
> **oldfred said:**
>  if users are just checking all the boxes on the grub install screen with Lucid. Did you check all the boxes? You have grub installed to many of the partitions.





It seems that a few have installed GRUB 2 to boot sectors of every partition on their machine. Seriously doubt it is a bug as none have been reported. Most likely user inexperience and/or error.

---

### Post by oldfred on 2010-04-21
Presence,

I have eight posters who ran the boot script with grub installed in the partitions. Many others who did not run script but windows stopped working and we just had them run the fixboot commands. It may not be a bug but you & I know the difference between MBR and PBR and what is required to boot. I get the idea new users think they want to be able to use all these partitions so they have to tell grub to "use" them, not realizing they are installing grub to the partition. With the adamant restrictions on installing grub2 to a partition I am surprised the grub menu makes it so easy to install to partitions. I am sure these are all new users making errors, but if this is any indication once Lucid is released we will be flooded with people having window not working.

---

### Post by presence1960 on 2010-04-22
> **oldfred said:**
> Presence,

I have eight posters who ran the boot script with grub installed in the partitions. Many others who did not run script but windows stopped working and we just had them run the fixboot commands. It may not be a bug but you & I know the difference between MBR and PBR and what is required to boot. I get the idea new users think they want to be able to use all these partitions so they have to tell grub to "use" them, not realizing they are installing grub to the partition. With the adamant restrictions on installing grub2 to a partition I am surprised the grub menu makes it so easy to install to partitions. I am sure these are all new users making errors, but if this is any indication once Lucid is released we will be flooded with people having window not working.

I agree. They will have to learn from their mistakes.

---

### Post by outleradam on 2010-04-22
Package Grub-PC says "If you are unsure choose all of them"
 
This is a bug.

---

### Post by presence1960 on 2010-04-22
> **outleradam said:**
> Package Grub-PC says "If you are unsure choose all of them"
 
This is a bug.

I  may be incorrect but I believe the message you are referring to has to with MBR (sda, sdb, sdc, etc) not partitions (sda1, sda2,sdb1,sdb2, etc)

---

### Post by outleradam on 2010-04-22
no, grub-pc says if you are unsure select all, then shows something like this
```

[*] SDA
  
[*] SDA1
  [ ] SDA2
  [ ] SDA3

[*] SDB
  [ ] SDB1
  [ ] SDB2

```This is what screwed me up.  My issue is resolved.

---

### Post by oldfred on 2010-04-22
I saw that grub install menu when I installed Lucid beta,  but it only had a drop down box to choose one MBR with the release candidate. I have not tried the dpkg reinstall yet as it runs some of the same grub install.

---

### Post by wilee-nilee on 2010-04-22
> **oldfred said:**
> I saw that grub install menu when I installed Lucid beta,  but it only had a drop down box to choose one MBR with the release candidate. I have not tried the dpkg reinstall yet as it runs some of the same grub install.

Well it looks like you and presence1960 and the others who really can diagnose and help others may have their work cut out for them. I just try to get people to post the bootscript to speed things along. This also generally gets the others who are throwing ideas at a possibly inexperienced user to lay back and let the people who can really help get to it.

I have never seen that choice as shown I am not sure where that is from. I will do a lucid install in virtual again to see if this comes up.

---

### Post by outleradam on 2010-04-23
It comes when you install windows XP.  Win XP killed the bootloader on another hard disk.  I booted from a USB, and then ran apt-get install grub-pc.  that's where the option came from.

---

