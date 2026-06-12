---
title: "White screen after Hardy install / login"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by diegolaz on 2008-04-26
I upgraded to Hardy with the upgrade manager. Took like 8-10 hs but all went ok.
After reboot I login and heare the post "login music" but get a white screen with nothing to do. With CTRL + ALT + BACKSPACE I get back to login screen.... but same happends each time I login.
Any idea? thanks!
Diego

EDIT: When I click CTRL + ALT + BACKSPACE to go back to login screen, I see the wallpaper for a second (no buttons or anything just the wallpaper)

---

### Post by nebu on 2008-04-26
before the update u were using some driver to support ur graphics card which hardy does not support....
(some thing like this happened to me with the fiesty-gutsy update)

(eg. you may have been using compiz with your old graphics driver but the new one which comes along with hardy is not supporting ur graphics card to run compiz.... so when compiz is started.... ur desktop goes white)

best thing to do is to close x server..... then reconfigure the package xserver.xorg

---

### Post by diegolaz on 2008-04-26
Thank you! I managed to enter in "GNOME FAILSAFE" tried to update but it said I was up to date, so I restarted and it's working ok now. although compiz is not working very good...
But the main problem is solved.
Thanks

---

### Post by eschenbach on 2008-05-03
Hey! I have the same problem with the white screen, what exactly did you do? My GOME FAILSAFE and KDE is also working, what did you try to update? I reinstalled xserver-xorg in Synaptic and restarted but there was a white screen in Gnome again...
thanks, Eschenbach

EDIT: Sorry, I managed it by myself, Thanks anyway!

---

