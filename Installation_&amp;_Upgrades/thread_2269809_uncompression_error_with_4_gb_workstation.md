---
title: "uncompression error with 4 gb workstation"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by PC-2011 on 2015-03-18
I have 3 workstations each with 4 gb of ram 160gb hard drives and Intel Core duo 2. I have installed ubuntu server on 2 of the workstations the install went fine but on one all I get is an uncompression error. I have looked online and every forms says it's when you have less then 512mb of ram but I have 4 gb. I have also tried reinstalling the os many times and replaced all the ram cards in the workstation with brand new ones and bios registers all four cards. Also on one of the other 2 work stations I can't find eth0 on the network interfaces it only shows lo and eth1 is eth1 the same as eth0?

---

### Post by dino99 on 2015-03-18
this often comes with low ram quality and/or badly inserted. With several banks it sometimes work by changing ram from a bank to an other.
Better to get a ramtest first. Then you can remove a ram stick to test and find which/where the issue is.
Hope you have bought that ram the same day to get the same model/make/serie number

note: glance at the mobo doc about ram. If it is using a custom frequency/voltage, then take attention to stability/temperature.

---

### Post by PC-2011 on 2015-03-18
Passed the memory test on the ubuntu disc. I started dell diagnostics in the bios so I will check on the result of it tomorrow. If that helps at all.

---

### Post by PC-2011 on 2015-03-19
Dell diagnostics said everything passes. So I took out every Ram stick cleaned each slot with air and put them back in and still passed. Is there anything else I could be missing?

---

### Post by PC-2011 on 2015-04-02
After changing every component of the workstation I found that it was a faulty motherboard.

---

