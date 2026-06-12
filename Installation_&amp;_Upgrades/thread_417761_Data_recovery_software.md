---
title: "Data recovery software"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by thegreenman on 2007-04-21
I spent hours searching for a freeware data recovery tool that worked for me when I accidentally formatted my windows XP NTFS partition installing Ubuntu. I am a noob, what can I say. :) 

Anyway, I found these tools Testdisk and Photorecovery which got me back 3 years worth of priceless photos movies of the first year of my baby's life. I thought I'd make a post here so they will be easier to find for someone else in need. (I'm including descriptions to aid searching.)

> [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") is OpenSource software and is licensed under the GNU Public License (GPL).

TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting your Partition Table). Partition table recovery using TestDisk is really easy. 

TestDisk can find lost partitions for all of these file systems:

    * BeFS ( BeOS )
    * BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
    * CramFS, Compressed File System
    * DOS/Windows FAT12, FAT16 and FAT32
    * HFS and HFS+, Hierarchical File System
    * JFS, IBM's Journaled File System
    * Linux Ext2 and Ext3
    * Linux Raid
          o RAID 1: mirroring
          o RAID 4: striped array with parity device
          o RAID 5: striped array with distributed parity information
          o RAID 6: striped array with distributed dual redundancy information 
    * Linux Swap (versions 1 and 2)
    * LVM and LVM2, Linux Logical Volume Manager
    * Mac partition map
    * Novell Storage Services NSS
    * NTFS ( Windows NT/2K/XP/2003/Vista )
    * ReiserFS 3.5, 3.6 and 4
    * Sun Solaris i386 disklabel
    * Unix File System UFS and UFS2 (Sun/BSD/...)
    * XFS, SGI's Journaled File System 






> Photorec is file data recovery software designed to recover lost files including video, documents and archives from Hard Disks and CDRom and lost pictures (thus, its 'Photo Recovery' name) from digital camera memory. PhotoRec ignores the filesystem and goes after the underlying data, so it will still work even if your media's filesystem has been severely damaged or re-formatted.

[PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") is free, this open source multi-platform application is distributed under GNU Public License. PhotoRec is a companion program to TestDisk, an app for recovering lost partitions on a wide variety of filesystems and making non-bootable disks bootable again. You can download them from this link.

For more safety, PhotoRec uses read-only access to handle the drive or memory support you are about to recover lost data from. Important: As soon as a pic or file is accidentally deleted, or you discover any missing, do NOT save any more pics or files to that memory device or hard disk drive; otherwise you may overwrite your lost data. This means that even using PhotoRec, you must not choose to write the recovered files to the same partition they were stored on. 

---

### Post by newlinux on 2007-05-03
Good stuff! Thanks.

---

### Post by albertjiang on 2007-05-05
I used testdisk to recover my data on fat32 file system, which is on the same hard disk with ubuntu6.06, however, my ubuntu disappeard after that. I only used testdisk to opearte my fat32.

May anybody offer any help? my email is: albert.w.jiang<at>gmail.com

Thanks.

---

### Post by MatthewACT on 2007-05-21
I'm running Ubuntu.  It's not the latest version because mine doesn't authenticate...  Ubuntu doesn't regognize the file type for one of the linux downloads, and cant even open the zip file for the other 2.  Con someone help?

---

### Post by cooljoe on 2007-09-17
In order to install testdisk just

```
sudo apt-get install testdisk
```

Should work just fine.  I used it to restore an ntfs partition, and it worked great ;D

---

### Post by az on 2007-10-15
> **cooljoe said:**
> In order to install testdisk just

```
sudo apt-get install testdisk
```

Should work just fine.  I used it to restore an ntfs partition, and it worked great ;D

If you need to recover your hard drive, but can't boot from it, you need to run testdisk from a live cd.  

Ubuntu-rescue-remix is a data recovery toolkit on a live cd.

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

You can download it here:
[http://ubuntu-rescue-remix.org/Download](http://ubuntu-rescue-remix.org/Download)


Testdisk can recover your partitions, but in case you run into trouble, you can use parted to fine-tune your partitions.  Parted also has a "rescue lost partitions" function that is very useful.

---

### Post by Kalifornia909 on 2007-10-19
will any of this software work for strictly ext2 file systems that decide to dump data

---

### Post by spamking2000 on 2007-10-19
First, thegreenman - THANK YOU SOOOOO MUCH FOR THAT POST!!!!

I was having similar trouble today. For whatever reason clonezilla killed off the partition table on my first hard drive and then errored out and left me in a shell.

I tried using gpart (not gparted) and then fdisk to set it back up, and it didn't work. Had to delete the partitions again!

One of the partitions had all my video captured from my video camera, so that was not something I was ready to lose!

Testdisk worked great and reset everything back to the way it should be!!!! Everything is working! I'm sooooooooooooooooooooooooooooooo relieved!!!!

To Kalifornia909 - that partition, for whatever reason (I'm not sure why) was set to ext2 when I first installed the drive. There were 2 others that were ext3, but yes... it did restore my ext2 partition and everything looks like its there and happy!

Thanks!!!!
spamking2000

---

### Post by razametal on 2007-11-30
I've deleted the compressed log files of squid located at  /var/log/squid/

Have you any idea about how can I recover it? I'm using EXT3 filesystem.

Any help of ideas will be very appreciated.


Regards,

---

### Post by frederik.nnaji on 2007-12-02
hi everybody,

i'm extremely happy to announce that i was able to successfully restore my ntfs, which just simply refused to mount anyway. even ntfsfix didn't move an inch, because my ntfs was allegedly invalid.

trying to mount the drive from gparted just rendered the following error message:
"unexpected clusters per mft record -128"

i went through some of the hints i found here:
[http://www.linux-ntfs.org/doku.php?id=ntfs-en]("http://www.linux-ntfs.org/doku.php?id=ntfs-en")
no help really... but very good information on how ntfs works and what an MFT is..

here i found out that i actually do have a healthy ntfs:
[http://www.linux-ntfs.org/doku.php?id=howto:hexedityourway]("http://www.linux-ntfs.org/doku.php?id=howto:hexedityourway")

then i proceeded to google once again.. found some ppl who spoke bad of testdisk, but i insisted to try it out for myself, because i personally love that software:

the hints looked reasonable, so i installed testdisk, started it and inside testdisk i went to 
Advanced > Boot > Backup BS

i actually found out, that ntfs writes it's boot sector in the first sector of the partition. and there is also a backup boot sector somewhere at the end of the partition..

testdisk repaired my disk for me, i could backup all my data safely and actually boot back into my (eeerhh) windoze without problem afterwards.

anybody lamenting about this ingenious application should think twice!

greetings and thanks to everyone involved in free software development and testing

---

### Post by Ptero-4 on 2007-12-06
Wow. All I can say is that this sw is a real godsend. My sister sent me recently a usb pen from one of her clients who wanted her to copy some stuff off her usb pen to his, long story short, his usb pen came DOA. Not even fsck would fix it. I tried photorec and it really salvaged everything there was in it. Even after my sister's windoze box declared it dead.

---

### Post by BLTicklemonster on 2007-12-07
Wow, no idea how to proceed here. I'm looking for some lost pictures, and I don't understand what I'm seeing well enough to use it. The pictures were deleted, and I'd just like to get them back again if I can.

NM, for magicrescue, I found this: [http://jbj.rapanden.dk/magicrescue/manpage.html](http://jbj.rapanden.dk/magicrescue/manpage.html) Getting tons of stuff now. Thanks!

---

### Post by Portable_Jim on 2008-06-19
Great to use to recover files from a flash disk.

---

