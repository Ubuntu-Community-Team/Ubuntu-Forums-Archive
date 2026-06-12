---
title: "compiz fusion on ubuntu 8.10"
date: 2008-08-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by donjo on 2008-08-29
how to enable back my compiz fusion??
before this i'm using ubuntu v  8.04,
but now i'm upgrade using v 8.10

so how to enable back the compiz settings??

what step that i try before was i have uninstalled it, 
and then reinstall back, but still can't use it ..

---

### Post by Crafty Kisses on 2008-08-29
Try the following: ```
compiz --replace
```

---

### Post by donjo on 2008-08-29
scorps@scorps-laptop:~$ sudo compiz --replace
[sudo] password for scorps: 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'notification'
Couldn't find a perfect decorator match; trying all decorators
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'fs'
Window manager warning: Failed to load theme "Human-Murrine": Failed to find a valid file for theme Human-Murrine

/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

this what i got,
well it's working now thanks.

---

### Post by donjo on 2008-08-29
why i can't use the desktop cube effect, rotate cube and so on in compiz fusion??

just a little setting that i can use,
it's not about conflict, it's just can't working, even i have enable it

---

### Post by overdrank on 2008-08-29
> **donjo said:**
> why i can't use the desktop cube effect, rotate cube and so on in compiz fusion??

just a little setting that i can use,
it's not about conflict, it's just can't working, even i have enable it

Hi and when you moved to intrepid you may have to reinstall your nvidia drivers. What is the model of the graphics card?

Moved to Intrepid :)

---

### Post by Caseyjp on 2008-08-29
> **donjo said:**
> why i can't use the desktop cube effect, rotate cube and so on in compiz fusion??

just a little setting that i can use,
it's not about conflict, it's just can't working, even i have enable it

If you have no video driver problems, realize that some settings may have gone back to default.  open the compiz settings manager (under system preferences) and under "general" select the "desktop size" and make it "4".

Also the 'desktop' section, ensure the "desktop cube" "rotate cube" choices are enabled.

---

### Post by SaThaRiel on 2008-08-29
> **donjo said:**
> scorps@scorps-laptop:~$ sudo compiz --replace
[sudo] password for scorps: 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'notification'
Couldn't find a perfect decorator match; trying all decorators
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'fs'
Window manager warning: Failed to load theme "Human-Murrine": Failed to find a valid file for theme Human-Murrine

/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

this what i got,
well it's working now thanks.

Assuming that its not working (after reading your next post). None said that you should use sudo. Just try```
compiz --replace
```without sudo.

Good luck.

---

### Post by donjo on 2008-08-30
> **Codename said:**
> Try the following: ```
compiz --replace
```

hey man, why the settings just temporary??
after i reboot or shutdown computer ,,
and turn on back, the settings is gone,
i need to re enable back the command above,

so how to make it permanently ???

---

### Post by olskar on 2008-08-30
Rightclick on desktop and choose to change background, then turn on desktop effects? Or that does not work?

---

