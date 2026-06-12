---
title: "Graphical problems installing edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by jonny84 on 2006-10-26
Hi guys,i downloaded ubuntu edgy but whet it loads the gdm I see more flashing lines and a can't enter in ubuntu.
what can i do?
Is a problem due to the graphic card?

i have a Nvidia GeForce 6200 256MB TC

Thanks

---

### Post by unisol on 2006-10-26
try running it in safe-graphics mode or download the alternate-installcd from:[http://ftp.osuosl.org/pub/ubuntu-releases/edgy/](http://ftp.osuosl.org/pub/ubuntu-releases/edgy/)

---

### Post by blackmh on 2006-10-26
When those lines appear press Ctrl - Alt - F1 and log in. Then do "sudo apt-get install nvidia-glx", then "sudo nano /etc/X11/xorg.conf" and find line with "nv" and change it to "nvidia", save.

restart with sudo shutdown -r now

---

### Post by jonny84 on 2006-10-27
> **blackmh said:**
> When those lines appear press Ctrl - Alt - F1 and log in. Then do "sudo apt-get install nvidia-glx", then "sudo nano /etc/X11/xorg.conf" and find line with "nv" and change it to "nvidia", save.

restart with sudo shutdown -r now

I love you....:mrgreen:

---

