---
title: "Problems with Atheros 5212"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by wundbread on 2009-03-13
My Atheros wireless card (on my Lenovo T61) isn't being detected by Jaunty alpha 6.  It worked with Intrepid if I compiled the madwifi snapshot.

Even if I manually modprobe ath_pci, I get nothing...  dmesg | grep ath returns no info about Atheros stuff.  It doesn't show up in lspci either.

Under Intrepid it was detected as:

ifi0: Atheros AR5424 chip found (MAC 10.3, PHY SChip 6.1, Radio 10.2)
ath_pci: wifi0: Atheros 5212: mem=0xdf2f0000, irq=17

Any Ideas?
It would suck to have to manually downgrade to a 2.6.27 kernel from intrepid...

---

### Post by RedSingularity on 2009-03-13
You try the ath5k or the ath9k drivers yet?

---

### Post by wundbread on 2009-03-13
I tried modprobing ath5k and ath9k as well, still iwconfig and proc/net/wireless don't show any devices

---

