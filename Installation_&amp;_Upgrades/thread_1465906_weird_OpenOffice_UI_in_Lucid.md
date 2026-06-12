---
title: "weird OpenOffice UI in Lucid"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by miesogeno on 2010-04-29
what's with the "windows 3.1" looking scrollbars and overall interface in openoffice? is it just in my computer?

i just upgraded karmic into lucid and openoffice was removed (didn't get why, but i had OOo 3.2). when i reinstalled, it looked like this...


[IMG]http://i40.tinypic.com/4h2rn5.png[/IMG]

i tryed looking in the openoffice preferences tabs but didn't get anywhere.
any ideas?

---

### Post by leandromartinez98 on 2010-04-29
In Jaunty there was a package called:  openoffice.org-style-human
that needed to be installed to theme in ooffice looks good (it was
installed by default). There may be an equivalent package in Lucid
for the new themes, that for some reason was not automatically 
installed when you updated.

---

### Post by miesogeno on 2010-04-29
thanks for your answer.

but i dont think thats it. that package is installed, maybe i have to do something else in order for it to work, but i dont think so. notice the icons belong to that package, just the scrollbars and menus aren't looking very good.

but you sent me looking in synaptic and i found something called openoffice.org-debian-menus, and i remember seeing some alert for that during the Lucid Lynx update, like, obsolete package, marking for removal.

i'm not sure if it's that, but its my best guess right now.
anyway synaptics isn't allowing me to install it so i'll look for it else where and i'll try to install it manually.

---

### Post by miesogeno on 2010-04-29
got it!

there's a package in synaptics called openoffice.org-gnome, witch integrates it with gnome, of course. openoffice now uses the desktop theme scrollbars.

obrigado pela ajuda leandro :)

---

