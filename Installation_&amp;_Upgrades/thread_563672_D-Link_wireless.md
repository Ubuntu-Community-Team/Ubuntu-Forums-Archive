---
title: "D-Link wireless"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by dagvei on 2007-09-30
How can I make my D-Link G122 wireless USB work in Ubuntu 7.10?

---

### Post by Pumalite on 2007-09-30
Are you trying to make a home LAN? What is your connection to the internet?

---

### Post by dagvei on 2007-09-30
I have both cables and wireless at home.
I am in the  "iwconfig" and gets thiese mess:

lo: no wireless extensions
wmaster0: no wireless extensions
wlano: IEEE 802.11g ESSID;""

I could not find a driver attached to the USB device when running the "lshw" command....

---

### Post by Pumalite on 2007-09-30
Make sure your BIOS recognizes the USB device.

---

### Post by dagvei on 2007-09-30
Yes, it's a D-Link G122 working fine in Windows. It's a plug-in type wireless.

The cabled connections were set up automatically with no problems, the wireless connections never started. No automatic search or config program starts. As far as I can understand, the driver to the D-Link is already in Ubuntu?

---

### Post by Pumalite on 2007-09-30
I found something that might help you:

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

---

### Post by wil313 on 2007-09-30
Hey, try this page, it worked like a charm for me:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by dagvei on 2007-09-30
EUREKA! I got it! The problem was incredibly stupid; had to type "3Com" and not 3Com..... and change from WPA to WEP......

Isn't it always like that; the most silly choices are the ones that work...

---

### Post by Pumalite on 2007-09-30
Glad you got it working.

---

