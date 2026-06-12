---
title: "GRUB/StartUp edit"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by chkl on 2010-10-30
I have a dual boot / dual HD DELL laptop with Win7 on HDA and Ubuntu10.10 (+ a Win 2008 server) on HDB.
It all works OK, exept for trying to edit the initial GRUB display, e.g. setting default OS and timeout via StartUp manager does not work. I suppose this is due to both HD's/MBR's beeing somehow involved in the boot process (???).
Any suggestions as how to edit GRUB options (without breaking the dual boot setup) in my case ?

```
               
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

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
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-CD82BE302475190B7D562D021E3B59D0.mbr is 
                       trying to chain load sector #63 on boot drive #1 
                       BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #63 on boot drive #1
    Operating System:  Windows 7
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
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

/dev/sda1                  63        80,324        80,262  16 Hidden FAT16
/dev/sda2              81,920    30,801,919    30,720,000  17 Hidden HPFS/NTFS
/dev/sda3    *     30,812,670   872,731,124   841,918,455   7 HPFS/NTFS
/dev/sda4         872,729,140   976,768,064   104,038,925   5 Extended
/dev/sda5         872,731,188   976,768,064   104,036,877   7 HPFS/NTFS

/dev/sda3 overlaps with /dev/sda4

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   450,122,960   450,120,913   7 HPFS/NTFS
/dev/sdb2         450,123,774   611,964,044   161,840,271   f W95 Ext d (LBA)
/dev/sdb5         450,123,776   574,227,359   124,103,584  83 Linux
/dev/sdb6         595,690,263   611,964,044    16,273,782  82 Linux swap / Solaris
/dev/sdb3         611,964,045   770,975,414   159,011,370   7 HPFS/NTFS
/dev/sdb4         770,975,415   787,843,664    16,868,250   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        F4D44968D4492E64                       ntfs       RECOVERY                      
/dev/sda3        DAC84D3FC84D1AE1                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        01CADD75298EB190                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2298F50498F4D76F                       ntfs       DATAPART1                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        01CAF053CB504E30                       ntfs       Win2008Srv                    
/dev/sdb4        01CB74219106B5F0                       ntfs       BData                         
/dev/sdb5        46c1385d-a56f-4c7b-b226-c2812c97b6dd   ext4                                     
/dev/sdb6        4ee72f9c-f91b-4208-83d3-53d995582370   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sda3/grub/grub.cfg: =============================

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
set default="5"
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
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda3: Location of files loaded by Grub: ===================


    ??GB: grub/core.img
    ??GB: grub/grub.cfg

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="3"
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
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 46c1385d-a56f-4c7b-b226-c2812c97b6dd
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod 
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 46c1385d-a56f-4c7b-b226-c2812c97b6dd
set locale_dir=($root)/boot/grub/locale
set lang=sv
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 46c1385d-a56f-4c7b-b226-c2812c97b6dd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=46c1385d-a56f-4c7b-b226-c2812c97b6dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 46c1385d-a56f-4c7b-b226-c2812c97b6dd
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=46c1385d-a56f-4c7b-b226-c2812c97b6dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set f4d44968d4492e64
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set dac84d3fc84d1ae1
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=46c1385d-a56f-4c7b-b226-c2812c97b6dd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4ee72f9c-f91b-4208-83d3-53d995582370 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 235.1GB: boot/grub/core.img
 231.9GB: boot/grub/grub.cfg
 242.0GB: boot/initrd.img-2.6.32-25-generic
 238.0GB: boot/initrd.img-2.6.35-22-generic
 236.7GB: boot/vmlinuz-2.6.32-25-generic
 237.6GB: boot/vmlinuz-2.6.35-22-generic
 238.0GB: initrd.img
 242.0GB: initrd.img.old
 237.6GB: vmlinuz
 236.7GB: vmlinuz.old

```

---

### Post by chkl on 2010-10-30
BTW, another odd thing (I think this has been commented on before but I cannot find the relevant thread):
Both GParted and KDE Partition manager fails to find any OS, partitions or files on /dev/sda  - why ?
/dev/sdb is displayed OK in both progs.

---

### Post by q999 on 2010-10-30
the short=in termanal:

sudo gedit

open boot/   open grub   / open grub.conf 
on defalt set to windows partion number? 2 4 or wherever
save
 reboot

theres many post on this
google=

[http://www.ehow.com/how_2251661_edit-grub-menu-ubuntu.html](http://www.ehow.com/how_2251661_edit-grub-menu-ubuntu.html)

---

### Post by q999 on 2010-10-30
the short=in termanal:

sudo gedit

open boot/   open grub   / open grub.conf 
on defalt set to windows partion line? 2 4 or wherever
save
 reboot

theres many post on this
google=

[http://www.ehow.com/how_2251661_edit-grub-menu-ubuntu.html](http://www.ehow.com/how_2251661_edit-grub-menu-ubuntu.html)

---

### Post by chkl on 2010-10-30
Thanks q999;
the "only" problem is that this does NOT (!!) work on my config.
The /boot/grub/grub.cnf (and /etc/default/grub) files are exactly as intended.

I should perhaps have mentioned that I have tried all kinds of changes in these files but nothing happens to my initial GRUB boot screen.
My guess is that these changes affects /dev/sdb MBR and not /dev/sta  (??) ...
Anybody with experience on a similar system who might care to comment ?

---

