---
title: "Can't Detect Wireless NIC with 5.04"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by nitrordx on 2005-07-14
I successfully installed 5.04 with a dual boot with Win XP, but I can't get 5.04 to detect my wireless NIC.  It's a standard Intel 2100 model that came with the Toshiba laptop.  Both Win XP and Knoppix detected the NIC automatically.

5.04 won't pick it up, even with the SSID and WEP provided.

Help please!
 :mad:

---

### Post by alastair on 2005-07-14
It does not detect the device? Or does not configure it?

Check :

/var/log/syslog or
/var/log/dmesg

for "ipw" e.g.

ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.0.2
ipw2100: Copyright(c) 2003-2004 Intel Corporation

Then, if you see that - check :

iwconfig
ifconfig -a

---

