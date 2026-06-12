---
title: "Dead Partition Help?"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by Hello71 on 2008-09-21
Does anyone know of a (free) software to restore a busted NTFS partition? By busted I mean the partition cannot be read or written to. I suspect the header is damaged as when mounting the drive (forced NTFS) or looking at the drive through partitioning software it doesn't work. Also, this happened after I forced GParted to stop resizing the drive, which adds to the theory that the headers are broken. (I think.)

---

### Post by Pumalite on 2008-09-21
rescuecd(TestDisk):
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by Hello71 on 2008-09-21
Thanks. I was actually going to reply that I found TestDisk and repaired the partition. The thing is, TestDisk doesn't always do exactly what you want. For me, the first time I did it it repaired the partition but made all the partitions disappear in GParted. The second time, I did it properly and set it to make them show up. However, it moved the broken partition out of the extended partition. What? Oh well, at least it moved it to where I wanted it. And it fixed my problem.

---

### Post by Pumalite on 2008-09-21
Always read the documentation first.

---

