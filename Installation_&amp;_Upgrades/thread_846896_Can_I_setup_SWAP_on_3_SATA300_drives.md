---
title: "Can I setup SWAP on 3 SATA300 drives?"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by can8dnSix on 2008-07-02
Odd question; I have 3 SATA300 drives. Would it make a difference to create three SWAP partitions on each of the drives if I'm going to dedicate them all to Ubuntu? Also was thinking of setting up a RAID with these disks. But main question is the SWAP. Thanks.

---

### Post by ibutho on 2008-07-02
It wouldn't make any difference as far as I know, but why would you want to split the swap space into 3? Even when multiple booting you can use just one swap space.

---

### Post by can8dnSix on 2008-07-02
The only reason would be, if the kernel was able to take advantage of multiple SWAP partitions and treat them as a "stripe" as it were. To reduce the bottle neck that can get created once I start using the SWAP partition. Typically this happens after I load about 2.5GB into RAM; the SWAP then loads about 1-2GB. I run virtualbox and install several Server 2003 (DC1), Exchange Server 2003, a CITRIX Server, and lastly a DNS/DHCP Server (DC2).
So I was just seeing if there might be an advantage to multiple SWAP partitions to reduce the said bottleneck at the hard drive.

---

### Post by ibutho on 2008-07-02
Apparently you can fine tune the performance of multiple swap partitions. Take a look at this article [here]("http://kbase.redhat.com/faq/FAQ_80_2506.shtm").

---

### Post by can8dnSix on 2008-07-02
Awesome, I was looking for something like that. Just amazing how I started looking into Filesystems too. Awesome... awesome, gotta read that up too. Let you know what happens. :)

---

