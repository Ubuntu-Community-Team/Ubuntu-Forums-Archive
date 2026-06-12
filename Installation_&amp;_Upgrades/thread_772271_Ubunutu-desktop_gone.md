---
title: "Ubunutu-desktop gone"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by anuban on 2008-04-28
I was running Evolution and suddenly my machine stopped responding. I did a hard reset. After that I don't see anything on my desktop. Desktop wallpaper is intact, besides that I don't see the two bars, any icon, nothing. I don't see anything except a wallpaper.
When I run in Failsafe mode, everything works fine.
I am not sure what I need to do run my machine as usual.
I am running a clean install Hardy with dual boot Vista on a Dell Inspiron 1505.
Please help.

---

### Post by ryanhaigh on 2008-04-28
Try pressing alt-f2 to bring up the run dialog and enter gnome-panel, then do the same again and enter nautilus

---

### Post by anuban on 2008-04-28
What do I do after entering nautilus?

---

### Post by ryanhaigh on 2008-04-28
Did your panels and desktop icons come back up? running gnome-panel should bring back the 'bars' and nautilus should show your desktop icons.

EDIT: just to be clear you have to press enter after entering gnome-panel and again after entering nautilus.

---

### Post by anuban on 2008-04-28
Got the trick:

[LIST]
[*] Press CTRL+ALT+F2
[*] Login and password
[*] sudo apt-get remove gnome-panel
[*] sudo apt-get install gnome-panel
[*] sudo apt-get install ubuntu-desktop.
[*] Restart...
[/LIST]
everything should be fine.:)

Thanks for the help guys...

---

