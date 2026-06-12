---
title: "Adding additional harddrives to the system"
date: 2005-08-17
forum: Installation &amp; Upgrades
---

### Post by wabble on 2005-08-17
I have installed ubuntu with thumbs up on my first serial ata harddrive (sda).

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14405   115708131   83  Linux
/dev/sda2           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris


I have then tried adding my second drive (sdb) so that i can use it. With less luck.

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

*The controller is a sil3112 (silicon image) (just for controlling. No raid)

I have several harddrives i want to add but only focus on the sdb drive for now, and just maybe i will know what to do when done with this second one  :-) 

it's now a ext2 partition on it after i fdisked it. (or what ever i did). (would prefer ext3 but don't know how)

i have created the directory /media/harddisk (do i have to chmod this "directory/folder" with some command?) 

I want to configure fstab so that i can start using the harddrive with read/write permissions mounting on boot and sharing the disk on the samba  :-) (don't need help on the samba bit..)

here is my current fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Thanks for all the help i can get, because im stuck  ](*,)

PS. is there an easy way one click operation for converting an ntfs partition to ext3 or am i just daydreaming..?

---

### Post by AnythingBut on 2005-08-17
This should do the trick for fstab.

# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sdb1 /media/harddisk ext2 defaults 0 1
/dev/sda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

I don't know of any conversion scheme for NTFS.  But you can mount an NTFS partition.  I've only ever mounted them as read only with an fstab line like

/dev/hde1       /mnt/windows    ntfs    umask=0222      0       0

---

### Post by wabble on 2005-08-18
[QUOTE=AnythingBut]This should do the trick for fstab.

# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sdb1 /media/harddisk ext2 defaults 0 1
/dev/sda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

I don't know of any conversion scheme for NTFS.  But you can mount an NTFS partition.  I've only ever mounted them as read only with an fstab line like

/dev/hde1       /mnt/windows    ntfs    umask=0222      0       0[/QUOTE]

I got an error on hotplug during reboot using this (the linux partiotion bit). So the mount went bad, maybe because of my partitioning so will try again when i get back on that computer later on. 

Are there any known problems with the silicon image 3112 raid controller? (just using it as a controller).

Tank you for your quick reply :)

---

### Post by AnythingBut on 2005-08-18
[QUOTE=wabble]
Are there any known problems with the silicon image 3112 raid controller? (just using it as a controller).
[/QUOTE]

Not that I know of.  Why?  Do you think it's the problem?

---

### Post by wabble on 2005-08-18
[QUOTE=AnythingBut]Not that I know of.  Why?  Do you think it's the problem?[/QUOTE]

I was afraid of it (but the sda worked so it was not the logical thing..)

Today i mounted and set up sdb1 and a hda1 device as well. Worked the first time, to little coffe maybe yesturday..

Thank you for helping me out. It's a good feeling when you get something like this to work! Nice to learn.


I have one final question though.. 

The disks installed are to be used by the local users read/write and samba user/s. (as noted down in the next lines)

I did a "gksudo nautilus" and changed the permissions as follows.

- created a folder/directory on the disk
- set ownership and file group to user on local machine
- enabled sticky read/write/execute (1700)

I am wondering what the correct permissions (and owner/file group) settings for this kind of setup is. (Samba is set to use 700 but i havent set up the share for these folders, yet), I am from the world of windows and want to do this "the right way" from the start when first moving 100% over to linux.

Is this something you maybe could help me out with also (the disk permissions/ovner part) or should i do a new thread? ;)

Again. Thanks for helping me out :)

---

### Post by AnythingBut on 2005-08-19
Sorry.  I don't use Samba much, so I can't help you much there.  The permissions you mention do, however, seem a little strange… especially the sticky bit part.  Directories are usually marked sticky when you want to allow different users to write to the directory but not allow them to mess with each other’s files.  A good example is the /tmp directory.

---

### Post by wabble on 2005-08-25
[QUOTE=AnythingBut]Sorry.  I don't use Samba much, so I can't help you much there.  The permissions you mention do, however, seem a little strange… especially the sticky bit part.  Directories are usually marked sticky when you want to allow different users to write to the directory but not allow them to mess with each other’s files.  A good example is the /tmp directory.[/QUOTE]

Got it all up and running now. With no sticky [-X 

Thanks for the help  :)

---

