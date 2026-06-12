---
title: "Grub Rescue error : Core.img not found- Help installing Ubuntu on External Hard Drive"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by Sibetron on 2011-09-18
Hello all,
I am a newbie to Ubuntu and wanted some help on getting the installation done on an external hard drive.

I have  a Live USB version (11.04 Ubuntu)  from where I am performing the installation.

I followed the steps mentioned in the following link 
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

Installation went fine .
However, when I try to boot from external hard drive, I see a screen which says Grub Rescue> .

I searched online and found it had to do with the MBR not being setup correctly.

Just some info on my PC and external hard drive .

My internal Hard drive is drive : sda

SDB is my pen drive, where the Live USB is present.

My external hard drive is sdc .

On my external hard drive, initially the entire hard disk was formatted to NTFS and I used to use it for storage. 
I created a free space of 25Gb on external hard drive for Ubuntu installation from WIn 7 using shrink volume feature.

SO due to this my hard drive had SDC1/SDC2 which were prior partitions , and after free space allocation, i further split them into Sdc3 - boot , sdc4 - Home , Sdc5 - swap area etc ....

I followed the steps mentioned in the following link 
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

Under the &#8220;Device for boot loader installation&#8221; section, I selected the entry that matches the external disk that I  just partitioned (SDC - External HD).  I did NOT select SDC3 where the boot area of the Ubuntu installation is present .

I am not sure if that is the error.

On reading some posts i followed this one : 
[http://ubuntuforums.org/showthread.php?t=1528371](http://ubuntuforums.org/showthread.php?t=1528371)

And captured the bootinfo . I see some error with regards to core.img not being found ? highlighted below. I am not sure if thats the problem though.

Can someone please help with this ?
Thanks for your help .

Below is the results.txt 
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 15274 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

[B]    File system:       ext2
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdc3 
                       and looks at sector 942295178 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img[/B]

sdc4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdc8: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   312,578,047   312,576,000   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
129 heads, 32 sectors/track, 948 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,915,775     3,915,744   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   935,813,167   935,811,120   7 NTFS / exFAT / HPFS
/dev/sdc2    *    935,815,168   942,209,023     6,393,856   7 NTFS / exFAT / HPFS
/dev/sdc3         942,209,024   942,712,831       503,808  83 Linux
/dev/sdc4         942,714,878   976,771,071    34,056,194   5 Extended
/dev/sdc5         942,714,880   946,618,367     3,903,488  82 Linux swap / Solaris
/dev/sdc6         966,152,192   976,771,071    10,618,880  83 Linux
/dev/sdc7         946,620,416   962,097,151    15,476,736  83 Linux
/dev/sdc8         962,099,200   966,148,095     4,048,896  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B23C58853C58468F                       ntfs       SHISH
/dev/sdb1        130D-3153                              vfat       PENDRIVE
/dev/sdc1        22FE8FF0FE8FBA95                       ntfs       Elements
/dev/sdc2        86DA7A0BDA79F7AF                       ntfs       PENDRIVE
/dev/sdc3        fe976c88-9f06-4950-a4ff-9d0b107077f5   ext2       
/dev/sdc6        8d426315-1eb7-4fe4-8554-47807c08a855   ext4       
/dev/sdc7        86a7f3c7-a328-464f-99e7-b2753ab1b3be   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc2        /media/PENDRIVE          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc3        /media/fe976c88-9f06-4950-a4ff-9d0b107077f5 ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc6        /media/8d426315-1eb7-4fe4-8554-47807c08a855 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc7        /media/86a7f3c7-a328-464f-99e7-b2753ab1b3be ext4       (rw,nosuid,nodev,uhelper=udisks)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

============================= sdc3/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos7)'
search --no-floppy --fs-uuid --set=root 86a7f3c7-a328-464f-99e7-b2753ab1b3be
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos3)'
search --no-floppy --fs-uuid --set=root fe976c88-9f06-4950-a4ff-9d0b107077f5
set locale_dir=($root)/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos3)'
    search --no-floppy --fs-uuid --set=root fe976c88-9f06-4950-a4ff-9d0b107077f5
    linux    /vmlinuz-2.6.38-8-generic root=UUID=86a7f3c7-a328-464f-99e7-b2753ab1b3be ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos3)'
    search --no-floppy --fs-uuid --set=root fe976c88-9f06-4950-a4ff-9d0b107077f5
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=86a7f3c7-a328-464f-99e7-b2753ab1b3be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos3)'
    search --no-floppy --fs-uuid --set=root fe976c88-9f06-4950-a4ff-9d0b107077f5
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos3)'
    search --no-floppy --fs-uuid --set=root fe976c88-9f06-4950-a4ff-9d0b107077f5
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root B23C58853C58468F
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
--------------------------------------------------------------------------------

=================== sdc3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 449.503020287 = 482.650192896  grub/core.img                                  2
 449.502021790 = 482.649120768  grub/grub.cfg                                  1
 449.325525284 = 482.459609088  initrd.img-2.6.38-8-generic                   73
 449.295414925 = 482.427278336  vmlinuz-2.6.38-8-generic                      19

=============================== sdc7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc7 during installation
UUID=86a7f3c7-a328-464f-99e7-b2753ab1b3be /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc3 during installation
UUID=fe976c88-9f06-4950-a4ff-9d0b107077f5 /boot           ext2    defaults        0       2
# /home was on /dev/sdc6 during installation
UUID=8d426315-1eb7-4fe4-8554-47807c08a855 /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
#UUID=3c4716c3-c6c3-454d-8c12-43013f6b9502 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected



```

---

### Post by drs305 on 2011-09-18
Your system isn't finding core.img, which is generated by the grub-install command.

Boot a LiveCD and mount your Ubuntu partition, then the /boot partition. Then run the grub-install command again. Do not specify a partition in the third command:
```

sudo mount /dev/sdc7 /mnt
sudo mount /dev/sdc3 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sdc
```

When you reboot, make sure your BIOS is set to boot your SDC drive first.

Added:
I also see you are using a large drive and the grub files are located deep into the drive. If the above doesn't work, at the grub prompt. Use the "ls" command to determine which partition is your /boot partition. If it isn't (hd3,3), change the following command.

Corrected:
```
ls (hd**2**,3)/boot/grub
```
Does Grub find a lot of *.mod files?

---

### Post by Sibetron on 2011-09-18
Hey,

I tried the first 3 commands .
Basically I pasted  from your post : 
sudo mount /dev/sdc7 /mnt sudo mount /dev/sdc3 /mnt/boot sudo grub-install --root-directory=/mnt /dev/sdc
After that on rebooting I got an error 
Grub Error : unknown filesystem.

On typing ls , it showed 
(hd0) (hdo.msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1) 

I tried 
ls (hd3,3)/boot/grub


the error was : error : hd3 cannot get C/H/S values. 

I am not sure regarding the *.mod files .

I still see the unknown file system error and the grub rescue screen.

---

### Post by drs305 on 2011-09-18
Actually, I made an error and it should have been (hd2,3)/boot/grub. hd2 should be sdc, unless the computer reorders them.

However, Grub is seeing only two drives (hd0), (hd1). It is not seeing your third drive, which I assume is your Ubuntu drive since neither of the others lists more than 3 partitions.

Try this, but I don't think it's the correct drive:
```
ls (hd0,1)/boot/grub
```

---

### Post by Sibetron on 2011-09-18
Hey drs305,

i tried with  (hd2,3)/boot/grub ,
however as you mentioned it looks as if hd2 is not seen at all . and this command failed with 
error : hd2 cannot get C/H/S values

when I tried the other command with hd0,1 ,
it showed the error
unknown filesystem .

Any other clues as to how to fix it.

Thanks for your help.

---

### Post by drs305 on 2011-09-18
I'm assuming you still have the same 3 devices connected that you did when you ran the boot info script. If so, Grub should find (hd0), (hd1) and (hd2). 

Other than checking cables, etc I'm not good at troubleshooting this kind of problem. If you boot the LiveCD, can you see all the drives and partitions. You can run Gparted or use Disk Utility, or use the command line and run:
```
sudo blkid && sudo fdisk -l # lowercase L
```

If you are more comfortable in Windows, you should be able to boot into that OS if you change the BIOS to boot your Windows drive first.

I'll go through the RESULTS.txt again line by line but I don't know why Grub isn't seeing the drive.

**Added: **I see your fstab has a /dev/mapper  listing. Did you use RAID at one time. (Note: I'm not a RAID user but know that remants of an old RAID setup can mess up Grub).

---

### Post by Sibetron on 2011-09-18
Yes, I have the same 3 devices connected.

I tried the ommand , and I am able to see the sdc listed .\
Here is the output 

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="SHISH" UUID="B23C58853C58468F" TYPE="ntfs" 
/dev/sdb1: LABEL="PENDRIVE" UUID="130D-3153" TYPE="vfat" 
/dev/sdc1: LABEL="Elements" UUID="22FE8FF0FE8FBA95" TYPE="ntfs" 
/dev/sdc2: LABEL="PENDRIVE" UUID="86DA7A0BDA79F7AF" TYPE="ntfs" 
/dev/sdc3: UUID="fe976c88-9f06-4950-a4ff-9d0b107077f5" TYPE="ext2" 
/dev/sdc6: UUID="8d426315-1eb7-4fe4-8554-47807c08a855" TYPE="ext4" 
/dev/sdc7: UUID="86a7f3c7-a328-464f-99e7-b2753ab1b3be" TYPE="ext4" 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b9a18af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 2004 MB, 2004877312 bytes
129 heads, 32 sectors/track, 948 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         949     1957872    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(956, 128, 32) logical=(948, 75, 32)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00157178

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       58252   467905560    7  HPFS/NTFS
/dev/sdc2   *       58252       58650     3196928    7  HPFS/NTFS
/dev/sdc3           58650       58682      251904   83  Linux
/dev/sdc4           58682       60802    17028097    5  Extended
/dev/sdc5           58682       58925     1951744   82  Linux swap / Solaris
/dev/sdc6           60141       60802     5309440   83  Linux
/dev/sdc7           58925       59888     7738368   83  Linux
/dev/sdc8           59888       60140     2024448   83  Linux

Partition table entries are not in disk order

---

### Post by drs305 on 2011-09-18
The only suggestion I can think of at the moment is to purge and reinstall Grub 2. I wrote a guide about it. First inspect the 3 and 7 partitions and make sure they have the boot files on 3 and the / files on 7. Then run the purge/reinstall chroot procedure, making sure to follow the additional instructions for users with a separate /boot partition.

[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by Sibetron on 2011-09-18
I actually take my earlier response back.
While I am trying to boot from my external Hard drive, i remove the usb out (the Live USB) as it starts boot from that , instead of the external hard drive. 

Probably thats the reason why we see only hd0 & hd1 .
I however tried all options at the grub menu ls (hd*,#)/boot/grub 

* - 0 & 1
# 1,2,3,4

But still either i see filesystem unknown or i see partition not found as the error messages.

---

### Post by drs305 on 2011-09-18
Are you getting all 7 or 8 partitions now? That was what I was concentrating on.

However, the normal 'ls' commands I gave you probably aren't correct since you have a separate boot. 

Work your way up:
```
ls
ls (hdX,Y)/
ls (hdX,Y/grub

```
Even if you find the grub files, experiment to try to find the other Ubuntu files.

My main concern though is that it's not seeing all the partitions. Even if we find the /boot partition, if it doesn't see the others it won't matter.

---

### Post by Sibetron on 2011-09-18
The problem as you point out still remains.

My internal HD on Gparted shows up as sda1 & sda2 with sda 2 having unallocated space (10MB) .

The external HD has mainly 4 partitions ,
sdc1 - NTFS 
sdc2 - NTFS
sdc3 - Boot - ext2
sdc4 - extended 
Withing sdc4 is sdc 7 - ext4 
and also within sdc4 is sdc 5 & sdc8  which are swap areas .

So by this i am assuming hd0 is this drive which comes up on grub.
The main problem seems to be why is it not seeing sdc7 ? which lies within sc4 in the hierarchy.

Also I am unsure why sdc 5/6/7 are listed as under sdc4 and not in the parent directory where sdc 1-4 are listed .

---

### Post by drs305 on 2011-09-18
Boot into BIOS and see what the reported drive size is. If the drive is reported as 137GB or less, it's possible that you are running into a BIOS limitation. I've dealt with this issue many times before, but your indications are not the same. That could be because you have a separate boot partition but I don't think so.

If the BIOS reports a disk size of 137GB or less, I can provide some options. If it doesn't, I don't really have any more ideas other than deleting partitions 3 and higher, reformatting, and reinstalling Ubuntu.

I still don't fully understand the swap listing in your fstab, which includes 'dev/mapper/cryptswap'

---

### Post by Hakunka-Matata on 2011-09-18
> **Sibetron said:**
> The problem as you point out still remains.

My internal HD on Gparted shows up as sda1 & sda2 with sda 2 having unallocated space (10MB) .

The external HD has mainly 4 partitions ,
sdc1 - NTFS 
sdc2 - NTFS
sdc3 - Boot - ext2
sdc4 - extended 
Withing sdc4 is sdc 7 - ext4 
and also within sdc4 is sdc 5 & sdc8  which are swap areas .

So by this i am assuming hd0 is this drive which comes up on grub.
The main problem seems to be why is it not seeing sdc7 ? which lies within sc4 in the hierarchy.

**Also I am unsure why sdc 5/6/7 are listed as under sdc4 and not in the parent directory where sdc 1-4 are listed .**

sdc5, 6, 7, & 8 are all Logical partitions, they live inside the Extended partition.  sdc1,2,3,4 are all primary partitions.  1..4, are always primary partitions, and anything above 4 is a Logical.

---

