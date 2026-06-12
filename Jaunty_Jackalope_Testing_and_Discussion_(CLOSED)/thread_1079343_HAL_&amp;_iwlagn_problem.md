---
title: "HAL &amp; iwlagn problem"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Quadchris on 2009-02-24
Hi all,

I've the following issue with Jaunty and my ASUS Laptop :

when I'm rebooting or halting I've a kernel oops with Hal and the module iwlagn. The error message doesn't appear on my log files but only on console. What I understand of this message is that HAL remove my device before the deconfiguration and the device is NULL when the network deconfiguration occurs. After this message the termintaing all process and the network deconfiguration failed and the reboot or halt sequence is stopped. Only a hardware shutdown by pressing power button during 5 secs permits to recover the control.

Anyone has a similar problem or am I the only one ?

Anybody have a solution for getting the console message except of copy it with my own hands :)

Thanks by advance.

P.S. : I'm french so excuse the english faults :)

---

