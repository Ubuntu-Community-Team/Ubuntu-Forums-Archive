---
title: "GDM crashes when pressing Enter or selecting a user"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2010-04-15
Every time I press Enter or select a user from the GDM login screen, it crashes. There's no way I can login unless I stop and restart GDM from the console. My searching has lead me to [this bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/532047") which makes sense because when I restart GDM it starts on TTY8 instead of 7. But it says that bug has been fixed, but I'm still having this problem. Is anyone else?

Edit: Actually this is unrelated to that bug. In order to login I have to stop GDM, delete /var/lib/gdm/.gconf and then start GDM. This is really weird.

---

### Post by FuturePilot on 2010-04-24
This was actually caused by [this bug]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200") which was fixed with nvidia-96 96.43.17-0ubuntu1

---

