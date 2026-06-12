---
title: "firefox only bootable as superuser"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SpenceMakesSense on 2009-09-08
When attempting to boot firefox from an icon on the desktop or within menus it does seem to want to boot. When booting from the terminal it gives no output just goes back to the command line. It only seems to be able to boot when running sudo firefox. 

When I do this it loads all my personal settings and such which from my experience it shouldn't it should load the personal settings of the root user.

Strange as it is when running gksu firefox it loads the root users settings. 
Anyone know whats up?

---

### Post by cariboo on 2009-09-08
No Firefox should load root's seetings, as there are none. Check ownership and permission of the ~/.mozilla directory. Mine is owned by my user and has a permission of 750.

BTW you don't boot a program, you just start it. :)

---

