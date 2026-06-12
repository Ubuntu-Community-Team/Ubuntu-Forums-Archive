---
title: "Unable to boot windows 8.1 after Ubuntu install"
date: 2014-03-30
forum: Installation &amp; Upgrades
---

### Post by vsavlidis95 on 2014-03-30
I installed Ubuntu 13.10 this afternoon and weird things started to happen to my PC. I cannot boot from Windows 8.1 but I can boot from Ubuntu through GRUB. I tried Boot Repair and I got the following results. [http://paste.ubuntu.com/7182440/](http://paste.ubuntu.com/7182440/). Can anyone help me boot from Windows again? 

Thanks

---

### Post by vsavlidis95 on 2014-03-30
Any help would be appreciated

---

### Post by Mark Phelps on 2014-03-30
The routine waiting time for bumping a thread is 24 hours, not one hour.  This is a worldwide forum and the best help could very well be from someone 12 timezones away.  Getting impatient and bumping is only going to discourage folks from helping.

---

### Post by slooksterpsv on 2014-03-30
There's no Windows 8/8.1 partition, you have a missing 700GB block:
```

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
1      1049kB  420MB   419MB   ntfs         Basic data partition          hidden, diag
2      420MB   693MB   273MB   fat32        EFI system partition          boot
3      693MB   827MB   134MB                Microsoft reserved partition  msftres
4      827MB   251GB   250GB   ext4         Basic data partition          msftdata
5      966GB   966GB   472MB   ntfs                                       hidden, diag
6      966GB   967GB   408MB   ntfs                                       hidden, diag
7      967GB   1000GB  33.7GB  ntfs         Basic data partition          hidden, msftdata

```
285GB of data. There's 2 things we can try:

How did you install Ubuntu exactly? The way the partitions are setup it looks like you installed over Windows 8 instead of partitioning and installing in the blank space. The reason I say this is cause if you look at the partitions 4 starts on 827 where 3 ends on 827,  so I hope you have recovery media. Otherwise we can try the following but it'll be rare if it fixes it.



EDIT: I see that efibootmgr was run in the boot-repair, but that partition is missing. Followthe next step.

2. To run testdisk boot from the Ubuntu DVD/USB you made. Run live mode only and connect to the internet. Open a terminal and type the following:
```

pkexec apt-get update
pkexec apt-get install testdisk
pkexec testdisk

```

Get online and post back here if you're running testdisk.

---

