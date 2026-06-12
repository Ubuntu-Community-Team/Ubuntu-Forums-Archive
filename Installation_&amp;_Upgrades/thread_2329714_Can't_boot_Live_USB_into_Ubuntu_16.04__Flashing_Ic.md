---
title: "Can't boot Live USB into Ubuntu 16.04:  Flashing Icons, or nothing at all"
date: 2016-07-04
forum: Installation &amp; Upgrades
---

### Post by UserJB on 2016-07-04
I'm trying to diagnose problems with my new 16.04 install, so I tried to boot into the LIVE USB for 16.04.  I see this error message during the process

nouveau: failed to load fecs_inst

Also, when it finally boots, I only see a screen with the pink/purple ubuntu background.  No icons or panels.  If I right-click I might get a menu where I can create a new folder, or launch a terminal, but then that menu and those icons are flashing at a rate of about once per second.

Does anyone know how I can fix this?  I've already spent 10+ hours trying to install first Ubuntu 15.10, and now 16.04.

UPDATE: I solved this problem by typing CTRL+ALT+F1 to get a login  window in text mode.  Then I did 'apt-get dist-upgrade' and restarted  the X server.

---

### Post by UserJB on 2016-07-04
UPDATE: I solved this problem by typing CTRL+ALT+F1 to get a login window in text mode.  Then I did 'apt-get dist-upgrade' and restarted the X server.

---

