---
title: "Mouse cursor freezes (for 0.5-1 sec) after upgrade to 21.10"
date: 2021-10-17
forum: Installation &amp; Upgrades
---

### Post by yamagami on 2021-10-17
Hi!

Lenovo Carbon X1 9th gen
Upgrade from 21.04. 

After the upgrade, my mouse cursor freezes randomly for anything between 0.5 to 1 second, and then comes back to life. 
This happens both on my Bluetooth mouse (Logitech MX Anywhere 2) or on the trackpad. 
I tried to tail logs (kernel, syslog, dmesg) to see if anything is spat out while that happens but nothing  is.  
Not sure where to go from here or how to debug something like that. 
Any ideas?

Thanks!

---

### Post by yamagami on 2021-10-18
It appears this happened when bluetooth is on in general. While researching this, it also appears the problem suddenly self corrected... 
I can't explain it, but i'll take the victory.

---

### Post by yamagami on 2021-10-28
The plot thickens - it seems to resolve itself when I connect the laptop to a dock. 
This happens both with a Bluetooth mouse and the built in touch pad. It appears that even keyboard activity lags every few seconds for a few milisecs. 
it's incredibly annoying.

---

