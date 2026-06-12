---
title: "upgrade to 14.04.1 delete some files"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by etienne.mon on 2014-08-28
Hi,

after upgrading from 14.04 to 14.04.1, I discover that all my pictures that where in the Pictures folder were deleted. How can I recover them ?

anyone has an idea
Etienne

---

### Post by kansasnoob on 2014-08-28
What method did you use to upgrade?

I assume you actually meant 12.04 to 14.04.1????

Really need to clarify what exactly you did.

---

### Post by etienne.mon on 2014-08-29
When I turn on my computer, I had the advice to upgrade my system to 14.04.1.
I just accept it.
I was in 14.04

---

### Post by kansasnoob on 2014-08-29
I'd think it would have been either 13.10 (Saucy) or 12.04 (Precise) to be offered a release upgrade to 14.04.1 (Trusty). The change from 14.04 to 14.04.1 is just a point release designation and you'd see no actual notification before applying that update. 

Regardless, performing a release upgrade via update manager should not have deleted any files that existed in your Home folder or any of it's sub-folders. So I'm guessing that the old Pictures folder is still there somewhere. Is this possibly an encrypted install?

Please post the output of the following commands so we can start to get some idea what's up:

```
df -H
```

```
sudo parted -l
```

```
cat /etc/fstab
```

```
sudo blkid -c /dev/null
```

---

### Post by etienne.mon on 2014-08-29
Just some more informations, the folder was about 40G. Of course it is not in the trash !
I look aroune by some commandes like "du -sh" but I did not find any other such a folder.

When I did this ungrade, I was sending some photos to  my "google +". And I also delete some photos and these photos are in the trash :)


```
emann@ANR:~$df -H
Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
/dev/sda1          242G    175G   56G  76% /
none               4,1k       0  4,1k   0% /sys/fs/cgroup
udev               2,1G    4,1k  2,1G   1% /dev
tmpfs              410M    1,5M  408M   1% /run
none               5,3M       0  5,3M   0% /run/lock
none               2,1G    201k  2,1G   1% /run/shm
none               105M     66k  105M   1% /run/user
```


```
emann@ANR:~$sudo parted -l
[sudo] password for emann: 
Modèle: ATA Hitachi HTS72502 (scsi)
Disque /dev/sda : 250GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos

Numéro  Début   Fin    Taille  Type      Système de fichiers  Fanions
 1      1049kB  246GB  246GB   primary   ext4                 démarrage
 2      246GB   250GB  4149MB  extended
 5      246GB   250GB  4149MB  logical   linux-swap(v1)
```

```
emann@ANR:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c653ec9e-eac0-42d1-9694-52005f4da28a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9f497735-c1ec-4bb8-87f9-badcbd7cf4cc none            swap    sw              0       0

```

```
emann@ANR:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="c653ec9e-eac0-42d1-9694-52005f4da28a" TYPE="ext4" 
/dev/sda5: UUID="9f497735-c1ec-4bb8-87f9-badcbd7cf4cc" TYPE="swap"
```

---

### Post by kansasnoob on 2014-08-29
That's all quite straight forward, sadly I've never used Google + so I'm really clueless.

---

### Post by Nistegmos on 2014-08-29
You might have a much easier time searching for files using CatFish.  It's available from the Ubuntu application menu under "Accessories".  After it loads, use the "update" command so that is starts searching using a more accurate index.  You will need to enter your password for the update to work.  After that, just type in the name of a file you are looking for, or just a partial name, such as a few letters of the name or part of the name.  This is very easy.  You can also specify if you want it to search in just a certain place.  

The busy sign is displayed at the bottom of the screen, and when it's done, you will see a huge sortable list of results if stuff is found.  

So for your pictures, type in the name or part of name of a picture that you know should exist.  Or if you can't remember any names at all, just type in .jpg or .png and wait a really long time for it to show ALL of the .jpg (JPEG) or .png (Portable Network Graphics) files on your system.  

Good luck.

---

### Post by kansasnoob on 2014-08-30
Have you had any luck yet?

Wish I could have been of at least a little help :redface:

---

### Post by etienne.mon on 2014-08-31
no, I did not find them...
I try also CatFish but I does not work
Now I am trying with owncould beacue I had install owoncloud on a rasberry pi with owncould to do a back up. For the moment, I did not succeed to get these files

---

### Post by kansasnoob on 2014-09-02
It may be possible to recover some or all using [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") or [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"), but it may also be possible to lose additional files!

I've used them with a fair level of success where an entire partition has been lost but I always begin by copying the existing partitions to an external drive just in case things get even worse, and I'm not proficient enough with them to offer any detailed advice - I always have to just muddle through the step-by-step guides I linked to above.

---

### Post by kansasnoob on 2014-09-02
Just thought to add, those apps are in the Ubuntu repos:

```
lance@lance-desktop:~$ apt-cache show testdisk
Package: testdisk
Priority: optional
Section: universe/admin
Installed-Size: 1269
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Jean-Michel Kelbert <kelbert@debian.org>
Architecture: i386
Version: 6.14-2
Depends: e2fslibs (>= 1.41.0), libc6 (>= 2.11), libjpeg8 (>= 8c), libncursesw5 (>= 5.6+20070908), libntfs-3g841, libtinfo5, libuuid1 (>= 2.16), zlib1g (>= 1:1.1.4)
Filename: pool/universe/t/testdisk/testdisk_6.14-2_i386.deb
Size: 547578
MD5sum: 31b81d658c38c9b0cfdd0982e472ef5f
SHA1: dba071a0d790fc6ba0286824ddceb7bebcbdeb15
SHA256: 09bbf723edafa2e985a2914fe8205f3955db993e3edf45610916663e5341c22b
Description-en: Partition scanner and disk recovery tool
 TestDisk checks the partition and boot sectors of your disks.
 It is very useful in recovering lost partitions.
 It works with :
  * DOS/Windows FAT12, FAT16 and FAT32
  * NTFS ( Windows NT/2K/XP )
  * Linux Ext2 and Ext3
  * BeFS ( BeOS )
  * BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
  * CramFS (Compressed File System)
  * HFS and HFS+, Hierarchical File System
  * JFS, IBM's Journaled File System
  * Linux Raid
  * Linux Swap (versions 1 and 2)
  * LVM and LVM2, Linux Logical Volume Manager
  * Netware NSS
  * ReiserFS 3.5 and 3.6
  * Sun Solaris i386 disklabel
  * UFS and UFS2 (Sun/BSD/...)
  * XFS, SGI's Journaled File System
 .
 PhotoRec is file data recovery software designed to recover
 lost pictures from digital camera memory or even Hard Disks.
 It has been extended to search also for non audio/video headers.
 It searches for following files and is able to undelete them:
  * Sun/NeXT audio data (.au)
  * RIFF audio/video (.avi/.wav)
  * BMP bitmap (.bmp)
  * bzip2 compressed data (.bz2)
  * Source code written in C (.c)
  * Canon Raw picture (.crw)
  * Canon catalog (.ctg)
  * FAT subdirectory
  * Microsoft Office Document (.doc)
  * Nikon dsc (.dsc)
  * HTML page (.html)
  * JPEG picture (.jpg)
  * MOV video (.mov)
  * MP3 audio (MPEG ADTS, layer III, v1) (.mp3)
  * Moving Picture Experts Group video (.mpg)
  * Minolta Raw picture (.mrw)
  * Olympus Raw Format picture (.orf)
  * Portable Document Format (.pdf)
  * Perl script (.pl)
  * Portable Network Graphics (.png)
  * Raw Fujifilm picture (.raf)
  * Contax picture (.raw)
  * Rollei picture (.rdc)
  * Rich Text Format (.rtf)
  * Shell script (.sh)
  * Tar archive (.tar )
  * Tag Image File Format (.tiff)
  * Microsoft ASF (.wma)
  * Sigma/Foveon X3 raw picture (.x3f)
  * zip archive (.zip)
Description-md5: 57eed94bd37bdf941fb0391250f2cfab
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

---

