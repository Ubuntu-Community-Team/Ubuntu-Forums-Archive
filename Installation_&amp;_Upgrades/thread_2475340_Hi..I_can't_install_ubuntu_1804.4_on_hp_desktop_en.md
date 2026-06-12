---
title: "Hi..I can't install ubuntu 1804.4 on hp desktop envy TE01-3xxx, not show partitions"
date: 2022-05-23
forum: Installation &amp; Upgrades
---

### Post by yperdomof on 2022-05-23
Hello everyone, I am trying to install ubuntu 1804.4 in hp envy and does not show the partitions on other occasions in laptops I have changed the mode to AHCI, but in bios setup I do not see the change option (Also don't see any Advanced options configuration)

  I already change the quick start of windows and nothing. 
Modify grub at startup by pressing and adding quiet splash **nvme_core.default_ps_max_latency_us=250** and nothing.

 I bought 2 laptops not compatible I have had q return and now HP envy also prevents me. 

Any help would come well. Nice day 

**HP ENVY Desktop PC TPE01-3000i**

---

### Post by tea for one on 2022-05-23
Please supply the specification of your PC?
e.g. If the PC is very new, you should try Ubuntu 22.04 rather than 18.04.

---

### Post by yperdomof on 2022-05-23
hello thanks for reply .i need to use ubuntu 18.04.4 Lts.


Processor    12th Gen Intel(R) Core(TM) i5-12400   2.50 GHz
Installed RAM    12.0 GB (11.7 GB usable)
System type    64-bit operating system, x64-based processor
sn530 nvme ssd 1tb

---

### Post by tea for one on 2022-05-23
> **yperdomof said:**
> hello thanks for reply .i need to use ubuntu 18.04.4 Lts.

In the first place, I would try Ubuntu 22.04 to see if your hardware is recognised.
If that is successful, you can then identify the kernel used.

What is the specific reason for 18.04.4?

---

### Post by yperdomof on 2022-05-23
ok i will try, i use that distro because pentalinux is fully 1804 compatible.

---

