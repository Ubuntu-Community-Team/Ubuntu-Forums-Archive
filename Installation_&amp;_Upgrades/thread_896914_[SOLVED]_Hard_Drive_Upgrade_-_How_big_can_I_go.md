---
title: "[SOLVED] Hard Drive Upgrade - How big can I go?"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by bpdp on 2008-08-21
Hi All,
I'm new to linux and I have a small file server that I'm looking to upgrade the HD in. The server is a old converted PC with no documentation to speak of. I'm wondering if there is command that will tell me the max HD size that will be compatible with this system. below is some more info:

$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: SAMSUNG SV4002H
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: QP10
       serial: 0413J1FRA12829
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=55054103

Any help would be great. thanks.

*sorry I think I posted this in the wrong forum*

---

### Post by ilrudie on 2008-08-22
Max HD size (as far as I know) is more a function of file system than hardware.  I don't think there is a single hard drive made today that can max out ext3 (Ubuntu's standard file system).  I think the limit is something like 16TB for a single partition in ext3.

---

### Post by mordak13 on 2008-08-22
Imagine what a 16TB Harddrive would cost!??!?!? OUCH.

---

### Post by bpdp on 2008-08-25
Thanks everyone, so I should be good as long as the drive is an ATA, correct?

---

### Post by tamoneya on 2008-08-25
that drive uses ata 100 which corresponds to all the drives listed here: [http://www.newegg.com/Product/ProductList.aspx?Submit=Property&Subcategory=14&Description=&Type=&N=2010150014&srchInDesc=&MinPrice=&MaxPrice=&PropertyCodeValue=359%3A7789](http://www.newegg.com/Product/ProductList.aspx?Submit=Property&Subcategory=14&Description=&Type=&N=2010150014&srchInDesc=&MinPrice=&MaxPrice=&PropertyCodeValue=359%3A7789)

---

### Post by bpdp on 2008-08-25
Thank you everyone - very helpful

---

