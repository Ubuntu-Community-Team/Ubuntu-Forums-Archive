---
title: "Ubuntu 10.04 Installed ,  Windows 7 Not Booting, Imp Data left on Windows 7 - Help"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by Paidi on 2010-10-19
Hello All,

Recently a friend advised me try ubuntu. He handed me a CD of version 10.04. I installed it on my computer and everything is fine, right now i am browsing from my newly installed ubuntu, the problem is i couldn't log in to my Windows 7 operating system. I am a full time marketer. I have some important data left on one of my windows drive :( (#1 mistake i did, otherwise i would have least worried about OS, #2 mistake i did, didn't read any internet resources before installing from live CD).

Installation - What i did ?

I emptied one of my drive in Windows 7 and deleted the partition, So i got 70GB free space. (nearly)

Later installed the live CD and rebooted the system. I went on through the screen promts, Setting time, Keyboard type, next i selected "advanced partitions configure" (something like this) and alloted the 70GB (nearly) free space (Created as a new partition) to install the OS.

Next everything went good and i logged into my Ubuntu 10.04 and configured the basic settings. Later, when i tried to log on the windows 7 OS, It displayed a message as

"Windows couldn't boot,  A recent software/hardware changes  has caused this error , try repairing with CD.. etc etc "

The error code it displayed is 0xc0000225

Also i noticed some changes in boot Screen

My boot Screen was like
> GNU - Grub Version 1.98 - 1ubuntu7
Ubuntu with linux 2.6.32 - 25 - generic
Ubuntu with linux 2.6.32 - 25 - generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda2 )


I realized that something went wrong and started browsing the forums/resources (done it for the past 24 hrs, tired ... should have cared about it earlier ..my bad )

I came across this thread ([http://ubuntuforums.org/showthread.php?t=1531519](http://ubuntuforums.org/showthread.php?t=1531519)). So I am posting the results

results for -  sudo update-grub
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2

```

results for sudo fdisk -l
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xecd0e75a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          13      102400   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              14        8924    71576577    5  Extended
/dev/sda4            8924       38914   240889176   42  SFS
/dev/sda5              14        8924    71576576   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204884992 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd1b68b41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25497   204800000    7  HPFS/NTFS
/dev/sdb2           25497      121601   771958784    7  HPFS/NTFS

```

Bootinfo script results
```
                Boot Info Script 0.55    dated February 15th, 2010                   

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:      
    Boot sector type:  Windows Vista/7
    Boot sector info: 
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has
                       143359999 sectors, but according to the info from
                       fdisk, it has 481778351 sectors.
    Operating System: 
    Boot files/dirs:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       206,847       204,800  42 SFS
/dev/sda3             208,894   143,362,047   143,153,154   5 Extended
/dev/sda5             208,896   143,362,047   143,153,152  83 Linux
/dev/sda4         143,362,048   625,140,399   481,778,352  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204884992 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   409,602,047   409,600,000   7 HPFS/NTFS
/dev/sdb2         409,602,048 1,953,519,615 1,543,917,568   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                        

/dev/sda2        0A620FD1620FC105                       ntfs                                    
/dev/sda3: PTTYPE="dos"
/dev/sda4        703A2C0F3A2BD140                       ntfs       Ubuntu                       
/dev/sda5        fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0   ext4                                    
/dev/sda: PTTYPE="dos"
/dev/sdb1        5E2045112044F217                       ntfs       VDrive                       
/dev/sdb2        BEF65D25F65CDEE9                       ntfs       Movies                       
/dev/sdb: PTTYPE="dos"

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/VDrive            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/Movies            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0
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
search --no-floppy --fs-uuid --set fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0a620fd1620fc105
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
UUID=fced8eb3-2bd9-4ee5-a752-0fe5e538b7b0 /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


  51.7GB: boot/grub/core.img
   9.2GB: boot/grub/grub.cfg
  51.9GB: boot/initrd.img-2.6.32-21-generic
  52.0GB: boot/initrd.img-2.6.32-25-generic
  51.8GB: boot/vmlinuz-2.6.32-21-generic
  52.0GB: boot/vmlinuz-2.6.32-25-generic
  52.0GB: initrd.img
  51.9GB: initrd.img.old
  52.0GB: vmlinuz
  51.8GB: vmlinuz.old
```

Screen shot

[IMG]http://img214.imageshack.us/img214/3638/screenshotjan.png[/IMG]
*(i used gimp :) )*

So According to my guess, 
1 - Where the Ubuntu 10.04 is installed 
2 - Windows OS and Data 
3 - My External 1 TB data disk (partitioned as 800GB and 200GB )



So, What should i do now ? Please help me to get my data and have a smooth move to UBUNTU OS.

---

### Post by oldfred on 2010-10-20
It looks like you have a windows file system that has caused lots of issues even for windows users. Windows claims converting back to basic will destroy all data. Using non-windows tools may have caused issues.

Win dynamic disk
[http://support.microsoft.com/kb/314343](http://support.microsoft.com/kb/314343)
Dynamic disk & explanation of 63 vs 2048
[http://en.wikipedia.org/wiki/Logical_Disk_Manager](http://en.wikipedia.org/wiki/Logical_Disk_Manager)

fdisk shows type 42 SFS
42 Windows 2000 dynamic extended partition marker If a partition table entry of type 0x42 is present in the legacy partition table, then W2K ignores the legacy partition table and uses a proprietary partition table and a proprietary partitioning scheme (LDM or DDM)
Windows claim converting back to standard will destroy all data.
Says they will preserve data:
[http://www.partitionwizard.com/](http://www.partitionwizard.com/)

Your sda2 has the boot flag adn boot files that may be just in a boot partition, but you are missing /Windows/System32/winload.exe which is in the working directory. Or I do not see your windows partition. Also the /grldr is a grub4dos folder that can cause issues. I would delete it unless you are using it for something.

---

### Post by Paidi on 2010-10-20
thanks for the fast reply. 
But what can i do now ?
I can't boot the windows OS, I stored some data in one of the logical drive in windows ..

Should i take my laptop to a hard disk specialist ?
Can i get the data ?

your answer is bit geekish :) 

Mine is DELL STUDIO 15

once again ..thanks for the reply ...

---

### Post by Paidi on 2010-10-20
I just tried to boot from Windows 7 DVD. Its not working. too bad 
but boot from ubuntu live CD is working perfectly.

---

### Post by oldfred on 2010-10-20
Did you try using the partition wizard?

But it looks like you may have overwritten the main windows working partition,  so it will start to boot from the boot partition but then cannot find the main install.

---

