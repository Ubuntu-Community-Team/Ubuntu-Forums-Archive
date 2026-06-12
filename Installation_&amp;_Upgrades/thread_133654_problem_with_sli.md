---
title: "problem with sli?"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by lunatec on 2006-02-20
I can get through the entire install...but just get a black screen when it should launch the login.

Help?

---

### Post by Jason_25 on 2006-02-20
SLI with a linux system huh?  Seems like a waste of graphics power.  Anyway, the nv driver probably doesn't support your card(s).  You'll need to ctrl-alt-F1 and then login.  Then 
```

sudo nano /etc/X11/xorg.conf

```
 and change the driver line from nv to vesa.  Then ctrl-O, hit enter, then ctrl-z and reboot (or restart gdm).  That should get you started.  You'll want to load the nvidia driver after you've gotten into the GUI.

---

### Post by Lord Illidan on 2006-02-20
[quote=Jason_25]SLI with a linux system huh?  Seems like a waste of graphics power.  Anyway, the nv driver probably doesn't support your card(s).  You'll need to ctrl-alt-F1 and then login.  Then 
```

sudo nano /etc/X11/xorg.conf

```  and change the driver line from nv to vesa.  Then ctrl-O, hit enter, then ctrl-z and reboot (or restart gdm).  That should get you started.  You'll want to load the nvidia driver after you've gotten into the GUI.[/quote]

Why is it a waste of graphics power? When you can run Quake 4, Quake 3, Doom 3, Unreal Tournament 2004, WoW under Cedega and all the like??

---

### Post by lunatec on 2006-02-21
Tried the above listed, and to no avail. Any idea how to install the nVidia drivers from the command line? I am getting really frustrated now... I hate my own ignorance.:cry:

---

