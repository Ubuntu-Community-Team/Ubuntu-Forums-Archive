---
title: "Disable 'Are you sure you want to close all programs and log out of the computer?'"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubername on 2010-04-15
I have tried
gksu gconf-editor
apps>gnome-session>options> uncheck the 'logout prompt' option, but it makes no difference.

(This is when I select 'logout' from the me-menu I think - it's in the Indicator applet area with my user name and a speech bubble to the left, a logout button to the right.)

Anyone know how to get rid of this? ctl-alt-del brings up a menu which doesn't include logout, but shutdown and restart which work without prompts.

Edit - also tried gconf-editor (without gksu) as I realised that I needed to change the settings for my user rather than root. Still no joy.

---

### Post by 101011010010 on 2010-04-15
Hello, have you tried ? > gconf-editor/apps/indicator-session/suppress_logout_restart_shutdown I hope this helps.

---

### Post by grandtoubab on 2010-04-15
yes

---

### Post by ubername on 2010-04-20
> **101011010010 said:**
> Hello, have you tried ?  I hope this helps.

Thanks, that works.

(No idea why the 'gconf-editor/apps/indicator-session/suppress_logout_restart_shutdown' wasn't quoted along with the rest of your post!)

---

### Post by aviramof on 2010-04-20
I Use ubuntu tweak it has an option there to do that and it's much easier then
'gconf-editor/apps/indicator-session/suppress_logout_restart_shutdown' i the is 
also an option to remove mounted drives from desktop whcih is also easier then 'gconf-editor'

---

