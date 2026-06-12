---
title: "The partition is misaligned"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by changsheng on 2011-07-24
I had installed Ubuntu11.04, but when I checking disk, it warning that "The partition is misaligned by 1024 bytes. This may result in very poor performance. Repartitioning is suggested."
Partition was attached.
I want to known how should I repartition?
Thanks!

---

### Post by MinDokan on 2011-07-24
Same here. I'm in a dual boot system.

---

### Post by 2F4U on 2011-07-24
Repartitioning would mean that you delete the original partition and therefore loose all that contained in it. Do you really want to do that? Do you have performance problems that would justify such a step?

---

### Post by Quackers on 2011-07-24
Try installing gparted and see what that says about the partition alignment.

---

### Post by devansh.j2007 on 2011-07-24
Well if anyone is using windows then :D i probably seem to have the solution. and it is EASEUS Partition Master in windows it is a really great tool as it can let you resize the partitions so first you make a partition small then make it big again. I had same problem once i was lucky i had access to windows i used EASEUS Partition Master v5.5.1 Pro version. chk for any cracked version if u wish it stays with u forever!

---

### Post by changsheng on 2011-07-24
> **Quackers said:**
> Try installing gparted and see what that says about the partition alignment.

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00016bef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6375    51097600    7  HPFS/NTFS
/dev/sda3            6375       91202   681371649    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda5            6375       19506   105472000    7  HPFS/NTFS
/dev/sda6           19506       32254   102400000    7  HPFS/NTFS
/dev/sda7           32254       51759   156672000    7  HPFS/NTFS
/dev/sda8           51759       51789      244736   83  Linux
/dev/sda9           51789       52039     2000896   82  Linux swap / Solaris
/dev/sda10          52039       86688   278319104   83  Linux
/dev/sda11          86688       91202    36256768   83  Linux

What should I do?

---

### Post by Quackers on 2011-07-24
This is nothing to worry about
"Partition 1 does not end on cylinder boundary."

I'm not sure about this one
"Partition 3 does not start on physical sector boundary."

Extended partitions can get a bit iffy sometimes.

Are you experiencing any problems with booting or using your operating systems?

Other forum users will see this thread later in the day. I would wait for more expert advice on this.

---

### Post by changsheng on 2011-07-24
Installing software is very slow on windows&#65307;
Transfering files is very slow on windows and ubuntu.

---

