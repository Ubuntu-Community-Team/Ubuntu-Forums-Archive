---
title: "Revert Changes"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by Haneef Mubarak on 2012-01-19
So I added the Debian Sid repo to one of my family's computers, and it worked fine. That is, until I restarted the computer. The GUI failed, and upon going to a tty, I noticed that instead of saying 'Ubuntu *' (* means blah blah blah), it said 'Debian GNU/Linux wheezy/sid [computer name] tty1' . I tried ```
service start lightdm
``` and ```
/etc/init.d/lightdm
``` restart to fix the GUI, but neither worked. I had removed the repo and updated+upgraded (and manually solved dependencies), but it still remained the same.

---

### Post by Haneef Mubarak on 2012-01-22
Bump!

---

