---
title: "Dell Dimension 2400 - cannot start X"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Lutin on 2009-08-17
Had a go at installing Karmic on a spare computer (Dell Dimension 2400) and, so far, can only get any sense out of it by booting to the command prompt (recovery mode). I cannot get a GUI up at all.

At first I thought it was due to my installing Alpha3 with its attendant warning about Intel integrated graphics. So, I upgraded when Alpha4 was released, but still no joy.

Booting to the root shell, running startx in an attempt to start the Gnome Desktop (background screen comes up, top and bottom taskbars are in place, some icons are installed into the top task bar) when it bombs out with an error message -

.....
(EE) Failed to load module "i810" (module does not exist, 0)
Setting master

waiting for X server to shut down Dropping master
ddxSigGiveUp: Closing log



If I start the machine normally, I get to log-in, the desktop background comes up along with a white cursor arrow and the machine just stalls. A little disk activity for about a minute, but nothing else.

So, any thoughts on this?

---

