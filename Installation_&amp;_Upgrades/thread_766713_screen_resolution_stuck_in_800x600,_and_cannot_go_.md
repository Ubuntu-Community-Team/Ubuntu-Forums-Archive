---
title: "screen resolution stuck in 800x600, and cannot go any higher"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by bbmak on 2008-04-25
I just deploy xubuntu 804 to my laptop, and my screen resolution stuck in 800x600, and i cannot go any higher.

My laptop model, Toshiba Portage 2000
My display card is Trident CyberBlade XP AGP

---

### Post by chek2fire on 2008-04-25
What gpu you have?

---

### Post by gmasters on 2008-10-20
What parameters did you need to put on the command line after pressing F6 to get the installation to proceed. I hsve a Toshiba Satellite S273-1805 with a Trident Cyberblade A/i card and get a black scrren with a hang. I don't proceed to the GUI.

---

### Post by Ryadt on 2008-10-20
Try reconfiguring x-server. This might help.```
sudo dpkg-reconfigure xserver-xorg
```

---

