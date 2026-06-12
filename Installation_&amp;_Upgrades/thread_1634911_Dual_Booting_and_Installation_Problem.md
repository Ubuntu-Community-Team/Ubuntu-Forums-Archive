---
title: "Dual Booting and Installation Problem"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by welley on 2010-12-01
I have a Windows 7 installed in my notebook. but when I try dual boot with ubuntu 10 becoming a problem. when booting from the live cd ubuntu for installation process the message appear "no drives found, aborting installation"

please help me

---

### Post by zvacet on 2010-12-03
First resize your Windows partition (if you didn´t done that before) and then use manual way to install Ubuntu.

---

### Post by sikander3786 on 2010-12-03
If you were unable to figure that out, post the output of following command while booting from an Ubuntu Live CD/USB.

Applications > Accessories > Terminal.

```
sudo fdisk -lu
```

We'll see if your partitions are read correctly and if they are not formatted Dynamic (SFS) in Windows 7 ;-)

---

