---
title: "Gnome-Panel follows mouse"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scaine on 2009-08-13
Anyone else confirm this?  Just set your gnome-panel to NOT "expand".  You should now have a gnome-panel centred in your display.  Now, put your mouse over the panel, anywhere, and watch it drag itself around with your mouse.

I even managed to get it to break from the top of the screen!  The whole gnome-panel following my mouse like a pointer...

The only way to stop this behaviour is to click on it somewhere.  Very strange.  If someone else confirms, I'll raise a bug (probably tomorrow, because it's nearly midnight and I need sleep).

[EDIT : I've just changed my panel back to non-expand mode again and it's fine.  If anyone can be bothered, please try rebooting with the panel in non-expand mode to see if it's reproducible]

---

### Post by wayne_cat on 2009-08-13
tested ..

- switched to "not expanded"
- rebooted

everything is ok on my system

---

### Post by phenest on 2009-08-14
No problems here.

---

### Post by scaine on 2009-08-14
Thanks everyone.  Every reboot now sees my gnome-panel situate itself about 2/3'rds of the way down the screen.  I can only move it back to the top by ticking "expand", then unticking it again.  Very strange.

Probably a side effect of the custom ATI drivers I'm testing from an earlier thread.  I'll dig that thread out and see if I can find a launchpad bug on it.  If not, I'll try to create one.

---

### Post by wayne_cat on 2009-08-14
> **scaine said:**
> Thanks everyone.  Every reboot now sees my gnome-panel situate itself about 2/3'rds of the way down the screen.  I can only move it back to the top by ticking "expand", then unticking it again.  Very strange.

Probably a side effect of the custom ATI drivers I'm testing from an earlier thread.  I'll dig that thread out and see if I can find a launchpad bug on it.  If not, I'll try to create one.


The packages from xorg-edgers or ubuntu-x-swat?

---

### Post by scaine on 2009-08-14
x-swat.  I don't use the edgers stuff, man, I'm too scared...  :)

From this post by Bryce : [http://www2.bryceharrington.org:8080/drupal/node/84](http://www2.bryceharrington.org:8080/drupal/node/84)

---

### Post by wayne_cat on 2009-08-14
I use them on a second Karmic partition:

- ATI x1600 Mobile
- Gnome + all updates from today
- Compiz enabled

sorry ... no problems with this constellation :(

---

