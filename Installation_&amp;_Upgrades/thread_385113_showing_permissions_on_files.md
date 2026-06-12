---
title: "showing permissions on files"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Porta on 2007-03-15
Hi there;
I recently upgraded to Edgy and it went oke, there is one thing that is not quite oke.
On Dapper, when you right-click a file you can see what rights the file has (read,write,execute etc.) even when root is the owner, i mis that in Edgy, is there a way to bring this info back?

regards
Porta

---

### Post by mcduck on 2007-03-15
Press Alt-F2 and run 'gconf-editor'. Then browse to apps/nautilus/preferences and enable 'show_adwanced_permissions'. This should give you back the permissions tab used in previous Gnome versions.

---

### Post by Porta on 2007-03-15
Thanks mcduck, that did the trick:cool: 8).



Regards
Porta

---

