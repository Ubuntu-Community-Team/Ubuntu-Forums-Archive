---
title: "Ubuntu beta 9.10 falis to load drivers for wireless on Dell XPS M1530"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TheGorf on 2009-10-25
The Dell XPS M1530 seems to continue to have a challenge with the wireless drivers.  I thought I would throw 9.10 on while it was still in beta and see if I could find any problems.  And I did,

The M1530 seems to fail to load drivers.  From my dmesg:

[   10.173535] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   10.193459] cfg80211: World regulatory domain updated:
[   10.193461] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.193463] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.193465] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.193467] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.193469] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.193471] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.217124] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[   10.217168] b43: probe of ssb0:0 failed with error -95
[   10.217196] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   12.806401] __ratelimit: 3 callbacks suppressed

I am happy to offer any help I can on tracking this down.  I also noted that it doesn't offer me the inclusion of the proprietary drivers for the Broadcom b43 chip or the Dell specific drivers.  Is that just a function of the beta-ness of the release?

Also should I be documenting this on launchpad?

---

