---
title: "Intrepid network manager disconnects every 30s"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by heng on 2008-10-03
Under the new Intrepid Beta (not tried any earlier releases), Network manager drops its connection every 30s or so and then picks it back up immediately. Its a real disconnect as nothing that requires the network can happen during that time. This is on a wired network with DHCP. Everything was fine under Hardy.

lspci reports the ethernet driver as Broadcom Corporation BCM4401-B0 100Base-TX, but I don't know what driver its using.

---

### Post by Brandon Hoult on 2008-10-16
I have the same issue.  Wired seems to work but wireless keeps disconnecting about every 30 seconds.

It worked initially when I installed the intrepid beta, but after a update it started doing this.

lspci:
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by kubug on 2008-10-26
I had the same thing happen to me with (Broadcom) Wireless in intrepid. It seems that it disconnected me when I used the connection "full-speed", or in other words, copying large files. 

If I just checked emails or browsed, it seemed to hold the connection longer.

**What I did to fix it was changed the WPA Algorithms (WPA2 Personal Security) to AES (from TKIP)**. Ever since I did that, everything was fine.

Try that and see if that helps your wireless.

---

