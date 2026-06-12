---
title: "wlan doesn't work any more"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by pinus on 2008-10-11
The hardware is a Dell inspiron 6400 that came with Linux preinstalled. I had a 7.10 running. The wlan worked.
After updating to 8.04 wlan doesn't work any more. After wrestling with all kind of configurations and packages I gave up and reinstalled 8.04. And wow it does work again. Then I installed the lates updates and they broke the wlan again. The updates leave the old kernel 2.6.24.16 which works and the new kernel 2.6.24.19 which is broken.
I don't know what they did between the releases but it breaks the wlan support on my notebook. If you have the same notebook ane experience similar problems, try the older kernel.

lspci returns:
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

