---
title: "Installer dosen't show Partion tables?!"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by 22Ti on 2010-02-16
I am about to make a fresh install of ubuntu 9.10 on my 160gb hdd and keep my home directory. Here I also have Windows XP installed, the swap, home and root. All of these are done manually and given names such as 'sda1', 'sda5' ect.(I do see them in system monitor > file systems)
The problem is that the installer doesn't seem to show me these tables. I only get a 160gb big chunk. GParted will not show it either (but as root is running from their I guess it cant?). 

Can anybody help?

---

### Post by 22Ti on 2010-02-16
bump

---

### Post by darkod on 2010-02-16
Boot the live desktop of 9.10 (Try Ubuntu option) and open Gparted. It should show you all the partitions on the hdd.
Also, in terminal see what:

sudo fdisk -l

returns.
The installer can sometimes not recognize the hdd usually if there are raid settings on it. But if Gparted and fdisk from the live desktop also don't show it, that means another problem.

---

### Post by 22Ti on 2010-02-16
GParted on the live cd shows *sda* as 149gb unallocated  .

**sudo fdisk -l**
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ac6adf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         450     3614593+  12  Compaq diagnostics
/dev/sda2   *         451        3000    20482875    7  HPFS/NTFS
/dev/sda3            3001       19456   132182820    f  W95 Ext'd (LBA)
/dev/sda4            5551       19456   111699913+  83  Linux
/dev/sda5            3001        5488    19984797   83  Linux
/dev/sda6            5489        5550      497983+  82  Linux swap / Solaris

Disk /dev/sdb: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb7df0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291    5  Extended
/dev/sdb5               1        9733    78180259+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75ab1d98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

---

### Post by darkod on 2010-02-16
It seems that out of what ever reason, the partition table is not read by Gparted. So showing it as unallocated.
Sorry, I'm not expert enough to help with this, I might just mess it all up. You'll have to wait for someone else to jump in.
I think TestDisk can be used to sort this out, but I don't know how to use it in details.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by 22Ti on 2010-02-16
Thx anyway. 
I will try the alternate cd and see if that will recognize my partitions...

If anybody else has any ideas iam all open..

---

### Post by 22Ti on 2010-02-16
Update: The alternate cd installer showed the same as the live cd. :cry:

Don't really know what to do next?

---

