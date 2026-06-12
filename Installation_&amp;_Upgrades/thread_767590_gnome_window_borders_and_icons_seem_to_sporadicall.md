---
title: "gnome window borders and icons seem to sporadically refresh"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by kacheng on 2008-04-25
I've just completed a dist-upgrade from Gutsy to Hardy.

This is a minor issue, but the Gnome window borders and icons seem to sporadically refresh themselves.
They switch to some Gnome default style/theme for a second and then back to 'Ubuntu Human'.
This is especially noticeable when I start a program like Synaptic.  

Any ideas how to fix this?  It seems to cause some slowness when starting programs.

Thanks

---

### Post by kacheng on 2008-04-26
I think this message has something to do with the problem.

It pops up as a dialog box after 5-10 mins from login.
I tried reinstalling Gnome and Metacity already.

Any idea what this means?  
Thanks.


```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

GNOME will still try to restart the Settings Daemon next time you log in.
```

---

### Post by kacheng on 2008-04-26
Tried deleting 

/home/user/.gconf
/home/user/.gconfd
/home/user/.gnome2
/home/user/.gnome2_private
/home/user/.metacity

No changes.

---

### Post by kacheng on 2008-04-28
Even after this morning's updates, which included gvfs and gtk2 updates, I still get the "There was an error starting the GNOME Settings Daemon." error dialog box.

Anybody have any suggestions as to what else I may try?

---

### Post by kacheng on 2008-05-01
This is definitely profile related.

Another profile runs properly and very quickly.

Can anyone give pointers on how to completely reset a profile?

Thanks.

---

