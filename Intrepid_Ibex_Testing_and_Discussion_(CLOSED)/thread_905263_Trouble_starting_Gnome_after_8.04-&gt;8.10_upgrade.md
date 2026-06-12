---
title: "Trouble starting Gnome after 8.04-&gt;8.10 upgrade"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by manuska on 2008-08-30
After startup, I get gdm-login window as previously. After I login using Gnome session, all I get is a light brown screen (the default background color).
Kde session works fine.
Gnome-failsafe works fine.
Terminal-failsafe works fine, and if I give command "gnome-session", Gnome starts just fine.

Is it possible that some file from Hardy is left behind and is conflivting with Intrepid? I even created fresh user for Intrepid but problem remains.

.xsession_errors says:
```

Xlib:  extension "RANDR" missing on display ":0.0".
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=fi_FI.
Start IM through /home/manu/.xinput.d/fi_FI linked to /etc/X11/xinit/xinput.d/scim-bridge.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Xlib:  extension "RANDR" missing on display ":0.0".
XIO:  fatal IO error 2 (No such file or directory) on X server ":0.0"
      after 24 requests (6 known processed) with 0 events remaining.
Ikkunointiohjelman varoitus: Vakava IO-virhe 11 (Resource temporarily unavailable) näytöllä ":0".
[Warning: Serious IO-error 11 on screen ":0"]

```

Any ideas besides a fresh install?

---

### Post by dinxter on 2008-08-30
shouldnt need a reinstall i think. seems to be due to left over config data in your home directory. you could either, create a new user giving a fresh set of home directory configs which is nice and simple.

or maybe see if theres a file like .Xmodmap or something similar in your home directory and get rid of that. the ubuntu.xmodmap is in package kdebase-bin for kde3 in hardy, the new ones in intrepid are kde4 and dont have this file so if the failure of xmodmap is the problem you need to get rid of whatever config setting is calling that file

---

### Post by dinxter on 2008-08-30
oh, and it goes without saying, try and make sure your packages are in sync with the new repositories and that nothing important has been removed by a 'smart upgrade'. i recommend using synaptic to keep an eye on what can safely be upgraded and what cant

---

### Post by manuska on 2008-08-30
SOLVED:
After checking all hte settings I could think of I noticed that for some reason gdm had set "Perfom xclient command" as default instead of "Gnome". So as I thought I was starting Gnome, in reality I was using some xclient command....damn..
So now that I actually start Gnome, everything works fine.

---

### Post by TekNullOG on 2008-09-09
How did you change this? I would love to know the solution!

---

### Post by TekNullOG on 2008-09-09
I tried selecting GNOME from the list of session instead of the failsafe GNOME and it worked. It asked me if I wanted to make it default and when I rebooted, it continued to work.

I don't know why it was no longer default after doing updates. Hope this helps others.

---

