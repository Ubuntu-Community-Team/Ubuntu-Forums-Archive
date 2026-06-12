---
title: "Installed Karmic beside windows now xp wont boot"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by tfultz33 on 2010-07-06
I just installed Karmic 9.10 on a Compaq Presario on the same hard drive with XP. The 2nd hard drive may have a recovery partition on it. Im not sure right now, but it has in the past. The Same drive with Ubuntu and Windows on it has a recovery partition.

Well, the install went well. I booted into ubuntu fine. When i rebooted and selected Windows XP Media Center Edition from the Grub2 menu I get a blank black screen with a flashing curser. Thats it. NO errors.

I installed it before on this computer on the 2nd HD and had the same problem so i reformatted it (and accidentally put windows on it, hence the recovery partition. Not sure if i deleted that partition or not) and just use it for extra storage.

 This time I put them both on the same drive. Still the same problem.

Thanks for any help.

---

### Post by tfultz33 on 2010-07-06
I just ran a boot_info_script and this is the output:

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => HP/Gateway is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x079c3f6f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   178,610,669   178,610,607   7 HPFS/NTFS
/dev/sda2         294,598,080   312,575,759    17,977,680   c W95 FAT32 (LBA)
/dev/sda3         178,610,670   294,583,904   115,973,235   5 Extended
/dev/sda5         178,610,733   289,764,404   111,153,672  83 Linux
/dev/sda6         289,764,468   294,583,904     4,819,437  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        88306D49306D3EF6                       ntfs       PRESARIO                      
/dev/sda2        5438-79C7                              vfat       PRESARIO_RP                   
/dev/sda5        d0411299-5eae-44a1-8d60-5f54fc291641   ext4                                     
/dev/sda6        8531f26f-03f3-473d-be2d-3add4647238a   swap                                     
/dev/sdb1        52A04F66A04F4FA1                       ntfs       Extra Store                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

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
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set d0411299-5eae-44a1-8d60-5f54fc291641
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d0411299-5eae-44a1-8d60-5f54fc291641
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d0411299-5eae-44a1-8d60-5f54fc291641 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d0411299-5eae-44a1-8d60-5f54fc291641
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d0411299-5eae-44a1-8d60-5f54fc291641 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 88306d49306d3ef6
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 5438-79c7
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=d0411299-5eae-44a1-8d60-5f54fc291641 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8531f26f-03f3-473d-be2d-3add4647238a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 102.8GB: boot/grub/core.img
 102.8GB: boot/grub/grub.cfg
  92.0GB: boot/initrd.img-2.6.31-14-generic
  91.9GB: boot/vmlinuz-2.6.31-14-generic
  92.0GB: initrd.img
  91.9GB: vmlinuz

---

### Post by oldfred on 2010-07-06
I do not see anything wrong with your boot_info script results. It does show an old wubi in sda2's boot.ini.

You can try the windows fixes.
XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

You may need to run checkdisk
To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 

If you run fixMBR you can directly test booting XP but then have to reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by tfultz33 on 2010-07-06
I assumed an easy fix like add a line of coade or change a line, since this seems to have been a very common problem. I dont want to mess with my windows boot files unless absolutely necessary. I am not reinstalling windows again.

Thank you for the reply.

---

### Post by tfultz33 on 2010-07-06
I tried the fixboot and the chkdsk. Still the same. The blinking cursor in the upper left hand corner like it is going to start loading something but never does. Dead ends.

---

### Post by tfultz33 on 2010-07-06
Hmm. Just found something interesting. When i did the chkdsk, it evidently checked D: instead of c: 

I typed fixboot c:

It saved a log on my D: drive which is labeled Extra Store:

Checking file system on \DosDevices\C: 
The type of the file system is NTFS. 
Volume label is Extra Store. 
Cleaning up minor inconsistencies on the drive. 
Cleaning up 10 unused index entries from index $SII of file 0x9. 
Cleaning up 10 unused index entries from index $SDH of file 0x9. 
Cleaning up 10 unused security descriptors. 
CHKDSK is verifying Usn Journal... 
Usn Journal verification completed. 
CHKDSK is verifying file data (stage 4 of 5)... 
File data verification completed. 
CHKDSK is verifying free space (stage 5 of 5)... 
Free space verification is complete. 
 
 117218240 KB total disk space. 
  27848484 KB in 953 files. 
       288 KB in 69 indexes. 
         0 KB in bad sectors. 
     75192 KB in use by the system. 
     65536 KB occupied by the log file. 
  89294276 KB available on disk. 
 
      4096 bytes in each allocation unit. 
  29304560 total allocation units on disk. 
  22323569 allocation units available on disk. 
 
Internal Info: 
20 04 00 00 0a 04 00 00 e7 05 00 00 00 00 00 00   ............... 
87 00 00 00 00 00 00 00 19 00 00 00 00 00 00 00  ................ 
de 39 1a 00 00 00 00 00 fc be 80 00 00 00 00 00  .9.............. 
92 fe 1e 00 00 00 00 00 c4 13 e5 96 01 00 00 00  ................ 
9e 92 15 9b 05 00 00 00 bc 62 5f 34 07 00 00 00  .........b_4.... 
99 9e 36 00 00 00 00 00 b9 03 00 00 00 00 00 00  ..6............. 
00 90 bc a3 06 00 00 00 45 00 00 00 00 00 00 00  ........E.......

---

### Post by tfultz33 on 2010-07-07
Any Takers?:popcorn:

---

### Post by tfultz33 on 2010-07-07
The recovery partition boots up. I dont get it.

---

### Post by oldfred on 2010-07-07
Did you change windows in sda1.
the boot.ini in sda says one version and the recovery boot.ini says another.
Windo ws XP Media Center Edition
Micro soft Windows XP Professional

I would make sure you have run all the repairs on sda1 that you did to sda2.

---

### Post by tfultz33 on 2010-07-07
This just in: I moved my extra files from D: (my extra store) and reformatted with FAT. then ran update-grub, rebooted, and nothing different. But, I booted back into recovery console and typed map at the prompt and it only listed 2 drives: C: (My newly blank Extra Store) and D:(Windows Recovery Console).

It is not even recognising the main drive with the xp partition. I have mounted the Xp partition and all files are safe and sound.

The main drive is a sata drive listed first in hd boot priority. The 2nd drive is an older eide WD drive plugged in through a ribbon cable.

Anyone know what's up?

Thanks.
Thomas

---

### Post by tfultz33 on 2010-07-07
Thanks for your help Fred. The fixes were applied to the wrong drive . Windows recovery wont see the main drive.

---

### Post by oldfred on 2010-07-07
Are you sure c: is extra store? It should be seeing c: as sda1 not sdb1. All the repairs should see the partition with the boot flag which in windows is the active partition and that is sda1.

---

### Post by tfultz33 on 2010-07-07
Yep Im sure It listed the space and wont list directories because there are none now. It s calling a blank drive c:

---

### Post by tfultz33 on 2010-07-07
I should unplug the blank drive and reboot. Or is there a way around it?

---

### Post by tfultz33 on 2010-07-07
That didnt help

---

### Post by oldfred on 2010-07-07
Because you repaired the sda2 partition it may have moved boot flag to sda2? If so move it back to sda1 and try repairs again.

You can use gparted or disk utility to set boot flag.

set boot flag on for sda1 (off for others)
sudo sfdisk -A1 /dev/sda

---

### Post by tfultz33 on 2010-07-07
Ok got access to the main drive finally and did fixboot c: It wiped out the boot menu. Now all I get is NTlr or whatever is missing. 

Im not worried about Windows anymore. How do I get my linux boot loader back? I dont want to reinstall linux.

I am using ubuntu off the cd.
Can i just run update grub?

---

### Post by oldfred on 2010-07-07
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda


XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

### Post by tfultz33 on 2010-07-07
when i type sudo fdisk -l i get:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      116388      126889    84344761   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      105915      222310   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?           1           1           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4               1      213826  1717556736    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by tfultz33 on 2010-07-07
Grub2 Will not boot WIndows XP. Run one or the other. SOLVED

---

### Post by scradock on 2010-07-07
> **tfultz33 said:**
> Grub2 Will not boot WIndows XP. Run one or the other. SOLVED

Excuse me? Windows XP boots fine using Grub2 - HP Pavilion zv6000. I also have 3 Ubuntu flavors installed, two in primary, one in a logical partition.

There must be an error in your partition table - can you get into Ubuntu and run boot_info script again, then post the results.

---

