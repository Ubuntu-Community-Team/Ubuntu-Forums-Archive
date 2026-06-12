---
title: "Promise Ultra100 TX2 ... Hidden HPFS/NTFS"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2005-04-23
Hi,

I've installed Ubuntu at a friends computer. There are two ntfs drives that I can't acces. The ubuntu installer saw the drives but it didn't see that there were filesystems on them.

this information from fdisk -l is relevant :

```

Disk /dev/hde: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1       24792   199141708+  17  Hidden HPFS/NTFS

Disk /dev/hdf: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1       24792   199141708+  17  Hidden HPFS/NTFS

```

the relevant fstab part :
```

/dev/hde1       /mnt/ntfs1      ntfs    umask=0222      0       0
/dev/hdf1       /mnt/ntfs2      ntfs    umask=0222      0       0

```

sudo mount -a gives :

```

sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hde1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hdf1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmes | tail :

```


NTFS-fs error (device hde1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hde1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hde1): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device hdf1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hdf1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hdf1): ntfs_fill_super(): Not an NTFS volume.

```


there's a diskcontroller. This is the line of lspci :

```

0000:02:03.0 Unknown mass storage controller: Promise Technology, Inc. PDC20268 (Ultra100 TX2) (rev 02)

```

So how do I get this promise controller working ?

---

### Post by alastair on 2005-04-23
How was the original filesystem made on these disks? 
Why the type : Hidden HPFS/NTFS ?
Can you boot XP and check the partition table on them?

Normally, this would just be "HPFS/NTFS" (id 7).

You could try using fdisk to change the partition types to "7" - this should be safe. But be warned that no guarantee! So backup your data first if you try this.

---

### Post by ubuntu_demon on 2005-04-23
I've tried modprobbing pdc202xx-new
[http://www.linuxcompatible.org/cdetail9946.html](http://www.linuxcompatible.org/cdetail9946.html)

didn't have any effect when I tried mount -a

---

### Post by ubuntu_demon on 2005-04-23
[QUOTE=alastair]How was the original filesystem made on these disks? 
Why the type : Hidden HPFS/NTFS ?
Can you boot XP and check the partition table on them?

Normally, this would just be "HPFS/NTFS" (id 7).

You could try using fdisk to change the partition types to "7" - this should be safe. But be warned that no guarantee! So backup your data first if you try this.[/QUOTE]
 I can't boot them the pc in windows .. it's gonna be a server and there's no windows XP installed anymore.

I'm going to look into the id. thnx!

---

### Post by ubuntu_demon on 2005-04-23
$sudo parted /dev/hdf

$print

gives this result (same for f) :
```


Disk geometry for /dev/hdf: 0.000-194481,000 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0,031 194474,355  primary               hidden

```

So the filesystem is unknown and should be set to ntfs / id 7 if I understand correctly

---

