---
title: "dell 1390 wireless trouble"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sjb05004 on 2009-03-31
can someone help me enable my wireless.  i have a dell 1390 broadcom chipset.  the restricted drivers pops up and i enable and reboot, but after a reboot it says wireless disabled even though the led is lit up. should i install the driver manually another way, or is there an easier way?

---

### Post by vahnx on 2009-03-31
Hm, I have the 1390 and after a fresh install of 8.10 it normally works after I enable and reboot. So in 9.04 I hope it's not broken! You can obtain the wireless inf file and use [ndiswrapper]("http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/") to install.

---

### Post by sjb05004 on 2009-03-31
I may have been hasty in my decision to give up.  After it did not work I went back to 8.10.  I'll give it another go and hope for the best.  If it does not work any idea on where to obtain the inf for the card?

---

### Post by sjb05004 on 2009-04-01
After a clean install of 9.04 I still have no working wireless.  Before enabling the restricted driver it says wireless disabled, as well as after installing the driver and rebooting.  I guess I will resort to ndiswrapper.  Any idea on where I could obtain the inf for this wifi card?

---

### Post by vahnx on 2009-04-03
If you download the Windows XP wireless driver from Dell's website, you can extract it with WinRaR or double click the self-extracting .exe and browse to the extracted folder. In that folder the .inf should be somewhere.

---

