---
title: "Unallocated and cylinder number issue"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by von Stalhein on 2010-11-01
My partition table misreports the sector number - as the table below states there are 312581808 sectors on the drive but the swap file ends at 312592769. This is causing gparted to report it as wholly unallocated. the drive is booting & operating fine (I think!).

```
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf66fc667

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    21029084    10514511   83  Linux
/dev/sdc2        21029085   300495824   139733370   83  Linux
/dev/sdc3       300495825   312592769     6048472+   f  W95 Ext'd (LBA)
/dev/sdc5       300495888   312592769     6048441   82  Linux swap / Solaris
```

Can anyone tell me how to "tell" the partition table it's correct size, or fix the sector number please?

---

### Post by coffeecat on 2010-11-01
I had virtually the same problem yesterday. [This link]("http://www.rodsbooks.com/missing-parts/index.html") has the answer and came to my rescue. You'll need to deal with the end sector for the extended partition sdc3 as well as the sdc5 swap partition.

---

### Post by srs5694 on 2010-11-01
I wrote the Web page to which coffeecat linked. It's virtually certain that the total number of sectors on the drive is being reported correctly and you've got a partition (two, technically; the extended partition and the swap partition) that are too large for the disk, as coffeecat suggests. Everything might seem to be working fine right now, but if your system ever started to need most of your swap space, it might hang or otherwise misbehave because it would be trying to access disk sectors that don't exist. Fortunately, deleting swap space isn't a big deal, although you might need to edit /etc/fstab to change the swap space's UUID value after you re-create it. Modifying the extended partition as described on my Web page can be a bit scary, but it shouldn't be too difficult if you take your time and pay attention to detail.

One further comment: I note that you've got no Windows partitions on the disk. If you don't intend to install Windows on it, you might consider converting it to [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) format. Once you delete the swap partition, you should be able to do this with [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) fairly easily. This conversion could actually be a little easier than repairing the MBR, since GPT fdisk does it automatically, and I don't know of any tools that will automatically repair oversized extended partitions. The downside is that you might need to re-install GRUB (although perhaps not, if GRUB is on the MBR of your /dev/sda).

Best of luck with it, however you choose to approach the problem.

---

### Post by von Stalhein on 2010-11-01
Fantastic you blokes, that's one of the things that I love about this OS - the ready community help when I bork it - thanks!!

I didn't give you all the info - I may be wrong but I'm not sure it's relevant to the issue with /dev/sdc/ but just in case here is the whole fdisk output: -

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x960c960c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   234436544   117218241    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3f79c20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   234436544   117210240    f  W95 Ext'd (LBA)
/dev/sdb5           16128   234436544   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf66fc667

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    21029084    10514511   83  Linux
/dev/sdc2        21029085   300495824   139733370   83  Linux
/dev/sdc3       300495825   312592769     6048472+   f  W95 Ext'd (LBA)
/dev/sdc5       300495888   312592769     6048441   82  Linux swap / Solaris

```

Thanks again.

And after following Rod's (srs5694)n00b friendly directions, gparted reports things as all good. fdisk output for dev/sdc/ :-
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    21029084    10514511   83  Linux
/dev/sdc2        21029085   300495824   139733370   83  Linux
/dev/sdc3       300495825   312581807     6042991+   f  W95 Ext'd (LBA)
/dev/sdc5       300495888   312581807     6042960   82  Linux swap / Solaris

```

---

### Post by coffeecat on 2010-11-02
> **srs5694 said:**
> I wrote the Web page to which coffeecat linked.

For which it's high time I thanked you, srs5694. I have learnt a lot from your posts and links. My need for your paper came after I had accidentally overwritten my sda partition table with random data. (Please don't ask. :oops:). Testdisk from a live Ubuntu CD performed magnificently but left me a few quirks to deal with.

Thanks once again.

---

### Post by srs5694 on 2010-11-02
> **coffeecat said:**
> For which it's high time I thanked you, srs5694. I have learnt a lot from your posts and links. My need for your paper came after I had accidentally overwritten my sda partition table with random data. (Please don't ask. :oops:). Testdisk from a live Ubuntu CD performed magnificently but left me a few quirks to deal with.

So TestDisk is definitely creating bogus extended partitions? If so, that's useful information, and it should definitely be reported to the TestDisk developers as a bug.

Also and FWIW, backing up your partition table is fairly easy. For MBR disks:

```

sudo dd if=/dev/sda of=sda.mbr bs=512 count=1
sudo sfdisk -d /dev/sda > sda.txt

```

The first command backs up the MBR of /dev/sda (change the device filename to back up another disk, of course), including both the primary partitions and the boot loader code. It doesn't back up your logical partitions, but they might reappear if you restore the MBR, depending on what damaged the partition table to require a restore operation. The second command backs up all the partitions, but not the boot loader code. Because the dd command can be dangerous if used incorrectly, it might be best to forego that command if you're comfortable restoring a boot loader. (If you reverse the if= and of= options, you'll *wipe out* your partitions rather than back them up!)

To restore, you'd use the reverse commands:

```

sudo dd if=sda.mbr of=/dev/sda
sfdisk /dev/sda < sda.txt

```

These commands won't work on the newer GPT disks, though, since they've got partition data at both the start and end of the disk, and both are required for a complete backup/restore. Also, sfdisk doesn't work with GPT. My GPT fdisk (gdisk and sgdisk) does do backups, though. This can be done via the "b" option on the gdisk main menu (and restored via "l" on the recovery & transformation menu), or via the following sfdisk commands to back up and restore:

```

sudo sgdisk --backup=sda.gpt /dev/sda
sudo sgdisk --load-backup=sda.gpt /dev/sda

```

These commands back up and restore to and from a file called sda.gpt. Note that the version of GPT fdisk included with Ubuntu is so old that it lacks the sgdisk utility. You'll need to download it from its [Sourceforge download page](http://sourceforge.net/projects/gptfdisk/files/) and install it manually to use it. (The "gdisk" package includes both the gdisk and sgdisk programs.)

In any event, whether you use MBR or GPT, a partition table backup is easy to make and it's cheap insurance against problems. Just be sure to store it on a removable medium -- you don't want to lose it when your partition table goes south!

---

### Post by coffeecat on 2010-11-02
> **srs5694 said:**
> So TestDisk is definitely creating bogus extended partitions? If so, that's useful information, and it should definitely be reported to the TestDisk developers as a bug.

I haven't got any hard data beyond the files I created with the help of your link showing  that the extended partition  extended beyond the last sector. The testdisk logs have gone the way of all live CD logs, so I have little documentation to offer for a bug report. However, when I'm feeling energetic and have a spare day, I'll setup a complex partition table with an extended partition on my currently unused no2 desktop machine, deliberately destroy the partition table and see what happens when I recreate it with testdisk, this time being careful to save all logs. If I get something useful, I'll pass it to the testdisk people.

> **srs5694 said:**
> In any event, whether you use MBR or GPT, a partition table backup is easy to make and it's cheap insurance against problems. Just be sure to store it on a removable medium -- you don't want to lose it when your partition table goes south!

Thanks for that. I'm meticulous about backing up personal files, but had never thought to backup a partition table. Until now, that is - stable doors and bolting horses and all that. Although, fortunately there was testdisk and your excellent paper to hand to catch the horse before it had done itself too much injury.

---

