---
title: "kernel 2.6.31 broke wireless atheros AR242x"
date: 2009-07-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-07-01
2.6.30-1 atheros wireless works, so good so that even the switch led works which I haven't seen in 2 years

2.6.31 atheros wireless doesn't work at all

acer aspire 3680 laptop> 03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

EDIT:  Probably should add that this is the kernel installed from the repos

---

### Post by sarelgrin on 2009-07-03
Same problem here with Atheros AR928X on Acer Extensa 5630z.

Worked great with 2.6.30-9. Stopped working after the latest update to kernel 2.6.31

> 03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by hardyn on 2009-07-03
Devs rarely check here; head over to the lauchpad and let them know.

---

### Post by buzzmandt on 2009-07-04
Woohoo, my first bug report.  Hope I did that right lol

here it is:  [https://bugs.launchpad.net/ubuntu/+bug/395565](https://bugs.launchpad.net/ubuntu/+bug/395565)

---

