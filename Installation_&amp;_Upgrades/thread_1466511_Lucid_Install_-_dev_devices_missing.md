---
title: "Lucid Install - /dev devices missing?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by doktorOblivion on 2010-04-30
I installed Lucid last night after having much trouble with Karmic.  In any case, it appears to be much better than 9.10 on my system.  One major problem I do see though is that not all devices show up under /dev.  This means I cannot mount them!  Any ideas?  Here is the parted information along with my /dev ls.

(parted) print partition                                                  
Model: ATA WDC WD2500KS-00M (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  52.4GB  52.4GB  primary  ntfs         boot
 2      160GB   250GB   90.0GB  primary  ext3


~$ ls /dev/sd*
/dev/sda  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb5  /dev/sdc  /dev/sdd  /dev/sde  /dev/sdf  /dev/sdf1

---

### Post by doktorOblivion on 2010-05-01
So my next question is, is this because the system is using ext4 and not ext3?  That is, are /proc/modules missing to support ext3 devices and that is the reason they are not recognized?

[FONT="Courier New"][COLOR="Blue"][SIZE="2"]:~$ sudo fdisk -l /dev/sda

Platte /dev/sda: 250.1 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spur, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x52a76317

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2           19458       30401    87907680   83  Linux

:~$ sudo mount -t ext3 /dev/sda2 d1
mount: Gerätedatei /dev/sda2 existiert nicht[/SIZE][/COLOR][/FONT]

---

### Post by Jose Catre-Vandis on 2010-05-01
Its not clear (to me) from what you have posted as to which devices you cannot access/mount? Are these additional internal HDDs, external HDDs, USB sticks, other?

There is an issue with thunar not automounting external USB HDDs and sticks. Is this the problem?

---

### Post by doktorOblivion on 2010-05-02
The problem is, there are ext3 devices as shown by fsck and parted that do NOT show up under the /dev dir.

**/dev/sda1** * 1 6374 51199123+ 7 HPFS/NTFS
**/dev/sda2** 19458 30401 87907680 83 Linux

When I try to mount one, it says it does not exist.

:~$ sudo **mount -t ext3 /dev/sda2 d1**
mount: device /dev/sda2 does not exist

When I ls the /dev dir for sd*, it only shows those top level devices I guess it thinks are important.

:~$ ls /dev/sd*
**/dev/sda  /dev/sdb  /dev/sdc  /dev/sdc1  /dev/sdc2  /dev/sdc5  /dev/sdd  /dev/sde**

I had thought that XUbuntu and its f/s subsystem would continue to report sub-devices for EVERY HDD, but apparently not.  Is this due to LVM or some other f/s upgrade?  Any way to get those devices gen'd?  They are there otherwise fsck and parted would not see them.

Thanks.

---

### Post by Jose Catre-Vandis on 2010-05-02
Your fdisk shows that on your sda HDD you have two partitions an NTFS ( @ 50GB) and a Linux (@ 85GB) with a gap between the two (Why?).

What other partitions were you expecting to find on your HDD?

Also if you are in /dev/sda2 your linux partition (e.g. running Linux/Ubuntu) you won't be able to mount it with that command as a) it is already mounted and b) you will have trouble mounting it on itself.

I have a mix of ntfs, ext4, and ext3 partition on my PC they all show, and it is odd that sda1 and sda2 are not showing with ls /dev/sd*

Also do you mean ext3 partitions and not ext3 devices?

---

### Post by doktorOblivion on 2010-05-03
So, here is the results of those missing file system.  They are they, just under /dev/mapper, instead of as HD SCSI drives in /dev.  Go figure.  Today, for some strange reason they just appeared all mounted as names using the UUID under /media.  E.g.

```
/dev/mapper/nvidia_ibdadbgd1 on /media/1814E10C14E0EE26 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/mapper/nvidia_ibdadbgd2 on /media/22aebe25-ce73-4281-b6a8-cd38720540a9 type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/mapper/nvidia_edibebag1 on /media/Anwendungen type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```

To me its still kind of a mystery, I would like to understand why this was implemented in such a obfuscatory way, but at least its working now.:confused:

---

