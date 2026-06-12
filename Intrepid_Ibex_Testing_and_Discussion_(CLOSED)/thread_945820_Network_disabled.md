---
title: "Network disabled"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sketcher on 2008-10-12
I installed kubuntu 8.10 daily build from 12 Oct. and I don't get any internet.
When I start up the network manager says connected but I can't do anything network related.
When I type "lshw -c network" I get the msg network disabled and by logical name it says pan0.

Is there any way to get it going? I know there was a e1000e bug but I have read that it was fixed. And I dont think my onboard lan even uses it. My motherboard is a asus k8n4-e deluxe and when I check the asus site it says it uses the 88E81111 chip.

Hope anyone can help me, thanks. :)

---

### Post by sketcher on 2008-10-14
Quess no one knows. ;)

---

### Post by Charlie708 on 2008-10-15
The fix prevents the NVRAM of the e1000e (82567) from being written on, it doesn't allow it to be used risk free.  Intel is still working on a real fix for this bug.

---

### Post by sketcher on 2008-10-24
I thought I'd try the release candidate from ubuntu to see if it might be working but I still have no internet.

---

