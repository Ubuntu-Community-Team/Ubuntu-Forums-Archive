---
title: "Install Ubuntu after Windows 7 - failure"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by manish m mulani on 2010-01-31
I left around 60 GB of space unallocated while installing windows 7. Now when I'm trying to install Ubuntu it shows that unallocated space as "partition unusable". 

Is there any limit on number of primary partitions(like 4) one can have on his hard disk.

coz in windows disk management, I see I've 4 partitions all being primary already.
1. OEM partition 196 MB
2. Recovery D: 15 GB NTFS
3. System Reserved 100 MB NTFS
4. C: 214.84 GB NTFS
( all primary along with the anallocated partition ).

Can anyone help me on this issue?

Thanks
Manish

---

### Post by Sef on 2010-01-31
You can only have 4 primary paritions.  However, you can make of of your primary paritions an extended (logical) partition.   Then you can have more partitions.

Windows should be on the first primary partition.

---

### Post by manish m mulani on 2010-01-31
So should I try extending the C: to the unallocated space?? Won't I be losing data on my C: ? And on extending, I 'll be able to see the unallocated partition as usable while installing ubuntu ?

Thanks
Manish

---

### Post by manish m mulani on 2010-01-31
actually I can extend my D: which is the recovery drive to the unallocated space then install ubuntu on this partition, which makes sense.

I'll try this and get back to u in case of any problems.

Thanks
Manish

---

