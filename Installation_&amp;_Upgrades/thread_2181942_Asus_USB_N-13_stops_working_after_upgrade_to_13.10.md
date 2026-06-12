---
title: "Asus USB N-13 stops working after upgrade to 13.10"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by marek-campus on 2013-10-19
Hi,

My Asus USB N-13 wireless stick was working fine with the alternate driver on Raring. (The alternate rtl8192cu driver was the one from the deb for 3.8 and 3.9 kernels from [here]("https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/").)

The built-in drivers with the 3.11 kernel in Saucy seems to choke on the WPA security (it fails to configure an IP address after a long delay). I've tried the deb and also the basic installation of the official Realtek drivers, following the basic instructions and also Chilli555's [from this thread]("http://ubuntuforums.org/showthread.php?t=2167956&p=12758603#post12758603"), but to no avail.

Is there something basic I'm missing?

Thanks.

---

### Post by marek-campus on 2013-10-21
Basically have fixed this by stepping back to my old 3.8 kernel. Not exactly solving the issue, but a few days of searching has left me fairly sure that the built-in drivers just don't work with WPA2 and the Realtek driver doesn't work with the stock 3.11 kernel at present.

One to keep an eye on for a while I suppose.

---

