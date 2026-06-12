---
title: "Gutsy and 700m, xinerama possible?"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Oreo on 2007-11-06
Does anyone using Gutsy with a Dell 700m laptop have xinerama working on a second monitor? If so please send me your xorg.conf!

I can get Xinerama working if I define the 700m display as a plug and play monitor (making that setting using Administration > Screens and Graphics). But I haven't found a setting that will allow the 700m screen to run with 1280 by 800 resolution. Also in this mode, some graphics don't work, like icons in Openoffice.

Or if I delete my xorg.conf and start over, the default xorg.conf that is created makes a good _clone_ monitor setup, and the graphics work. But I fail in getting this changed into a Xinerama setup.

I have tried making a large Virtual screen in the xorg.conf, such as 
Virtual    2048  2048
and to use xandr.
After doing this, is there an xandr command that will set up xinerama? It looks like from the message boards that I do this using Screens and Graphics.

BUT if I start the Screens and Graphics program after this, it zaps the good-working xorg.conf, and what replaces it often won't work. The replaced xorg.conf also doesn't retain the virtual setting 2048x2048.

Help!
Oreo

---

### Post by Oreo on 2007-11-06
Also the message boards mention using the older i810 driver rather than the new intel driver. I assume this means that the i810 driver in Gutsy is still the old one, right?

---

### Post by Oreo on 2007-11-11
Just in case anyone ever is interested, see my answer at:

[http://ubuntuforums.org/showthread.php?p=3753963#post3753963](http://ubuntuforums.org/showthread.php?p=3753963#post3753963)

---

