---
title: "lvm2 ext4 resize"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by idlehands on 2010-02-02
I just added a second drive to my lvm2 pool.
The pool was originally a single drive with a ext4 filesystem

I've done the following:
```

pvcreate /dev/sdb
vgextend saturn /dev/sdb
lvextend -L+1.82TB /dev/saturn/titan

```
and now have this:
```

--- Volume group ---
  VG Name               saturn
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  7
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               3.64 TB
  PE Size               4.00 MB
  Total PE              953864
  Alloc PE / Size       948963 / 3.62 TB
  Free  PE / Size       4901 / 19.14 GB
  VG UUID               o1Lzrd-LtLH-wdzQ-Dcmh-WQXq-m9q0-RZj4JH

```

so since the vg size has grown but the  free size hasn't, I assume i have to do a resize still? what commands should i be searching for?

this is 9.10 server.

Thanks

---

