---
title: "Remove Windows 8 from dual-boot system"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by lucacerone on 2013-02-21
Dear all,
I have decided to completely remove Windows 8 from my dualboot laptop. I also would like to remove the partition for the recovery since the occupy quite a lot of space.

Ideally I would like to end up with a system as if I installed Ubuntu (12.04 64 bit, don't know if it is important) using the
"use the whole disk" option during the installation.

Of course in principle I could do this, but I would prefer to avoid since I have a lot of files that need to work with and installed quite a lot of software and customized a lot of applications.

In order to make the system dual bootable I used the "Boot Repair" tool that resulted in the partition table listed below:
(as shown by)
```
sudo parted -l
```

```
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  525MB   524MB   ntfs            Basic data partition          hidden, diag
 2      525MB   840MB   315MB   fat32           EFI system partition          boot
 3      840MB   974MB   134MB                   Microsoft reserved partition  msftres
 4      974MB   487GB   486GB   ntfs            Basic data partition
 7      487GB   487GB   1049kB                                                bios_grub
 8      487GB   966GB   480GB   ext4
 9      966GB   975GB   8476MB  linux-swap(v1)
 5      975GB   999GB   24.2GB  ntfs            Basic data partition          hidden, diag
 6      999GB   1000GB  1074MB  fat32           Basic data partition          hidden, diag

```

How do I remove the partitions that do not belong to Ubuntu?
How can they be renamed so that the / is /dev/sda1 rather than sda8?
Also, since I have 8gb of RAM, shouldnt the swap partition be of a size of at least 16gb? If so how can I resize that as well?
Let me know if you need further information.
Thanks in advance,
Luca

---

### Post by oldfred on 2013-02-21
Out of a 1TB drive Windows and Windows recovery are really small. I would hesitate to uninstall at this time as some systems need Windows 8 for some secure boot issues.

But you can make Windows a lot smaller. NTFS partition prefer to have about 30% free so that becomes the limit on how small to make it.

Swap will probably never be used. You just about have to load every application and edit large videos to use that much. If you hibernate you need swap to match RAM in GiB (not GB). And you really do not want to use swap as hard drive is orders of magnatude slower than RAM.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by lucacerone on 2013-03-05
Thanks for your advice,
sorry if it took me some time to reply!
so you would just resize the partitition??

---

### Post by oldfred on 2013-03-05
Use Windows disk tools to shrink the NTFS partition and reboot so it can run chkdsk or make repairs due to resize.

Do both systems currently boot ok?

One advantage of gpt is that you can add partitions and not worry about primary and logical, so you can create another partition or move partitions. But move can be time consuming and may be a bit more risky as any power failue or interruption will corrupt data so have good backups.

---

