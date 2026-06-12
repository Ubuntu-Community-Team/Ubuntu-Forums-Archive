---
title: "trying to install nautilus-actions but no luck it's not working"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-13
in synaptic there is nautilus-actions 2.29.90 i installed it but when i press it in system-preference nothing happen i tried installin nautilus-actions-2.29.4.tar.gz but no luck with
install.sh and ./configure what am i doing wrong?

thanks in advance.

---

### Post by aviramof on 2010-02-13
this is the error i'm getting
checking for NAUTILUS_ACTIONS... configure: error: Package requirements (    glib-2.0                >= 2.16.0                gmodule-2.0                >= 2.16.0                gtk+-2.0>= 2.12.0                gconf-2.0                >= 2.8.0            libxml-2.0                >= 2.6.0    libnautilus-extension    >= 2.8.0        sm                >= 1.0.0                        uuid                unique-1.0                                    dbus-glib-1
) were not met:

No package 'glib-2.0' found
No package 'gmodule-2.0' found
No package 'gtk+-2.0' found
No package 'gconf-2.0' found
No package 'libxml-2.0' found
No package 'libnautilus-extension' found
No package 'sm' found
No package 'uuid' found
No package 'unique-1.0' found
No package 'dbus-glib-1' found

---

### Post by mc4man on 2010-02-13
This will get you most of them - 

```
sudo apt-get build-dep nautilus-actions
```

Then 
```
sudo apt-get install libunique-dev
```

If anything else read the configure error and search out in synaptic

The current nautilus-actions is broken, the 2.29.4 will run and you can create actions though last I checked they won't show up in the context menu - maybe it works now, maybe it'll work later...

---

### Post by aviramof on 2010-02-13
thank you very much it's installed everything except dbus-glib-1 which i installed manually 

then i used ./configure then sudo make install in nautilus-actions folder and that it:)

but now after installing it hopefully it was indeded succsefully installed 

i'm not 100% sure how to use it i don't see it in system-preference any way i can check

it was installed correctly and so some tips as to how to use it?

thanks in advance.

---

### Post by mc4man on 2010-02-13
well I built and installed it as a debian package so it did show up in System -> preferences.

You could start it with the command of
```
nautilus-actions-config
```

And see if it works... 
The new config tool is a bit different  than the old one, when it's operational looks to be superior.

(as mentioned didn't work right when I tried last week - haven't tried again since then

---

### Post by aviramof on 2010-02-13
ok i'v tried this and the command don't work but after several tries to install i'v used sudo make install i got the attached file altough i don't sure the installion process worked very well.

any way do you have any tips about how to use it now for instance i want to install [B]

optiPNG from this link:
[http://www.grumz.net/index.php?q=configlist](http://www.grumz.net/index.php?q=configlist)

i installed optiPNG because it's dependece now what?
[/B]

---

### Post by aviramof on 2010-02-14
if i need to see this option in right click menu and i don't that mean that something is 

wrong right?

i don't see anything even when i install picture to wallpaper via the import scheme.

and if that is the case how can i uninstall anything including build-deps?

thanks in advance.

---

