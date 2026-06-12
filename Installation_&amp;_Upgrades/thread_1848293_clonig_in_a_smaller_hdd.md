---
title: "clonig in a smaller hdd"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by cris_1986 on 2011-09-22
hy,
i have installed ubuntu 10.04 64 bit in a 500gb hdd.
I want to clone the hdd on a new ssd 64 gb.
Clonezilla doesnt work, becouse the destination is smaller than the source.
How can i resolve?

---

### Post by sanderd17 on 2011-09-22
take a look at dd: [http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

---

### Post by cris_1986 on 2011-09-22
to work with dd i must use a live cd ?

---

### Post by haqking on 2011-09-22
> **cris_1986 said:**
> hy,
i have installed ubuntu 10.04 64 bit in a 500gb hdd.
I want to clone the hdd on a new ssd 64 gb.
Clonezilla doesnt work, becouse the destination is smaller than the source.
How can i resolve?

is it one big 500gb partition ?

resize to the used space and then clonezilla will do it.

---

### Post by sanderd17 on 2011-09-22
> **cris_1986 said:**
> to work with dd i must use a live cd ?

You must at least unmount the partitions you're working on. So if it's a partition you need to run your OS, you have to do it from a live CD.

But before you use dd, please read the manuals etc.

---

### Post by cris_1986 on 2011-09-22
I only have one partition on the whole disc. data on the partition is about 15 gb

---

### Post by haqking on 2011-09-22
> **cris_1986 said:**
> I only have one partition on the whole disc. data on the partition is about 15 gb

so resize to about 20 then, and then you can clone that using clonezilla

---

### Post by cris_1986 on 2011-09-22
I just tried it with virtual machines but Clonezilla is not cloning because the destination disk is too small

---

### Post by haqking on 2011-09-22
> **cris_1986 said:**
> I just tried it with virtual machines but Clonezilla is not cloning because the destination disk is too small

i repeat, resize your 500GB partition to a smaller one, then clone that partition.

You can clone it as an image, then clone the image to your new HDD

---

### Post by cris_1986 on 2011-09-22
I resize the partition (40gb), I saved to an external drive.
I unplugged the old drive (500gb), I turned on Clonezilla and I restored the image on the new disk ssd.
Clonezilla tells me that the disk is too small and crashes

---

### Post by haqking on 2011-09-22
> **cris_1986 said:**
> I resize the partition (40gb), I saved to an external drive.
I unplugged the old drive (500gb), I turned on Clonezilla and I restored the image on the new disk ssd.
Clonezilla tells me that the disk is too small and crashes

mmm thats weird, are you sure when you cloned you didnt clone the disk instead of the 40gb partition ?

---

### Post by cris_1986 on 2011-09-22
I redid the whole process. I even cloned the partition (not disk) and then I restored. Clonezilla crashes and says the partition is corrupt ..
Can I change my software?

---

### Post by haqking on 2011-09-22
> **cris_1986 said:**
> I redid the whole process. I even cloned the partition (not disk) and then I restored. Clonezilla crashes and says the partition is corrupt ..
Can I change my software?

change what software ?

I dont know whats happening, as long as the partition is under the size of the destination, and was cleanly dismounted...if not you can ask clonezilla to do an expert mode and choose the fsck option.

Then choose partition to clone (40gb) clones as a file to an ext hdd.  Then restore that image to the destination.

I do it all the time with various paritions and such like, i  am not not sure what is going on your end

---

### Post by YesWeCan on 2011-09-22
Would you post the output of this so it's clear what the partition layout is on your 500GB drive?
[COLOR="DarkSlateBlue"]sudo fdisk -lu[/COLOR]

---

### Post by cris_1986 on 2011-09-22
i m working with a virtual machine and 3 hdd:    sda is the smaller disk(destination), sdb in the larger disk (source), sdc is the NTFS archive
```

sudo fdisk -lu
Disco /dev/sda: 19.3 GB, 19327352832 byte
255 testine, 63 settori/tracce, 2349 cilindri, totale 37748736 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00094c12

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    37748735    18873344    5  Esteso
/dev/sda5            4096    37748735    18872320   83  Linux

Disco /dev/sdb: 26.8 GB, 26843545600 byte
255 testine, 63 settori/tracce, 3263 cilindri, totale 52428800 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00094c12

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    20482047    10240000   83  Linux
/dev/sdb2        50169854    52426751     1128449    5  Esteso
/dev/sdb5        50169856    52426751     1128448   82  Linux swap / Solaris

Disco /dev/sdc: 53.7 GB, 53687091200 byte
255 testine, 63 settori/tracce, 6527 cilindri, totale 104857600 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00098d9e

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   104857599    52427776    5  Esteso
/dev/sdc5            4096   104857599    52426752    7  HPFS/NTFS

```

---

### Post by YesWeCan on 2011-09-22
```
sudo fdisk -lu
Disco /dev/sda: 19.3 GB, 19327352832 byte
255 testine, 63 settori/tracce, 2349 cilindri, totale [COLOR="Blue"]37748736[/COLOR] settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00094c12

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    37748735    18873344    5  Esteso
/dev/sda5            4096    37748735    18872320   83  Linux

Disco /dev/sdb: 26.8 GB, 26843545600 byte
255 testine, 63 settori/tracce, 3263 cilindri, totale 52428800 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00094c12

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    20482047    10240000   83  Linux
/dev/sdb2        50169854    [COLOR="Red"]52426751[/COLOR]     1128449    5  Esteso
/dev/sdb5        50169856    [COLOR="Red"]52426751[/COLOR]     1128448   82  Linux swap / Solaris
```
To copy sdb to sda you'll need to make sure you shrink the partitions on sdb so that the end sector of the last partition is less than the total sectors on sda.
Or you could delete sdb5 and sdb2 and then clone sdb to sda.

To clone sdb to sda (using a live CD/USB):
[COLOR="DarkSlateBlue"]sudo dd if=/dev/sdb of=/dev/sda bs=64k conv=notrunc,noerror[/COLOR]

After using dd you should tell the kernel to re-read the destination disk partition table:
[COLOR="DarkSlateBlue"]sudo hdparm -z /dev/sda[/COLOR]

**Important:** when you clone a disk its partition UUIDs are also cloned. This will cause problems for  Grub if you have two disks connected with duplicated UUIDs. So before you try to boot off the clone make sure you disconnect the original drive.

If you want to use both the original and clone at the same time, you should change the UUIDs on one of them. Check the UUIDs using 'sudo blkid'. Change them (on extfs partitions) using 'sudo tune2fs -U random /dev/sdxy'. Changing the UUID of NTFS is more complicated. Changing UUIDs will then require a change to the affected fstab file and a Grub reinstall.

---

### Post by cris_1986 on 2011-09-22
ok.. This problem exists only for this virtual machine? clone disks when in reality it is likely that still has this problem?
sorry for bad english

---

### Post by YesWeCan on 2011-09-22
> **cris_1986 said:**
> ok.. This problem exists only for this virtual machine? clone disks when in reality it is likely that still has this problem?
sorry for bad english
Which problem do you mean? I think what I have said applies just the same to real drives.

---

### Post by perspectoff on 2011-09-22
+1 for dd over Clonezilla

+1 for using dd from a LiveCD (or while running an OS from a partition other than the one you're trying to clone/move/copy).

As long as my destination partition is at least as big as the total aggregated size of the actual files on the partition being transferred (not the size of the source partition, which usually has lots of empty unused space), I haven't had a problem. I have shrunk a 200 Gb partition that only had 40 Gb in files down to a 45 Gb partition (for archival on an external hard drive) using dd. In fact, I do that periodically for full backups (although it is not efficient for differential backups).

The biggest problem in cloning/moving/copying/resizing partitions is doing it to/from network-mounted partitions. That is a horror show (because of permissions problems and symbolic links being dropped).

In that instance, move/copy/clone the partition to an external hard drive (using dd) first, and then move it to the final location from the external hard drive.

---

### Post by YesWeCan on 2011-09-22
> **perspectoff said:**
> +1 for using dd from a LiveCD (or while running an OS from a partition other than the one you're trying to clone/move/copy).
Thanks, I forgot to mention that. Never dd "live" partitions or disks.

---

### Post by Drew Woodard on 2012-01-19
Some of the confusion here may be due to what I assume is a bug introduced into recent versions of Clonezilla.

I have been using Clonezilla rather heavily for the last couple years, what I usually do is set up a machine with a small 20GB partition, install the os, then make a clonezilla image.
Then when I set up a new machine I take that disk image, apply it to the drive of the new machine, boot off the Ubuntu live cd, and then use gparted to expand the partition to take up the entire drive, be it a 90GB SSD or a 500GB HD.

This has always worked fine until this last week when I switched to the new version:
2011-11-25 - alternative stable Oneiric based
and I started getting these "destination disk is too small!" errors

I switched back to a previous version:
2011-09-22 - alternative stable Natty based
and everything started working again.

So in summary:
[2011-09-22 - alternative stable Natty based]("http://sourceforge.net/projects/clonezilla/files/clonezilla_live_alternative/OldFiles/20110922-natty/") (GOOD)
2011-11-25 - alternative stable Oneiric based (BUGGY/BROKEN)

---

