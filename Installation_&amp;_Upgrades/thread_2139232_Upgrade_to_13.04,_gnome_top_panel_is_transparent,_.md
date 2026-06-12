---
title: "Upgrade to 13.04, gnome top panel is transparent, icons enlarged"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by kfstephensii on 2013-04-26
I updated to 13.04, with the Gnome desktop. The top bar is transparent. The icons (battery, network, volume, etc) are very large, black and do not respond to mouse clicks. I attached a screenshot.
This also affects system dialogs (like the "authentication required", and the lock screen). Rather than the former black background, the dialogs are transparent and only the black text is visible. The text box for the password is not visible. This does not affect the gksudo password dialog, tho.
The bottom panel is not affected.

As mentioned, this also affects the lock screen. The clock is displayed on the lock screen but when presented with the 'enter password' dialog, it is also transparent. Plus, the entire screen is transparent so that the desktop can be seen. This does not happen on my 12.10 machine with the same settings (at least before I upgraded to 13.04).

If I use Gnome w/ CairoDock, everything works fine with the top bar. But I don't know if this uses the fallback or the full Gnome.

Not sure what information would be helpful but willing to provide. Thanks

[ATTACH=CONFIG]241806[/ATTACH]

---

### Post by kfstephensii on 2013-04-30
I resolved this problem. I enabled the "User Themes" extension and then applied a theme. All of the transparency problems are fixed.

Thought I would post this in case anyone else encounters this. Although I don't know why I have this problem and apparently no one else does. It makes we wonder if there is a glitch in the update that screwed-up my theme settings. Any useful comments would be appreciated.

---

