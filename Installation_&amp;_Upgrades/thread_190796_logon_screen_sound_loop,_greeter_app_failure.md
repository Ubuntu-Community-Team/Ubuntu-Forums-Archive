---
title: "logon screen sound loop, greeter app failure"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by Riverine on 2006-06-06
My laptop (emachines M5309) ran dual boot Breezy - Windows XP beautifully.

I recently upgraded the laptop to Dapper.

Now, the boot to Dapper shows normal until the logon screen arrives.  The tom-tom tatoo sound that announces the logon screen goes into a loop (at maximum volume and speed....sweet).  I can logon, but the drum loop rolls on.  The system monitor doesn't show any running processes (other than the system monitor).  When I shut down the system a failure shows for the shutdown of the periodic command scheduler.

This problem does not occur consistantly.  So far it happens on about 8 out of 10 logon attempts.  When the logon screen/logon sound problem does not happen Dapper is everything it ought to be.

Ideas?  Advice?

---

### Post by Cervantes on 2006-07-01
I've got the same problem, only worse.

The infinite sound loop occurs every time, and the furthest I can get is to enter my user name and password, after which the system hangs before the splash screen (though the drum beat continues).

I've got a pretty standard Creative Sound Blaster audio card. This is a fresh install of Dapper.

Has anyone got any ideas?

---

### Post by AI0867 on 2008-07-05
My 'solution' so far is to run gnome-control-panel, click login window, go to the accessibility tab and turn off the "login screen ready" sound.

This *immediately* stops the loop, though turning it back on brings it back.

Opening the login window options in KDE consistently disconnects my session. Though I can just 'login' again and continue.

---

