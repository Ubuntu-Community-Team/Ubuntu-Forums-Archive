---
title: "Upgrade Problems with 11.04"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by WhiteHorse on 2011-05-04
I recently upgraded from 10.10 to 11.04 and encountered the following problems:
1. Wireless drivers hosed(installed but not working)
2. Dial-up networking STILL doesn't work.
3. The interface was changed to a completely unusable and unfamiliar interface called Unity.

I solved them by changing the wireless driver for my broadcom BCM 4311 to the b43 driver and uninstalled the Broadcom STA driver. You can do this all through synaptic package manager (if you can find it in the Unity interface, haha). Please note, this required me to go to the job center and plug into their LAN because there is no other way to install the b43 driver without internet access.

I wasn't able to fix the dial-up networking. I just dropped it after the drivers wouldn't compile.

I fixed the Unity interface when I logged in by choosing classic Ubuttu instead of Unity. 

Anyway, thanks to the devs for all the hard work. I don't really see any difference and hate the unity interface. I like the fact that I actually get notifications for IM's and emails once again. I like the fact that this upgrade almost went smoothly and didn't require me to wipe my system and do a fresh install from CD.

---

