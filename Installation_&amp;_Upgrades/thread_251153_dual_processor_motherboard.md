---
title: "dual processor motherboard"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by mherring0209 on 2006-09-05
i have a MSI moboard with dual intel pIII 750 MHX processors.  After install ubuntu breezy and upgrade to dapper, i still cannot see both processors in the device list. and the hardware monitor shows only 1 cpu graph.  Any one know how to enable dual processor support.

---

### Post by amo-ej1 on 2006-09-05
Have you got a kernel with smp support installed ? Paste the output of the 'uname -a' command here.

---

### Post by mherring0209 on 2006-09-06
where or what repositories do i get the -smp kernel from?

---

### Post by MalcolmParsons on 2006-09-06
> **mherring0209 said:**
> where or what repositories do i get the -smp kernel from?
Using the standard ubuntu repositories:
sudo apt-get install linux-686-smp
or
sudo apt-get install linux-k7-smp

---

