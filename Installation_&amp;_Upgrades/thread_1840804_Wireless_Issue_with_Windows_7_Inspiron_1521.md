---
title: "Wireless Issue with Windows 7 Inspiron 1521"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by hirenpathak on 2011-09-08
I have seen other threads about this issue and tried different options but looks like my Inspiron 1521 is having wireless problems with Ubuntu 11.04. I don't see wireless settings under my networking.

I used to have Windows Vista but then upgraded to Windows 7 64 bit. Just two days ago, I installed Ubuntu as dual boot.

Can someone please help me?

Thank you.

---

### Post by hirenpathak on 2011-09-08
I tried the Broadcom STA Wireless driver but it doesn't work.

---

### Post by howefield on 2011-09-08
Are you able to connect wired ?

If so, update your sources and try Dash > Additional drivers to check for proprietary drivers for your wireless card.

There are a few threads regarding that machine and wireless in the forum that you might like to search for, most seem to be resolved.

---

### Post by hirenpathak on 2011-09-08
yeah I tried the addtional Driver path. It brings me to the screen that says Broadcom STA proprietary driver and I activated the driver but still no luck. I looked through other threads that had similar problem and tried the base43 (or something similar) on my machine but no luck. It showed the "wireless network" menu items but they were disabled and said "firmware missing for wireless"

---

### Post by hirenpathak on 2011-09-08
I was able to get it to work now. Thanks to the good man BertN45 who mentioned this in another thread. >  I deactivated the STA drivers and I and using the B43 drivers from the  synaptic package manager. I have installed the "firmware-b43-installer"  and the "b43-fwcutter". It works very reliable and I have absolutely no  complaints.

---

