---
title: "memory detection failure"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by thebird on 2007-12-30
I installed command line ubuntu v7.10 from the alternate CD. Everything works except that it can't get the correct memory size during boot. It assumes 16Mbyte. Although I'm  running vsftpd without any known errors and can connect to the server.

Memtest reports the correct amount of ram (448MB) and passes all tests. 

I have tried to add "linux mem=exactmap mem=640k@0 mem=447M@1M" to menu.lst for Grub. The machine hangs during boot and show the registers and stack values. I also tested smaller memory values. 

How can I get use of all of my 448MB of RAM memory? Help ASAP!

---

