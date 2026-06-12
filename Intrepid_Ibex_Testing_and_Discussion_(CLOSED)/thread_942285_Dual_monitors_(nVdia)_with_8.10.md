---
title: "Dual monitors (nVdia) with 8.10"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Lord_Takkera on 2008-10-09
I am trying to set up a dual display (like in XP) with Ubuntu 8.10. Everything goes fine until I click apply. It says "you need to save to the config file". I say, "ok", and click "save to config file". It then proceeds to tell me that "failed to parse existing X config file '/etc/X11/xorg.conf'!" I then click on save. It says "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'".

Any ideas on how to fix this problem would be greatly appreciated.

---

### Post by kabotage on 2008-10-09
type in terminal
```
sudo nvidia-settings
```

change settings to w/e you want. click save.

---

### Post by Lord_Takkera on 2008-10-10
I finally got it working, but through a roundabout and probably-won't-work-for-anyone-else kind of way. However, now the second monitor freezes up (and actually locks up the rest of Ubuntu) when I try to launch firefox in the second X screen. Any ideas?

---

