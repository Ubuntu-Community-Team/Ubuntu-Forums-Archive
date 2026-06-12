---
title: "update today broke likewise-open"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gmoore777 on 2010-03-22
I updated 2 LucidLynx machines today (one 64-bit, one 32-bit).
After rebooting (twice), I can no longer log into the machines with my ActiveDirectory username. 

Local Linux account works fine.

There was a likewise-open package in the update, but that did not break it, as on machine #2, i have yet to update that one package.

I do have a posting in the Likewise-Open forum: [http://www.likewise.com/community/index.php/forums/viewthread/649/](http://www.likewise.com/community/index.php/forums/viewthread/649/)


On the upgrade with machine#2, i did get this message (did not get this with the upgrade on machine#1):

 Incompatible PAM profiles selected.
 The following PAM profiles cannot be used together:
 Likewise Open, Winbind NT/ Active Directory authentication.
 Please select a different set of modules to enable.

I believe it was installing the "libpam-gnome-keyring" package
when it popped open that window. 

Does anyone have a clue of what happened?

Anyone have a clue of which package clobbered the likewise-open installation?

---

### Post by gmoore777 on 2010-03-23
i fixed my problem. I posted it at the likewise forum here:
[http://www.likewise.com/community/index.php/forums/viewthread/649/](http://www.likewise.com/community/index.php/forums/viewthread/649/)

---

