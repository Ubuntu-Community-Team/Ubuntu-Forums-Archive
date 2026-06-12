---
title: "Wubi, Vista and 8.04 LTS boot problems"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by SalishSea on 2010-02-14
I'm trying to install (or rather boot) a Wubi Ubuntu 8.04 LTS image from within a Vista Partition on a machine that is set up as follows: 

Before my involvement, the system had been partitioned into Vista and a non-Wubi Ubuntu 9.10 install; I can readily boot into either via Grub 1.96 I think).

I installed Ubuntu 8.04 within the VISTA partition, and that went fine, but when I reboot, the grub menu still only shows ubuntu 9.10 and Vista (ignoring memtest, XP, etc) and does not show the Ubuntu 8.04 LTS boot option.

When you select Vista, the machine boots normally and does not present 8.04 as a boot option.   

I assume that the issue is where does the option come to boot 8.04? From Grub? From the Windows boot loader? and once that is determined, how do I modify the relevant file to 
allow booting the 8.04 LTS O/S. 

I'd welcome suggestions before proceeding.

Thanks,

---

### Post by meierfra. on 2010-02-15
> I assume that the issue is where does the option come to boot 8.04? From Grub? From the Windows boot loader? 

It is supposed to come from the Vista boot loader. Since it doesn't something must have went wrong during the  Wubi installation.   It has also possible to boot Wubi   directly from the Grub menu, but this would have be set up manually. 

Since I'm not sure what went wrong during installation, could you follow these [instructions ]("http://bootinfoscript.sourceforge.net")to run the boot info script and post the RESULTS.txt.

---

