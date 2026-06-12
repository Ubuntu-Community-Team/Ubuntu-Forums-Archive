---
title: "How to backup/restore Ubuntu 9.10 server for repartitioning disks"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by jschweigl on 2010-02-07
Hi all,

I'm running Ubuntu 9.10 AMD64 Server on an Intel SS4200-EHW NAS barebone. There are 4 1.5 TB WD15EARS (those with 4K sector size) each containing a partition for boot, swap, root and data each. The partitions are grouped into RAID 1 across all four disks for everything but data, which is RAID 5.

I did too little investigation on 4k-sector drives before installing everything and want to repartition the drives now to place partitions on 4k boundaries. 

I could reinstall the whole box from scratch but would like to avoid that. My question is now: what is the best procedure to backup the whole system, repartition the drives and restore the system to exactly the same state as before?

Currently I'm taring everything into a big backup file, using 

```
tar -cpf /1tb/backup.tar --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/storage/share/video --exclude=/storage/share/books --exclude=/storage/share/installers --exclude=/1tb --exclude=/320gb /
```

The basic idea is to get a live system on thumbdrive or USB disk up and running, *fdisk -S 56* the four internal drives, recreate the raid arrays, restore the backup from tar and reboot.

As I've never done something similar before I'm not sure if something like the above would work and what the exact procedure is. The NAS hasn't got video hardware, so anything needs to be done via tty (which was fine during initial install).

Has anyone got advice for me?

Thanks

---

