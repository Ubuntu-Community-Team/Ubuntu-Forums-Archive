---
title: "x window managers cant be installed"
date: 2005-02-01
forum: Installation &amp; Upgrades
---

### Post by lycos on 2005-02-01
i have installed via apt-get some x window manager such as golem, openbox, fluxbox, ratpoison, lwm, flwm.
they were installed but when i resterted the computer i saw only fluxbox on the gdm startup window.
the others not exist.
why  :confused:  ?
any suggestion?
thanks for your time...

---

### Post by Sepero on 2005-02-03
When you open your "/etc/gdm/Sessions/fluxbox" file, you should see this:```
#!/bin/sh
#
# /etc/gdm/Sessions/fluxbox
#
# global fluxbox session file -- used by gdm

exec /etc/X11/Xsession /usr/bin/fluxbox
```


Are there files in /etc/gdm/Sessions/ for your other windowmanagers? If not, just create the files like so:```
#!/bin/sh
#
# /etc/gdm/Sessions/ratpoison
#
# global ratpoison session file -- used by gdm

exec /etc/X11/Xsession /usr/bin/ratpoison
```

---

