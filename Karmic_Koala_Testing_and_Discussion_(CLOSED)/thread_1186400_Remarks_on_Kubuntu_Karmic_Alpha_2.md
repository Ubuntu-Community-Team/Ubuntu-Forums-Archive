---
title: "Remarks on Kubuntu Karmic Alpha 2"
date: 2009-06-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2009-06-13
I see improvements yet I have the following remarks:

1) I don't see all the new features and plasmids that they added. I can't see the standard Microblogging plasmid or the new animated wallpapers.

2) I have always had a problem with activating the Nvidia driver on Kubuntu (not on Ubuntu with Gnome). When I do, everything looks crisp yet bigger than what it was. It is as if the resolution went down so everything looks a bit big and crowded yet looks detailed and crisp. It gives it a cheap look I can't get around of, not by reducing font size or anything.

3) I really like the new Package Manager front-end on KDE. It almost battles the great frontend on fedora 10-11 with packagekit.

4) I can't connect to secure wireless networks, something others have issues with.

---

### Post by taavikko on 2009-06-13
1. Using main server for sources?
click Alt+ds in desktop and select wallpaper? 

4. plasma-widget-network-manager is little bit buggy at the moment, for me it's always been broken. Alternative, use wicd to work around the issue.
3G modems are also affected by non-functional plasmoid.

---

### Post by Zorael on 2009-06-13
Have you added the Kubuntu ppas? [https://launchpad.net/~kubuntu-ppa](https://launchpad.net/~kubuntu-ppa)

Hmm, browsing them real quick reveals that there aren't many karmic packages there yet, though.

I'm on Jaunty and I have those animated wallpapers and the microblogging widget. *shrug*

---

### Post by PRGUY85 on 2009-06-13
Shouldn't Karmic Alpha 2 be updated on all KDE 4.3 beta 2 packages?

---

### Post by super.rad on 2009-06-13
> **PRGUY85 said:**
> 1) I don't see all the new features and plasmids that they added. I can't see the standard Microblogging plasmid or the new animated wallpapers.

3) I really like the new Package Manager front-end on KDE. It almost battles the great frontend on fedora 10-11 with packagekit.


1. I'm using Kubuntu alpha 2 and I have the new plasmoids and the animated wallpapers.
3. It is the same front-end as Fedora (at least the KDE version), it's just Kpackagekit

---

### Post by Darkshade on 2009-06-13
About #1 - I had the same problem. Install kdeplasma-addons and you're done.

---

### Post by PRGUY85 on 2009-06-14
My biggest issue right now is point #2.  Any ideas about that one?

---

### Post by aldeby on 2009-07-25
It could be the font DPI settings changed. Have a look at System Settings -> Appearance -> Fonts -> Force DPI and play with the options available. A logout and relogin is required for the changes to take effect.
Cheers

---

### Post by Asraniel on 2009-07-25
2) thats the DPI issue, change the dpi settings and your fine

---

