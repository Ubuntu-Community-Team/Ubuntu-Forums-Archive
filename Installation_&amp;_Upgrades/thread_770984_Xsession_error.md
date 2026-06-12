---
title: "Xsession error"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Emperor3434 on 2008-04-27
I just upgraded to Hardy last night and when I first rebooted, it gave me an error on logging in saying "Your session lasted less than 10 seconds..." and then I had to relog in.  When I would try logging in again, it worked a few times. Everything worked fine the second login.  That happened a few times.

Now suddenly I can't log on unless I use a failsafe mode.  I get the same error but now in .xsession.errors this is the output:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/local/bin/startxgl.sh: 2: Xgl: not found

(gnome-session:8318): Gtk-WARNING **: cannot open display: :1
```

I tried searching everywhere for the same error, but can't find out to fix it.  Can anyone help?

---

