---
title: "What kind of filesystems should I use?"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by Vasant56 on 2006-12-02
Hi,
I'm installing ubuntu, and I was wondering what kind of filesystems I should use. I use NTFS for windows. I thought I could use FAT32 to install ubuntu on, but it's saying I should use ext3. What is ext3, and should I go ahead and make my 10gig root point to that?

---

### Post by bulldog on 2006-12-02
Yes you need ext3 file system.
Don't forget to make a swap for about 1GB,similar as the windows pagefile.

10GB for a / root partition is enough for a decent try out.

You can make a fat32 partition to exchange data between windows and ubuntu,they both are capable of read and write to a fat32 file system.

---

### Post by wpshooter on 2006-12-02
Make your partitions as follows:

/root - ext3
/home - ext3
/swap - linux swap

and if you want partition to use between windows and Ubuntu
make a FAT32 partition.

---

### Post by Sef on 2006-12-03
Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") for info on how to dual boot.

---

### Post by Don_DiZzLe on 2006-12-03
Is the swap partition really necessary, since I always turn swapping off?

---

### Post by wpshooter on 2006-12-03
> **Don_DiZzLe said:**
> Is the swap partition really necessary, since I always turn swapping off?

Are you taking about M/S windows or Ubuntu/Linux ?

---

