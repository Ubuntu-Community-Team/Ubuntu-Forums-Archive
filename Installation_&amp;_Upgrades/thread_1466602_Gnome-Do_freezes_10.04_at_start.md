---
title: "Gnome-Do freezes 10.04 at start"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by winecurmudgeon on 2010-04-30
I installed Gnome-Do on a clean install of 10.04 from the repository. I checked the "start Gnome-Do at start" box. When I rebooted, the system asked me for a default keyring and was frozen. Nothing worked. I had to slip into the terminal with ctrl-F2 and remove Gnome-Do. Then I rebooted, and the system worked correctly. Any thoughts?

---

### Post by lvaillan on 2010-04-30
The same thing just happened to me, on two systems, one running Ubuntu Netbook Remix and the other with Lucid Lynx 10.04 64 bits. So far, I can't find any valid explanations on google...

---

### Post by winecurmudgeon on 2010-05-01
I think it has something to do with not using a password to sign in. I signed in with a password on 9.04, and gnome-do worked fine. I set up 10.04 so I didn't need to use a password, but gnome-do apparently looks for one and when there isn't one there, it locks up.

I reinstalled gnome-do, chose not to start it at startup, and start it by hand after my system comes up. It seems to be working fine.

---

### Post by caughran on 2010-05-20
Please see [http://ubuntuforums.org/showthread.php?t=1488340](http://ubuntuforums.org/showthread.php?t=1488340)

---

### Post by bg1256 on 2010-06-16
I'm having something similar; however, I can't get to the terminal via keyboard, as my system isn't accepting input from my keyboard.

Very strange bug. Ideas?

---

### Post by bg1256 on 2010-06-16
forgot to subscribe

---

### Post by gautier57 on 2011-04-12
You can kill gnome-do by using ctrl+alt+F1 -> login -> killall gnome-do -> ctrl+alt+F7 (if you don't want to restart).

---

