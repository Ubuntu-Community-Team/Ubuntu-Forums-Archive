---
title: "Garnome Installation Howto"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by Permafrost91 on 2006-12-09
I'm back to running Dapper after trying Edgy for a while (which was just too unstable for my taste). But I'd like to run Gnome 2.16 under Dapper so I compiled garnome-2.16.2 into /opt/gnome-2.16.2.

I created a /usr/local/bin/garnome-2.16.2-session file that looks like this:
```
#!/bin/bash

GARNOME=/opt/gnome-2.16.2

PATH=$GARNOME/bin:$PATH
LD_LIBRARY_PATH=$GARNOME/lib:$LD_LIBRARY_PATH
PYTHONPATH=$GARNOME/lib/python2.4/site-packages:$GARNOME/lib/python2.4/site-packages/gtk-2.0
PKG_CONFIG_PATH=$GARNOME/lib/pkgconfig:/usr/lib/pkgconfig
GDK_USE_XFT=1
XDG_DATA_DIRS=$GARNOME/share
XDG_CONFIG_DIRS=$GARNOME/etc/xdg
MANPATH=$GARNOME/man:$MANPATH
DBUS_LAUNCH="$GARNOME/bin/dbus-launch --exit-with-session"

export PATH LD_LIBRARY_PATH PYTHONPATH PKG_CONFIG_PATH \
       GDK_USE_XFT XDG_DATA_DIRS XDG_CONFIG_DIRS MANPATH DBUS_LAUNCH

exec $DBUS_LAUNCH $GARNOME/bin/gnome-session

```

and I have a /usr/share/xsessions/garnome-2.16.2.desktop file that looks like this:
```
[Desktop Entry]
Encoding=UTF-8
Name=Garnome 2.16.2
Comment=Garnome 2.16.2
Exec=/usr/local/bin/garnome-2.16.2-session
# no icon yet, only the top three are currently used
Icon=
Type=Application
#X-Ubuntu-Gettext-Domain=gnome-session-2.0

```

Generally, I have two questions at this point which I have not been able to answer yet through this forums or via Google:

1) when I run the garnome installation from GDM, basically no icons and themes in /usr/share are found and/or used; third party applications I have installed in the meantime (e.g. Xara Xtreme) don't show up in the Gnome Menu any longer ... how can I fix all that? How can I make this fresh compile of Gnome behave just like the version that ships with Dapper? (i.e. as if I just upgraded to Edgy)

2) is there a way to use the GDM installed to /opt/gnome-2.16.2/sbin/gdm instead of the GDM 2.14 that comes with Dapper?*

Thanks for any help!

* EDIT:

I tried setting the GDM executable to /opt/gnome-2.16.2/sbin/gdm in /etc/init.d/gdm and also not heeding the default display manager but all I got was the non-themed version of GDM that logs me into a screwed up version of Dapper's native Gnome 2.14 without giving me the garnome-compiled option.

---

### Post by Permafrost91 on 2006-12-10
no one? seriously?

---

