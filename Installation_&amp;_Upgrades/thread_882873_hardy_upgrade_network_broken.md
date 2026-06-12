---
title: "hardy upgrade network broken"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by gilman22 on 2008-08-07
I upgraded to 8.04.1 from 7.10 using the Internet connection. The upgrade went smooth but when I rebooted I could no longer access the network. I have tried manual configuration but can no longer ping my router. The full 8.04.1 install from CD had the same result. 7.10 reinstall works fine, I have a Gigabyte GA-G31-S2L motherboard with a Intel ICH7 South Bridge supporting a 10/100/1000 Ethernet. The Network is RTL8111C. Ubuntu detects RTL8111/8168B PCI in the diagnostics.

---

### Post by knightrous on 2008-08-07
Same motherboard as OP. I just upgraded from an AMD 3200+ S939 to Intel E2180, but kept my drives. It worked straight up, except it was only detecting 1 core (expected when you don't reinstall). Network connection was working at this stage. Just re-installed to get the dual core support and have lost my network like OP. 

Wierd that it all seemed to work on the install for an AMD which worked, yet fails with a fresh install :( Look forward to hearing other peoples comments and a solution :D

---

### Post by cariboo on 2008-08-08
Go to System-->Administration-->Network and check to see if roaming mode is enabled. THe other thing you can try is in a terminal:

```
dhclient eth0
```

This is assuming that your network card is set as default eth0.

Jim

---

### Post by gilman22 on 2008-08-08
I have tried both Roaming and Manual configurations. When I manually configure a fixed IP address it shows up in ifconfig. In roaming or auto dhcp the IP configured is not from the network.

---

