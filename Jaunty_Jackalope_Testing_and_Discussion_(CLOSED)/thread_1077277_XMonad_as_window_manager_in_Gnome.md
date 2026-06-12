---
title: "XMonad as window manager in Gnome"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by [myrddin] on 2009-02-22
Hi,

does someone know, how to change the window manager from compiz to xmonad in Gnome. Every way I knew, doesn't work anymore with Jaunty (.xsession, startup apps etc). Does someone here know how to do this?

Thanks

---

### Post by taavikko on 2009-02-22
sudo update-alternatives --config x-window-manager

---

### Post by [myrddin] on 2009-02-22
Thanks, but despite changing it to xmonad it still loads metacity. If I do a ```
killall metacity; xmonad
``` after starting Gnome it loads XMonad and I can use it. So XMonad config should be fine, but somehow Ubuntu Jaunty doesn't use the x-window-manager I configured. Do you have another idea?

Thanks.

---

### Post by BwackNinja on 2009-02-22
You could always do it the hackish way, move /usr/bin/compiz to /usr/bin/compiz.old, and make a script in /usr/bin/compiz to start XMonad (remember to chmod +x it :P)

---

