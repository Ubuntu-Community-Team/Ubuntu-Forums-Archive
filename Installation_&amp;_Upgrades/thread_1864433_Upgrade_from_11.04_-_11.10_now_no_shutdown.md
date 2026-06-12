---
title: "Upgrade from 11.04 - 11.10 now no shutdown"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by paulec on 2011-10-18
I have upgraded from 11.04 to 11.10 and now have no shutdown button.  The button that previously appeared at the top right corner of my desktop that conained all the options for change user, log out, restart, shutdown etc is no longer present.
 
To shutdown I need to ctr + alt + del and log out then the shutdown button is available from the login screen.

---

### Post by sammiev on 2011-10-18
There is a shut down button on the log in screen, so if you press log off it will take you there. I just hit the power button and it displays a menu of choice. :)

---

### Post by youngunix on 2011-10-19
you don't see a button at the top right corner that looks like a gear?

if not and until you can get it back, you don't need to log out in order to shut down your pc.
Just open your Terminal and type in:
```

sudo poweroff

```

---

### Post by Pesmontis on 2011-10-19
> **paulec said:**
> I have upgraded from 11.04 to 11.10 and now have no shutdown button.  The button that previously appeared at the top right corner of my desktop that conained all the options for change user, log out, restart, shutdown etc is no longer present.
 
To shutdown I need to ctr + alt + del and log out then the shutdown button is available from the login screen.

On my PC, I had to set / reset the Appearance - Theme in order to get the shutdown button:
- click <Dash Home>;
- click <more apps>;
- click <Appearance>;
- in the 'Appearance' window, click the <Theme> drop-down combobox;
- select a different theme, for instance if 'Ambiance' is selected, select 'Radiance'.

On my PC, not all theme settings became visible right away.
I restarted Ubuntu after a good night's sleep, and I found all my desktop icons and buttons nicely & beautifully in place on Unity 2D.

---

### Post by paulec on 2011-10-20
Thanks. That worked a treat.

---

