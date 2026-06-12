---
title: "Wine - Complete removal"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by mevets on 2007-03-13
I have several entries for Macromedia Dreamweaver, everything ranging from 1.2a to 8. My problem is that I am not able to completely remove these programs. I tried using the Wine software uninstaller, but it doesn't quite do the job. I tried going into Synaptic > Wine > Mark for Complete Removal and then reinstalling afterwards, but I am left with the same result.

Is there a way to get rid of everything wine has done to my system?

---

### Post by aidanr on 2007-03-13
have you deleted ~/.wine? (hidden folder in your home directory)

---

### Post by SuSUntu on 2007-03-13
Make sure that the hidden directory is removed:

**/home/username/.wine**

You may want to back that up before deleting it (or maybe just rename it). Either way, once that is taken out of the loop, the **.wine** directory should be recreated when you install Wine again, and you should have a clean slate.

Edit:

Sorry for the duplicate answer. Aidanr beat me to it.

---

### Post by mevets on 2007-03-13
Still Leaves me with MX in the Wine menu

---

### Post by aidanr on 2007-03-13
well you can delete that with "alacarte" or "sudo alacarte" from a terminal

---

### Post by KriZo on 2008-01-05
i've got the same problem but in alacarte the wine entry doesn't show up, but it's still in the gnome menu.

---

