---
title: "rt2860 wireless issues"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by eteq on 2009-08-13
I have a Linksys WMP600N wireless card based on the rt2860 chipset (at least, that's the driver that came up when Ubuntu started).  It partially works, but not totally.  Specifically, I can't seem to get 802.11n speeds even when connected to an N router, and I'm having trouble connecting toa  network that uses WPA (although WPA2 seems to work...) 

Anyone else have their rt2860 wireless working correctly or not?

---

### Post by gordboy on 2009-09-23
i'm not able to connect with WEP, either, also using a rt2860. i've had no problems connecting to the same network with 9.04. 

i don't believe N is supported in the kernel at all yet.

---

### Post by Akita on 2009-10-09
Lost N here too when I upgraded the notebook. Did either of you file a bug report? If so, please post the #.

---

### Post by cb951303 on 2009-10-09
In the bsd driver's manual page for rt2860, it says that N is not supported yet. I'm not sure if it's the same situation for linux but you might want to research it.

---

