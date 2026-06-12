---
title: "Ubuntu Installation won't start"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by Mammut1492 on 2010-09-07
Hi everybody,
 
I really need some help here. 
I'm a software developer and wrote my bachelor-thesis about Linux-Scheduling. So normally i can fix quite some probs on my own.
 
Well, long story short... Since I don't need Windows any more, I wan't to install Linux native on my dektop-pc. So here's the problem.
 
I downloaded the iso, burned it.
I checked MD5 sum and it works on another pc(not my desktop-pc).
But it freaking won't work on my desktop. 
Everything i get after some minutes of waiting is on screen 1 some error messages like:
 
udevd[104]: worker [110] unexpectedly returned with status 0x0100
udevd[104]: worker [110] failed while handling '/devices/pci0000:00/0000:00:1e.0/0000:06:06.0'
 
well... end of the road. On screen 7 i see 4 dot's representing the loading screen of Ubuntu... well... that's it.
 
I tried AHCI, RAID, IDE Mode for my SATA-Ports. I even used legacy IDE... won't change anything...
 
Anyone any idea?
 
**my system:**
Gigabyte-EP45-DS5 Mainboard
Intel Q8200 CPU CPU
Intel X25 SSD
8 GB DDR2 RAM
 
regards
Mammut

---

### Post by garvinrick4 on 2010-09-07
Google your hardware and drivers.

---

### Post by Mammut1492 on 2010-09-08
Well, i sorted it out... finally.
 
Disable the second onboard-SATA2-Controller (the one with purple slots) in BIOS at the bottom of the **Integrated Peripherals**-Screen. I think it's called "Enable SATA/IDE controller", ore something like that.
 
Save the changes and reboot. Make sure your harddisk is plugged in at the SATA-Controller with the **yellow slots** ( it should by anyways).
 
Take a look at 
 
[http://www.gigabyte.de/Products/Motherboard/Products_Spec.aspx?ProductID=2749](http://www.gigabyte.de/Products/Motherboard/Products_Spec.aspx?ProductID=2749)
 
at the section "Storage Interface". Unfortunately the kernel does not support the "GIGABYTE SATA2 chip".
 
regards

---

