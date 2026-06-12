---
title: "Network Manager applet disappeared after upgrade."
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by charlie_b on 2014-04-21
I've been using Xubuntu 14.04 beta2 for about two months now, with only minor problems. I just did my first major upgrade because the official release date has passed. However my Network Manager applet has disappeared from my system tray, and the clock applet appears twice. I've tried to get the Network Manager applet back by right-clicking on the panel, but it doesn't appear in the list of available options.  The only way I can run the Network Manager at the moment is through the command line. How do I get the applet back?

---

### Post by charlie_b on 2014-04-21
Okay I figured it out. Right click on the system panel, go to panel>add items> and add Indicator panel. The Network Manager applet is part of this.

---

### Post by Dooglus on 2014-04-21
I tried this, but there's nothing like "Indicator Panel" in the list of things I can add:

[IMG]http://i.imgur.com/ZA5xe1B.png[/IMG]

Note that I already have "Notification Area" added, which is where I think the icon used to be.

---

### Post by Dennis N on 2014-04-21
@Dooglus

You need **xfce4-indicator-plugin**. It provides network manager, power manager, and volume. I don't see it in your screenshot. It appears as 'Indicator Plugin' just above 'Keyboard Layouts' on my system. Check the installed status of this. It may not be installed.

You can also access network manager and power manager from  **Menu > All Settings > Hardware Section**.

---

### Post by Dooglus on 2014-04-21
Oh, it turns out I had to install a package called "xfce4-indicator-plugin", and then I could add the Indicator Panel.

When I did, it showed lots of icons I already had, in addition to the networking icon I wanted.  They were all white, ignoring my dark theme, and after a few seconds they all went away and a dialog popped up telling me that the indicator plugin had gone from the panel, and did I want to restart it.  I can restart it over and over, but it only stays up for a few seconds.  I can also try to disable some of the icons I don't want, but that doesn't work either.  Ugh.

---

