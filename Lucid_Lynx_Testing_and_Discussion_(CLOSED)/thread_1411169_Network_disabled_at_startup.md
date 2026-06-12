---
title: "Network disabled at startup"
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ybytyruzu on 2010-02-19
Hello, I installed 10.04 on an Acer Aspire 3100 and is working ok, but after last update these problem appear:
- Network is disabled at start up
- Volume icon disappear
- Shutdown function don't work

Over these items all is running very well.

any ideas about these problems?

Thanks

---

### Post by ybytyruzu on 2010-02-19
HI,

After some restarts networking is ok again.
Still missing volume icon and shutdown don't work.

JC

---

### Post by zika on 2010-02-19
> **ybytyruzu said:**
> Still missing volume icon and shutdown don't work.JCYou're not alone...

---

### Post by cariboo on 2010-02-19
Are you saying networking didn't start, or was the icon just missing? In most cases for me at least, even if the icon isn't in the notification area, networking still works.

---

### Post by bwucke on 2010-04-22
The icon appears, with exclamation mark. Left-clicking on it shows "Networking disabled" popup.
Right-clicking on the icon on some boot-ups shows the menu where I can check "Enable Networking" and everything goes back to norm. On some boot-ups it shows nothing at all, and I have to reboot to get network back.
I am 100% positive I have NOT disabled networking prior to this when it happened this morning. The system has not shut down cleanly (battery ran out while in sleep mode) and on new boot I could not use the net - it was disabled and the right-click menu was gone.

---

### Post by BrokeMahPC on 2010-04-22
I disabled networking - forgot about it and logged off. Logged in this morning and could not get networking to start even by selecting "Enable Networking". I found if you left click on the networking applet and choose "auto ethernet" it starts.

Panel trouble - messed up my panel in the past - use this to restore the default panel, have not used it since karmic so just tried it in lucid - still works! Code:     
```
gconftool-2 --recursive-unset /apps/panel
```
```
killall gnome-panel
```

---

### Post by null_pointer_us on 2010-04-22
Resetting the gnome panel did not fix the "networking disabled at startup" issue, but I wondered how to reset the panel. Thank you!

Sometimes 10.04 boots with auto eth0 disabled. Other times it starts enabled. :confused:


EDIT:

For those who lost their volume icon, this was apparently moved to a different panel applet some weeks ago. I right-clicked on the top panel and used [COLOR="Sienna"]Add to Panel...[/COLOR] to add an [COLOR="Sienna"]Indicator Applet[/COLOR].

---

