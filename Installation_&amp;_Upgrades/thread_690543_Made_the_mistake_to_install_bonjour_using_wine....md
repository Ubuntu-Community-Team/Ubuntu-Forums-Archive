---
title: "Made the mistake to install bonjour using wine..."
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by kristian_nissen on 2008-02-07
I want to run safari on my kubuntu, I installed Wine and installed Safari beta for windows afterwards, but I missed the note that I wasn't intended to install bonjour as well. Now I have bonjour installed as a Wine app and I cant get rid of it again.

I cant uninstall safari or bonjour from wine, what can I do?

---

### Post by lubod on 2008-02-28
This worked for me in the same situation: (Gutsy 7.10 i386 generic)

This MAY (it didn't in my case, but YMMV) cause ALL your previously installed windows programs under wine fail/need reinstallation, so if you care about any of them, DON'T DO IT!

A cleaner way to achieve the same goal is to remove from the wine "registry" the keys that relate to Safari, Bonjour, and Software update, so the install will run again, but I don't know what keys to remove and don't have the patience to hunt them down. Besides is there even a wine equivalent to regedit?

delete eveything under ~/.wine

```
sudo rm ~/.wine
```

reinstall wine (no need to download again):

open /var/cache/apt/archives find the right .deb file for wine, mine is /var/cache/apt/archives/wine_0.9.46-0ubuntu1_i386.deb double click it and click install.

run safari installer again, it should think it is installing for the first time again (mine did).

Of course even then it still doesn't work to browse, it opens but none of the menus/button work, you pretty much have to force quit it :-(

Oddly software update will work (to the extent of checking, and concluding you're up to date, after wine installs its 'gecko html component' (it prompted me to do so).

---

### Post by SIXAXIS on 2008-03-22
There is a wine equivalent to regedit. Just type 'regedit' in the command line and it emulates the Windows one.

---

