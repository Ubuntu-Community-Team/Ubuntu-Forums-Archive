---
title: "ubuntu 14.04 will not install"
date: 2015-10-07
forum: Installation &amp; Upgrades
---

### Post by yoshi3 on 2015-10-07
I've been trying to solve this problem for a few days now. I use Ubuntu as home laptop and enjoyed it.  I have a Sony Vaio FJ170 and it won't run Ubuntu 14.04 or versions of Ubuntu after 12. When I installed it using the netinstall method, it gives me "Disabling IRQ #9" and it hangs. I've tried acpi=off, noacpi and irqpoll but it still gave me the message. I tried using the LiveDVD today and turned on noacpi but halfway it shows me the BusyBox shell. I tried Install Ubuntu with noacpi and acpi=off and it's showing this nonstop.
```
stdin:Not a typewriter
/init: line 7: cant open /dev/sr0: No medium found
/init: line 7: cant open /dev/sr0: No medium found
```
Then going to the BusyBox shell again.
I've been trying many things to get it to work but it's driving me nuts.

My hard drive is fine and I'm using an USB DVD drive. The DVD is fine also. I've tried to install ArchLinux, LinuxMint and other distros but would not work. I've been thinking that theres something wrong with the kernel version but I don't know I'm not really good at Linux. Thanks for reading.

---

### Post by dino99 on 2015-10-07
Looks like /dev/sr0 is your DVD drive, and there is no dvd inside
But the problem is you need to do a real install, or boot each time from the dvd

---

### Post by yoshi3 on 2015-10-07
When I do a full install, it gives me Disabling IRQ #9 and when I try to go to Try Ubuntu Without Installing with noacpi and acpi=off, it freezes at the point mentioned at my previous post. I'll try to do it without the noacpi and acpi=off later today and post the results here.

---

