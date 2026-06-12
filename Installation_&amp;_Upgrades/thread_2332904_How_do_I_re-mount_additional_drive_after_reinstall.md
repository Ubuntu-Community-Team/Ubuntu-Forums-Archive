---
title: "How do I re-mount additional drive after reinstall"
date: 2016-08-05
forum: Installation &amp; Upgrades
---

### Post by gerasmus on 2016-08-05
I have reinstalled Ubuntu, it works fine. 
Error when accessing additional drive after reinstall.
How do I mount an previous additional drive after Ubuntu reinstall ?
How do I list the current folders on the drive I'd like to mount so I that I can mount the correct path ?
I have downloaded 100's GB of my Steam library on my second drive (in /steam) and don't want to download all again from scratch.

I used non-standard names for the drive mapping. 
On my current Ubuntu installation created /media/gerasmus/SATA-500gb1 but this can also be renamed to standard /media/{username}/hdd

```
*********************
**fstab entry**:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=1028dde7-6a14-4049-8f0c-97d6c4e85460 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=6522-BE13  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=3c8886e5-9261-4a38-b7a6-5d32dbe966ae none            swap    sw              0       0

/dev/sdb1	/media/gerasmus/SATA-500Gb1    ext4    defaults    0    0


**********************

**Error displayed**:

Error mounting system-managed device /dev/sdb1: Command-line `mount "/media/gerasmus/SATA-500Gb1"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

**************************************
**gerasmus@UBSPEL1** ~ $ dmesg | tail

[30947.774151] EXT4-fs (sdb1): get root inode failed
[30947.774154] EXT4-fs (sdb1): mount failed
[43158.655294] EXT4-fs (sdb1): ext4_check_descriptors: Checksum for group 0 failed (24405!=24275)
[43158.655299] EXT4-fs (sdb1): group descriptors corrupted!
[45912.797526] EXT4-fs (sdb1): ext4_check_descriptors: Checksum for group 0 failed (24405!=24275)
[45912.797529] EXT4-fs (sdb1): group descriptors corrupted!
[47362.532822] EXT4-fs (sdb1): ext4_check_descriptors: Checksum for group 0 failed (24405!=24275)
[47362.532825] EXT4-fs (sdb1): group descriptors corrupted!
[47509.919726] EXT4-fs (sdb1): ext4_check_descriptors: Checksum for group 0 failed (24405!=24275)
[47509.919729] EXT4-fs (sdb1): group descriptors corrupted!

****************************

**gerasmus@UBSPEL1** ~ $ sudo fdisk -l

Waarschuwing: GPT (GUID-partitietabel) gevonden op '/dev/sda'!
Het programma 'fdisk' ondersteunt GPT niet.  Gebruik GNU 'parted'.


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 koppen, 63 sectoren/spoor, 31130 cilinders, totaal 500118192 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 4096 bytes
in-/uitvoergrootte (minimaal/optimaal): 4096 bytes / 4096 bytes
Schijf-ID: 0x00000000

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1   500118191   250059095+  ee  GPT
Partitie 1 begint niet op een fysieke sectorgrens.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x00005fc1

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1            2048   976773119   488385536   83  Linux
gerasmus@UBSPEL1 ~ $ 

**I would like to have**:
```
1. List the folders/directories created on the additional drive, 
2. Associate folder on additional drive  again. There must be a simple solution which I can't find, probably because I am using the wrong words or search phrase.

---

### Post by ajgreeny on 2016-08-05
Show us the output of command ```
sudo blkid -c /dev/null
``` and we can show you how to edit /etc/fstab and add a line to mount the disk/partition at boot.

---

### Post by oldfred on 2016-08-05
Did you try fsck?

Since sdb1, you can run from your install, just make sure it is not mounted.
       #e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Usually better to mount partitions with UUID, not device like /dev/sdb1.
Did you do a new mkdir on you mount point so that exists as the place to mount the partition?

---

### Post by wildmanne39 on 2016-08-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by gerasmus on 2016-08-06
> **ajgreeny said:**
> Show us the output of command ```
sudo blkid -c /dev/null
``` and we can show you how to edit /etc/fstab and add a line to mount the disk/partition at boot.

Thank you for your resonse, next time I will know which command to use. The issue is now resolved, reformatted and reinstalled again which is not what i wanted. Currently I'm in the process of re-downloading my Steam library for Linux again which is several 100's gigabytes worth. However I fear the day that the drive fail, or the day that I wish to replace/upgrade the drive.  Before I reinstalled, the addional drive was mounted and functioning well. I had created a directory /steam on the root of my additional drive. My objective was to remount the additonal drive again after reinstall of Ubuntu and to continue where I left off.

I couldn't find a step-by-step tutorial on "*How to re-mount additional drive in Linux Ubuntu after reinstall/system restore*".  If a tutorial existed I couldn't find it, maybe i didn't use the correct terms/word order in my search ? I spent hours searching and all I could find was to [recover GRUB]("https://www.google.com/search?q=recover+linux+partition+after+reinstall&client=firefox-b-ab&start=10&sa=N&biw=1436&bih=750&bav=on.2,or.r_cp.&bvm=bv.129391328,d.ZGg&ech=1&psi=U_GlV4XaL-aOgAakqojoDw.1470493009951.3&ei=U_GlV4XaL-aOgAakqojoDw&emsg=NCSR&noj=1&gfe_rd=cr"), boot loader. There must be thousands of people that have done this before.

---

### Post by oldfred on 2016-08-06
Just clicking on a partition with Nautilus will automount a partition.
If an internal drive you probably want to permanently mount with every reboot by adding a mount point and an entry into fstab.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You need your UUID and a name or mount point. I link folders into /home, so I do not want it shown a second time in Nautilus so I mount as /mnt/data. But if you want it in Nautilus munt in /media/whateveryouwant. You may also need to set or reset ownership & permissions if formatted to a Linux format. NTFS has defaults only.


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

