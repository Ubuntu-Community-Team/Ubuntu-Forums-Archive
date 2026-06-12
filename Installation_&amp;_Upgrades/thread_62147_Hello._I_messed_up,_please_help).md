---
title: "Hello. I messed up, please help:)"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by kzu on 2005-09-03
I just installed ubuntu, but the screen resolution it used was 1600x1200@75hz which is something my monitor can't really handle, so I started xorgconfig and + things up, X won't start anymore... I can get to use things with Ubuntu recovery from boot menu, what should I do now?:/

---

### Post by transactionlogfiller on 2005-09-03
Try "sudo dpkg-reconfigure xserver-xorg"

---

### Post by mcmuffy on 2005-09-03
I don't want to sound like the language police but could you please refrain from using X rated language  :-# .

Oh and hello Sheffield. Firth Park calling  :grin:

---

### Post by bored2k on 2005-09-03
> Profanity: Mild profanity/swearing is allowed in the context of general speech. Explicit profanity/swearing is not allowed, and under no circumstances will we allow any profanity to be directed toward another person. Please see the Code of Conduct:Be Considerate, and the Code of Conduct:Be Respectful for more exact specifications. Moderate yourself or be moderated by us.

---

### Post by skatedawe on 2005-09-03
I did almost the same thing.
 
 Try; sudo nano /etc/X11/xorg.conf

 and edit your problem.

 You have to be root and do sudo to get the settings saved.

---

### Post by az on 2005-09-03
[QUOTE=transactionlogfiller]Try "sudo dpkg-reconfigure xserver-xorg"[/QUOTE]
Boot into recovery mode to do so.

Hit escape when you boot if the grub menu is not displayed.

---

