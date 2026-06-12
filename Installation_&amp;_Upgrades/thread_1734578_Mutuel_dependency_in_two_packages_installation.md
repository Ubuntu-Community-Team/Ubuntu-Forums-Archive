---
title: "Mutuel dependency in two packages installation"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by hissou86 on 2011-04-20
[SIZE=4]Hi every body,

I wanted to install [COLOR=Navy]**playonlinux**[/COLOR] under my *ubuntu10.04 *in order to run IE7 for test purposes.
So,...
When i launched the installation, it mentioned that it depends on [COLOR=Navy]**python-wxgtk2.8 **[/COLOR]so i went to the "*Ubuntu.packages*" and downloaded it but when trying to install it, i found out that it depends on [COLOR=Navy]**python-wxversion2.x**[/COLOR] so i tried to install it but its dependency was on python-wxgtk2.8 ( i am in [COLOR=Red]**cycle**[/COLOR] now).

I didn't find the solution, i need your help please,

regards 
[/SIZE]

---

### Post by hissou86 on 2011-04-25
[CENTER][SIZE=4]I found the answer, we have just to use the fact of editing *_[COLOR=Blue]**sources.list** [/COLOR]_*file and add the appropriate source of the needed package. Because it's a bad habit to install manually the packages[/SIZE]
[/CENTER]

---

