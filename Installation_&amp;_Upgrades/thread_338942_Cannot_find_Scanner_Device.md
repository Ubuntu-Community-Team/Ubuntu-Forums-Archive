---
title: "Cannot find Scanner Device"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by reb68 on 2007-01-15
I apologize if I am in the wrong forum. I upgraded to 6.10 from 6.06 and all seemed well except xscan cannot find device when I try to scan. Kooka will not open. The printer works fine  (ran a test page after reinstalling it to try to solve problem) I have a HP PSC 1410 all in one. It worked fine in the ver. 6.06 but will not open device in 6.10. 
Thanks for any help.
Dick Barmann

---

### Post by Sef on 2007-01-15
How is your PSC hooked up: parallel or usb?

---

### Post by reb68 on 2007-01-15
It is a USB hookup.

---

### Post by dolphinsonar on 2007-01-17
Same problem here in Edgy with a USB printer/scanner using Xsane.

I had to actually remove libsane and reinstall the dapper version.  After rolling it back it works just as it did in dapper.  I am not sure if Kubuntu uses libsane but I imagine getting the dapper library appropriate to your scanning utility would yield similar results.

---

