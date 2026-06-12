---
title: "ubuntu 9.10 - ubuntustudio 9.10 from cdrom = grub - unkown filesystem"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by matthus on 2010-05-04
Hi I had two partitions on my hard disk, one with ubuntu 9.10 which I generally don't use until recently when I read there is hope for my audio interface to be included.
I am on limited internet on a payg dongle so upgraded it to ubuntustudio 9.10 using an ISO I had lying around in one of my windows folders.
Now when I boot without using a cd bootloader I get the error message unknown filesystem with a "grub rescue>" on command line style screen.
I've read bits and bobs here and there some saying grub has a yet again different set of commands, I was hoping I could install a fresh grub or other bootloader in place of it like the one I have on a cd.
I just do not know how and don't have alot of knowledge about filesystems and such.
I know how to create new partitions although it would be usefull to know how to check for a corrupted grub and wipe that first or which files to place in a fresh partition and what kind of partition that needs to be, I've read a couple of things on the net that say the new ubuntu release gets round this though I cannot download something that large at the moment due to bandwidth limitations and a system update doesn't seem to solve it.
Any ideas or suggestions are welcome :0)


thankyou

---

### Post by matthus on 2010-05-04
if it helps thats slightly in the wrong order.
windows and ubuntu side by side were fine.
Bodged an ubuntu studio installation over old ubuntu by wiping the partition.
got the same grub error.
So reinstalled old ubuntu 9.10 from disk and updated it to ubuntu studio thinking it may resolve it, it worked at first though not for long and back to square 2
here are the results from running bootinfoscript as recommended to someone here with a similar problem

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffbb6029

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   421,963,289   421,963,227   7 HPFS/NTFS
/dev/sda2         421,963,290   976,768,064   554,804,775   5 Extended
/dev/sda5    *    421,963,353   958,646,744   536,683,392  83 Linux
/dev/sda6    *    958,646,808   975,900,554    17,253,747  83 Linux
/dev/sda7         975,900,618   976,768,064       867,447  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/cryptswap1 e1a63b1a-5290-462c-b3f1-e3b9185e4181   swap                                     
/dev/sda1        EE1C5FAB1C5F6D99                       ntfs                                     
/dev/sda5        67ed7d38-ffa5-4016-aa78-9a5d237fe74b   ext3       fire                          
/dev/sda7        d6a29f80-f82f-4ac1-b955-edb9e86b8041   swap                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
cryptswap1
cryptswap1_unformatted

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=matt)
/dev/sr1         /media/O2 USB Modem      iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 67ed7d38-ffa5-4016-aa78-9a5d237fe74b
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=67ed7d38-ffa5-4016-aa78-9a5d237fe74b ro  quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 67ed7d38-ffa5-4016-aa78-9a5d237fe74b
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=67ed7d38-ffa5-4016-aa78-9a5d237fe74b ro single  quiet
	initrd	/boot/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=67ed7d38-ffa5-4016-aa78-9a5d237fe74b /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=5138b227-b215-4d55-92a1-bace4a64af55 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sda5: Location of files loaded by Grub: ===================


 307.5GB: boot/grub/grub.cfg
 307.5GB: boot/initrd.img-2.6.31-9-rt
 307.4GB: boot/vmlinuz-2.6.31-9-rt
 307.5GB: initrd.img
 307.4GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

arrgggh !!!

---

### Post by matthus on 2010-05-05
er bump? (please)

---

### Post by cchhrriiss121212 on 2010-05-06
I would boot into a live cd and format the ext3 and unknown partitions, then try a fresh install of 9.10. What happened when you tried to upgrade to studio?

---

### Post by matthus on 2010-05-07
There were some errors on original install of ubuntustudio hence why I updated it from my ubuntu install as the same issue occurred. I think theres some corrupt files on my ubuntu studio disk, got a gparted disk so will give that a go and try and aquire a iso of new ubuntu studio, will kepp it posted like. I thankyou

---

