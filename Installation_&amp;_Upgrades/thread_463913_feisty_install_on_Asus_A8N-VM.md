---
title: "feisty install on Asus A8N-VM"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by trhendr on 2007-06-04
I tried about 2 1/2 weeks to install feisty onto a Asus A8N-VM and couldn't.  I had the latest "beta" bios, and no matter what I tried, it wouldn't work.

Well I finally found success.  I was using a brand new Maxtor 300 GB IDE disk drive, and I switched to a WD 160MB SATA drive, and the whole thing installed perfectly.

I wonder if the feisty install was making some sort of partitioning error on the 300GB drive which caused it to fail.  The symptoms were that it would be in the final 90-something percent completed part of the install when it was configuring hardware, and it would reboot the system or lock up (the num lock led would be flashing).

I moved the 300GB Maxtor to a Asus M2NPV-VM motherboard and it also installed just fine.  Without issue, so there was definately some interaction between the A8N-VM and the 300GB drive which caused an issue.

In both cases, I was letting feisty do a guided install using the whole disk.

-Tom-

---

