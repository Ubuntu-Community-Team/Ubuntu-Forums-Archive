---
title: "problem after upgrade"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by matt91 on 2007-04-20
i upgraded to 7.04 (using update manager) and my desktop now first comes up with the error:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

then the top and bottom taskbars load up very slow, and even more slow for the desktop icons.

it takes a long time to open directories in nautilus, terminal is normal.

this is kind of the same symptoms i got after a routine hard disk check in 6.06 but i could get back to normal by restarting.


I am yet undecided weather to upgrade my server if it is going to cause problems.

---

### Post by matt91 on 2007-04-20
if i cant solve this will a clean install keep my settings if i keep home and etc?

---

### Post by SpanishFranks on 2007-04-20
you can add

gnome-settings-manager

to the sessions startup list. That should fix it

---

### Post by matt91 on 2007-04-20
iv added gnome-settings-manager to the startup and doesnt work. also tried loading gnome-settings-manager with terminal and it wasnt found.

---

