---
title: "Can I save the newly installed image/OS to re-install or share with another computer?"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by tuproxy on 2007-12-15
Here is what I want to do. Install a full OS with programs and add-on's like MP3 support,VMware and other services.  I also want to get all the updates downloaded and installed, network interfaces, SAMBA and IPTables setup.

I don't want to do this on each PC, so isit possible to "Clone" this install and download it to another?

I also want to setup a PC as a router and be able to share the installation with others. Is this possible?  

I just did an install with Novell ZenWorks that downloaded via a linux server and installed an XP image on it. Can someone explain if this same type of thing is possible without Novell ZenWorks?

Thanks

---

### Post by Icehuck on 2007-12-16
> **tuproxy said:**
> Here is what I want to do. Install a full OS with programs and add-on's like MP3 support,VMware and other services.  I also want to get all the updates downloaded and installed, network interfaces, SAMBA and IPTables setup.

I don't want to do this on each PC, so isit possible to "Clone" this install and download it to another?

I also want to setup a PC as a router and be able to share the installation with others. Is this possible?  

I just did an install with Novell ZenWorks that downloaded via a linux server and installed an XP image on it. Can someone explain if this same type of thing is possible without Novell ZenWorks?

Thanks

What you are wanting to do is called creating an image. When you want to transfer that image to another machine just make sure you have the exact same hardware.  There is tons of software out there that can do this, and you shouldn't need ZenWorks for any of it.

---

### Post by tuproxy on 2007-12-16
how would I install the image to a new machine?  Can it be done on the network?

---

### Post by ian dobson on 2007-12-16
Hi,

I've used norton Ghost to clone harddisks for along time and it works very well, but it's a commercial product.

I think there's a free "clone" of it called G4L. I've never used it myself but it might do what you want.

Regards
Ian Dobson

---

### Post by Sef on 2007-12-16
Look at [Clonezilla]("http://gpartedclonz.tuxfamily.org/index.php") (GParted site.)  

From the [Gparted-Clonezilla]("http://gpartedclonz.tuxfamily.org/index.php") site:

> This is a multi-boot livecd booting off GRUB. It can load the last GParted-livecd or Clonezilla
to backup file system localy or through the network. Clonezilla supported ext2, ext3, reiserfs,
xfs, jfs of GNU/Linux, and FAT, NTFS file system.
UnlikePartimage or ntfsclone, which only for partitions. Clonezilla, containing some other programs,
can save and restore not only partitions, but also a whole disk.
Unlike G4U or G4L, in Clonezilla, if file system is supported, only used blocks in harddisk are
saved and restored. This increase the clone efficiency.
For unsupported file system, sector-to-sector copy is done by dd in Clonezilla.


---

