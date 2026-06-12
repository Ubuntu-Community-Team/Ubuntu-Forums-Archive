---
title: "Ath0 wi-fi card"
date: 2005-08-27
forum: Installation &amp; Upgrades
---

### Post by Hakon Marius on 2005-08-27
Hi, 

Just installed Hoary on my IBM think-pad x40 with a Ath0 network-card. Now, the computer detects the card, and even reads signals from it. But it won't let me connect to the net. 

Anyone has any idea of what I can do?

---

### Post by kleeman on 2005-08-27
You might have new firmware that the hoary madwifi driver cannot handle.
Run dmesg at the commandline and see if this message is there:

HAL status 13
If it is check for a line like
ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)
This means your driver is outdated. To upgrade follow this guide:


[http://www.ubuntuforums.org/showthread.php?t=36800](http://www.ubuntuforums.org/showthread.php?t=36800)

If you see instead

ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)

then your out of luck as the new driver won't work either....

---

