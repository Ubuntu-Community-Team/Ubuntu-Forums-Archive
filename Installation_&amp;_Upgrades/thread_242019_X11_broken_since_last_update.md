---
title: "X11 broken since last update"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by mcptron on 2006-08-23
since the last update of xserver-xorg-core to version 1:1.0.2-0ubuntu10.4, x11 does not start any more on my nc6000 hp notebook.

i've looked at xorg.conf which has not been modified during update. how can i repair the situation fromout the text console?

thx & rg.
michael

---

### Post by Scythe!? on 2006-08-23
sudo apt-get update

sudo apt-get install xserver-xorg-core

sudo reboot

This got my X back on its feet.

---

### Post by mcptron on 2006-08-23
yup, after upgrading to 1:1.0.2-0ubuntu10.4 everthing works fine again.

thx & rg.
michael

---

### Post by suwongca on 2006-08-23
Hey Dude, my undying gratitude goes to you.  Saved my live on this one.  Your suggestion worked perfectly.  Hugs and Kisses ... Susie

---

