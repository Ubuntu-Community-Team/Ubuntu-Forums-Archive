---
title: "Dual boot Karmic and Windows 7 - GRUB2 can't find Ubuntu"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by oxy- on 2010-04-21
Greetings,
I recently did a fresh install of Windows 7 together with Ubuntu 10.04 and everything worked fine until I rebooted after accessing the windows part (I found a post somewhere advicing to remove the ATI restricted as a fix so that might have been the reason as well). After that I could not access linux anymore, I found it on the grub menu but the screen just turned black and froze with two static _ signs. After trying a few basics tricks I figured I just go for the 9.10 Karmic stable instead.
- Guess what, the same thing happened again

**So now I'm in Ubuntu 9.10 Karmic** and I tried reinstalling grub2 (*GNU GRUB 1.97 beta4* according to -v) through the guide on [http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide). Everything worked fine except that during '*update-grub' *it only detects my Windows 7 installation - which works without problems by the way. If I proceed as it didn't happen only Windows 7 shows up on the boot list. Now I've removed the ATI drivers but can't find my ubuntu installation to give it a second go...

**QUESTION!** Am I supposed to run
```
grub-install /dev/sda6
``` like they mention in the guide even if I have a /boot? I did as they said but I'm open for any stupid user error I might have done :D

**fdisk -l**
[PHP]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda10: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    56,578,047    56,371,200   7 HPFS/NTFS
/dev/sda3          56,580,094   312,580,095   256,000,002   5 Extended
/dev/sda5         308,533,248   312,580,095     4,046,848  82 Linux swap / Solaris
/dev/sda6    *     56,580,096   105,408,511    48,828,416  83 Linux
/dev/sda7         105,418,593   193,679,639    88,261,047   7 HPFS/NTFS
/dev/sda8         213,295,068   308,528,324    95,233,257  83 Linux
/dev/sda9         193,679,703   213,295,004    19,615,302  83 Linux
/dev/sda10        193,679,641   193,679,701            61  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F832B59732B55AF8                       ntfs       System Reserved               
/dev/sda2        EABECB60BECB2443                       ntfs       windows                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        497f8b58-2c80-46d6-8b80-06ebefadb00c   swap                                     
/dev/sda6        8c22082e-ab7b-4871-8ee6-d1cfe650fdc7   ext4       root                          
/dev/sda7        61A56E633C6DCB40                       ntfs                                     
/dev/sda8        51e63744-271a-4dfd-a798-98cdb4c24912   ext4       entertainment                 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /mnt                     ext4       (rw)
/dev/sda1        /mnt/boot                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev             /mnt/dev                 none       (rw,bind)
/dev/sda8        /media/entertainment     ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/61A56E633C6DCB40  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=8c22082e-ab7b-4871-8ee6-d1cfe650fdc7     /                   ext4    errors=remount-ro 0       1
UUID=51e63744-271a-4dfd-a798-98cdb4c24912    /mnt/entertainment    ext4    defaults      0      0
# swap was on /dev/sda5 during installation
UUID=497f8b58-2c80-46d6-8b80-06ebefadb00c     none                swap    sw                0       0
/dev/scd0                       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

UUID=EABECB60BECB2443                /mnt/windows        ntfs-3g    defaults      0      0
UUID=61A56E633C6DCB40                /mnt/harmony        ntfs-3g    defaults      0      0
[/PHP]Note: 
/dev/sda1 is boot. 
/dev/sda2 is Windows 7.
/dev/sda6 is Ubuntu.
/dev/sda7 & 8 & 9 is data
/dev/sda10 I have no clue....

**/boot/grub/grub.cfg**
[PHP]
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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 8c22082e-ab7b-4871-8ee6-d1cfe650fdc7
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f832b59732b55af8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
[/PHP]Note: I just noticed it mentions my linux partition in the beginning, hd(0,6)

- My system is Lenovo T400 and the Ubuntu is 64bit.
Is there any other information that could be useful?

---

### Post by oldfred on 2010-04-21
the boot is a windows boot but you are now missing the windows boot files. Win7 when installed new creates a 100mb boot partition and then the main install. The windows boot is not related to a grub/ubuntu boot partition. IF you had your Ubuntu files in sda1 they are gone.

For the windows repairs to work you need to move the boot flag (*) or active partition for windows back to sda1. You can use gparted on the liveCD. Right Click on the partition and manage flags. Make sure you only have one boot flag per drive and it needs to be on a primary partition(which sda1 is).

You Ubuntu partition is missing grub files and the boot files so they must have been in sda1? 

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

