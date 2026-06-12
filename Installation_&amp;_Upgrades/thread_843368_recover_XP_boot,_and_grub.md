---
title: "recover XP boot, and grub"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by tinkerpad on 2008-06-28
Hello all,
I am using a Thinkpad R40.

Before I recently installed Ubuntu, my disk layout was the following:

1. 31 GB, primary, XP pro boot (C:\)
2.  5 GB, primary, data (ntfs) (D:\)
3.  3 GB, hidden XP recovery area (not a partition)

To install Ubuntu, I emptied the 5GB partition but did not delete it in XP.
Then I hibernated XP

In the installing process I deleted the 5GB partition which left me a 8 GB free space for installation since linux fdis does not "recognize" the hidden space as unusable. So now I have 7GB ubuntu and 1GB swap.

Everything worked fine, I could boot both systems in the boot menu. Windows still listed D:\ in the file explorer, I did not try to access thogh.

However once I shut down XP (no hibernation), and could not get it booted again (blue screen with "BOOT_PARTITION_MOUNT_FAIL", well i cannot remember exactly). In the recovery console started from the XP install CD nothing worked either (no chkdsk, fixboot), it always said something like "error with the partition". Still possible to mount in linux though.

Then I tried TestDisk, which said that the number of cylinders for in the partition table of the ntfs partition did not match with the actual size:
testdisk.log
```
Interface Advanced
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
heads/cylinder 240 (NTFS) != 255 (HD)

```

This seemed to correspond to the "hidden area".
Anyway, I made TestDisk write a new boot record on the partition:

```
Write new boot!

ntfs_boot_sector
 1 * HPFS - NTFS              0   1  1  3823 254 63   61432497
     NTFS, 31 GB / 29 GiB
NTFS at 0/1/1
NTFS at 0/1/1
filesystem size           61432497
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               3839531
clusters_per_mft_record   -10
clusters_per_index_record 1
Boot sector
Status: OK

```

That did't help anything.

So I wanted XP to write a new MBR and reinstall grub afterwards.
So did I from the XP recover console with a 

fixmbr

Well, this only made grub go to hell and I cannot boot anything. The ntfs partition is still not accessible from the XP recovery console.


What can i do to get the XP back to boot, and reinstall grub?

Thanks a lot for reading if you came along until here :)

Chris

BTW, a fdisk -lu gives:

```

ubuntu@ubuntu:/media/ZAPP/boot_bakcup/linux$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        61432560    76083839     7325640   83  Linux
/dev/sda3        76083840    78140159     1028160   82  Linux swap / Solaris

```

---

### Post by Victormd on 2008-06-28
Hypothesis: The problem lies on how you created your partitions and the fact that you hibernated XP instead of shutting it down. When you hibernate, XP keeps control of your ntfs partitions, but when you come back from hibernation, it does not try to mount again because it assumes that you didn't change anything. Then you installed ubuntu and removed the partition and this changed the drive configuration so when you shut down xp and restarted, it did not recognize your partitions and crashed.

The steps I would suggest are:
1. download gparted live CD and boot from it to fix your partitions (or use the ubuntu live CD and start gparted from there);
2. download supergrub CD boot from it to fix your boot menu and reinstall grub.

These should get you going again. However, if you don't want to download and go through the above steps, and considering that you have just installed ubuntu and probably haven't customized anything, you could try to reinstall ubuntu and when you reach the partition editor section of the install, choose "Manual" and you will be able to edit your partitions. delete and recreate your ubuntu partition and you should be good to go.

---

### Post by Victormd on 2008-06-28
> **tinkerpad said:**
> Well, this only made grub go to hell and I cannot boot anything. The ntfs partition is still not accessible from the XP recovery console.

This is the 3GB partition you merged with the 5GB backup partition to install ubuntu, that's why it can't access it.

---

### Post by tinkerpad on 2008-06-29
> **Victormd said:**
> 1. download gparted live CD and boot from it to fix your partitions (or use the ubuntu live CD and start gparted from there);

Thanks for your reponses.

How could I 'fix' the the NTFS partition with gparted?
When i show 'Information' of the partition it says:
"Unable to read contents of this file system!
Because of this some operations may be unavailable"

The partition can be mounted in a running linux though.

BTW I don't know what it could help to   reinstalling ubuntu since my ubuntu works fine, but maybe this was meant as alternative to reinstall grub (which i could actually do using the ubuntu live cd)

---

### Post by tinkerpad on 2008-06-29
> **Victormd said:**
> This is the 3GB partition you merged with the 5GB backup partition to install ubuntu, that's why it can't access it.

No, I think windows sees actually the right partition but cannot mount ("access") it, because if I boot from windows CD and choose installation it finds this 31GB partition as NTFS, but with 31GB free space.
Consequently, it does also not propose the "fix installation" option, which reinstalls the OS  but keeps all files and settings.

---

### Post by Pumalite on 2008-06-29
Those 31 GB as 'free space' are lost .You either format them ntfs or ext3.

---

### Post by tinkerpad on 2008-06-29
> **Pumalite said:**
> Those 31 GB as 'free space' are lost .You either format them ntfs or ext3.

why should they be lost? I am running ubuntu, the 31GB partition is mounted and I can access the files.

It was Windows which said on boot that it could not be mounted (UNMOUNTABLE_BOOT_DEVICE), before i made TestDisk "repair" it. 
Now it just gets stuck.

---

### Post by Pumalite on 2008-06-29
Then they are not 'free space'. If you want to see them from Windows; install this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by tinkerpad on 2008-06-29
From what I understand this link provides means to mount ext2 in Windows.

My problem is that I have a XP/ntfs partition (31GB), which can be mounted in linux, but is not bootable.
It seems that it got corrupted when installing Ubuntu while XP was hibernated.

Do you know something that could repair this NTFS partition?

---

### Post by Pumalite on 2008-06-29
rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by tinkerpad on 2008-06-30
Hi guys,
thanks for your help so far.
Meanwhile the situation is the following:

-I did a fixboot C: in the XP recovery console, although there was no way to "log on" to the ntfs partition
=> screwed the disk completely up. Only one big partition visible 

-I ran testdisk on the drive
=> could restore the ntfs and the linux partition, not swap though.
   Windows still not bootable of course

- reinstalled grub

-I went back to the recovery console, and this time I could log on to the XP partition! well, there isn't no progress at all... : )

-did a fixboot this partition
=>still cannot boot.

Linux fdisk says the following about my disk:   
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        4736     7325640   83  Linux

However, gparted sees only one 37GB FAT16 partition (with problems).
(BTW when I ran testdisk from the rescuecd, it would find a 37GB drive too and could not properly recover. It worked well though when booting the ubuntu live and running testdisk-static downloaded from the net)

I don't know if I stick with my plan to recover a fully bootable XP partition, for the time being I am fine with ubuntu which is running, and I would just like to have a consistent partition layout without having to backup and reinstall everything.

Any hints?

Another thing is that I am running linux without swap now, it did not complain so far, and it is running well - I have only 512MB of ram though...

thanks a lot!

---

### Post by Pumalite on 2008-06-30
Try Super Grub and see if you can boot and/or fix your XP:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

