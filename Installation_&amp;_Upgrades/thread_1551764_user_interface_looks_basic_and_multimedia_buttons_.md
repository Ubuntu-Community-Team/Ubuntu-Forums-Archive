---
title: "user interface looks basic and multimedia buttons dont work"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by lucubrator on 2010-08-12
Hi everyone - I'm a new user and this is my first post so I'd like to start by saying thanks to all the developers and community members that make using lucid so easy. 

So I updated Lucid yesterday, and when I restarted the user interface was changed to a more simple feeling display. This makes me think I'm stuck in a "basic" mode or something. I attached a screen shot, but to give you an idea ill describe some issues. For one thing the minimize buttons are now on the right. The volume control, which used to appear on the top right of the screen, is gone and my multimedia volume control buttons on my Inspiron 1420 no longer work. Furthermore, the command terminal is now white and the keyboard shortcuts for copy and past don't work. 

Immediately after updating I also got an error message at login (which also appears different and gives options on bottom of screen like gnome Failsafe) which said something like "gnome default power management installed incorrectly...". I followed the advice of a forum thread that involved the purge command and that seemed to remedy that message.

Anyhow, I greatly appreciate any and all help.

Thanks

---

### Post by LADmaticCA on 2010-08-12
It appears that something has gone wrong with your theme, or it got changed. Try right clicking on the desktop and choose "Change background". Next select the "Theme" tab and try selecting Ambiance or Radiance.

On the missing volume control... try reloading the gnome-panel. Open the terminal (Applications>Accessories>Terminal) and type:

```
killall gnome-panel
```

If that doesn't work you may have to manually add it back.

Right click on the panel and select "Add to panel" Scroll down and select "Indicator Applet"

I don't have a suggestion for the multimedia buttons not working. Maybe someone else can help.

---

