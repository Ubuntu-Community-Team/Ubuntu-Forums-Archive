---
title: "Installation migration attempt gone wrong"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by TimInCali on 2011-02-27
I installed Ubuntu 10.04 (32 bit version) a few months ago on a system  with two IDE drives (cable select configuration).  The primary drive  (/dev/sda) is 40GB and the secondary drive (/dev/sdb) is 80GB.  I  created all of my partitions on the primary drive and left the secondary  drive unconfigured.  After a month or so I noticed that two of my  partitions had quickly reached 50% capacity, as I had just taken a guess  at an appropriate partition size when I first installed Ubuntu.

Since  I had a larger unused drive already in place, I decided to migrate my  installation from the smaller drive to the larger drive, but sizing the  partitions in question more appropriately (i.e., much larger).  I  assumed :lolflag:  that I could install Ubuntu on the bigger drive with larger partitions,  byte-for-byte copy all my existing partitions from the old disk to the  new one, edit /etc/fstab, reboot, and GBTW.  Naturally that didn't work  as I expected.

Here's what I did:

[LIST=1]
[*]Carefully logged my existing partitions on /dev/sda and their mount points
[*]Used  a live CD to install the same version of Ubuntu on the larger drive  (/dev/sdb), using its partition tool to generously size my partitions.  I  carefully logged the new partitions and their mount points.
[*]For  each partition on /dev/sda (except for /boot and swap), I used dd to  create a gzip'd image and stored all of those images on a backup drive.
[*]I  then used dd to complete the task of migrating all of these partitions  (again, all but /boot and swap) to their respective partitions on  /dev/sdb.
[*]Ran blkid to see all of my partitions.  I noticed that  some of the UUIDs existed on both drives.  I thought "hmmm...that's  weird" and moved on.
[*]Mounted my new root partition (/dev/sdb6) on a contrived mount point.
[*]Edited  /etc/fstab (after backing it up) and carefully replaced all the old  UUIDs with their respective counterparts on my new drive.  Also replaced  the device reference for /boot with its respective counterpart.
[*]Crossed fingers.  Rebooted.   Got some warnings about missing UUIDs.
[*]After  the system completely booted, I used the graphical disk utility and saw  that the system mounted some partitions from /dev/sda and others from  /dev/sdb.  Not good.
[/LIST]
Since then I've done a lot of lurking and  research on these forums.  I followed steps people have taken to fix  somewhat-related issues and almost made it to where I need to be.  Here  are the steps I took since lurking here:


[LIST=1]
[*]gave all sdb[\d]+ devices a new UUID(using tune2fs [target] -U random) and verified uniqueness across both disks
[*]mounted sdb6? (root partition) and edited /etc/fstab to reflect newly generated UUIDs
[*]re-generated grub.cfg (following instructions at [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) for method #3)
[*]booted; noticed references to unix kernels on sda in bootup screen. grrrrrr....
[*]unix graphical disk utility shows all mounted filesystems are /dev/sdb[\d]+.  Yay!
[*]system monitor shows partition sizes are old partition sizes (from /dev/sda). grrrrr....
[*]ran os-prober.  it only lists os on /dev/sda6.  grrr....
[*]edited /etc/initramfs-tools/conf.d/resume to point to UUID of swap partition on /dev/sdb
[*]ran update-initramfs -u
[/LIST]
It seems my installation still has an identity crisis.  What steps should I take from here to force my Ubuntu installation to only use my partitions on /dev/sdb?

p.s.: was there an easier way for me to migrate my installation to a new drive?

---

### Post by TimInCali on 2011-02-28
Oops, forgot my boot info script results.  Here they are:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /etc/fstab

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     1,953,791     1,951,744  83 Linux
/dev/sda2           1,955,838    75,587,583    73,631,746   5 Extended
/dev/sda5           1,955,840     5,273,599     3,317,760  82 Linux swap / Solaris
/dev/sda6           5,275,648    13,086,719     7,811,072  83 Linux
/dev/sda7          13,088,768    24,805,375    11,716,608  83 Linux
/dev/sda8          24,807,424    32,618,495     7,811,072  83 Linux
/dev/sda9          32,620,544    40,431,615     7,811,072  83 Linux
/dev/sda10         40,433,664    52,150,271    11,716,608  83 Linux
/dev/sda11         52,152,320    75,587,583    23,435,264  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       976,895       974,848  83 Linux
/dev/sdb2             978,942   102,539,263   101,560,322   5 Extended
/dev/sdb5             978,944     8,790,015     7,811,072  83 Linux
/dev/sdb6           8,792,064    32,227,327    23,435,264  83 Linux
/dev/sdb7          32,229,376    40,040,447     7,811,072  83 Linux
/dev/sdb8          40,042,496    63,477,759    23,435,264  83 Linux
/dev/sdb9          63,479,808    75,196,415    11,716,608  83 Linux
/dev/sdb10         75,198,464    98,633,727    23,435,264  83 Linux
/dev/sdb11         98,635,776   102,539,263     3,903,488  82 Linux swap / Solaris
/dev/sdb3         102,542,895   150,384,464    47,841,570  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1003 MB, 1003487232 bytes
16 heads, 32 sectors/track, 3828 cylinders, total 1959936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064     1,959,935     1,951,872   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       92abfe6c-8bb4-4f61-9bdf-82c2c07d82cb   ext3                                     
/dev/sda11       8ee5f948-380e-43df-87d4-4370c1d07fe3   ext3                                     
/dev/sda1        21d43c8c-8ef3-4b45-a4ae-b634ed50e54b   ext2                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7a90260c-a3fb-481b-b8b9-6649f5a0e81b   swap                                     
/dev/sda6        66f0d4dc-8552-41bd-97de-66cf962dee10   ext3                                     
/dev/sda7        4331a2f3-7ad6-4f0c-a613-e56c5a3938e6   ext3                                     
/dev/sda8        6fe64cdc-4bfc-4b53-b5c5-fd51a5caebc4   ext2                                     
/dev/sda9        5b2c58db-c9ac-4069-8d56-2f1f7c52b382   ext2                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb10       0b256425-6dc7-4600-8ba9-fa14f8baedad   ext3                                     
/dev/sdb11       f32a7983-5f0a-4e62-8f28-0b90a65bdefd   swap                                     
/dev/sdb1        2e936b81-6517-4aa3-a614-482601d6f95c   ext2                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        f23235de-acbb-40d6-9688-18dac93c2a29   ext4       imagefucker                   
/dev/sdb5        c94d847a-0c65-4150-ab43-a2c74c4cf3dd   ext3                                     
/dev/sdb6        83a9485a-644e-428e-b6de-993ae36ee2a2   ext3                                     
/dev/sdb7        2ec44f50-89d5-49fb-9c89-5823dd614781   ext2                                     
/dev/sdb8        17420479-4ae1-4697-965f-2959985be82d   ext2                                     
/dev/sdb9        3eca8cd2-24a9-404d-9601-4f340333ebc3   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D83E-037B                              vfat       MASHERY                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 4331a2f3-7ad6-4f0c-a613-e56c5a3938e6
if loadfont /share/grub/unicode.pf2 ; then
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
search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux    /vmlinuz-2.6.32-27-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro   quiet splash
    initrd    /initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /vmlinuz-2.6.32-27-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux    /vmlinuz-2.6.32-26-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro   quiet splash
    initrd    /initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /vmlinuz-2.6.32-26-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux    /vmlinuz-2.6.32-24-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro   quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 918c4d70-782a-4a37-97dd-43bbc3459774
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=918c4d70-782a-4a37-97dd-43bbc3459774 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 918c4d70-782a-4a37-97dd-43bbc3459774
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=918c4d70-782a-4a37-97dd-43bbc3459774 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .7GB: grub/core.img
    .7GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-24-generic
    .0GB: initrd.img-2.6.32-26-generic
    .0GB: initrd.img-2.6.32-27-generic
    .0GB: vmlinuz-2.6.32-24-generic
    .0GB: vmlinuz-2.6.32-26-generic
    .0GB: vmlinuz-2.6.32-27-generic

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
UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 /               ext3    errors=remount-ro 0       1
/dev/sda1       /boot           ext2    defaults        0       2
# /home was on /dev/sda11 during installation
UUID=8ee5f948-380e-43df-87d4-4370c1d07fe3 /home           ext3    defaults        0       2
# /tmp was on /dev/sda8 during installation
UUID=6fe64cdc-4bfc-4b53-b5c5-fd51a5caebc4 /tmp            ext2    defaults        0       2
# /usr was on /dev/sda7 during installation
UUID=4331a2f3-7ad6-4f0c-a613-e56c5a3938e6 /usr            ext3    defaults        0       2
# /usr/local was on /dev/sda10 during installation
UUID=92abfe6c-8bb4-4f61-9bdf-82c2c07d82cb /usr/local      ext3    defaults        0       2
# /var was on /dev/sda9 during installation
UUID=5b2c58db-c9ac-4069-8d56-2f1f7c52b382 /var            ext2    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=7a90260c-a3fb-481b-b8b9-6649f5a0e81b none            swap    sw              0       0

============================= sdb1/grub/grub.cfg: =============================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 83a9485a-644e-428e-b6de-993ae36ee2a2
if loadfont /share/grub/unicode.pf2 ; then
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
search --no-floppy --fs-uuid --set 2e936b81-6517-4aa3-a614-482601d6f95c
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2e936b81-6517-4aa3-a614-482601d6f95c
    linux    /vmlinuz-2.6.32-28-generic root=UUID=c94d847a-0c65-4150-ab43-a2c74c4cf3dd ro   quiet splash
    initrd    /initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2e936b81-6517-4aa3-a614-482601d6f95c
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /vmlinuz-2.6.32-28-generic root=UUID=c94d847a-0c65-4150-ab43-a2c74c4cf3dd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2e936b81-6517-4aa3-a614-482601d6f95c
    linux    /vmlinuz-2.6.32-24-generic root=UUID=c94d847a-0c65-4150-ab43-a2c74c4cf3dd ro   quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2e936b81-6517-4aa3-a614-482601d6f95c
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=c94d847a-0c65-4150-ab43-a2c74c4cf3dd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2e936b81-6517-4aa3-a614-482601d6f95c
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2e936b81-6517-4aa3-a614-482601d6f95c
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux /vmlinuz-2.6.32-27-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro quiet splash
    initrd /initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux /vmlinuz-2.6.32-27-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro single
    initrd /initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux /vmlinuz-2.6.32-26-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro quiet splash
    initrd /initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux /vmlinuz-2.6.32-26-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro single
    initrd /initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux /vmlinuz-2.6.32-24-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro quiet splash
    initrd /initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 21d43c8c-8ef3-4b45-a4ae-b634ed50e54b
    linux /vmlinuz-2.6.32-24-generic root=UUID=66f0d4dc-8552-41bd-97de-66cf962dee10 ro single
    initrd /initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb1: Location of files loaded by Grub: ===================


    .3GB: grub/core.img
    .3GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-24-generic
    .0GB: initrd.img-2.6.32-28-generic
    .0GB: vmlinuz-2.6.32-24-generic
    .0GB: vmlinuz-2.6.32-28-generic

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
UUID=c94d847a-0c65-4150-ab43-a2c74c4cf3dd /               ext3    errors=remount-ro 0       1

/dev/sdb1       /boot           ext2    defaults        0       2

# /home was on /dev/sdb10 during installation
UUID=0b256425-6dc7-4600-8ba9-fa14f8baedad /home           ext3    defaults        0       2

# /tmp was on /dev/sdb7 during installation
UUID=2ec44f50-89d5-49fb-9c89-5823dd614781 /tmp            ext2    defaults        0       2

# /usr was on /dev/sdb6 during installation
UUID=83a9485a-644e-428e-b6de-993ae36ee2a2 /usr            ext3    defaults        0       2

# /usr/local was on /dev/sdb9 during installation
UUID=3eca8cd2-24a9-404d-9601-4f340333ebc3 /usr/local      ext3    defaults        0       2

# /var was on /dev/sdb8 during installation
UUID=17420479-4ae1-4697-965f-2959985be82d /var            ext2    defaults        0       2

# swap was on /dev/sdb11 during installation
UUID=f32a7983-5f0a-4e62-8f28-0b90a65bdefd none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  9a b8 38 3e 6e 19 b1 82  9d 4c 84 7e 82 ba 54 67  |..8>n....L.~..Tg|
00000010  8f 36 5d 85 87 15 88 6d  f8 ea f8 53 1b 90 60 bc  |.6]....m...S..`.|
00000020  16 1c b8 9b ed a2 2f e5  2b 06 f1 8d 84 88 cb ae  |....../.+.......|
00000030  75 3e be 1a 89 d4 8b a5  c8 29 40 c8 12 12 64 8c  |u>.......)@...d.|
00000040  82 38 44 ee 04 e8 6c a4  84 67 ea 9e 0a 38 8b a9  |.8D...l..g...8..|
00000050  c2 48 61 c5 c5 95 8a 56  13 f0 b8 7a dc b5 35 74  |.Ha....V...z..5t|
00000060  53 59 0c 45 d2 17 93 8c  c3 6e 5f 95 ae 5f 77 13  |SY.E.....n_.._w.|
00000070  27 56 7e 05 4b 3e aa ab  a4 a0 88 80 95 ad ee d4  |'V~.K>..........|
00000080  53 ea c6 29 e0 f1 48 08  44 49 5e 7a 4a 9e 84 52  |S..)..H.DI^zJ..R|
00000090  44 cd a0 f0 23 c5 ab a4  90 a2 7a 54 ce 4b c8 4b  |D...#.....zT.K.K|
000000a0  d4 4f 22 91 92 c4 ce 48  3f 90 79 40 d2 a3 7d 39  |.O"....H?.y@..}9|
000000b0  61 4e 84 e2 9d 4c d8 54  f1 3b 1a 14 a2 49 18 2a  |aN...L.T.;...I.*|
000000c0  43 60 97 fc 71 2f db ca  63 53 f2 f5 13 70 c5 25  |C`..q/..cS...p.%|
000000d0  0d ca a4 61 01 27 44 8c  1c e3 c1 ab 2a 55 3b 84  |...a.'D.....*U;.|
000000e0  64 55 bb b4 bb a8 af e3  61 c9 eb df 1e 12 0d 89  |dU......a.......|
000000f0  17 e8 1e 00 ca ab 45 8f  4e 22 56 1d bd e1 25 40  |......E.N"V...%@|
00000100  22 10 78 d5 08 ea 61 2a  52 f2 89 12 c1 4a 37 4b  |".x...a*R....J7K|
00000110  db 10 a2 83 93 2a af 61  55 d3 f5 52 d7 c8 f6 6c  |.....*.aU..R...l|
00000120  e7 f3 5f a3 53 a1 a8 76  ff db 00 80 35 30 63 9f  |.._.S..v....50c.|
00000130  14 46 6e 6e 16 42 e5 64  43 65 21 ec 22 c6 f3 24  |.Fnn.B.dCe!."..$|
00000140  bf 21 93 2d d4 f5 fa f9  78 2c ee ee 75 4f 3b db  |.!.-....x,..uO;.|
00000150  44 02 f9 fd 0d bf 1a 86  a0 33 99 b4 9a 49 d3 05  |D........3...I..|
00000160  32 63 6b d9 20 dd f5 bb  06 1e 80 6f bf ac 62 1b  |2ck. ......o..b.|
00000170  5f 77 9e 23 97 4f 83 ed  39 1c dc 84 c0 48 6a a2  |_w.#.O..9....Hj.|
00000180  0e 80 e6 9a 80 dc 69 57  4b 87 1f 42 3d c4 aa a4  |......iWK..B=...|
00000190  54 7d da ad af f1 50 34  d9 2a 90 f5 d4 c7 16 fa  |T}....P4.*......|
000001a0  02 5f 7a 27 8f 3f da 04  43 16 28 c6 f9 a7 93 e9  |._z'.?..C.(.....|
000001b0  2b ce ac 7a b0 a9 4f a3  4c 4c 6e 83 ae fb 00 ee  |+..z..O.LLn.....|
000001c0  33 3c 83 27 84 23 02 00  00 00 00 30 77 00 00 27  |3<.'.#.....0w..'|
000001d0  85 23 05 fe ff ff 02 30  77 00 00 a0 65 01 00 00  |.#.....0w...e...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by TimInCali on 2011-03-02
I ended up just reinstalling Ubuntu on fresh partitions and using rsync to restore my home folder.

In the future, I would migrate by (1) doing a fresh install on a new disk and (2) using rsync -azvc to restore the home folder of each user.  Definitely less trouble than going down all the bad roads I did in this adventure!

---

### Post by grahammechanical on 2011-03-02
It is a bit late I know but with that wonderful thing called hindsight you could have

1) backed up all your data.

2) Did a fresh install setting the larger 80GB disc the mount point of /home and the smaller 40GB disc the mount point of /

3) Put all your backed up data into you new home folder on your new /home partition. You would not have noticed that you were using two drives.

I think that it is good to keep the Home folder on a separate partition or drive.

Regards.

---

