---
title: "AMD processor Booting  problem"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by nirmal.santhosh on 2008-04-11
I am having HP Pavillon tx 1000 z which is having AMD Turion 64 bit processor. I have downloaded the kubuntu-7.10 for AMD 64 and booted the laptop withthe live cd. It is booting and after that screen is black, can any one please suggest me how to over come this problem.
Advance Thanks!!!!!!!!!!!!!!.

---

### Post by warp99 on 2008-04-11
You can try using some boot options to load into the kernel string:

[https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29](https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29)

The howto on appending the kernel string and what the boot options are is available at the link above. I would try the kernel boot options acpi=off and irqpoll and maybe vga=xxx to continue the install

---

