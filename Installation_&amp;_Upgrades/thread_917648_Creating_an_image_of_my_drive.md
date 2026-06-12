---
title: "Creating an image of my drive"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by chrisrx on 2008-09-12
I want to create an image of my drive for backup purposes and as far as I know linux treats devices as files.
So am I right in thinking that to create an image of my drive I can use
```
cat /dev/sda1 > image.img
```
or possibly
```
cp /dev/sda1 image.img
```
Which should then create an image which can be properly mounted with
```
mount -o loop
```

Am I right in thinking this?

---

### Post by forger on 2008-09-12
You must be looking to install partimage (Applications > Accessories > Terminal):
```
sudo apt-get install partimage
sudo partimage
```

> Description: backup partitions into a compressed image file
 Partition Image is a partition imaging utility. It has support for the
 following file systems:
  * Ext2/3, the linux standard
  * Reiser3, a journalised and powerful file system
  * FAT16/32, DOS and Windows file systems
  * HPFS, IBM OS/2 file system
  * JFS, journalised file system, from IBM, used on AIX
  * XFS, another journalised and efficient file system, from sgi, used on Irix
  * UFS (beta), Unix file system
  * HFS (beta), MacOS File system
  * NTFS (experimental), Windows NT, 2000 and XP
 Only used blocks are copied and stored into an image file.
 The image file can be compressed in the GZIP/BZIP2 formats to save disk space,
 and split into multiple files to be copied onto removable media (ZIP for
 example), burned on a CD-R, etc.
 .
 This makes it possible to save a full Linux/Windows system with a single
 operation. In case of a problem (virus, crash, error, etc.), you just have
 to restore, and after several minutes, your entire system is restored
 (boot, files, etc.), and fully working.
 .
 This is very useful when installing the same software on many machines: just
 install one of them, create an image, and restore the image on all other
 machines.
 .
  Homepage: [http://www.partimage.org](http://www.partimage.org)


edit: partimage can't work with mounted partitions, but **mondo** might be able to create a partition of a mounted partition:
```
sudo apt-get install mondo
sudo mondoarchive
```

---

### Post by prshah on 2008-09-12
> **chrisrx said:**
> I want to create an image of my drive for backup purposes 

Close, but not exactly. You need to use the "dd" command instead of cat. See [Exact duplicate of entire HDD]("http://ubuntuforums.org/showthread.php?t=874643") for exact details.

If you want to backup just a single partition, then partimage (as previously mentioned) off a live CD is the best solution.

---

### Post by chrisrx on 2008-09-12
If I use partimage can I then mount the image using```
mount -o loop
```

Because I want to be able to pick out files from my backup instead of restoring the whole partition.

---

### Post by prshah on 2008-09-12
> **chrisrx said:**
> If I use partimage can I then mount the image using```
mount -o loop
```

Because I want to be able to pick out files from my backup instead of restoring the whole partition.

Well, the default partimage image is compressed (gzip / bzip) so I don't think you can loopmount that.

Maybe you can loopmount an uncompressed image, but I've never tried it and cannot comment on it.

---

### Post by forger on 2008-09-13
**mondo** makes .iso backup files which you can either use as bootup disks to restore your partition or just mount them as you say and find out your files
Edit: Actually, I'm not sure if you can restore them by file. Maybe you could use the **tar** command to make backups of your files instead

---

