---
title: "laptop with atheros AR2413 (belkin plugin)"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hoodwink on 2009-03-28
Jut installed jaunty on my laptop (hp ze4630us) which has a defective builtin broadcom wireless card, but I'm using a belkin plugin card for wireless, so of course the installer didn't do the right thing.

After a little research, here's what's needed to get wireless working:

1. The builtin card is detected as wlan0, so of cource b43legacy module is loaded. I added a new /etc/modprobe.d/blacklist-b43legacy.conf file to suppress this. Still get nasty messages in dmesg, but that's ok.

2. The installer also detected the atheros card as wlan1, but decided to enable ath_pci which doesn't work for this card. I added ath5k to /etc/modules.

Wireless is now working.

Hmmm I just noticed that b43legacy is still loaded in spite of the blacklist.

Perhaps someone can suggest a better way to handle this.

---

