---
title: "How to restore grub in ubuntu 9.10 with wubi"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by rkrinfo on 2010-02-21
Hi

i hav not much experience in linux

i hav dual boot system with Windows Xp and Ubuntu 9.1 **using Wubi **

i have 5 partitions at one 250gb harddisk
windows is working on C:
i have ubuntu on the 5th on** G: installed under windows**

While i am experimenting with startupmanager i selected to show spalshscreen and restarted ubuntu

then i found a problem with grub
and i have only a terminal to enter grub commands named **sh:grub:>**

how can i restore the grub and boot into ubuntu

Get me out of this grub command screen   :confused:

thanx in advance

---

### Post by meierfra. on 2010-02-21
Try this

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If this did not cure your problem, follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt


You can also try to boot  Wubi from the grub prompt:


```
linux /vmlinuz root=[COLOR="Red"]/dev/sda6[/COLOR] loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot

```

/dev/sda6 has be adjust. It needs to be the device name of your Wubi partition.  Since you  only have  one hard disk, "/dev/sda" is correct and you only have to figure out the correct number.

---

### Post by rkrinfo on 2010-02-22
[B]Thanks for your reply

i copied the file wubildr in to my G: drive
but i don't know what to do with it
and while restarting and boot in to ubuntu, the problem remained

and i tried the code as you said, but it failed too[/B]

```
linux /vmlinuz root=[COLOR=Red]/dev/sda6[/COLOR] loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot

```
**here is the contents of my RESULTS.TXT**

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

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
    Boot files/dirs:   /boot.ini /wubildr.mbr /wubildr

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63. According to the info in the boot 
                       sector, sda8 has 159717312 sectors, but according to 
                       the info from fdisk, it has 159718166 sectors.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda8/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006300c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,977,844    41,977,782   7 HPFS/NTFS
/dev/sda2          41,977,845   488,392,064   446,414,220   f W95 Ext d (LBA)
/dev/sda5          41,977,908    84,983,849    43,005,942   7 HPFS/NTFS
/dev/sda6          84,983,913   226,275,524   141,291,612   7 HPFS/NTFS
/dev/sda7         226,275,588   328,673,834   102,398,247   7 HPFS/NTFS
/dev/sda8         328,673,898   488,392,064   159,718,167   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       9ccf85da-da82-45e4-b387-08a38cb10e58   ext4                                     
/dev/sda1        9288DEFD88DEDF33                       ntfs                                     
/dev/sda5        0244F9B544F9AB93                       ntfs       Program Files                 
/dev/sda6        5AC4C112C4C0F175                       ntfs       Working Data                  
/dev/sda7        01CA21C3E57E7610                       ntfs       Backup                        
/dev/sda8        3E64E27064E229FB                       ntfs       Entertainment                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/9288DEFD88DEDF33  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/Program Files     fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6        /media/Working Data      fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7        /media/Backup            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=C:\wubildr.mbr
[operating systems]
C:\wubildr.mbr = "Ubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Open Solaris" /noexecute=optin /fastdetect

================================ sda5/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Open Solaris" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

======================== sda8/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3e64e27064e229fb
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro  vga=792 splash  quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3e64e27064e229fb
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single  vga=792 splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3e64e27064e229fb
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro  vga=792 splash  quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3e64e27064e229fb
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single  vga=792 splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 9288defd88dedf33
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda8/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda8/Wubi: Location of files loaded by Grub: =================


   4.9GB: boot/grub/grub.cfg
   3.9GB: boot/initrd.img-2.6.31-14-generic
   3.9GB: boot/initrd.img-2.6.31-19-generic
   2.4GB: boot/vmlinuz-2.6.31-14-generic
   2.0GB: boot/vmlinuz-2.6.31-19-generic
   3.9GB: initrd.img
   3.9GB: initrd.img.old
   2.0GB: vmlinuz
   2.4GB: vmlinuz.old

```

**and i tried as i saw in the file, neglecting the splash parameters **

```
    insmod ntfs
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3e64e27064e229fb
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro
    initrd /boot/initrd.img-2.6.31-19-generic
    boot

```

[B]and it worked and i managed to get my ubuntu again

i dont know to correct the grub
so i unchecked the boot splash option and restarted

then the grub command screen came again

Please help me to fix it permanently [/B]

---

### Post by rkrinfo on 2010-02-22
Hi

its my previous thread
[http://ubuntuforums.org/showthread.php?t=1413008](http://ubuntuforums.org/showthread.php?t=1413008)

i hav dual boot system with Windows Xp and Ubuntu 9.1 **using Wubi **

While i am experimenting with startupmanager i selected to show spalshscreen and restarted ubuntu

then i found a problem with grub
and i have only a terminal to enter grub commands named **sh:grub>**

i entered the code and i managed to get in to ubuntu

```

    insmod ntfs
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3e64e27064e229fb
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro
    initrd /boot/initrd.img-2.6.31-19-generic
    boot

```[B]i dont know to correct the grub

While restarting, the grub command screen came again

Please help me to fix it permanently [/B]

---

### Post by ajgreeny on 2010-02-22
Sorry about that advice;  I didn't notice that it was a wubi install.

Note to self:   Must read OP more carefully!

---

### Post by meierfra. on 2010-02-22
> 4.9GB: boot/grub/grub.cfg

Your grub.cfg is outside the 4GB limit your current wubildr can see.  
Looking at you boot.ini:

> C:\wubildr.mbr = "Ubuntu"


it  seems that the Window boot  loader actually uses the wubildr on the C: drive. So copy  the new wubildr to "C:"

---

### Post by meierfra. on 2010-02-22
I did respond in your other thread.
Please don't start two threads on the same subject.  
Also do not follow ajgreeny's  advice.  Those  instruction are for Ubuntu, but will not work for Wubi.

---

### Post by overdrank on 2010-02-22
Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by rkrinfo on 2010-02-23
[COLOR=Blue][B]I am really sorry for creating multiple threads for same issue
I am a new kid around here
and those are the only threads created ever
I am sorry again, I promise i won't repeat that[/B][/COLOR]

thanks to **meierfra **for helping me
as you said i copied the downloaded **wubildr **to my c: drive and it didnt work

and i tried
**sudo dpkg-reconfigure grub-pc**
 here is my new RESULTS1.TXT

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr 
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
    Boot files/dirs:   /boot.ini /wubildr.mbr /wubildr

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63. According to the info in the boot 
                       sector, sda8 has 159717312 sectors, but according to 
                       the info from fdisk, it has 159718166 sectors.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda8/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

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
Disk identifier: 0x0006300c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,977,844    41,977,782   7 HPFS/NTFS
/dev/sda2          41,977,845   488,392,064   446,414,220   f W95 Ext d (LBA)
/dev/sda5          41,977,908    84,983,849    43,005,942   7 HPFS/NTFS
/dev/sda6          84,983,913   226,275,524   141,291,612   7 HPFS/NTFS
/dev/sda7         226,275,588   328,673,834   102,398,247   7 HPFS/NTFS
/dev/sda8         328,673,898   488,392,064   159,718,167   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       9ccf85da-da82-45e4-b387-08a38cb10e58   ext4                                     
/dev/sda1        9288DEFD88DEDF33                       ntfs                                     
/dev/sda5        0244F9B544F9AB93                       ntfs       Program Files                 
/dev/sda6        5AC4C112C4C0F175                       ntfs       Working Data                  
/dev/sda7        01CA21C3E57E7610                       ntfs       Backup                        
/dev/sda8        3E64E27064E229FB                       ntfs       Entertainment                 
/dev/sdb1        8804C9AE04C99F94                       ntfs       FreeAgent Drive               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/9288DEFD88DEDF33  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=C:\wubildr.mbr
[operating systems]
C:\wubildr.mbr = "Ubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Open Solaris" /noexecute=optin /fastdetect

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

================================ sda5/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Open Solaris" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

======================== sda8/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3e64e27064e229fb
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro   quiet
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3e64e27064e229fb
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3e64e27064e229fb
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro   quiet
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 3e64e27064e229fb
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 9288defd88dedf33
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda8/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda8/Wubi: Location of files loaded by Grub: =================


   6.2GB: boot/grub/grub.cfg
   3.9GB: boot/initrd.img-2.6.31-14-generic
   3.9GB: boot/initrd.img-2.6.31-19-generic
   2.4GB: boot/vmlinuz-2.6.31-14-generic
   2.0GB: boot/vmlinuz-2.6.31-19-generic
   3.9GB: initrd.img
   3.9GB: initrd.img.old
   2.0GB: vmlinuz
   2.4GB: vmlinuz.old

```whenever i need to boot into ubuntu i have to type these codes into grub command window, and its really hurts

```

insmod ntfs
set root=(hd0,8)
search --no-floppy --fs-uuid --set 3e64e27064e229fb
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-19-generic
boot 
```
i found some code to recover grub2 using livecd such as
```

sudo fdisk -l
mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
sudo update-grub
```but i am afraid to use them because i could be wrong with it

** please help me**

sorry for late replys, normally i got connected once or twice daily

---

### Post by meierfra. on 2010-02-23
I'm not sure what is going on.

Could you post the output of 

```
ls

set
```

at "grub:sh" prompt?

Also type  

```
insmod ntfs
loopback loop0 (hd0,8)/ubuntu/disks/root.disk
set root=(loop0)
configfile /boot/grub/grub.cfg

```

Does this display the Grub menu?

Finally just to reduce the amount of typing you have to do to boot into Wubi try

```
insmod ntfs
set p=/ubuntu/disks/root.disk
loopback loop0 (hd0,8)$p
set root=(loop0)
linux /vmlinuz root=/dev/sda8 $p ro
initrd /initrd.img
boot
```

This should still boot you into Wubi.

---

### Post by meierfra. on 2010-02-23
One more thing. You  also have a "wubildr" on "/dev/sda5". If you have not done so yet, replace it by the new wubildr. (/dev/sda5" is a 22GB ntfs partition)

---

### Post by rkrinfo on 2010-02-23
thanks a lot meierfra
it worked!
i downloaded "wubildr" again and copied to C: (sda5) and restarted
now it shows an error message "error : file  not found" but after 4 or 5 seconds it continues to boot successfully
i may had the wrong "wubildr" in c:

i am very happy now
i am not worried about the error message, anyway i got my ubuntu back

i owe you meierfra, thanks a lot :D

---

### Post by davdalx on 2010-04-02
Hi.
I got this error after my computer had a sudden shutdown when it accidentally got unplugged (the battery wasn't in), now it can't boot into Ubuntu at all. I only have 2 partitions, the Windows one and the HP Recovery Partition.
@meierfa
I run the command ls and set and got this:

```
sh:grub> ls
(hd0) (hd0,2) (hd0,1)

sh:grub> set
?=0
color_highlight=
color_normal=
pager=
prefix=(hd0,1)/boot/grub
root=hd0,1
show_panic_message=true
```

I tried to run your other commands but I keep getting errors like "you must start the kernel first" or "fix signature no match"

Please help! I can't afford to reinstall Ubuntu and lose everything.

---

### Post by Mark Phelps on 2010-04-02
Sorry to point this out at this late date, but this is one of the key reasons to NOT use Wubi on any long term basis.

The section in the linked Wubi Guide below indicates what you have to do:

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu]("https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu")

And please note what it says about there NOT being a Linux equivalent of CHKDSK.  Some folks have claimed that ntfsfix IS this equivalent, but they are mistaken because that can only repair some basic NTFS problems.  If can not repair ALL NTFS problems.

---

### Post by davdalx on 2010-04-06
Thanx Mark. I'll just install Ubuntu permanently. With VirtualBox I don need Windows anymore

---

