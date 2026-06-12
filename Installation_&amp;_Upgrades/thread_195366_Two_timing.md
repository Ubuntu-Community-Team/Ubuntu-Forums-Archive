---
title: "Two timing?"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by LanDroid on 2006-06-12
The system shows the correct time, but when I attempt to "sudo reboot", it refuses, saying something like "This command exceeds the time limit".  At the end of that message it lists the time as two hours in the future.  Evidently the system thinks I'm telling it to reboot two hours from now?   I noticed the system time (shown on the desktop) uses the 12 hour clock, but the reboot error message uses the 24 hour clock.  Are there two time settings that are out of synch?  Thanks for any help...

---

### Post by confused57 on 2006-06-12
For rebooting have you tried Ctrl+Alt+Del
or
sudo /sbin/shutdown -r now

I'm not sure about the clock issue.

---

