---
title: "Startup Applications Preferences"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by dreamquartz on 2010-10-18
I installed Tomboy and after that I started to go through all kinds of different settings and came across "Startup Applications Preferences".
Under Options you can tick "Automatically remember running applications when when logging out" or "Remember Currently Running Application"

I should not have ticked the "Automatically.....", because whatever I do, removing & re-installing Tomboy, it will start up at boot.

Does anyone know where the settings are kept for the "Startup Applications Preferences" so that I can prevent Tomboy from starting up at boot?

---

### Post by Lazaruss on 2010-10-18
Preferences Menu > Startup Applications

---

### Post by dreamquartz on 2010-10-23
> **Lazaruss said:**
> Preferences Menu > Startup Applications

I wish it was that simple. Tomboy does not show up in the Startup Applications.
Somewhere in my Home Folder is the information. 
I created a new temp. user and Tomboy did not start up.
The problem is now that there is a lot of info in my Home Folder, and so far the settings have eluded me.

---

### Post by ChAoS.ct on 2010-11-12
I had the same problem and Finally I solved it!

For some reason Tomboy gets added to the gnome saved session...

[LIST]
[*]Just go to $HOME/.config/gnome-session/saved-session/
[*]Find a .desktop file that mentions tomboy
[*]delete this file
[/LIST]

Tomboy stopped to automatically start itself in every boot!

---

### Post by newbiealan on 2010-11-14
Thank you a good fix, I've been trying to solve this for a while.

---

