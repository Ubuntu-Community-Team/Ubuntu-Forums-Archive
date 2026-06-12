---
title: "Thai Keyboard layouts were not available in IBus (14.04, 14.10, 15.04)"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by Suradet_Jitprapaik on 2015-06-21
The Thai Keyboard Layouts were not available in IBus in Lubuntu 14.04, 14.10, or 15.04 (Although they were available during installation but once the installation was completed, the Thai Keyboard Layouts were not there).  For version 12.04, the Thai Keyboard Layouts was available through Lxkeymap.

---

### Post by Rex Bouwense on 2015-06-21
What language did you use for installation?  There should be a country code in your LXPanel.  It will either be a two letter code or a flag.  Right click it and select "Keyboard Layout Handler" settings.  On the right side of the new window you need to un-check keep system layouts.  That will allow you to select Add  a keyboard layout on the left side.  Scroll down to Thai and select it.  You can move it to the top so it will become the default layout if you want.  Before you exit this window you need to re-check keep system layouts for it to be effective.  This will take effect after a reboot.  Now I believe that you have to have the Thai language installed before you do this.  Hope this helps.  It has worked for me in Lubuntu 14.04.

---

