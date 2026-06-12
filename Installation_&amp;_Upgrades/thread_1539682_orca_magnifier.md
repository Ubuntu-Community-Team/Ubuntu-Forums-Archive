---
title: "orca magnifier"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by asal.mostafa on 2010-07-26
guys i'm in a big problem 
i installed orca magnifier just to try it 
after i restart my pc the screen comes very big and i couldn't even login 
i started safemode and also couldn't login 
just i wanna uninstall orca 
help plz !!

---

### Post by themusicalduck on 2010-07-27
You can remove the magnifier program, I think, like this.

Boot Ubuntu in recovery mode from the grub menu. When it asks, pick to drop into root shell.

Run this command ```
apt-get remove gnome-mag
```

Hopefully that'll stop it magnifying on startup and you can go and take it out of the startup applications if you want.

---

