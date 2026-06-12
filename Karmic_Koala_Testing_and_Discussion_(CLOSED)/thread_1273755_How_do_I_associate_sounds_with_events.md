---
title: "How do I associate sounds with events?"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-09-23
Hi, The title says it. I especially want to disable the login sound which has just started to play each time I boot. There used to be a dialog "gnome-sound-properties" for setting sound events but it doesn't exist on my system any more. I wonder if it should?
Cheers, Mike

---

### Post by ktraub on 2009-09-24
bump

---

### Post by DOSn3rd on 2009-09-24
Go to System > Preferences > Sound and click on the "Sounds"-tab ;D

---

### Post by HomerSp on 2009-09-24
Currently it doesn't seem like you can edit the themes directly, so I suppose you could try and go to /usr/share/sounds/ubuntu/stereo and rename/remove the sounds you don't want (although I'm not sure exactly what would happen when the system is trying to play a sound that's missing).

---

### Post by Nerd_bloke on 2009-09-24
There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700") in launchpad.

But it hasn't been reported [upstream]("https://bugzilla.gnome.org/buglist.cgi?product=gnome-media&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&component=gnome-volume-control") against gnome-volume-control so likely won't get fixed.

---

### Post by mdurham on 2009-09-24
> **HomerSp said:**
> Currently it doesn't seem like you can edit the themes directly, so I suppose you could try and go to /usr/share/sounds/ubuntu/stereo and rename/remove the sounds you don't want (although I'm not sure exactly what would happen when the system is trying to play a sound that's missing).
Yes thanks, I thought of doing that. I'll replace with a short silence.
Cheers, Mike

---

### Post by mdurham on 2009-09-24
> **Nerd_bloke said:**
> There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700") in launchpad.

But it hasn't been reported [upstream]("https://bugzilla.gnome.org/buglist.cgi?product=gnome-media&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&component=gnome-volume-control") against gnome-volume-control so likely won't get fixed.
Thanks for that Nerd bloke, that explains everything.

---

