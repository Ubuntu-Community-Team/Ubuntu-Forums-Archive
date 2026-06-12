---
title: "weird problem mounting second drive"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by littleman54321 on 2007-07-11
I think this is the right forum...if not I apologize. Anyway, I actually have 3 drives, an 80gig, 120gig, and a 300gig.

The 300gig is on a PCI IDE "Ultra ATA IDE Controller Card" by silicon image. Anyway, not worried with that one atm. System doesn't even see in i a fdisk -l

So onto the problem. The 80gig has the Ubuntu install on it. It seems to be fine, as I am running just fine, did some upgrades w/ the auto upgrader, etc. But the 120 drive doesn't want to mount. Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=63556a8a-4686-4e14-accc-5cad7ff0d545 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8c2ffe45-b10a-47c9-8b77-6348ee3a5065 none            swap    sw              0       0
/dev/sdb5	/media/120_Storage	auto	rw, user           0	   0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

And here is a fdisk -l

```

Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9732     3028252+   5  Extended
/dev/sda5            9356        9732     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       14946   120045712+   f  W95 Ext'd (LBA)
/dev/sdb5               2       14946   120045681    7  HPFS/NTFS

```

Now, I've run a few different versions of Ubuntu in the past, and I remember my drives being like hda, not sda. I think I glanced over a link to something explaining it, but was busy, and then lost it.

The "System" column on the 120gig drive looks weird to me also. I'm guessing that it's NTFS formatted? But wtf is the W95 Ext'd (LBA)?

Also, and I don't know if this is helpful or not, but when I right click on the 120gig drive (It shows up in Places -> Computer) and select "Mount Volume", I get this:

```
[mntent]:line 9 in /etc/fstab is bad
mount: can't find /media/120_Storage in /etc/fstab or /etc/mtab
```

I'm out of thoughts...so I ask you Guru's....what am I doing wrong?

Just tried something, if I change the fstab line to this:
```
/dev/sdb1	/media/120_Storage	auto	rw, user	0	0
```

I get this error when trying to access the drive:

```
matt@matt-desktop:~$ mount: wrong fs type, bad option, bad superblock on /dev/sdb5, missing codepage or other error In some cases useful info is found in syslog - try dmesg | tail or so
matt@matt-desktop:~$
```

---

### Post by littleman54321 on 2007-07-12
shameless bump!

---

### Post by offchance on 2007-07-13
I'm also curious about what the lba flag means. all the howto's just list the flags without explaining them!

---

### Post by merlinus on 2007-07-13
From what I can see, sdb1 is an extended windows partition, and sdb5 is formatted as ntfs.

So the line in /etc/fstab probably hould be changed to:

/dev/sdb5 /media/120_Storage ntfs defaults,locale=en_US.UTF-8 0 1

And if you want to be able to write to it from ubuntu, install ntfs-3g and ntfs-config.

-merlin

---

### Post by littleman54321 on 2007-07-14
> **merlinus said:**
> From what I can see, sdb1 is an extended windows partition, and sdb5 is formatted as ntfs.

So the line in /etc/fstab probably hould be changed to:

/dev/sdb5 /media/120_Storage ntfs defaults,locale=en_US.UTF-8 0 1

And if you want to be able to write to it from ubuntu, install ntfs-3g and ntfs-config.

-merlin

Thanks =D

---

