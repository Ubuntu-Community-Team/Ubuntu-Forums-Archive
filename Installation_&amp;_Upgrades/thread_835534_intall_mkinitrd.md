---
title: "intall mkinitrd"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by rraghav2 on 2008-06-20
I have problems installing mkinitrd on ubuntu 8.04

I tried apt-get install initrd-tools but I get this message - 
apt-get install initrd-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package initrd-tools

Tried it again after doing an apt-get update but not use. 

How do I install mkinitrd.

Thanks,
Raghu

---

### Post by avtolle on 2008-06-20
Not familiar with the app, but do you have the relevant repository enabled?

---

### Post by rraghav2 on 2008-06-20
Saw a couple of similar posts in the forum. Some people seem to have no problems with apt-get install initrd-tools.

---

### Post by rraghav2 on 2008-06-20
> **avtolle said:**
> Not familiar with the app, but do you have the relevant repository enabled?

How do I check this?

---

### Post by avtolle on 2008-06-20
I don't know in which repository it resides, but in Software Sources, be sure that all four of the sources are checked, check any of these not checked, reload and try again.

---

### Post by rraghav2 on 2008-06-20
> **avtolle said:**
> I don't know in which repository it resides, but in Software Sources, be sure that all four of the sources are checked, check any of these not checked, reload and try again.

I am not able to reload after updating the software sources, The reload seems to hang after trying to download package information for a while.

However, going back to the original problem, I was able to create an initrd image without mkinitrd (of package initrd-tools). To be more specific, "update-initramfs -c -k 12.6.25" command (of package initramfs-tools) seems to do the same job as "mkinitrd" which I was trying to install. 

Thanks

---

