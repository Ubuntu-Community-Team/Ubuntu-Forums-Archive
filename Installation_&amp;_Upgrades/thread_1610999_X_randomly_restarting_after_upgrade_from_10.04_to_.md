---
title: "X randomly restarting after upgrade from 10.04 to 10.10"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by rsevero on 2010-11-01
I'm a rather experienced Gentoo user but have little experience with Ubuntu.

I have upgraded a friends notebook from 10.04 to 10.10. Everything was fine with 10.04.

The upgrade process runed smoothly but after booting 10.10 the X system randomly restarts. It seems to not be able to run for more than 10 minutes without X abruptly restarting and the login page being presented. 

I still couldn't even identify some pattern nor relate the restarts with some specific software.

I've looked in /var/log/messages but there is nothing registered there that seems to be related to this issue.

Despite being an old notebook, I don't think it's hardware related because the problem appeared for the first time after Ubuntu upgrade and it keeps repeating itself after that.

Any ideas?

Please let me know if more info is needed.

---

### Post by jlanawalt on 2010-12-07
I'm experiencing something similar on my account on my desktop system. I'll be doing something and then X dies and I'm back at the login screen. Other users on the desktop system seem to be unaffected. I am also not having the trouble on my laptop that was also upgraded from 10.4 to 10.10. 

The restart seems to happen when new windows are created on the screen, such as opening a new tab in Firefox or Chrome, or clicking menus in Kino or Kdenlive, or clicking the Print button from the PDF viewer. Occasionally it has happened when I was away from the computer for a few minutes. Sometimes I can go hours without a restart like tonight. Usually it happens within minutes. 

I've tried checking the Xorg.0.log and Xorg.0.log.old. There is never an error message at the end of the just-finished .old log, nor a mention of errors in the noew .log after a restart. I've tried enabling Apport, but it doesn't seem to be catching the error. I haven't seen any core files. Still more to work through on the debugging instructions: [https://wiki.ubuntu.com/X/Backtracing](https://wiki.ubuntu.com/X/Backtracing)

---

### Post by rsevero on 2010-12-07
The problem I was facing was related to some custon configuration I did for VNC to start automatically. After I removed it, my problem disappeared.

Be aware that I'm not referring to the "Remote desktop" feature from gnome. As I said it was some custom configuration I did manuaaly editing some configuration files.

---

