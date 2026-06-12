---
title: "Upgrade to Natty froze - weird orange window borders afterwards"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by Resurge on 2011-04-02
While upgrading 10.10 netbook edition to 11.04 by using 'update-manager -d' The installer froze while trying to update the grub config file.

I rebooted the pc by choosing "restart the pc to complete the update procedure". While shutting down the shutdown loader kept running so I force-shutdown the pc by holding in the power button.

Afterwards I booted ubuntu in safe mode and chose the dpkg restore option (or dpkg repair or something similar) And some packages were (re)installed/grub repaired.

I then booted Ubuntu up normally and everything seems to work except I have some weird stuff going on with my window borders when the windows are not maximized. [[example]]("http://i.imgur.com/mTYw7.png")

I tried changing themes and some seem to work normally, like Clearlooks, but others don't work at all (like ambiance) or only half (meaning the border is styled correctly but the buttons aren't and the buttons are also aligned right instead of left).
I already tried to reinstall any packages with unity in it's name and also the package 'light-themes', which contains the ambiance theme but nothing changes.
For clarification: I want the default theme (Ambiance) as the active theme but when selecting that I get the window borders problem.


Any ideas what I could do to fix this?

---

### Post by shahmish on 2011-04-30
I've got the same problem. My upgarde went well, though, no bugs or freezes, but orange borders with no chance for change... It also seems to work much slower. weird.

---

