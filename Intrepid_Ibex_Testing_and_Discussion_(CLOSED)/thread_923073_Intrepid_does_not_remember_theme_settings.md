---
title: "Intrepid does not remember theme settings"
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Lucretius on 2008-09-18
I have tried both upgrading from hardy and installing a fresh version of intrepid and the result are the same.

Intrepid boots up into the default gnome environment and on every boot I have to go into "appearance" to restore the human or new-human theme.

Using different theme's/fonts etc has no effect... the results are the same.

---

### Post by Nullack on 2008-09-18
I cant replicate the problem

---

### Post by billyShears on 2008-09-18
I've upgraded from hardy and I've got a similar problem, custom settings for gnome (like theme, mouse speed, keyboard shortcuts) are not loaded on startup until I open preference dialogs like appearance, then everything is loaded correctly. But the biggest problem is that I tried to change mouse pointer acceleration and it got stuck to zero, so the desktop becomes unusable. Luckily that setting is not loaded automatically on startup, so that's not a critical problem.

---

### Post by Lucretius on 2008-09-18
the problem only becomes apparent after installing and enabling the nvidia driver

after restarting the system xorg tends to fail unless I enable "default" settings.

I can then enter the correct resolution using the gnome desktop control panel, however my theme settings are not remembered.

---

### Post by billyShears on 2008-09-18
I've more or less isolated the problem... it looks like /usr/lib/gnome-settings-daemon/gnome-settings-daemon is loaded correctly on startup, but then it terminates (that process is not active after desktop is booted, while I suppose it should). If I start it when desktop is loaded, preferences load correctly, so I've added to startup programs a script that loads gnome-settings-daemon.

---

### Post by anders_c_ on 2008-09-18
i have the same problem and running "gnome-settings-daemon" solves it for me.

---

### Post by Xgen on 2008-09-19
I have the same problem with theme and monitor refresh rate reverting to defaults with a NVidia card...although 'gnome-settings-daemon' is in Sessions. Added in Terminal afterward corrects the theme problem but not the refresh. With the resolution/refresh rate added to 'xorg.conf' all the problems are corrected when restarted.

---

### Post by Lucretius on 2008-09-20
thanks for helping track down the problem.:popcorn:

is it worth waiting for a bugfix or sorting the issue myself?

---

### Post by gjoellee on 2008-09-20
this is may be an issue with GDM. Report this bug to launchpad

---

### Post by billyShears on 2008-09-24
the latest updates fix the problem for me

---

