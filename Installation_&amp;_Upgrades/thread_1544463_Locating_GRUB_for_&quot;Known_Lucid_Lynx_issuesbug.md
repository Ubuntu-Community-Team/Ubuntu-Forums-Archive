---
title: "Locating GRUB for &quot;Known Lucid Lynx issues/bugs with workarounds&quot;"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by ubuntu1sttimer on 2010-08-02
After updating 9.10 to 10.04 I found myself being unable to boot into Windows Vista on my dual boot system. The "sticky" for this forum has a way to deal with this but requires in step "Second" that I know the windows system partition. Since it appears that there are two windows ntfs partitions on sda I don't know which to pick. I have attached my results.txt from runing boot_info_script*.sh

Any help would be greatly appreciated.


Below: Instructions indicating what hard drive I need to select.

  First   screen:  Select "No Log" and press enter.
  Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".
  Third   screen:  "intel"
  Fourth  screen:  "advanced",
  Fifth   screen:  Select the Windows system partition  and choose "boot"
  Sixth   screen:  "BackupBS"
  Seventh screen:  type "Y" to confirm

---

### Post by Rubi1200 on 2010-08-02
In future, please post the results of the bootscript like this (it makes for much easier reading):
 
```
 
Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 279359 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sda2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 279359 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   
sda3: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 279359 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
sdb1: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 279359 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________
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
/dev/sda1               2,048     3,147,775     3,145,728  27 Hidden HPFS/NTFS
/dev/sda2           3,147,776    44,943,359    41,795,584   f W95 Ext d (LBA)
/dev/sda5           3,149,824    44,943,359    41,793,536   7 HPFS/NTFS
/dev/sda3    *     44,943,360   625,139,711   580,196,352   7 HPFS/NTFS
 
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1                  63   966,807,764   966,807,702  83 Linux
/dev/sdb2         966,807,765   976,768,064     9,960,300   5 Extended
/dev/sdb5         966,807,828   976,768,064     9,960,237  82 Linux swap / Solaris
 
blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/sda1        EEF81F38F81EFE91                       ntfs       RECOVERY                      
/dev/sda2: PTTYPE="dos" 
/dev/sda3        DCA021C6A021A84A                       ntfs       Local Disk                    
/dev/sda5        AA54205E54202F8D                       ntfs       ImageBackup                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        862ff519-00d8-4af1-8781-8c0dc43c83eb   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        72f8374a-337e-4408-851a-baa2bf1e3e63   swap                                     
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
 
=========================== sdb1/boot/grub/grub.cfg: ===========================
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 862ff519-00d8-4af1-8781-8c0dc43c83eb
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 862ff519-00d8-4af1-8781-8c0dc43c83eb
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
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 862ff519-00d8-4af1-8781-8c0dc43c83eb
 linux /boot/vmlinuz-2.6.32-22-generic root=UUID=862ff519-00d8-4af1-8781-8c0dc43c83eb ro   quiet splash
 initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 862ff519-00d8-4af1-8781-8c0dc43c83eb
 echo 'Loading Linux 2.6.32-22-generic ...'
 linux /boot/vmlinuz-2.6.32-22-generic root=UUID=862ff519-00d8-4af1-8781-8c0dc43c83eb ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 862ff519-00d8-4af1-8781-8c0dc43c83eb
 linux /boot/vmlinuz-2.6.31-22-generic root=UUID=862ff519-00d8-4af1-8781-8c0dc43c83eb ro   quiet splash
 initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 862ff519-00d8-4af1-8781-8c0dc43c83eb
 echo 'Loading Linux 2.6.31-22-generic ...'
 linux /boot/vmlinuz-2.6.31-22-generic root=UUID=862ff519-00d8-4af1-8781-8c0dc43c83eb ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-10-rt' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 862ff519-00d8-4af1-8781-8c0dc43c83eb
 linux /boot/vmlinuz-2.6.31-10-rt root=UUID=862ff519-00d8-4af1-8781-8c0dc43c83eb ro   quiet splash
 initrd /boot/initrd.img-2.6.31-10-rt
}
menuentry 'Ubuntu, with Linux 2.6.31-10-rt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 862ff519-00d8-4af1-8781-8c0dc43c83eb
 echo 'Loading Linux 2.6.31-10-rt ...'
 linux /boot/vmlinuz-2.6.31-10-rt root=UUID=862ff519-00d8-4af1-8781-8c0dc43c83eb ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.31-10-rt
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 862ff519-00d8-4af1-8781-8c0dc43c83eb
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 862ff519-00d8-4af1-8781-8c0dc43c83eb
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
 insmod ntfs
 set root='(hd0,3)'
 search --no-floppy --fs-uuid --set dca021c6a021a84a
 drivemap -s (hd0) ${root}
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sdb1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=862ff519-00d8-4af1-8781-8c0dc43c83eb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=72f8374a-337e-4408-851a-baa2bf1e3e63 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sdb1: Location of files loaded by Grub: ===================
 
    .1GB: boot/grub/core.img
    .5GB: boot/grub/grub.cfg
   6.5GB: boot/initrd.img-2.6.31-10-rt
  11.6GB: boot/initrd.img-2.6.31-22-generic
  11.7GB: boot/initrd.img-2.6.32-22-generic
   4.2GB: boot/vmlinuz-2.6.31-10-rt
   4.4GB: boot/vmlinuz-2.6.31-22-generic
   4.2GB: boot/vmlinuz-2.6.32-22-generic
  11.7GB: initrd.img
   6.5GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old
 

```

---

### Post by oldfred on 2010-08-02
Your windows is in sda3 as that is where the boot files are. You have grub everywhere but in other partitions it is an area not otherwise used so it does not really matter.

---

### Post by ubuntu1sttimer on 2010-08-03
Thanks for the help "oldfred".  

Unfortunately, it did not go well. Have given up and reformated the drive, reinstalled Vista, and called it quits with Ubuntu dual boot. Ubuntu is nice when it works but when it doesn't which has happened all too often for me, it causes too many problems. Will continue to use Ubuntu for basic needs only.

---

