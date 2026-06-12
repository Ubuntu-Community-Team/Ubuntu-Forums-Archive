---
title: "Cannot Install new SATA Controller and Drive"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by manuzza on 2006-09-05
I bought a new SATA Controller and SATA Drive, but cannot get it to work.

I have loaded the sata_sil and sata_sil24 modules, and lspci sort of detects the controller (a Silicon Image 3112):

```
$ lspci
0000:02:03.0 RAID bus controller: Silicon Image, Inc. (Wrong ID): Unknown device 3112 (rev 02)
```

However that is as far as I get. The attached drive cannot be detected or seen. I am assuming the issue relates to the "error" shown by lspci.

How do I fix it and get the drive running?

Thanks.

Murray

---

