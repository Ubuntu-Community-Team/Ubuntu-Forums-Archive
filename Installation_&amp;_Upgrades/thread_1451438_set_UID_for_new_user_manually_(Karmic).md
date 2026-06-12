---
title: "set UID for new user manually (Karmic)"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by fbusse on 2010-04-10
I need to set a new user's UID to "501", 'cause an existing network directory has to be mounted as his home directory.

In the KDE system settings, "User Management", I can define the new user and set the UID to "501" (straight forward, so far). But when I accept the settings using the "OK" button, the user is defined with UID 1001. - Using these (wrong) settings, the new user can log in to the system and the KDE desktop is built correctly.

However, when I manually redefine the user's UID to "501" in /etc/passwd (before the user logs in for the first time), he can't log and building the KDE desktop fails ("kstartupconfig4 does not exist or fails"). Error messages say that ~/.kde/share/config/knotifyrc and foorc cannot be created in his home directory.

Any idea?

(duplicate posting in [german forum]("http://forum.ubuntuusers.de/topic/uid-fuer-neuen-benutzer-manuell-setzen/"))

edit: **sudo usermod -u 501 [user name]** does the trick

---

