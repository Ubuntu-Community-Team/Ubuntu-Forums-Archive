---
title: "Install and boot off WD Passport external USB drive"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by eddy_k560078 on 2007-04-17
I am trying to install ubuntu on a partition on a WD Passport external USB drive such that I can use it to boot my laptop which runs Windows XP Home. Despite having partitioned the external drive and isntalled ubuntu on the partition and having made sure grub is on the external drive, I get a grub error and am unable to boot off the hard disk. Any help is appreciated

---

### Post by robbyg on 2007-04-24
> **eddy_k560078 said:**
> I am trying to install ubuntu on a partition on a WD Passport external USB drive such that I can use it to boot my laptop which runs Windows XP Home. Despite having partitioned the external drive and isntalled ubuntu on the partition and having made sure grub is on the external drive, I get a grub error and am unable to boot off the hard disk. Any help is appreciated

DOwnload a win98 se boot disk image
burn iso to cd
boot laptop from cd
select boot with cd
at prompt type the following
fdisk /mbr
remove 98se boot disk and restart pc
evrything should be back as normal.

I havent managed to get ubuntu working on my external WD passport drive yet
hope you have more luck 2nd time around
Many Regards ...  RobbyG

---

