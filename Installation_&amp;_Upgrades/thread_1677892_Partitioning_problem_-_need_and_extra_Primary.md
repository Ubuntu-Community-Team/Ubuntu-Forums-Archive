---
title: "Partitioning problem - need and extra Primary"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by Packwood1 on 2011-01-29
I have installed 10.10 on an Acer laptop.  The machine was supplied with 3 Primary partitions:

/dev/sda1 ntfs PQSERVICE 13GB
/dev/sda2 ntfs SYSTEM RESERVED 100MB
/dev/sda3 ntfs Win7 59GB

Now I have added the following for Ubuntu and all works fine

/dev/sda4 extended 20GB
   /dev/sda5 ext4 14GB
   /dev/sda6 linux-swap 6GB
unallocated unallocated 142GB

No you see I wanted to use the 142GB as an additional ntfs partition for storage and accessible from Ubuntu and Win7.  I cannot of course because I have used my four Primary partitions. So how can I re-organise things, or start again without disturbing Win7?

What are my options?

Thanks.

---

### Post by mikewhatever on 2011-01-29
So that storage partition would have to be logical instead of primary. Just expand the extended partition to cover the unallocated space, then create a logical partition inside it.

---

### Post by Packwood1 on 2011-01-29
Will I then be able to make it NTFS so that it is accessible from Win7?

Thanks.

---

### Post by srs5694 on 2011-01-29
Yes, Windows has no problems accessing logical partitions.

---

