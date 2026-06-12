---
title: "Upgrade from Kernal 2.6.32-27 to 32.28 excessive memory usage"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by usalabs on 2011-01-26
Earlier I powered on my PC and was greeted with updates available, so I updated, which in turn also updated the kernel to 2.6.32-28, and when the update was complete, it said I needed a reboot, which I then performed, it took ages for the desktop icons to show up, about 30s, during this time, only the desktop background was being shown, eventually, when the desktop icons appeared, I started the system monitor, and noticed a significant increase in memory and cpu usage, even when the desktop and icons have loaded, the cpu usage is constant at 95% and memory usage leveled at 720Mb, as apposed to kernel 2.6.32-27, which only used cpu of about 12%, and memory at 250Mb.

I'll be going back to Kernel 2.6.32-27 until this huge resource usage has been fixed.

---

### Post by Frogs Hair on 2011-01-26
Hi and Welcome

Open the terminal and run the top command , this will at least tell you what the offending program/s are.```
top
```

---

### Post by usalabs on 2011-01-26
Thanks for the reply.

I tried using top and also as user, IE, top -u <user> the %CPU still showed 95%, I also noticed it is Xorg that was using 92% of the CPU, but compared to Kernel 2.6.32-27, which Xorg only used 5.3% +-1%, it seems there is some sort of resource leakage, with kernel 2.6.32-28 something is filling the memory, thus increasing CPU usage, until the memory has reached about 720Mb then the swap file started increasing.

Switching back to kernel 2.6.32-27 from startup at the grub menu, the same tests using 'top' showed different readings, %CPU = around 12%, Xorg = between 5 and 6%, swap = 0%, system memory = about 250Mb.

---

