---
title: "wireless super slow"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by note32 on 2009-10-11
in windows wireless is fast in ubuntu sadly slow](*,) is there a way to make it faster? i have a wireless router 802.11g 54mps could it be my wireless card? i have a Asus 1005ha netbook im using ubuntu 9.10 because thats the only version of ubuntu that wireless will work out of the box

lspci:
       Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


thats my wireless card

---

### Post by bapoumba on 2009-10-11
Moved to karmic.

---

### Post by taavikko on 2009-10-11
Known bug...
[https://bugs.launchpad.net/bugs/414560](https://bugs.launchpad.net/bugs/414560)

---

### Post by hoggarth on 2009-10-21
On the known error link you posted there's a very good post #20 from kervel with a patch which worked well for me on my 1005HA with AR9285 Wireless chip and Karmic (Kernel 2.6.31-11). Improves speed and stability a lot.

---

