---
title: "Alt+F[1-7] switches consoles after update"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by kamazee on 2010-05-03
Alt+F[1-7] (just Alt+, not Ctrl+Alt+) started switching physical consoles after updating karmic to lucid.
This behavior disappears after logout-login but comes back after reboot.
What should I do to use Alt+F* shortcuts and make consoles to switch by Ctrl+Alt+F[1-7]?
Thanks in advance.

---

### Post by kamazee on 2010-05-03
Add the following lines to the /etc/X11/xorg.conf if you experience the same problem:

Section "ServerFlags"
        Option  "VTSysReq"              "false"
EndSection

Despite of the value mentioned above is default for xorg (man said so), Alt+Fn started working correctly whan I put it into xorg`s config.

Thanks `man`, as always :]

---

