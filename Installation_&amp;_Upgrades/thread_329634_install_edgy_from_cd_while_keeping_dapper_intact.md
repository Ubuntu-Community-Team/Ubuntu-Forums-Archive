---
title: "install edgy from cd while keeping dapper intact?"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by quonsar on 2007-01-01
i have plenty of disk space so i can put edgy on its own partition. currently i have a dual boot system with a partition for windoze, a partition for dapper and a seperate partition for /home. what do i need to do? to look out for? will i be able to choose which system to boot from in grub? tia! :confused:

---

### Post by aysiu on 2007-01-01
Your gut is right on.

Install Edgy to the new partition, mount /home (which will be shared between Dapper and Edgy), and Edgy's Grub will install to the MBR and automatically add Windows and Dapper to the boot menu.

---

