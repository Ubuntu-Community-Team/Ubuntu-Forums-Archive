---
title: "Partition question - Ubuntu on Vista laptop"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by te.ss on 2008-04-18
Hi, I have a laptop pre-installed with Vista and want to transfer Ubuntu (wubi installation) to a separate partition.  The disk size is 60GB.  Gparted shows the current partitions as follows:

unallocated                       1.0 mb 
/dev/sda1 ntfs                  16.0 mb    (EISA configuration per VISTA)
/dev/sda2 ntfs                    1.0 gb     (EISA configuration per VISTA)
/dev/sda3 ntfs (/boot, /host)  27.0 gb   Flag = boot
/dev/sda4 ntfs                    27.87 gb empty
unallocated                       1.56 mb

I want to use /dev/sda4 (ntfs) to have a primaty and a swap partitions but I don't know how to proceed safely (without a disaster).  If I format /sda4 to ext3 and shrinks it, I am not allowed to make a new partition to format it as swap.   

Will someone help me with this, please ?

---

### Post by mikewhatever on 2008-04-18
You can only have 4 primary partitions per HDD. I'd suggest making sda4 an extended partition, and then creating two logical ones for / and swap. You'll have to delete that partition entirely, then right click on the unallocated space, select 'new partition' option and make sure you create extended/logical partitions.

---

### Post by te.ss on 2008-04-18
Thanks mikewhatever,

Now I have an extended partition.  A step closer to where I want to go.

---

