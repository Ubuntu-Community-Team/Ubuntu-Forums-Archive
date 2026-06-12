---
title: "about LV partition"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by satimis on 2012-12-27
Hi all,

Ubuntu 12.04 desktop 64bit

I selected manual partioning and selecting logical on;

/boot
/root
swap

However after reboot I can't find LV;

$ sudo fdisk -l```

[sudo] password for satimis: 

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f463

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      976895      487424   83  Linux
/dev/sda2          978942  2930276351  1464648705    5  Extended
/dev/sda5          978944  2911133695  1455077376   83  Linux
/dev/sda6      2911135744  2930276351     9570304   82  Linux swap / Solaris

```
I tried 3 times with the same result.  I also tried not selecting /boot logical

Please help.  Whether HD exceeding 1TB can't partitioned as LV?

TIA

B.R.
satimis

---

### Post by darkod on 2012-12-27
The info you posted shows one primary (sda1) and two logical (sda5 and sda6) partitions on your disk.

Logical partitions are numbered starting from 5 and higher, even if not all four primary partitions are used.

When you say LV you mean logical partition, or logical volume? LV is usually short for Logical Volume as part of Logical Volume Management (LVM).

Logical partition is NOT a logical volume.

For LVM you install in a different way. Is this what you want to do?

Or you just got confused which partitions are logical in the partitions list?

---

### Post by satimis on 2012-12-27
> **darkod said:**
> The info you posted shows one primary (sda1) and two logical (sda5 and sda6) partitions on your disk.

Logical partitions are numbered starting from 5 and higher, even if not all four primary partitions are used.

When you say LV you mean logical partition, or logical volume? LV is usually short for Logical Volume as part of Logical Volume Management (LVM).

Logical partition is NOT a logical volume.

For LVM you install in a different way. Is this what you want to do?

Or you just got confused which partitions are logical in the partitions list?
Hi,

Thanks for your advice.  I'm a little bid confused.  I'm now on another Ubuntu box;

Ubuntu 12.04 desktop 64bit

$ sudo fdisk -l```

[sudo] password for satimis: 

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  3907028991  1953263617    5  Extended
/dev/sda5          501760  3907028991  1953263616   8e  Linux LVM

Disk /dev/mapper/ubuntu-root: 1991.7 GB, 1991682031616 bytes
255 heads, 63 sectors/track, 242141 cylinders, total 3890003968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 8317 MB, 8317304832 bytes
255 heads, 63 sectors/track, 1011 cylinders, total 16244736 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

```

The output is completely different showing /dev/mapper.  The command is the same "sudo fdisk -l"

satimis

---

### Post by darkod on 2012-12-27
Because this computer does have LVM installed. The first doesn't.

On the second computer, the whole sda5 partition is used as physical device for the LVM, and inside the LVM exists the Volume Group 'ubuntu' which has the Logical Volumes 'root' and 'swap_1'.

For the LVs the full device name is /dev/mapper/VGname-LVname, in this case /dev/mapper/ubuntu-root and /dev/mapper/ubuntu-swap_1.

---

### Post by satimis on 2012-12-27
> **darkod said:**
> Because this computer does have LVM installed. The first doesn't.
I'm now on the 1st PC.

Both PCs are newly installed, basic installation.  The 2nd PC was installed about 3 days ago.  I can't resolve why lvm2 is NOT installed on this PC.

Install lvm2 but situation remains unchanged.

$ sudo fdisk -l```


Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f463

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      976895      487424   83  Linux
/dev/sda2          978942  2930276351  1464648705    5  Extended
/dev/sda5          978944  2911133695  1455077376   83  Linux
/dev/sda6      2911135744  2930276351     9570304   82  Linux swap / Solaris

```

Other advice noted and thanks

---

### Post by darkod on 2012-12-27
When you have non-LVM installation only installing the lvm2 package will NOT convert it to LVM installation. You will have to reinstall, that's easiest.

For LVM you need to use the alternate install cd. It has support for LVM. When you reach the partitioning step there will be an option like 'Guided use whole disk with LVM'. I guess that it what you used on the first computer.

On the second you seem to have used manual partitioning and created partitions for /boot, / and swap, but normal partitions, not LVM.

---

### Post by satimis on 2012-12-27
> **darkod said:**
> When you have non-LVM installation only installing the lvm2 package will NOT convert it to LVM installation. You will have to reinstall, that's easiest.

For LVM you need to use the alternate install cd. It has support for LVM. When you reach the partitioning step there will be an option like 'Guided use whole disk with LVM'. I guess that it what you used on the first computer.

On the second you seem to have used manual partitioning and created partitions for /boot, / and swap, but normal partitions, not LVM.
Hi Darkod,

On this computer, the newly installed Ubuntu 12.04, I haven't used the Alternative Install CD.  On another computer which I installed about 3 days I used Alternative Install CD.  I'll reinstall this computer with Alternative Install CD.

satimis

---

### Post by satimis on 2012-12-28
Hi darkod,

I have Ubutu 12.04 desktop 64bit reinstalled running Alternative Installer.

$ sudo fdisk -l```

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bf74f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   8e  Linux LVM
/dev/sda2          501758  2930276351  1464887297    5  Extended
/dev/sda5          501760  2930276351  1464887296   8e  Linux LVM

Disk /dev/mapper/LVM1.5D-root: 300.0 GB, 299997593600 bytes
255 heads, 63 sectors/track, 36472 cylinders, total 585932800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/LVM1.5D-root doesn't contain a valid partition table

Disk /dev/mapper/LVM1.5D-swap: 4999 MB, 4999610368 bytes
255 heads, 63 sectors/track, 607 cylinders, total 9764864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/LVM1.5D-swap doesn't contain a valid partition table

Disk /dev/mapper/LVM1.5D-data: 1195.0 GB, 1195045289984 bytes
255 heads, 63 sectors/track, 145289 cylinders, total 2334072832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/LVM1.5D-data doesn't contain a valid partition table

```

What does it mean;```

Disk /dev/mapper/LVM1.5D-data doesn't contain a valid partition table

``` ?

Edit
====
/data is owned by root.  Can I change its owner to satimis(myself) for convenience.  So that I can save working documents on it?

---

### Post by darkod on 2012-12-28
The message about the partition table is not important. fdisk can't look inside the LVM so it just says it can't find valid partition table for that device. That's normal.

You can give /data open permissions for all, that way your user and all other users can write to it.

On the other hand, if you want to give your user ownership, it was something like:
```
sudo chown satimis:satimis /data
```

---

### Post by satimis on 2012-12-28
> **darkod said:**
> The message about the partition table is not important. fdisk can't look inside the LVM so it just says it can't find valid partition table for that device. That's normal.

Noted.  Thanks


> 
You can give /data open permissions for all, that way your user and all other users can write to it.

On the other hand, if you want to give your user ownership, it was something like:
```
sudo chown satimis:satimis /data
```
OK

If there are several users whether add them to "satimis" group?  Assign each user with a password?

Thanks

---

### Post by darkod on 2012-12-28
Yeah, for several users they will all have to be part of the same group (it can be satimis or another group that you can create for that purpose), and you will assign the wanted group permissions on /data.

---

