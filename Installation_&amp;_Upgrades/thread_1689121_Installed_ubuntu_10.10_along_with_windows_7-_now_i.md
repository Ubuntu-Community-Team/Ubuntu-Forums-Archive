---
title: "Installed ubuntu 10.10 along with windows 7- now it straight away boots ubuntu"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by dejavu007 on 2011-02-16
I am new to ubuntu. I installed ubuntu after installing windows 7 in different partition now i cannot boot windows7. grub is not showing at all. when i use shift key while starting up it shows the grub but there is no option to select windows.
i used this sudo fdisk -l
here is what i get.
[HTML]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c011c00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       60800   426934673    f  W95 Ext'd (LBA)
/dev/sda5            7650       19122    92156841    7  HPFS/NTFS
/dev/sda6           19123       30595    92156841    7  HPFS/NTFS
/dev/sda7           30596       31343     6000000   82  Linux swap / Solaris
/dev/sda8           35817       46655    87056384    7  HPFS/NTFS
/dev/sda9           46656       60800   113613824    7  HPFS/NTFS
/dev/sda10          31343       35816    35936256   83  Linux

Partition table entries are not in disk order[/HTML]And this is what i get in boot info script
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #10 for (,msdos10)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 646. But according to the info from fdisk, 
                       sda9 starts at sector 749522944.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
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

/dev/sda1    *             63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sda2         122,881,246   976,750,591   853,869,346   f W95 Ext d (LBA)
/dev/sda5         122,881,248   307,194,929   184,313,682   7 HPFS/NTFS
/dev/sda6         307,194,993   491,508,674   184,313,682   7 HPFS/NTFS
/dev/sda7         491,509,760   503,509,759    12,000,000  82 Linux swap / Solaris
/dev/sda8         575,397,888   749,510,655   174,112,768   7 HPFS/NTFS
/dev/sda9         749,522,944   976,750,591   227,227,648   7 HPFS/NTFS
/dev/sda10        503,511,040   575,383,551    71,872,512  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7840 MB, 7840259584 bytes
242 heads, 62 sectors/track, 1020 cylinders, total 15313007 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62    15,304,079    15,304,018   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       c0dc4353-01d3-4625-89b8-17f1a8192aaa   ext3                                     
/dev/sda1        5E8643FB8643D1E7                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        128C86538C8630F1                       ntfs                                     
/dev/sda6        C614920C1492001B                       ntfs                                     
/dev/sda7        92dea14a-c50c-4ee2-9c64-11725dd2edce   swap                                     
/dev/sda8        B0D4550BD454D566                       ntfs       MOVIES A                      
/dev/sda9        AC64A96F64A93CC8                       ntfs       MOVIES B                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        82C6-5A34                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/82C6-5A34         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda6        /media/C614920C1492001B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/128C86538C8630F1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

========================== sda10/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set c0dc4353-01d3-4625-89b8-17f1a8192aaa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set c0dc4353-01d3-4625-89b8-17f1a8192aaa
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set c0dc4353-01d3-4625-89b8-17f1a8192aaa
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c0dc4353-01d3-4625-89b8-17f1a8192aaa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set c0dc4353-01d3-4625-89b8-17f1a8192aaa
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c0dc4353-01d3-4625-89b8-17f1a8192aaa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set c0dc4353-01d3-4625-89b8-17f1a8192aaa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set c0dc4353-01d3-4625-89b8-17f1a8192aaa
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=c0dc4353-01d3-4625-89b8-17f1a8192aaa /               ext3    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0

=================== sda10: Location of files loaded by Grub: ===================


 282.6GB: boot/grub/core.img
 282.7GB: boot/grub/grub.cfg
 282.6GB: boot/initrd.img-2.6.35-22-generic
 282.7GB: boot/vmlinuz-2.6.35-22-generic
 282.6GB: initrd.img
 282.7GB: vmlinuz
```

---

### Post by Quackers on 2011-02-16
Open up a terminal and run
```
sudo update-grub
```
then watch as grub.cfg is configured to see if the Windows Loader is picked up. If it is, reboot and try to boot Windows from the grub menu.
Looking at your boot script output Windows may not boot because of this line
[code]sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       [COLOR="Red"]/boot/grub/core.img[/COLOR]
[COLOR="Black"]which should not be there. If you can get to the root of your Windows system you should delete that folder.[/COLOR]

---

### Post by dejavu007 on 2011-02-16
Thanks a lot Quackers... Deleting [COLOR=Red]/boot/grub/core.img[/COLOR] and running sudo update grub detected windows boot.. I think i had messed that up earlier..
Now when i boot, grub works fine showing windows option..:grin:
Once more thanks for the help...

---

