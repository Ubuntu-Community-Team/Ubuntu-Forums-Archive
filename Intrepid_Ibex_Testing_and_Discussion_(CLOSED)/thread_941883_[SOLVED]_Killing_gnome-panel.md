---
title: "[SOLVED] Killing gnome-panel"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by benzo8 on 2008-10-08
I used to be able to go to gnome-session-properties, and in there find the gnome-panel, set it to "Normal" rather than "Refresh" and issue a "killall gnome-panel" to get rid of the little bugger... In Intrepid, I don't seem to have that option and can find no other way of removing the gnome-panel once and for all... Any ideas?

---

### Post by rsambuca on 2008-10-08
Can't you just right-click and "Delete this panel"?

---

### Post by benzo8 on 2008-10-08
Nope - the final panel has that option greyed out...

---

### Post by benzo8 on 2008-10-09
In contrary to the swathe of "WTF! Bugs in a beta!" posts, I thought the devs might like to know that upgrading 8.10 on top of 8.04 on an Acer Aspire 5610 laptop worked without a hitch, only requiring me to resinstall apps which I had installed from third party sources beforehand...

And yes, this is a shameless bump, because getting rid of this darned gnome-panel would make Intrepid Ibex pretty much perfect for me! Anyone? Bueller? Bueller?

---

### Post by taavikko on 2008-10-09
> **benzo8 said:**
>  Anyone? Bueller? Bueller?

Lol, Ferris....

If you don't need gnome-panel, why you won't remove it.
That pretty much solves your annoyances with it?

```
sudo apt-get -s remove gnome-panel
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatiedot... Valmis        
Seuraavat paketit POISTETAAN:
  fast-user-switch-applet gnome-applets gnome-panel ubuntu-desktop
0 päivitetty, 0 uutta asennusta, 4 poistettavaa ja 0 päivittämätöntä.
Remv ubuntu-desktop [1.119]
Remv fast-user-switch-applet [2.24.0-0ubuntu2]
Remv gnome-applets [2.24.0.1-0ubuntu1]
Remv gnome-panel [1:2.24.0-0ubuntu1]

```

That was just a Simulated run. Don't mind the jibberish language, just 
Finnish...

---

### Post by benzo8 on 2008-10-09
I always worry when something says "Remove ubuntu-desktop"... I assume that isn't as painful, or final, as it sounds then? Because if not, this is the ideal solution...

---

### Post by taavikko on 2008-10-09
> **benzo8 said:**
> I always worry when something says "Remove ubuntu-desktop"... I assume that isn't as painful, or final, as it sounds then? Because if not, this is the ideal solution...

ubuntu-desktop is just meta-pkg that installs its dependencies.
note: for proper updates on ubuntu desktop this pkg needs to be installed.

you can always install it back if you choose to.

---

### Post by MacUntu on 2008-10-09
*double post*

---

### Post by benzo8 on 2008-10-09
> **taavikko said:**
> ubuntu-desktop is just meta-pkg that installs its dependencies.
note: for proper updates on ubuntu desktop this pkg needs to be installed.

you can always install it back if you choose to.

Reinstalling ubuntu-desktop (obviously) wants to reinstall gnome-panel too, so I'll leave it uninstalled for the moment and try and remember that if something major breaks to reinstall it and see if that fixes things.

Thanks for all you help...

---

### Post by Sam Lars on 2008-10-14
So did that work out for you?  I know in Hardy if you removed gnome-panel it would keep you from logging in correctly... it would crash or you'd get a blank background or something.  That's why I was doing the same removing it from the session trick.
Is it safe to remove gnome-panel or is it still needed to log in properly?

Edit: Yes, I'm pretty sure it is.  I removed gnome-panel and a bunch of its cousins, and Gnome loaded fine.  So I guess now it's an even war between XFCE and Gnome...

---

### Post by MaX on 2008-10-14
Why run gnome without the panel?

Why not run xfce with nautilus as your filebrowser instead?

---

### Post by MaX on 2008-10-14
Oops double post...

---

### Post by phenest on 2008-10-14
> **MaX said:**
> Why run gnome without the panel?

Because some of use use an alternative, such as AWN.

---

### Post by Sam Lars on 2008-10-14
> **MaX said:**
> Why not run xfce with nautilus as your filebrowser instead?

That's an interesting idea...
I tried it a while ago but couldn't make much from it.  I didn't give it much time, though.

Edit: I'm using it right now and loving it, thanks for the suggestion!

---

