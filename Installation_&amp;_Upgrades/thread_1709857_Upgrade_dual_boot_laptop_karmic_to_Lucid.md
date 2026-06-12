---
title: "Upgrade dual boot laptop karmic to Lucid"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by dieselglock on 2011-03-18
Hello,

I have been running Karmic 9.10 on my laptop with a dual boot with Windows 7. The lap top has 1 ssd and 2 hd's. Karmic is on one of the std drives and win7 is on the ssd. This has been running flawless for over a year. 

I have been contemplating upgrading to Lucid but have not gotten up the gut's to do it. I have spent the last day reading posts on these forums but still am unsure. I am most worried about the grub updating and messing things up. I am not sure where the grub is to installed.

I have also read in a tutorial that it is best to un-install all 3rd party apps

Any tips on doing this upgrade would be appreciated thanks Len

Here is my boot script.
    Boot Info Script 0.55    dated February 15th, 2010                    
```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=8cc0247b-c605-4f2b-8fa8-448f3861320d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe2f2be63

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb648a4a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   488,922,209   488,920,162   7 HPFS/NTFS
/dev/sdb2         488,922,210   976,768,064   487,845,855   5 Extended
/dev/sdb5         488,922,273   956,911,724   467,989,452  83 Linux
/dev/sdb6         956,911,788   976,768,064    19,856,277  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6939953e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1       409,639       409,639  ee GPT
/dev/sdc2             411,648   625,141,759   624,730,112   7 HPFS/NTFS


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              40       409,639       409,600 System/Boot Partition
/dev/sdc2         411,648   625,141,759   624,730,112 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        9088896188894726                       ntfs                                     
/dev/sdb1        EA460D0B460CD9E9                       ntfs       Storage                       
/dev/sdb5        8cc0247b-c605-4f2b-8fa8-448f3861320d   ext4                                     
/dev/sdb6        4e57350e-ff2f-4416-b939-a601054046b9   swap                                     
/dev/sdc1        70D6-1701                              vfat       EFI                           
/dev/sdc2        969CFCDE9CFCBA37                       ntfs       DATA                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc2        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set 8cc0247b-c605-4f2b-8fa8-448f3861320d
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
menuentry "Ubuntu, Linux 2.6.31-23-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 8cc0247b-c605-4f2b-8fa8-448f3861320d
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=8cc0247b-c605-4f2b-8fa8-448f3861320d ro  splash quiet  quiet splash
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-23-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 8cc0247b-c605-4f2b-8fa8-448f3861320d
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=8cc0247b-c605-4f2b-8fa8-448f3861320d ro single  splash quiet
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 8cc0247b-c605-4f2b-8fa8-448f3861320d
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=8cc0247b-c605-4f2b-8fa8-448f3861320d ro  splash quiet  quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 8cc0247b-c605-4f2b-8fa8-448f3861320d
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=8cc0247b-c605-4f2b-8fa8-448f3861320d ro single  splash quiet
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 9088896188894726
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb5 :
UUID=8cc0247b-c605-4f2b-8fa8-448f3861320d / ext4 errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=4e57350e-ff2f-4416-b939-a601054046b9 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdc2 /media/DATA ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb5: Location of files loaded by Grub: ===================


 250.4GB: boot/grub/core.img
 250.9GB: boot/grub/grub.cfg
 252.7GB: boot/initrd.img-2.6.31-20-generic
 259.5GB: boot/initrd.img-2.6.31-22-generic
 259.5GB: boot/initrd.img-2.6.31-23-generic
 256.6GB: boot/vmlinuz-2.6.31-22-generic
 256.4GB: boot/vmlinuz-2.6.31-23-generic
 259.5GB: initrd.img
 259.5GB: initrd.img.old
 256.4GB: vmlinuz
 256.6GB: vmlinuz.old
```

---

### Post by dieselglock on 2011-03-19
Anybody have any tips to do this the best way? 

If I do a clean install will it hose the grub2 already in place? 

Should I update the grub2 already installed first?

How would you handle this?

---

### Post by dieselglock on 2011-03-20
I have decided I would like to do a clean install of 10.04 lts on the drive that has 9.10 on it now. Can anybody give me any pointers as to how to accomplish this with out hosing the whole set up. I am not sure where to actually install 10.04 and what will happen to the grub2 that is in place now.

Thanks Len

---

### Post by mörgæs on 2011-03-20
You don't need to worry about Grub. During installation, 10.04 will provide a new one.

Just back up your files in /home and keep a wired internet connection while installing, and you should be fine.

---

### Post by dieselglock on 2011-03-20
> **mörgæs said:**
> You don't need to worry about Grub. During installation, 10.04 will provide a new one.

Just back up your files in /home and keep a wired internet connection while installing, and you should be fine.

I hope thats how it will work. If I do a clean install to the partition sdb5 it will overwrite the grub2 then with a new grub2 ?

---

### Post by Quackers on 2011-03-22
The answer to your last question is yes.
However, unless your disc designations have somehow changed, you have grub2 installed on the Windows drive, and Windows bootloader installed on the Ubuntu drive, and no bootloader at all installed on the BSD drive!

I can recommend fixing the first 2 properly, so that they can boot independently of each other. This means that Windows will boot even if the other drives are disconnected. But, if the Ubuntu drive is connected as well as the Windows drive you will get the choice of which system to boot from the grub menu.

First things first. Do you have a Windows Vista/7 installation disc or repair disc?

---

### Post by dieselglock on 2011-03-22
> **Quackers said:**
> The answer to your last question is yes.
However, unless your disc designations have somehow changed, you have grub2 installed on the Windows drive, and Windows bootloader installed on the Ubuntu drive, and no bootloader at all installed on the BSD drive!

I can recommend fixing the first 2 properly, so that they can boot independently of each other. This means that Windows will boot even if the other drives are disconnected. But, if the Ubuntu drive is connected as well as the Windows drive you will get the choice of which system to boot from the grub menu.

First things first. Do you have a Windows Vista/7 installation disc or repair disc?

Thanks for responding

Just for info, the system as it stands at this time does boot fine into either system. And has been working for 1 year like this maybe I am lucky.

Yes I do have a Win7 install disc

---

### Post by Quackers on 2011-03-22
> **dieselglock said:**
> Thanks for responding

Just for info, the system as it stands at this time does boot fine into either system. And has been working for 1 year like this maybe I am lucky.

Yes I do have a Win7 install disc

Presumably then, neither drive has been disconnected at any time and the bios is set to boot from the Ubuntu drive?

---

### Post by Quackers on 2011-03-22
Actually bios must be set to boot from the Windows drive at the moment.
Anyway, if you use the upgrade option from within 9.10 using update manager, grub will not be changed. Grub2 will only be replaced if you actually install 10.04 by cd.

---

### Post by dieselglock on 2011-03-22
> **Quackers said:**
> Presumably then, neither drive has been disconnected at any time and the bios is set to boot from the Ubuntu drive?

You are correct no drive has been disconnected at any time. The system is a triple hard drive set up. One drive win 7 sda, 2nd drive has a shared storage partition ntfs a Ubuntu partition ext4 and a swap partition. The 3 rd drive is data only for windows.

The win7 disk sda is first in the boot order.

---

### Post by Quackers on 2011-03-22
Ok thanks. Did you see the post one above your last?

---

### Post by dieselglock on 2011-03-22
Thanks for your help. I was just under impression that a clean install was a better way to go. I do have some added software. So would be better off to try uninstalling all the extra packages not recognized by synaptic and then upgrade. Via the upgrade program.

---

### Post by Quackers on 2011-03-22
Yes, it often is recommended, but I have done successful upgrades, particularly when only one upgrade is being run (eg 9.10 to 10.04)
In case of problems, it would be prudent to backup anything you would not want to lose.

---

### Post by dieselglock on 2011-03-22
Thanks again for taking the time.

Len

---

