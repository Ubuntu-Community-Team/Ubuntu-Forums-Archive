---
title: "Problems whit installation ubuntu 17.10"
date: 2017-10-11
forum: Installation &amp; Upgrades
---

### Post by qeris on 2017-10-11
Hi, so yesterday I decided to switch from windows to Linux completely. I am web developer(also a fresh one) and until now I used Linux only in VMs. I tried a few distros, but still I am pretty much big noob about it. 

I installed ubuntu and all was good until reboot. After that I can't boot back in. In bios I can see that under "Boot" there is no longer my SSD disk. There is only one option and that is my other HDD which I use only as "storage". During the installation I chose manual option for partitioning. I made "swap" of 20GB, "/" of 22GB and "home" the rest of... I assume this is where I did something wrong since I never before did manual partitioning. I chose it because I was afraid that if I don't it might get install on my "STORAGE" drive and I would lose my work etc... 

Also, I had some problems during installation whit my motherboard (Gigabyte: GA-970A-DS3P), none of the USB ports was working until I changed option in BIOS "IOMMU" to enabled and only my USB 2.0 ports ware working, 3.0 did not.

I can boot back in as "try ubuntu" and I can even take option to do fresh install again. Which might be the easy way? Maybe to unplug my "STORAGE" drive and just override current ubuntu installation whit new one and this time let him partition automatically? 

But I would like to know why this happened and how to fix it so in future I can make no such mistake.
Sorry if I misspelled something, English is not my native language. Thx

---

### Post by mörgæs on 2017-10-14
Hi, welcome to the fora. 

> **qeris said:**
> Maybe to unplug my "STORAGE" drive and just override current ubuntu installation whit new one and this time let him partition automatically? 



Yes, that would be a good idea. Keep the storage drive disconnected for some time while applying updates and testing that everything works fine.

---

