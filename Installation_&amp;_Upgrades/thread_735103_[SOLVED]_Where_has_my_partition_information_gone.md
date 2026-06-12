---
title: "[SOLVED] Where has my partition information gone?"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by Lars Skovbo on 2008-03-25
I have a hdd partitioned in 3 (...), one for windows, one for 7.10, and one for 8.04b. But when i want to install 8.04b the partition manager (in the installation process) tells me that my whole harddisk is unpartitioned. But its not, because I'm writing from 7.10 right now :D GParted tells me the same thing. Where has this partition table information gone? And how do i recover it, so that I can install 8.04b without having to reinstall the other OS'es as well?

---

### Post by confused57 on 2008-03-25
> **Lars Skovbo said:**
> I have a hdd partitioned in 3 (...), one for windows, one for 7.10, and one for 8.04b. But when i want to install 8.04b the partition manager (in the installation process) tells me that my whole harddisk is unpartitioned. But its not, because I'm writing from 7.10 right now :D GParted tells me the same thing. Where has this partition table information gone? And how do i recover it, so that I can install 8.04b without having to reinstall the other OS'es as well?
I've never used it but I think Parted can recover partition tables:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

If you opt to reinstall anyway, then Parted might be worth checking into.

---

### Post by Pumalite on 2008-03-25
You can also use TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by zvacet on 2008-03-25
@ **Lars Skovbo**


>  Where has this partition table information gone?

Nowhere.I had same problem ( if we can call it that name) with Gparted live Cd.Try with alternate CD.

---

### Post by Lars Skovbo on 2008-03-27
Thanks for the help

---

