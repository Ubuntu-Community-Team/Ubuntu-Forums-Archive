---
title: "New system install"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by elite0083 on 2012-12-10
So I bought a brand new machine and built it. I was planning on dual booting so I installed windows first and then I popped the Ubuntu disk in. When it got past the initial screen a bunch of text came up and wouldn't let me go any further. Motherboard asus m4a89gtd pro USB 3.0 processor Amd fx 8320 ram Kingston hyperx ddr3 1600 MHz. Some notes I tried cd, USB and multiple Ubuntu including kubuntu and Ubuntu 12.04 12.10 and 10.04.
Thank you

---

### Post by Bucky Ball on 2012-12-10
You might try hitting F6 when you boot from the install disk and hit the 'Try Ubuntu' options. 

Hit F6 and you should be given some boot options. Try 'nomodset' then proceed with the install. 

What happened? Also, how many partitions do you already have on the drive? If you already have four primary partitions (the maximum), there is no room for Ubuntu. You will need to get rid of one, make an extended partition, and create logical drives inside that when you install/partition Ubuntu.

---

