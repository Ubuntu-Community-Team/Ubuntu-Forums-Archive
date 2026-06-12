---
title: "Desktop icons missing after 12.10 upgrade"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by nLinked on 2012-10-20
As the title suggests, my desktop icons don't show on the desktop after I upgraded to 12.10 from 12.04. Also, I can't right-click on the desktop - no menu appears. Everything else seems OK though. What could it be?

If I open Nautilus, my desktop icons and files are still there in my Desktop folder.

---

### Post by Frogs Hair on 2012-10-20
Make sure the Advanced Settings/ Gnome Tweak tool is installed . There is a new version in 12.10 for Gnome 3.6 .I don't know if it would have been replaced during the upgrade since I did a clean installation . That is where the desktop icons and nautilus control desktop settings are.

---

### Post by nLinked on 2012-10-20
> **Frogs Hair said:**
> Make sure the Advanced Settings/ Gnome Tweak tool is installed . There is a new version in 12.10 for Gnome 3.6 .I don't know if it would have been replaced during the upgrade since I did a clean installation . That is where the desktop icons and nautilus control desktop settings are.

That fixed it, thanks!

---

### Post by Frogs Hair on 2012-10-20
You're Welcome ! :)

---

### Post by lateatnight on 2012-10-24
Thank you, you helped me too :)

---

### Post by Dobly on 2013-02-28
> **Frogs Hair said:**
> Make sure the Advanced Settings/ Gnome Tweak tool is installed . There is a new version in 12.10 for Gnome 3.6 .I don't know if it would have been replaced during the upgrade since I did a clean installation . That is where the desktop icons and nautilus control desktop settings are.

So, after an update today I'm on a desktop with no icons, no side menu, nothing. Alt-T got me a terminal and I am able to run Firefox. Here I am. 

How do I 'make sure I have Advanced Settings/ Gnome Tweak installed?

---

### Post by phoenix90005 on 2013-03-26
> **Dobly said:**
> So, after an update today I'm on a desktop with no icons, no side menu, nothing. Alt-T got me a terminal and I am able to run Firefox. Here I am. 

How do I 'make sure I have Advanced Settings/ Gnome Tweak installed?

that's my question too ..... and how do apply Advanced Settings/ Gnome Tweak through terminal ?
what shall i do ?

---

### Post by phoenix90005 on 2013-03-27
hey guys i found a solution and it worked for me just fine 

from terminal type this :

[B]unity --reset-icons

[/B]to return UNITY interface to original state, type:
[B]unity --reset


[/B]to return COMPISE to its original state, type:
[B]gconftool-2 --recursive-unset /apps/compiz-1  unity --reset
[/B]
again type this command for the last time:
**unity --reset**

then log out or restart the system .
that's it... hope that would work

---

