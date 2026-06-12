---
title: "Messed up Ubuntu installation"
date: 2017-06-26
forum: Installation &amp; Upgrades
---

### Post by yueor on 2017-06-26
I had windows 10 and debian installed on my laptop, and I intended to replace debian with Ubuntu. I was careless and and selected the "erase disk and install ubuntu" option by mistake. Although I didn't hit go on the "write changes to the disc" window that pops after it. I don't understand if I have wiped out both my windows and debian or just made them inaccessible. gparted shows: sda1: size 512mb, used 1.02mb sda2: size 488mb, used 17.66mb sda3: size 930mb, no data for used Wtf have I done and how can I fix it?

---

### Post by oldfred on 2017-06-27
I do not know exact erase & reinstall procedure. But expect first thing it does is erase & create new partitions to install into. If you stopped in time, you may still be able to recover old partitions and some or most of old data.
Usually testdisk works, but it uses the very old CHS - cylinder, heads, sectors, where all drives are LBA or large block allocation and use sectors.
If you know or have an idea of partitions starts & sizes, you may be able to use parted rescue or gparted.

Of course best to just reinstall & restore from backups.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL][http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 

Major Windows updates often "forget" to write a Linux partition. 
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331) 
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462) 






[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

### Post by johndough2 on 2017-06-29
Hi

I suggest making a recovery / media using clonezilla.  [http://clonezilla.org/](http://clonezilla.org/)

Relevant section below, but read the entire page before committing.

Based on [Partclone]("http://partclone.org") (default), [ Partimage]("http://www.partimage.org") (optional), [ntfsclone]("http://www.linux-ntfs.org/")  (optional), or dd to image or clone a partition. However, Clonezilla,  containing some other programs, can save and restore not only  partitions, but also a whole disk.

I would suggest trying to repair/recover first, if not try and get your windows partitions back, even if you need to use the second part of the HDD, but a USB stick may suffice.

---

