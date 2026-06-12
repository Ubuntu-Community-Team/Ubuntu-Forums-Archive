---
title: "Video Problem Ubuntu 13.04 - Radeon HD4650"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by ve3pkc on 2013-05-03
I have been having problems with video since 12.04. When I upgraded to 12.1, I lost video completely. When I saw that 13.04 was out, I tried again. This time I used my Toshiba LCD TV as a monitor rather than my older Viewsonic VPA150. Everything went well when I upgraded. However, when I rebooted the screen was visible in the middle, but all the menu items on the left hand side and top had a moire pattern and were not visible. I then booted into my older VPA150 monitor and the same thing. By trial and error I was able to get a system settings menu and checked the display. It said unknown, using the Gallium driver. My pc is an HP p6102f with ATI Radeon HD4650. I rebooted into a recovery screen with a lower video capability. Now the screen was all visible, but had a slow response. I checked the system settings again, this time it said Laptop. Every time I try a menu item I also get "Internal System Error". 

Any ideas on what driver I can use to get a stable video similar to earlier releases for my setup? Best Regards.

---

### Post by ve3pkc on 2013-05-06
Tried various things...went back to 12.04 and everything stable.

---

### Post by Mark Phelps on 2013-05-06
That's most likely because AMD dropped restricted Linux driver support for their HD 2x/3x/4x series cards last summer.  As a result, the last Ubuntu version that supports the fglrx driver with these cards is 12.04.1.  Starting with 12.04.2, and continuing through 12.10 and 13.04, the X-server version is incompatible with the AMD restricted driver that works with those cards.

---

### Post by ve3pkc on 2013-05-20
Many thanks Mark.

---

