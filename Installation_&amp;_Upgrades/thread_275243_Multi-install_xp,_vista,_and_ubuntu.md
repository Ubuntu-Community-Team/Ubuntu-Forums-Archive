---
title: "Multi-install xp, vista, and ubuntu"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by gzevspero on 2006-10-11
Hi, I'd like to install Windows XP, Vista and Ubuntu on the same machine. What would be the best way to partition the drive, and in what order should I install the OS's?
Thanks.

---

### Post by Kateikyoushi on 2006-10-11
Install XP first, second vista, finally ubuntu.
For partitions make 2 ntfs for the two windows, for ubuntu a swap and a / partition with whatever filesystem you dig, can't go wrong with ext3.
Ubuntu recognized my vista install and created a correct grub menu.

---

### Post by jpmrblood on 2006-10-11
Don't forget to have one fat32 (vfat) partition(s) as a data place so that XP/Vista can share data with your Ubuntu linux.

---

### Post by Kateikyoushi on 2006-10-11
He can use [this driver]("http://www.fs-driver.org/") as well for that.

---

### Post by gzevspero on 2006-10-11
So how many partitions in all?
So far I have:

ntfs for xp
ntfs for vista
ext3 for /
(ext3 for /home?)
ext3 for swap

and I'll use the driver to allow windows to see the ext3 partitions.
Is it possible to create 5 primary partitions, though? If not, should I create extended/logical ones, or just use 4 and do without  a separate partition for /home?

Thanks.

---

### Post by Kateikyoushi on 2006-10-11
There can be maximum 4 primary partitions on a disk.
You can put swap on logical partition.

---

### Post by Robor on 2006-10-11
> **gzevspero said:**
> So how many partitions in all?
So far I have:

ntfs for xp
ntfs for vista
ext3 for /
(ext3 for /home?)
ext3 for swap

and I'll use the driver to allow windows to see the ext3 partitions.
Is it possible to create 5 primary partitions, though? If not, should I create extended/logical ones, or just use 4 and do without  a separate partition for /home?

Thanks.
As Kateikyoushi said, you can only have 4 primaries.  Also, the partition used for swap will be formatted as linux-swap (I think that's the term).

---

