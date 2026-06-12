---
title: "Setting a Static IP under Karmic."
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sslaxx on 2009-09-29
Which option do I need for setting a static IP with Karmic's network tools?

---

### Post by wizard10000 on 2009-09-29
Mentioned it in another thread on the front page but I understand network manager is broken - why not reserve an IP address on your router for the machine rather than hardcoding an IP address on the PC?

---

### Post by zika on 2009-09-29
> **wizard10000 said:**
> Mentioned it in another thread on the front page but I understand network manager is broken - why not reserve an IP address on your router for the machine rather than hardcoding an IP address on the PC?
I have static address set in Network Manager. I used /etc/network/interfaces in Jaunty because NM was broken at the Beta stage of Jaunty but in Karmic I've went back to NM ... Recommended.

---

### Post by xeddog on 2009-10-04
I have been using Karmic on an old machine since A1, but for about two weeks now my network-manager has been broken.  It just tells me that I am disconnected from the network.  I have to use terminal and manually assign an ip address, netmask, and default route to get any connectivity.

Other than that it has been a "normal" alpha/beta process for me.

xeddog

---

### Post by canabal on 2009-10-04
please report that it effects you here, the more people we get doing it, the faster it will be fixed: 

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/442583](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/442583)

---

