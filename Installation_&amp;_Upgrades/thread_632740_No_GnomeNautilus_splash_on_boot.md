---
title: "No Gnome/Nautilus splash on boot"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by teamalpha on 2007-12-05
Usually in ubuntu (from 1 month past experience) i have noted that after you logon, but before you see your desktop, there is a gnome/nautilus splash. I recently clean reinstalled gutsy gibbon on my laptop, but to my dismay, the gnome/nautilus splash does not appear anymore. This is just a small problem, but it seems very strange to me. can anyone please help?

this is how it should look:
[IMG]http://debianadmin.com/copper/albums/edgy/3.png[/IMG]

but i do not get this 

thanks in advance!

---

### Post by adamleander on 2007-12-06
Hey, I was wondering that same thing.  I found out somewhere, can't remember where, that if you open up Synaptic Package manager, and search for tweak, you'll find a gtweakui.  Right click it and mark for installation and then apply the changes.  After it installs you will find a "gtweakui - session" option under the Preferences menu (plus a few other neat ones that install as well).  It has an option for a splash screen which show the same things loading as Nautilus did.

Hope it works for you.

---

### Post by banewman on 2007-12-06
There's also the gconf editor in the menu - configuration editor.
Open that and browse to -  apps - gnome-session - options - and there is an option for the splash screen. :)

---

### Post by teamalpha on 2007-12-09
Thanks all. I will check the changes later, dont really have much time. by the way, is this official or unofficial, i dont really feel good a bout messing up my ubuntu, thats why i needed to reinstall...

---

### Post by NilsE on 2007-12-09
You can also install the Gnome Splashscreen Manager, it will show up in System > Preferences and turn it on.

---

### Post by teamalpha on 2007-12-14
Wait a second, when i first installed ubuntu, a clean install over vista:mad:, the first time i booted, that screen showed, even before i saw my desktop, but now it does not do that, even though i still clean installed over ubuntu. if the first time i did this, and it showed before i installed anything, why do i have install something this time? possibly something is corrupted?:confused:

---

