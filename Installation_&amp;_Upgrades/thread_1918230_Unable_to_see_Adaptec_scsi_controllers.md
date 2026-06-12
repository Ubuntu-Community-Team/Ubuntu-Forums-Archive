---
title: "Unable to see Adaptec scsi controllers"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by fjtesta on 2012-01-31
I have installed Lubuntu 11.10, with 3.0.0-15-generic kernel and am unable to see either my Adaptec 1502, or 1515 scsi controller cards.

I have tried:

/lib/modules/3.0.0-15-generic/kernel/drivers/scsi$ insmod aha152x.ko
insmod: error inserting 'aha152x.ko': -1 No such device

How do I add driver support for these controllers to the kernel?

Thanks.

---

