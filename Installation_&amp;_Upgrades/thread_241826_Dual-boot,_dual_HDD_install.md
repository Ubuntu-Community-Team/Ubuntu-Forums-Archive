---
title: "Dual-boot, dual HDD install"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by jaywatkins on 2006-08-22
Here is a setup that I have never been able to get rolling properly.

I would like to install Windows and Ubuntu, but have each be on a separate hard disk drive (HDD).  Every time I attempt this, Ubuntu will not recognize the second drive and onlt wants to install on the extended partition.  If it does see the second drive, after the install neither OS will boot.

Any ideas?

Thanks

---

### Post by amohanty on 2006-08-23
So what happens if you do the following:
1. Primary master - windows on primary partition (leave primary slave unformatted)
2. Primary slave - ubuntu on another primary partition
3. grub on MBR on primary master.

Does that work??

AM

---

