---
title: "GRUB Error 16"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by Fatstink on 2005-12-06
After I get done installing Kubuntu I take out the CD to boot and then by grub loader says Loading... Error 16.  What does this mean and how do I fix it?

---

### Post by Zaventh on 2005-12-06
This is probably due to grub not detecting your partitions correctly. It happened to me. 

Try, when booting into the kernel, pressing a key to stop the autoboot. Then highlight your installed kernel (eg. "Ubuntu, kernel 2.6.12-10-386"). Press "E" I believe, then select the line with "root  (hd0,0)". That stands for the first drive and the first partition. Originally, Kubuntu set it up as (hd1,1) for me. Depending on the number of drives/partitions you maintained changing the numbers around to suit your environment.

---

