---
title: "startup issue with 6.10"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by dowbjts on 2007-01-17
I recently upgraded from 6.06 to 6.10 on a Dell L400 laptop (ATI mobility video)

When 6.10 boots, my screen goes blank when the gnome desktop tries to load.

If I boot in recovery mode, I can get to the command line and can type in "startx" the gnome desktop loads...(except I don't have the shutdown and restart choices)  but, everything else works ok.

I've fiddled with re-configuring the x-server xorg setup...but still can't get it to crank up the desktop on a normal boot sequence.

Kinda disappointing since everything worked fine in 6.06.  Must be some bug in the upgrade?

Any tips are appreciated!  I need to either fix this or re-install 6.06 (any easy way to "undo" the upgrade???)

thx!

---

### Post by lukew on 2007-01-17
> **dowbjts said:**
> I recently upgraded from 6.06 to 6.10 on a Dell L400 laptop (ATI mobility video)

When 6.10 boots, my screen goes blank when the gnome desktop tries to load.

If I boot in recovery mode, I can get to the command line and can type in "startx" the gnome desktop loads...(except I don't have the shutdown and restart choices)  but, everything else works ok.

I've fiddled with re-configuring the x-server xorg setup...but still can't get it to crank up the desktop on a normal boot sequence.

Kinda disappointing since everything worked fine in 6.06.  Must be some bug in the upgrade?

Any tips are appreciated!  I need to either fix this or re-install 6.06 (any easy way to "undo" the upgrade???)

thx!
[

Does: 

CODE]
sudo dpkg-reconfigure xserver-xorg[/CODE]

fix the issue?

---

### Post by dowbjts on 2007-01-17
nope.  I ran that and it didn't fix it.

---

### Post by lukew on 2007-01-18
> **dowbjts said:**
> nope.  I ran that and it didn't fix it.

which drivers are you using? Try swapping nvida with nv or swapping fglrx with ati; start from there and see what does work!

Thanks

Luke

---

