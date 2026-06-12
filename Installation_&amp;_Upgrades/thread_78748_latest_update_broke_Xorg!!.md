---
title: "latest update broke Xorg!!"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by brainsick on 2005-10-18
Hello,

I have a Ubuntu 5.04 machine and I just did the last batch of updates (two su-related packages) and I can no longer boot into the Desktop.  The following is the only thing I see in the logs:

Oct 18 20:38:19 localhost gconfd (todd-7260): starting (version 2.10.0), pid 7260 user 'todd'
Oct 18 20:38:19 localhost gconfd (todd-7260): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct 18 20:38:19 localhost gconfd (todd-7260): Resolved address "xml:readwrite:/home/todd/.gconf" to a writable configuration source at position 1
Oct 18 20:38:19 localhost gconfd (todd-7260): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

It prompts me for the login, and it displays a blank brown screen, but GNOME doesn't load any further.

No other changes have been made.

Update: changed ssh-related to su-related

---

### Post by aysiu on 2005-10-18
I have no idea how to solve your problem, but does [this Google search](http://www.google.com/search?hl=en&q=%22xml%3Areadonly%3A%2Fetc%2Fgconf%2Fgconf.xml.mandatory%22&btnG=Google+Search) turn up anything helpful?

---

### Post by brainsick on 2005-10-19
Well, hell if I know what happened.  I walked away from the computer and just let it sit overnight; when I came back in the morning, the desktop was there and everything seemed fine.  'top' never showed anything unusual going on.

Are there other ways to look into what's going on when something like this happens?  /var/log/messages and 'top' are the only things I know about.

---

