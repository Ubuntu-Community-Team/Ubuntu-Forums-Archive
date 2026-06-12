---
title: "While installing Ubuntu12.04 64Bit OS on mirror server,system prompted for ISCSI IP"
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by dhanesh1212 on 2013-09-20
Hi All,

While installing Ubuntu12.04 64Bit OS on mirror server,system prompted for ISCSI IP.

Unable to install Ubuntu 12.04 server on below hardware with RAID 1.

Adaptec AIC-9410W SAS/SATA Host Adapter, device 0000:04:02.0

Without raid we have installed ubuntu 12.04 server and enabled RAID 1 and its showing below details

**1. dmesg | grep aic (for checking Raid Controller Properties)**


[    1.649863] aic94xx: Adaptec aic94xx SAS/SATA driver version 1.0.3 loaded
[    1.649937] aic94xx 0000:04:02.0: PCI IRQ 16 -> rerouted to legacy IRQ 16
[    1.649942] aic94xx 0000:04:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.650566] aic94xx: found Adaptec AIC-9410W SAS/SATA Host Adapter, device 0000:04:02.0
[    1.650569] scsi2 : aic94xx
[    1.677170] aic94xx: Found sequencer Firmware version 1.1 (V17/10c6)
[    1.725693] aic94xx: device 0000:04:02.0: SAS addr 50030480002f8d20,  PCBA SN ORG, 8 phys, 8 enabled phys, flash present, BIOS build 1951


**2. fdisk -l**

Disk /dev/sda: 146.8 GB, 146815737856 bytes
255 heads, 63 sectors/track, 17849 cylinders, total 286749488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006cb5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2000895      999424   83  Linux
/dev/sda2         2000896     6000639     1999872   82  Linux swap / Solaris
/dev/sda3         6000640    46000127    19999744   83  Linux
/dev/sda4        46002174   286748671   120373249    5  Extended
/dev/sda5        46002176    66000895     9999360   83  Linux
/dev/sda6        66002944   286748671   110372864   83  Linux

Disk /dev/sdb: 146.8 GB, 146815737856 bytes
255 heads, 63 sectors/track, 17849 cylinders, total 286749488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006cb5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     2000895      999424   83  Linux
/dev/sdb2         2000896     6000639     1999872   82  Linux swap / Solaris
/dev/sdb3         6000640    46000127    19999744   83  Linux
/dev/sdb4        46002174   286748671   120373249    5  Extended
/dev/sdb5        46002176    66000895     9999360   83  Linux
/dev/sdb6        66002944   286748671   110372864   83  Linux

**3. df -HT**

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb3      ext3       21G  3.8G   16G  20% /
udev           devtmpfs  4.2G  4.1k  4.2G   1% /dev
tmpfs          tmpfs     1.7G  812k  1.7G   1% /run
none           tmpfs     5.3M     0  5.3M   0% /run/lock
none           tmpfs     4.2G  8.2k  4.2G   1% /run/shm
/dev/sdb1      ext3      1.1G   44M  913M   5% /boot
/dev/sda6      ext3      112G  399M  106G   1% /home
/dev/sdb5      ext3       11G  643M  9.0G   7% /var


Kindly advice us how to proceed further with raid 1 enabled.



Configuration details:

 [TABLE="width: 394"]
[TR]
[TD="align: left"] Intel Xeon E5410 2.33 Ghz 12 MB L2 cache[/TD]
[/TR]
[TR]
[TD="align: left"] Motherboard-intel chipset S5000P[/TD]
[/TR]
[TR]
[TD="align: left"] SAS Hot Swap Hard Disk Drive (2*146 GB, 15 RPM)[/TD]
[/TR]
[/TABLE]

Regards,
Dhanesh

---

### Post by dhanesh1212 on 2013-10-04
Hi Team,


Is this fake Raid?

Can some one point me about fake raid and normal hardware raid.


Regards,
Dhanesh

---

