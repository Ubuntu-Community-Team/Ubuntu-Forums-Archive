---
title: "Cannot see the HD while installing server 10.04"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by conquer on 2010-08-03
I'm installing ubuntu server 10.04 on HP Proliant DL140 G3, but in the partition part, HD doesn't appear. 

two SATA disks are configured as RAID1, the card is HP Embedded SATA RAID, which came along with the server.

fdisk shows there're two disks, sda and sdb. 

Ubuntu website says HP DL140 is certified.

is it because lack of drives? 

any quick response is appreciated. thanks.

---

### Post by conquer on 2010-08-04
Is it because ubuntu server 10.04 doesn't support SATA RAID? Hope anyone can help with this ...

---

### Post by ronparent on 2010-08-04
I'm not familiar with your hardware. Is it a hardware raid or a MB base chipset software raid (most often referred to as 'fakeraid'? If not sure, try running following in terminal:

```
sudo dmraid -ay
```

If the response discloses no raid devices you probably have a hardware raid that requires it's own linux drivers. If it lists raid devices then you have fakeraid. If a fakeraid, then if you are installing with a desktop cd, you would have to run the install from a live cd session. A program called 'kpartx' is needed for the partitioning process during the install to see the raid drive you are trying to install to. Without it the install would fail. Simply use sysnaptics package manager to install it in the live cd session prior to running the install.

---

