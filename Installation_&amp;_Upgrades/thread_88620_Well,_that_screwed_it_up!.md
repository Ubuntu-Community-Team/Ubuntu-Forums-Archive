---
title: "Well, that screwed it up!"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by Dogers on 2005-11-10
So the install went great, everything was fine.

Ubuntu was running through it's first boot thing, then I suddenly threw a spanner in the works - I made my computer froze (don't ask :) )

Now when I log in as the user I created (or any other user I subsequently create) I'm missing the bottom bar in Gnome and the top bar is about an inch long and has no icons!

Is there any way to rerun the initial setup script again?? :confused:

---

### Post by Kyral on 2005-11-10
```
sudo dpkg-reconfigure ubuntu-desktop
```

Might help

---

### Post by az on 2005-11-10
[QUOTE=Dogers]So the install went great, everything was fine.

Ubuntu was running through it's first boot thing, then I suddenly threw a spanner in the works - I made my computer froze (don't ask :) )

Now when I log in as the user I created (or any other user I subsequently create) I'm missing the bottom bar in Gnome and the top bar is about an inch long and has no icons!

Is there any way to rerun the initial setup script again?? :confused:[/QUOTE]
X is misconfigured.

Try booting into recovery mode and running
dpkg-reconfigure xserver-xorg

then run 
init 2
to get into desktop mode.

If that does not help, try adjusting your screen resolution.

---

### Post by Dogers on 2005-11-12
Neither of those worked unfortunately, so I just threw in the towel and reinstalled! Alls fine now, thanks for the ideas though! :)

---

