---
title: "problem space on HD maybe partition/format problem..."
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by nosmokenofire on 2010-09-17
Hi,

I'm new to Ubuntu and certainly not a computer expert. Basically I'm fed up with windows and everything Microsoft in general. I was thinking about changing to mac but a friend told me to try out linux. I'd always thought you had to be a computer expert to be able to use it but he said that it is no longer the case.

I have installed Ubuntu 10.4.1 32bit from here [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and I like it. I have an ACER Aspire 5100 laptop.

Now onto my problem: when I bought my laptop it had Windows Vista home basic already installed on the C drive. There is also a D drive. I presumed that my computer has 2 hard drives C and D. As there was not enough space left on C I installed Ubuntu on D. All is going well... I installed thunderbird in Ubuntu as I was used to it in windows and then tried to import my profiles from the windows version to the Ubuntu version. I get some kind of message telling me that there is not enough free space on the hard drive. When I check using windows there is about 20 odd Giga of space left, and when I check using Ubuntu there is only about 1.9G. From what I can figure out from internet searches the problem may be that the HD is partitioned (hence C and D drives) and that ubuntu does not recognise the type of formating used on the D drive.

Does this make sense? Can anyone help?

Many thanks.

---

### Post by nosmokenofire on 2010-09-17
here is a screenshot of the hard drive information, all in french I'm afraid. I wonder if I could get the same info in English

---

### Post by Rubi1200 on 2010-09-17
Hi and welcome to the forums :)

Do you still have the Ubuntu CD?

If yes, please boot the laptop with it and choose to try Ubuntu in live mode.

Then, post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by nosmokenofire on 2010-09-17
Many thanks for your help Rubi, attached is the result.

---

### Post by nosmokenofire on 2010-09-17
One thing I forgot to mention about my previous post: I do not have a CD as my CDburner is having problems, so I installed ubuntu on my ext. hard drive and used it like a USB stick. I hope this does not affect the results.

Thanks for any help.

---

### Post by Rubi1200 on 2010-09-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,370,234    16,370,172  27 Hidden HPFS/NTFS
/dev/sda2    *     16,370,235    86,654,609    70,284,375   6 FAT16
/dev/sda3          86,654,610   156,296,384    69,641,775   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2ac143a9-67d6-4d10-ab96-cb05242424ad   ext4                                     
/dev/sda1        8A408E8916D9B5D2                       ntfs       PQSERVICE                     
/dev/sda2        64700DE6700DBFB2                       ntfs       ACER                          
/dev/sda3        BA78567378562DFF                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3104-170B                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ba78567378562dff
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ba78567378562dff
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8a408e8916d9b5d2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64700de6700dbfb2
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


   5.0GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.32-24-generic
   1.4GB: boot/vmlinuz-2.6.32-24-generic
   1.5GB: initrd.img
   1.4GB: vmlinuz
```

---

### Post by srs5694 on 2010-09-17
It looks to me like you've got a WUBI install, which is a way to install Linux inside a Windows partition. I've never used WUBI myself, but from what I've read, it's got a lot of limitations. It can be an acceptable way to get your feet wet with Linux, as it were, but it's not the best solution if you want to use Linux in a major way.

If you want to use Linux in a more serious way, I recommend you delete your WUBI installation and then re-install Linux using a traditional dual-boot configuration, in which you give a certain amount of space to Linux, a certain amount to Windows, and perhaps another batch of space to be used by both OSes (for documents you want to access in either OS, say). You'll need to decide how to partition your disk to accomplish this goal. There are gobs of threads on this topic here, so I suggest you peruse the forums a bit and then come back with more specific questions you might have.

---

### Post by nosmokenofire on 2010-09-20
I guess I just jumped into all this way too fast without reading the manual. it looks suspiciously like you are right, I think I do have a Wubi setup. I had a look round in the threads and found a link to [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) I'll work from this and open a new thread if I come up against any more specific problems. I'm marking this one as solved.

Many thanks for your help.

---

