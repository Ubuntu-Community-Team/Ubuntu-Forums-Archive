---
title: "grub will not install into GPT bios partition"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by cncook001 on 2010-12-07
I think I have found a grub bug but want to confirm here before submitting a bug report.

Ubuntu 10.04, grub-install (GNU GRUB 1.98-1ubuntu9)

I am trying to install grub2 to a bios partition on GPT.  I have a RAID5 mdadm array on 3 disks.  I want to get grub onto them and try and boot from them.

I copied my root parition using tar to my lvm rootvol.

Used gdisk 0.6.9 to setup my GPT

remove grub from mbr
dd if=/dev/zero of=/dev/sdb bs=440 count=1
dd if=/dev/zero of=/dev/sdc bs=440 count=1
dd if=/dev/zero of=/dev/sdd bs=440 count=1

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 4724543 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

vg_01-swapvol: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

vg_01-extravol: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

vg_01-rootvol: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md/0: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 2,918,223,314 2,918,223,252  83 Linux
/dev/sda2       2,918,223,315 2,930,272,064    12,048,750   5 Extended
/dev/sda5       2,918,223,378 2,930,272,064    12,048,687  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048         4,095         2,048 Bios Boot Partition
/dev/sdb2           4,096 3,907,029,134 3,907,025,039 -

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1           2,048         4,095         2,048 Bios Boot Partition
/dev/sdc2           4,096 3,907,029,134 3,907,025,039 -

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdd1           2,048         4,095         2,048 Bios Boot Partition
/dev/sdd2           4,096 3,907,029,134 3,907,025,039 -

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/vg_01-extravol ffbb1dda-7fac-43ab-ac0e-6fb93a497918   xfs                                      
/dev/mapper/vg_01-rootvol 2f669269-f77c-4a01-b121-09253583552b   ext4                                     
/dev/md/0        ab8Tr1-J7Cw-C3RZ-e3Et-TrMd-VVe1-EFn1Y3 LVM2_member                               
/dev/md0         ab8Tr1-J7Cw-C3RZ-e3Et-TrMd-VVe1-EFn1Y3 LVM2_member                               
/dev/sda1        2242e7bb-97a5-46ba-bc56-782578a5323b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b3895b4a-570a-42f0-99d8-5ab3af7257bd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2        ff11f97c-92bc-a496-0f8c-68d2d4523718   linux_raid_member pc1:0                         
/dev/sdb: PTTYPE="gpt" 
/dev/sdc2        ff11f97c-92bc-a496-0f8c-68d2d4523718   linux_raid_member pc1:0                         
/dev/sdc: PTTYPE="gpt" 
/dev/sdd2        ff11f97c-92bc-a496-0f8c-68d2d4523718   linux_raid_member pc1:0                         
/dev/sdd: PTTYPE="gpt" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
vg_01-extravol
vg_01-rootvol
vg_01-swapvol

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/mapper/vg_01-extravol /extra                   xfs        (rw)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=myth)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_gpt
insmod lvm
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
search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
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
search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.31-20-generic
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2242e7bb-97a5-46ba-bc56-782578a5323b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda5    none            swap    sw              0       0
#UUID=4ce3cd72-134c-42b7-a780-88c706009920 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
#UUID=904dc02e-67f5-4efb-a0f9-798eb4921481  /extra        xfs     defaults        0       2
/dev/mapper/vg_01-extravol  /extra        xfs     defaults        0       2

=================== sda1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
  47.4GB: boot/grub/grub.cfg
  21.5GB: boot/initrd.img-2.6.31-20-generic
  92.4GB: boot/initrd.img-2.6.32-22-generic
   7.1GB: boot/initrd.img-2.6.32-23-generic
 998.7GB: boot/initrd.img-2.6.32-24-generic
1467.9GB: boot/initrd.img-2.6.32-25-generic
 553.2GB: boot/initrd.img-2.6.32-26-generic
  10.7GB: boot/vmlinuz-2.6.31-20-generic
  17.4GB: boot/vmlinuz-2.6.32-22-generic
 705.5GB: boot/vmlinuz-2.6.32-23-generic
   6.8GB: boot/vmlinuz-2.6.32-24-generic
  10.7GB: boot/vmlinuz-2.6.32-25-generic
  17.2GB: boot/vmlinuz-2.6.32-26-generic
 553.2GB: initrd.img
1467.9GB: initrd.img.old
  17.2GB: vmlinuz
  10.7GB: vmlinuz.old

====================== vg_01-rootvol/boot/grub/grub.cfg: ======================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod lvm
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
search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
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
search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== vg_01-rootvol/etc/fstab: ===========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2242e7bb-97a5-46ba-bc56-782578a5323b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda5    none            swap    sw              0       0
#UUID=4ce3cd72-134c-42b7-a780-88c706009920 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
#UUID=904dc02e-67f5-4efb-a0f9-798eb4921481  /extra        xfs     defaults        0       2
/dev/mapper/vg_01-extravol  /extra        xfs     defaults        0       2

=============== vg_01-rootvol: Location of files loaded by Grub: ===============


  24.2GB: boot/grub/core.img
  26.4GB: boot/grub/grub.cfg
  11.0GB: boot/initrd.img-2.6.31-20-generic
  10.9GB: boot/initrd.img-2.6.32-22-generic
  11.0GB: boot/initrd.img-2.6.32-23-generic
  11.0GB: boot/initrd.img-2.6.32-24-generic
  11.0GB: boot/initrd.img-2.6.32-25-generic
  10.9GB: boot/initrd.img-2.6.32-26-generic
  24.3GB: boot/vmlinuz-2.6.31-20-generic
  24.3GB: boot/vmlinuz-2.6.32-22-generic
  24.3GB: boot/vmlinuz-2.6.32-23-generic
  24.3GB: boot/vmlinuz-2.6.32-24-generic
  24.3GB: boot/vmlinuz-2.6.32-25-generic
  24.2GB: boot/vmlinuz-2.6.32-26-generic
  10.9GB: initrd.img
  11.0GB: initrd.img.old
  24.2GB: vmlinuz
  24.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown GPT Partiton Type
0f889da1fc053b4da006743f0f84911e
Unknown GPT Partiton Type
0f889da1fc053b4da006743f0f84911e
Unknown GPT Partiton Type
0f889da1fc053b4da006743f0f84911e
Unknown BootLoader  on sdb1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 31 00 20 08  |............1. .|
00000200

Unknown BootLoader  on sdc1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 31 00 20 08  |............1. .|
00000200

Unknown BootLoader  on sdd1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 31 00 20 08  |............1. .|
00000200

```grub-install /dev/sdb1
/usr/sbin/grub-setup: error: unable to identify a filesystem in hd1,1; safety check can't be performed.

Try just doing it to the root of the disk, since from what I have read grub2 should detect a bios partition and install the core.img file to it.  Does not work though.

```

 grub-setup -v /dev/sdb
grub-setup: info: the size of hd0 is 2930277168.
grub-setup: info: the size of hd0 is 2930277168.
grub-setup: info: the size of hd0 is 2930277168.
grub-setup: info: the size of hd0 is 2930277168.
grub-setup: info: the size of hd1 is 3907029168.
grub-setup: info: the size of hd1 is 3907029168.
grub-setup: info: the size of hd1 is 3907029168.
grub-setup: info: the size of hd1 is 3907029168.
grub-setup: info: the size of hd2 is 3907029168.
grub-setup: info: the size of hd2 is 3907029168.
grub-setup: info: the size of hd2 is 3907029168.
grub-setup: info: the size of hd2 is 3907029168.
grub-setup: info: the size of hd3 is 3907029168.
grub-setup: info: the size of hd3 is 3907029168.
grub-setup: info: the size of hd3 is 3907029168.
grub-setup: info: the size of hd3 is 3907029168.
grub-setup: info: the size of vg_01-rootvol is 62914560.
grub-setup: info: the size of vg_01-rootvol is 62914560.
grub-setup: info: the size of hd0 is 2930277168.
grub-setup: info: the size of hd0 is 2930277168.
grub-setup: info: the size of hd0 is 2930277168.
grub-setup: info: the size of hd0 is 2930277168.
grub-setup: info: the size of hd1 is 3907029168.
grub-setup: info: the size of hd1 is 3907029168.
grub-setup: info: the size of hd1 is 3907029168.
grub-setup: info: the size of hd1 is 3907029168.
grub-setup: info: the size of hd2 is 3907029168.
grub-setup: info: the size of hd2 is 3907029168.
grub-setup: info: the size of hd2 is 3907029168.
grub-setup: info: the size of hd2 is 3907029168.
grub-setup: info: the size of hd3 is 3907029168.
grub-setup: info: the size of hd3 is 3907029168.
grub-setup: info: the size of hd3 is 3907029168.
grub-setup: info: the size of hd3 is 3907029168.
grub-setup: info: the size of vg_01-rootvol is 62914560.
grub-setup: info: the size of vg_01-rootvol is 62914560.
grub-setup: info: changing current directory to /dev.
grub-setup: info: changing current directory to ati.
grub-setup: info: changing current directory to v4l.
grub-setup: info: changing current directory to by-path.
grub-setup: info: changing current directory to dvb.
grub-setup: info: changing current directory to adapter2.
grub-setup: info: changing current directory to adapter1.
grub-setup: info: changing current directory to adapter0.
grub-setup: info: changing current directory to snd.
grub-setup: info: changing current directory to by-path.
grub-setup: info: changing current directory to shm.
grub-setup: info: changing current directory to vg_01.
grub-setup: info: changing current directory to md.
grub-setup: info: changing current directory to disk.
grub-setup: info: changing current directory to by-label.
grub-setup: info: changing current directory to by-uuid.
grub-setup: info: changing current directory to by-path.
grub-setup: info: changing current directory to by-id.
grub-setup: info: /dev/sda1 starts from 63.
grub-setup: info: opening the device hd0.
grub-setup: info: the size of hd0 is 2930277168.
grub-setup: info: DOS partition 0 starts from 63.
grub-setup: info: getting the size of /boot/grub/boot.img.
grub-setup: info: reading /boot/grub/boot.img.
grub-setup: info: getting the size of /boot/grub/boot.img.
grub-setup: info: getting the size of /boot/grub/core.img.
grub-setup: info: reading /boot/grub/core.img.
grub-setup: info: getting the size of /boot/grub/core.img.
grub-setup: info: the size of hd0 is 2930277168.
grub-setup: info: the size of hd1 is 3907029168.
grub-setup: info: setting the root device to `hd0,1'.
grub-setup: info: dos partition is 0, bsd partition is -1.
grub-setup: info: the core image will be embedded at sector 0x800.

``````

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 2048 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 4724543 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

vg_01-swapvol: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

vg_01-extravol: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

vg_01-rootvol: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md/0: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 2,918,223,314 2,918,223,252  83 Linux
/dev/sda2       2,918,223,315 2,930,272,064    12,048,750   5 Extended
/dev/sda5       2,918,223,378 2,930,272,064    12,048,687  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048         4,095         2,048 Bios Boot Partition
/dev/sdb2           4,096 3,907,029,134 3,907,025,039 -

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1           2,048         4,095         2,048 Bios Boot Partition
/dev/sdc2           4,096 3,907,029,134 3,907,025,039 -

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdd1           2,048         4,095         2,048 Bios Boot Partition
/dev/sdd2           4,096 3,907,029,134 3,907,025,039 -

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/vg_01-extravol ffbb1dda-7fac-43ab-ac0e-6fb93a497918   xfs                                      
/dev/mapper/vg_01-rootvol 2f669269-f77c-4a01-b121-09253583552b   ext4                                     
/dev/md/0        ab8Tr1-J7Cw-C3RZ-e3Et-TrMd-VVe1-EFn1Y3 LVM2_member                               
/dev/md0         ab8Tr1-J7Cw-C3RZ-e3Et-TrMd-VVe1-EFn1Y3 LVM2_member                               
/dev/sda1        2242e7bb-97a5-46ba-bc56-782578a5323b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b3895b4a-570a-42f0-99d8-5ab3af7257bd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2        ff11f97c-92bc-a496-0f8c-68d2d4523718   linux_raid_member pc1:0                         
/dev/sdb: PTTYPE="gpt" 
/dev/sdc2        ff11f97c-92bc-a496-0f8c-68d2d4523718   linux_raid_member pc1:0                         
/dev/sdc: PTTYPE="gpt" 
/dev/sdd2        ff11f97c-92bc-a496-0f8c-68d2d4523718   linux_raid_member pc1:0                         
/dev/sdd: PTTYPE="gpt" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
vg_01-extravol
vg_01-rootvol
vg_01-swapvol

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/mapper/vg_01-extravol /extra                   xfs        (rw)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=myth)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_gpt
insmod lvm
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
search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
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
search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.31-20-generic
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2242e7bb-97a5-46ba-bc56-782578a5323b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda5    none            swap    sw              0       0
#UUID=4ce3cd72-134c-42b7-a780-88c706009920 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
#UUID=904dc02e-67f5-4efb-a0f9-798eb4921481  /extra        xfs     defaults        0       2
/dev/mapper/vg_01-extravol  /extra        xfs     defaults        0       2

=================== sda1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
  47.4GB: boot/grub/grub.cfg
  21.5GB: boot/initrd.img-2.6.31-20-generic
  92.4GB: boot/initrd.img-2.6.32-22-generic
   7.1GB: boot/initrd.img-2.6.32-23-generic
 998.7GB: boot/initrd.img-2.6.32-24-generic
1467.9GB: boot/initrd.img-2.6.32-25-generic
 553.2GB: boot/initrd.img-2.6.32-26-generic
  10.7GB: boot/vmlinuz-2.6.31-20-generic
  17.4GB: boot/vmlinuz-2.6.32-22-generic
 705.5GB: boot/vmlinuz-2.6.32-23-generic
   6.8GB: boot/vmlinuz-2.6.32-24-generic
  10.7GB: boot/vmlinuz-2.6.32-25-generic
  17.2GB: boot/vmlinuz-2.6.32-26-generic
 553.2GB: initrd.img
1467.9GB: initrd.img.old
  17.2GB: vmlinuz
  10.7GB: vmlinuz.old

====================== vg_01-rootvol/boot/grub/grub.cfg: ======================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod lvm
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
search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
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
search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2242e7bb-97a5-46ba-bc56-782578a5323b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/mapper/vg_01-rootvol)" {
    insmod ext2
    set root='(vg_01-rootvol)'
    search --no-floppy --fs-uuid --set 2f669269-f77c-4a01-b121-09253583552b
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2242e7bb-97a5-46ba-bc56-782578a5323b ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== vg_01-rootvol/etc/fstab: ===========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2242e7bb-97a5-46ba-bc56-782578a5323b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda5    none            swap    sw              0       0
#UUID=4ce3cd72-134c-42b7-a780-88c706009920 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
#UUID=904dc02e-67f5-4efb-a0f9-798eb4921481  /extra        xfs     defaults        0       2
/dev/mapper/vg_01-extravol  /extra        xfs     defaults        0       2

=============== vg_01-rootvol: Location of files loaded by Grub: ===============


  24.2GB: boot/grub/core.img
  26.4GB: boot/grub/grub.cfg
  11.0GB: boot/initrd.img-2.6.31-20-generic
  10.9GB: boot/initrd.img-2.6.32-22-generic
  11.0GB: boot/initrd.img-2.6.32-23-generic
  11.0GB: boot/initrd.img-2.6.32-24-generic
  11.0GB: boot/initrd.img-2.6.32-25-generic
  10.9GB: boot/initrd.img-2.6.32-26-generic
  24.3GB: boot/vmlinuz-2.6.31-20-generic
  24.3GB: boot/vmlinuz-2.6.32-22-generic
  24.3GB: boot/vmlinuz-2.6.32-23-generic
  24.3GB: boot/vmlinuz-2.6.32-24-generic
  24.3GB: boot/vmlinuz-2.6.32-25-generic
  24.2GB: boot/vmlinuz-2.6.32-26-generic
  10.9GB: initrd.img
  11.0GB: initrd.img.old
  24.2GB: vmlinuz
  24.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown GPT Partiton Type
0f889da1fc053b4da006743f0f84911e
Unknown GPT Partiton Type
0f889da1fc053b4da006743f0f84911e
Unknown GPT Partiton Type
0f889da1fc053b4da006743f0f84911e
Unknown BootLoader  on sdb1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 31 00 20 08  |............1. .|
00000200

Unknown BootLoader  on sdc1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 31 00 20 08  |............1. .|
00000200

Unknown BootLoader  on sdd1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 31 00 20 08  |............1. .|
00000200


```

---

### Post by srs5694 on 2010-12-07
I think you misunderstand how GRUB installs to the BIOS Boot Partition. You do *not* specify the device filename for the BIOS Boot Partition when using grub-install; you specify the device filename for the whole disk (/dev/sda, /dev/sdb, or whatever). The grub-install program then installs part of itself in the MBR, locates the BIOS Boot Partition, and installs another part of itself in the BIOS Boot Partition.

That said, there is another current thread here from somebody who's having problems doing "grub-install /dev/sda" and it's not working. The focus in that thread has been on hardware problems, but it's conceivable there's a bug in recent versions of GRUB that's causing it to not correctly locate and install to the BIOS Boot Partition.

---

### Post by cncook001 on 2010-12-08
ok.  I did not realise grub installed itself in two places.  does my grub-setup -v /dev/sdb output point to a faulty setup by me?  What is the other thread called?  I can join in on that one.

Thanks

Craig

---

### Post by cncook001 on 2010-12-09
Did some more testing.  Using the 10.10 Alternate Install CD in rescue mode I am able to update the MBR of /dev/sdb if I select a root disk of /dev/sda1 (still only updates the MBR, not my bios partition).  If I choose root disk of /dev/vg_01/rootvol it gives a fatal error and refuses to install grub.

Is my issue something to do with using LVM with grub?

---

