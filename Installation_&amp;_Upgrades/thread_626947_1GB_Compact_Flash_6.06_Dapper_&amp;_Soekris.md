---
title: "1GB Compact Flash 6.06 Dapper &amp; Soekris"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by ervin23 on 2007-11-29
hi, 

I'm pxe booting dapper 6.06 to a Soekris 4501 (64MB RAM & 1GB Compact Flash card) ...  dhcp, tftp and the server install is running smoothly until I want to write the partitioning to the CF card .... 

I tried guided and manual partitioning .... same issue, which is:

**The attempt to mount a file system with type swap in IDE1 master,  |            | partition #5 (hda5) at none failed.        **      

Made tests on different CF card 1GB & 4GB and both SANDisk & IBM ... no difference. 

My manual partitions: 

200 MB           / 
100 MB           swap
350 MB           /usr
350 MB           /var  

 
Ideas?     8)

---

### Post by webdr on 2007-11-29
Try Jeos or Voyager

---

