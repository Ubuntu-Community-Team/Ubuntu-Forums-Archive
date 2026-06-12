---
title: "frozen session in the middle of an upgrade"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by neilbags on 2011-07-29
Im in the middle of upgrading 10.04 to 10.10 using the GUI update-manager.

It got to the stage of merging config files (smb.conf) then something happened to my session and I couldn't get focus on the window anymore (also no borders, minimise/maximise buttons etc). I hit ctrl-alt-f1 and now i can't get back to X at all, or a console - I just have a blinking cursor.

I can get in via SSH and see that the upgrade is still running. the last thing on ps -ef is:

/bin/bash /usr/bin/ucf --three-way --debconf-ok /var/run/samba/upgrades/smb.conf /etc/samba/smb.conf

How can I continue this upgrade cleanly from the console? If someone can help me over IRC in realtime (nick: neilbags) that would be great!

---

