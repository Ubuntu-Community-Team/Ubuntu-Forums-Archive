---
title: "DMraid - Sil raid set - uses wrong signature"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by shadowplane676 on 2008-09-11
I have Kubuntu 8,04 installed on my desktop. I have two WD 160GB hard drives in a RAID 0 stripe on the SiL chipset (which works fine in Windoze). however, dmraid sees 1 of the 2 drives as having TWO signatures (sil and hpt45x) and uses the hpt45x instead of the correct sil signature. 

```
[root-12:08:12]:~# dmraid -r
/dev/sde: "sil" and "hpt45x" formats discovered (using hpt45x)!
/dev/sdf: sil, "sil_afaeagabcbde", stripe, ok, 312579712 sectors, data@ 0
/dev/sde: hpt45x, "hpt45x_SPARE", spare, ok, 312581797 sectors, data@ 0
0
```

i cant seem to find a way to make dmraid see /dev/sde correctly so i can mount the two NTFS partitions on the RAID stripe.

feel free to ask for readouts or more info

---

