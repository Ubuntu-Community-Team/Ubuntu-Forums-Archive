---
title: "I need assistance removing windows install."
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by troseph on 2007-05-23
Hello! I am trying to remove my windows xp partitions (NTFS) through gparted (via the gparted live disc and inside my Ubuntu 7.04 install) and it will not delete, resize or format my windows partitions. Is there something I need to do? Or should I use my windows install disc to format them to raw? Any assistance would be greatly appreciated. This is my partitioning scheme as of now:

```
sda:
	v sda1		extended	49.99GiB *this can go*
	   sda5		ntfs		49.99GiB *this can go*
	     sda2	ntfs		136.31GiB *this can go*


sdb:
	  sdb1		ntfs		116.25GiB *this can go*
	  sdb2		ext3		67.21GiB *this is where my Ubuntu install is now*
	v sdb3		extended	2.84GiB
	   sdb5		linux-swap	2.84GiB
```

On sda I would like to whipe the drive and format it to 2x 93GB drives formated to ext3
On sdb I would like to allocate all space to  sdb2 if possible while keeping sdb2 intact.

This is my ideal scheme:

```
sda:
	sda1		ext3		93GiB *Media, MP3,Pictures, etc*
	sda2		ext3		93GiB *Backup & Storage*

sdb:
	sda2		ext3		183.46GiB *ubuntu install*
	sdax		linux-swap	2.84GiB
```

Any help I can get would be great!

---

### Post by scrooge_74 on 2007-05-23
Gparted should be able to do it, tell it to erase the file system on the partitions, then you can resize the blank space and change the file system

---

### Post by troseph on 2007-05-24
Ok. I managed to do it with the gparted live disk. Now I have a couple questions about setting mount points on my extra disks. What software would I use to set the mount points and managing to get them to mount on start up. I have one with the old mount point but it won't mount. (I think be cause I formatted it to a different FS)

---

### Post by Wim Sturkenboom on 2007-05-25
No Ubuntu at hand, but mounting is (usually) defined in the file */etc/fstab*; not sure if Ubuntu has changed that.

With regards to your original problem:
this problem might have occured  because the ntfs partition was already mounted by the Ubuntu live-CD. And you can not work on mounted partitions.

---

