---
title: "Network settings when cloning to identical hardware"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by Twelveone on 2010-08-09
The company I work for use Ubuntu on the PC's that control the system they manufacture. To simplify and speed up the OS install we use a standard PC (all the same hardware) and install a disk image on each system. The disk image was produced from one of the systems and the network settings were set to use a Static IP

However every time we clone a system the network settings change from the static IP settings to Roaming Mode.

Does anyone know why this happens or if it is possible to have the static IP settings remain after the clone?

Thanks

Stewart

---

### Post by clrg on 2010-08-09
If you clone the system's IP, you'll get an address conflict. There cannot be two systems with the same IP.

Alternatively, configure your DHCP server to always give the same IP address to your MAC.

---

### Post by Twelveone on 2010-08-09
Thanks clrg, I guess you're answering the first part of the question. I understand that 2 PC's on the same network with the same IP Address will cause problems. However these PC's are connected in a standalone environment with just the PC and our system connected using TCP/IP. 

So I would still like to know if it's possible to have the static IP settings remain after the clone?

---

### Post by clrg on 2010-08-09
I don't know if there is a way to do this. A workaround that requires little effort would be to configure the network interface after every boot via script. For example, edit /etc/rc.local and lines similiar to:

```
sudo ifconfig eth0 10.2.3.4 netmask 255.255.255.0
sudo route add default gw 10.2.3.1
```

That will set eth0 to specified parameters after every boot. Not the proper way to do it, but will definitively work :)

(If you don't have subnetting in that network, don't even need routing.)

---

### Post by Twelveone on 2010-08-09
Thanks, that sounds like a solution that would work

Thanks again

Stewart

---

### Post by clrg on 2010-08-09
Please mark the thread as solved.

---

