---
title: "Theming GDM in Karmic"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pitris on 2009-10-04
Hello guys!
I've installed Karmic to my sister's laptop (jaunty's kernel didn't know her ethernet card) and I've realized that login window (gdm) changed completely. It cannot be customized anymore? Why? Will it be possible to theme it again in future? I'm not going to upgrade my computer anymore if I'm forced to use the default gdm theme.

Thanks for answers,
--pitris

---

### Post by WilyWyrm on 2009-10-04
Hi, pitris.

I've been wondering the exact same thing and it seems that while there isn't a built in way, there IS a way.


1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.

I've tried it myself and it works, though I stuck with the default background image because I sort of like it. :P Hope that helps!

(Source: [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html))

---

### Post by fela on 2009-10-04
Well in karmic they've rewritten the GDM.

I think theming is a feature that's going to be re-implemented, but as it is they're concentrating more on bug fixes and getting it more polished as it's still really new.

---

### Post by samjh on 2009-10-04
I hope this is not another "feature is too complicated" design decision taken by Gnome developers.

---

### Post by pitris on 2009-10-05
@WilyWyrm: Thanks for hints, I've already found this. But this is *NOT* a GDM theming. This is to change wallpaper, GTK theme and fonts, not the GDM theme (you cannot move the login prompt eg.). That's not what I'm looking for.

I found a possible way, maybe. There's a package gdm-2.20 in karmic, which can be installed and replaces the default gdm package. This should be the good old gdm we used to know. But after installing gdm doesn't work, even the Xserver doesn't start. It keeps telling something like "Cannot create /etc/X11/xorg.conf.failsafe" or something like that (I'm not at home and I don't remember the exact frase). I even found a bug report on launchpad regarding gdm-2.20 in karmic (the exact link is at home as well :)).
If anyone can install gdm-2.20 and make it work, it would be highly appreciated I guess.

Thanks.

---

### Post by pitris on 2009-10-05
Here's the link to the bug: [https://bugs.launchpad.net/ubuntu/+source/gdm-2.20/+bug/432316](https://bugs.launchpad.net/ubuntu/+source/gdm-2.20/+bug/432316)

---

### Post by pitris on 2009-10-07
Guys, solved! :D
The thing is that in /etc/gdm/gdm.conf the path to X server binary is wrong. It should be /usr/bin/X, not /usr/X11R6/bin/X as it used to be in jaunty.

The bug report I created is here: [https://bugs.launchpad.net/ubuntu/+source/gdm-2.20/+bug/445256](https://bugs.launchpad.net/ubuntu/+source/gdm-2.20/+bug/445256)

My little tutorial is here: [http://pitris.info/ubuntu](http://pitris.info/ubuntu)

---

