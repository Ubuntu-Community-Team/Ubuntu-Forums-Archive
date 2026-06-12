---
title: "Help partitioning"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by dieselglock on 2011-03-31
Hello,

I have laptop with 3 hdd. It is a dual boot win7 and lucid install. I recently installed lucid on one of the drives. The laptop boots both systems fine. I was looking at the way the drive that has lucid on it and it does not look right. Can someone please help. Here is my fdisk -l
output.
```
awrence@lawrence-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2f2be63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb648a4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30434   244460081    7  HPFS/NTFS
/dev/sdb2          [COLOR=Red] 30435       60801[/COLOR]   243922897    5  Extended
/dev/sdb5           [COLOR=Red]30435       59565[/COLOR]   233994726   83  Linux
/dev/sdb6           59566       60801     9928138+  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6939953e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          26      204819+  ee  GPT
/dev/sdc2              26       38914   312365056    7  HPFS/NTFS
lawrence@lawrence-laptop:~$ 

```sdb2 and sdb5 are on top of each other (dont know if thats the right terminology)

This is my boot script ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
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
    Operating System:  Ubuntu 10.04.2 LTS
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
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   488,922,209   488,920,162   7 HPFS/NTFS
/dev/sdb2         488,922,271   976,768,064   487,845,794   5 Extended
/dev/sdb5         488,922,273   956,911,724   467,989,452  83 Linux
/dev/sdb6         956,911,788   976,768,064    19,856,277  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

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
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EA460D0B460CD9E9                       ntfs       Storage                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        908af3eb-0d15-4862-9370-8eb860e33919   ext4                                     
/dev/sdb6        4e57350e-ff2f-4416-b939-a601054046b9   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        70D6-1701                              vfat       EFI                           
/dev/sdc2        969CFCDE9CFCBA37                       ntfs       DATA                          
/dev/sdc: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdc2        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/sda1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 908af3eb-0d15-4862-9370-8eb860e33919
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 908af3eb-0d15-4862-9370-8eb860e33919
set locale_dir=($root)/boot/grub/locale
set lang=
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 908af3eb-0d15-4862-9370-8eb860e33919
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=908af3eb-0d15-4862-9370-8eb860e33919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 908af3eb-0d15-4862-9370-8eb860e33919
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=908af3eb-0d15-4862-9370-8eb860e33919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 908af3eb-0d15-4862-9370-8eb860e33919
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 908af3eb-0d15-4862-9370-8eb860e33919
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb5 :
UUID=908af3eb-0d15-4862-9370-8eb860e33919    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdc2 :
UUID=969CFCDE9CFCBA37    /media/DATA    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=EA460D0B460CD9E9    /media/Storage    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=9088896188894726    /media/sda1    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sdb6 :
UUID=4e57350e-ff2f-4416-b939-a601054046b9    none    swap    sw    0    0



=================== sdb5: Location of files loaded by Grub: ===================


 377.2GB: boot/grub/core.img
 396.5GB: boot/grub/grub.cfg
 252.2GB: boot/initrd.img-2.6.32-30-generic
 377.2GB: boot/vmlinuz-2.6.32-30-generic
 252.2GB: initrd.img
 377.2GB: vmlinuz
```Thanks in advance for any help on this.

---

### Post by ajgreeny on 2011-03-31
sda2 is an extended partition and contains the two logical partitions, sda5 and sda6, which are your ubuntu root partition and linux swap.  What you are seeing is absolutely normal and nothing to worry about 
```
/dev/sdb2 [COLOR=Red]          30435[/COLOR] [COLOR=Blue]      60801[/COLOR]   243922897    5  Extended
/dev/sdb5 [COLOR=Red]          30435[/COLOR]       59565   233994726   83  Linux
/dev/sdb6           59566 [COLOR=Blue]      60801[/COLOR]     9928138+  82  Linux swap
```
If you look you will see that sda5 starts at the same point as sda2 ([COLOR=Red]30435[/COLOR]), and sda2 ends at the same point as sda6 ([COLOR=Blue]60801[COLOR=Black]); all as it should be.

I am assuming that both your OSs boot OK and run as you want them to.
[/COLOR][/COLOR]

---

### Post by dieselglock on 2011-03-31
> **ajgreeny said:**
> sda2 is an extended partition and contains the two logical partitions, sda5 and sda6, which are your ubuntu root partition and linux swap.  What you are seeing is absolutely normal and nothing to worry about 
```
/dev/sdb2 [COLOR=Red]          30435[/COLOR] [COLOR=Blue]      60801[/COLOR]   243922897    5  Extended
/dev/sdb5 [COLOR=Red]          30435[/COLOR]       59565   233994726   83  Linux
/dev/sdb6           59566 [COLOR=Blue]      60801[/COLOR]     9928138+  82  Linux swap
```If you look you will see that sda5 starts at the same point as sda2 ([COLOR=Red]30435[/COLOR]), and sda2 ends at the same point as sda6 ([COLOR=Blue]60801[COLOR=Black]); all as it should be.

I am assuming that both your OSs boot OK and run as you want them to.
[/COLOR][/COLOR]

Thank you for taking the time. Ok I understand now. Yes it all seems to be working fine. 

A couple of other questions if you don't mind.

1. When i go into computer in Nautilus and check the properties on each of the drives and partitions and check permissions it say's that the permissions can not be determined.

2. On sdc I have a boot section at the beginning of the drive that I don't thimk should be there as this drive just stores data to be read by both systems. If I delete this boot section will mess things up.

Len

---

### Post by vanadium on 2011-03-31
* Drives use the ntfs file system, which is a Microsoft file system that does not support Linux permissions.

* Don't worry too much about your partitions if your system is running fine. If it ain't broken, don't attempt to fix it.

---

### Post by srs5694 on 2011-03-31
Your /dev/sdc is a GUID Partition Table (GPT) disk with a [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) Hybrid MBRs are ugly and dangerous hacks that are used mainly to enable Macs to dual-boot Windows. Since you're using Windows 7 and not booting from the disk, it will work fine as a legal (non-hybrid) GPT disk. Thus, I recommend getting rid of the hybrid MBR. You can do this by installing [GPT fdisk (gdisk and sgdisk)](http://www.rodsbooks.com/gdisk/) from its [SourceForge download page](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/gdisk-binaries/) (do *not* use the version in the Ubuntu repositories, which is extremely old) and doing the following:


[list=1]
[*]Launch gdisk on the disk by typing "sudo gdisk /dev/sdc" at a Linux shell prompt.
[*]Type "p" to view the GPT partitions and verify you're working on the right disk. If you're not, exit by typing "q" and re-launch gdisk on the correct disk.
[*]Type "x" to enter the experts' menu.
[*]Type "o" to view the MBR data. You should see two partitions, one of type 0xEE and one of type 0x07.
[*]Type "n" to create a new protective MBR.
[*]Type "o" to view the MBR data. It should show just one partition, of type 0xEE, that spans the entire disk. If this is *not* what you see, type "q" to quit without saving and post your gdisk session.
[*]Type "w" to save your changes to the disk.
[/list]


I wouldn't worry about the EFI System Partition (what the Boot Info Script calls a "System/Boot Partition"). Some disk utilities create EFI System Partitions automatically on GPT disks over a certain size, since they're required to boot from a disk on EFI-based systems. Although you're not booting from this disk, it's consuming so little space (200 MiB, or about 0.07% of the disk's capacity) that the risks involved in deleting it and recovering its space far outweigh the potential benefits of removing it.

---

### Post by dieselglock on 2011-03-31
> **srs5694 said:**
> Your /dev/sdc is a GUID Partition Table (GPT) disk with a [hybrid MBR.]("http://www.rodsbooks.com/gdisk/hybrid.html") Hybrid MBRs are ugly and dangerous hacks that are used mainly to enable Macs to dual-boot Windows. Since you're using Windows 7 and not booting from the disk, it will work fine as a legal (non-hybrid) GPT disk. Thus, I recommend getting rid of the hybrid MBR. You can do this by installing [GPT fdisk (gdisk and sgdisk)]("http://www.rodsbooks.com/gdisk/") from its [SourceForge download page]("https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/gdisk-binaries/") (do *not* use the version in the Ubuntu repositories, which is extremely old) and doing the following:


[LIST=1]
[*]Launch gdisk on the disk by typing "sudo gdisk /dev/sdc" at a Linux shell prompt.
[*]Type "p" to view the GPT partitions and verify you're working on the right disk. If you're not, exit by typing "q" and re-launch gdisk on the correct disk.
[*]Type "x" to enter the experts' menu.
[*]Type "o" to view the MBR data. You should see two partitions, one of type 0xEE and one of type 0x07.
[*]Type "n" to create a new protective MBR.
[*]Type "o" to view the MBR data. It should show just one partition, of type 0xEE, that spans the entire disk. If this is *not* what you see, type "q" to quit without saving and post your gdisk session.
[*]Type "w" to save your changes to the disk.
[/LIST]


I wouldn't worry about the EFI System Partition (what the Boot Info Script calls a "System/Boot Partition"). Some disk utilities create EFI System Partitions automatically on GPT disks over a certain size, since they're required to boot from a disk on EFI-based systems. Although you're not booting from this disk, it's consuming so little space (200 MiB, or about 0.07% of the disk's capacity) that the risks involved in deleting it and recovering its space far outweigh the potential benefits of removing it.


Thanks for replying. Not sure which version to download this is a 64 bit system. Sorry still new to the Linux thing. Also are these two separate programs.

---

### Post by srs5694 on 2011-03-31
> **dieselglock said:**
> Thanks for replying. Not sure which version to download this is a 64 bit system. Sorry still new to the Linux thing. Also are these two separate programs.

Get the amd64 .deb file.

---

### Post by dieselglock on 2011-03-31
> **srs5694 said:**
> Get the amd64 .deb file.

Sorry to be a pain I downloaded the file. When I clicked on the file I got this.

[COLOR=Red]Error: Dependency is not satisfiable: libpopt0 (>= 1.16)[/COLOR]

---

### Post by dieselglock on 2011-03-31
[COLOR=Red]Error: Dependency is not satisfiable: libpopt0 (>= 1.16)

[COLOR=Black]It seems like the version of this file is in the 10.10 version of Ubuntu and I have the 1.15 version in 10.04 [/COLOR]
[/COLOR]

---

### Post by srs5694 on 2011-03-31
Sorry about that. These dependency issues can be a real pain sometimes. I recommend you do one of four things:


[list]
[*]Try installing the previous version of gdisk (0.7.0) rather than the latest version (0.7.1). I can't promise it will work any better, but there's a good chance that it will.
[*]Install by typing "sudo dpkg --install --ignore-depends gdisk_0.7.1-1_amd64.deb". The popt library is used only by the sgdisk program, not by gdisk, so you'll still be able to use gdisk if you install this way (assuming no other problems), but sgdisk might not work. APT might also complain in the future, so you might need to uninstall gdisk once you're done with it to do future system updates.
[*]Download [PartedMagic](http://partedmagic.com) or [System Rescue CD,](http://www.sysresccd.org) boot with it, and use gdisk from there. Both these rescue CDs come with gdisk, but probably not the very latest version. The actions I'm suggesting you take don't require a particularly recent version, though.
[*]Build gdisk from source code. You can do this manually (via the .tgz file; consult the README file it contains) or by using the source RPM (via the .src.rpm file). Either approach will require installing various development tools -- GCC (including the g++ compiler) and various development libraries (libpopt-dev, uuid-dev, libicu-dev, and maybe something else I'm forgetting). The source RPM approach will require installing alien and all its dependencies. Building a source RPM is briefly described near the bottom of [this page.](http://www.rodsbooks.com/gdisk/download.html) Once you've got a binary RPM, you can use alien to convert it to a .deb file and install that.
[/list]

---

### Post by dieselglock on 2011-04-01
> **srs5694 said:**
> Sorry about that. These dependency issues can be a real pain sometimes. I recommend you do one of four things:


[LIST]
[*]Try installing the previous version of gdisk (0.7.0) rather than the latest version (0.7.1). I can't promise it will work any better, but there's a good chance that it will.
[*]Install by typing "sudo dpkg --install --ignore-depends gdisk_0.7.1-1_amd64.deb". The popt library is used only by the sgdisk program, not by gdisk, so you'll still be able to use gdisk if you install this way (assuming no other problems), but sgdisk might not work. APT might also complain in the future, so you might need to uninstall gdisk once you're done with it to do future system updates.
[*]Download [PartedMagic]("http://partedmagic.com") or [System Rescue CD,]("http://www.sysresccd.org") boot with it, and use gdisk from there. Both these rescue CDs come with gdisk, but probably not the very latest version. The actions I'm suggesting you take don't require a particularly recent version, though.
[*]Build gdisk from source code. You can do this manually (via the .tgz file; consult the README file it contains) or by using the source RPM (via the .src.rpm file). Either approach will require installing various development tools -- GCC (including the g++ compiler) and various development libraries (libpopt-dev, uuid-dev, libicu-dev, and maybe something else I'm forgetting). The source RPM approach will require installing alien and all its dependencies. Building a source RPM is briefly described near the bottom of [this page.]("http://www.rodsbooks.com/gdisk/download.html") Once you've got a binary RPM, you can use alien to convert it to a .deb file and install that.
[/LIST]


Hello again,

I can download and install the 0.6.14 version easily. I have run the terminal as per your instructions in the previous post right up till the point of actually completing the final command and it seems fine to that point. Should I proceed. 

Len

---

### Post by srs5694 on 2011-04-01
If everything seems fine as I've described, then yes, save your changes.

---

### Post by dieselglock on 2011-04-01
> **srs5694 said:**
> If everything seems fine as I've described, then yes, save your changes.

Ok everything seemed like it was working but I don't think its right. It looks like the whole partition is now Gpt.

Here is my fdisk out put i did reboot after the proceedure.

```
lawrence@lawrence-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2f2be63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb648a4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30434   244460081    7  HPFS/NTFS
/dev/sdb2           30435       60801   243922897    5  Extended
/dev/sdb5           30435       59565   233994726   83  Linux
/dev/sdb6           59566       60801     9928138+  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 320.1 GB, 320072933376 bytes
256 heads, 63 sectors/track, 38761 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38762   312571223+  ee  GPT
lawrence@lawrence-laptop:~$ 

```

---

### Post by dieselglock on 2011-04-01
More investigation reveals that the output of the gdisk is this now.

```
lawrence@lawrence-laptop:~$ sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sdc: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9E6EADDB-7721-4CAB-8376-E1F24DD0D10D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 8-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          411648       625141759   297.9 GiB   0700  UNTITLED

Command (? for help): x

Expert command (? for help): o
MBR disk identifier: 0x00000000
MBR partitions:
Number     Boot     Start (sector)     Length (sectors)    Type
   1                        1          625142447     0xEE

Disk size is 625142448 sectors (298.1 GiB)

Expert command (? for help): 

```

---

### Post by srs5694 on 2011-04-01
That's correct. The MBR partitions (shown by fdisk) are unimportant for GPT, unless it's a hybrid MBR disk -- and as I wrote earlier, hybrid MBRs are ugly and dangerous. That was the point of the exercise -- to rid yourself of the danger inherent in an unnecessary hybrid MBR.

---

### Post by dieselglock on 2011-04-01
> **srs5694 said:**
> That's correct. The MBR partitions (shown by fdisk) are unimportant for GPT, unless it's a hybrid MBR disk -- and as I wrote earlier, hybrid MBRs are ugly and dangerous. That was the point of the exercise -- to rid yourself of the danger inherent in an unnecessary hybrid MBR.

OK then thank you very much for all your help. It is very much appreciated.


Len

---

### Post by dieselglock on 2011-04-02
One thing I have noticed when I mount my internal storage drives is I get this error don't know if this has anything to do with what we did yesterday or not.


lawrence@lawrence-laptop:~$ sudo mount -a
Invalid locale, encoding to UTF-8
Invalid locale, encoding to UTF-8
lawrence@lawrence-laptop:~$

---

### Post by srs5694 on 2011-04-02
I doubt if the partitioning changes would cause a locale warning like that. My suspicion is that your NTFS partitions are set for a locale that Ubuntu doesn't recognize, but I'm not an expert on locales or their interactions with filesystems, so take that with a grain of salt. If you don't see any problems with filenames getting garbled, I wouldn't worry about it.

---

