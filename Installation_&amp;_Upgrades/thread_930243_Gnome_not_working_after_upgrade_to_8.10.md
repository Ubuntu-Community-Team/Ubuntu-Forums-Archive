---
title: "Gnome not working after upgrade to 8.10"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by The Desert Fox on 2008-09-25
Hey There
I just upgraded to 8.10 yesterday and after the reboot gnome never came up. It always gets me to the console. I have tried changing the terminal using Ctr-Alt-F6 but I get a blank screen. It does try to start the "Gnome Display Manager" but I dont see it. I only see a blank screen even tho gnome appears to be running. 
Regards

---

### Post by The Desert Fox on 2008-09-25
Here is what  I see in the sys log:
Glib Critical g_hash_table_lookup_extended assertion 'hash_Table != NULL' failed

ALso in gdm log i see:
Module ABI major version (0) does not match the screen version (1)
Failed to load module "dri"
VESA no valid monitor
Screens found but none have a usable config.

---

### Post by cariboo on 2008-09-25
You would be much better off asking your questions here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

There are a lot of smart prople that only look in this forum.

It looks to me like you've got a video driver problem, have you tried booting into recovery mode and tried xfix?

Jim

---

### Post by chemical0815 on 2008-09-26
^_^

---

### Post by The Desert Fox on 2008-09-26
Thanks I have tried that already. I will try a new driver. Why is Chemical0815 sad?

---

### Post by The Desert Fox on 2008-09-27
Ok updating everything with aptitude fixed it. Yay! Thanks for helping out.

---

