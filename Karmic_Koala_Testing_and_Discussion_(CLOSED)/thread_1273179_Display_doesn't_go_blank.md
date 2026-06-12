---
title: "Display doesn't go blank"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by moviemaniac on 2009-09-23
Hi guys,

I'm having this problem with Karmic ever since I installed it (starting with Alpha 4). I use the fglrx-drivers for my HD2600XT and when the display is set to shut off (i.e. in the power preferences) it only shuts of for a fraction of a second and then I get a black screen but with the backlight of the monitor turned on when it should be _completely_ off. It used to work in Intrepid (can't say anything about Jaunty).

Anyone with the same bug? Anyone with an idea which package to file the bug against?

cheers

---

### Post by forumache on 2009-09-23
Known bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/413168](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/413168)

---

### Post by moviemaniac on 2009-09-23
Thank you! I was looking everywhere I could think of in Launchpad but didn't look at the power-manager package ;)

---

### Post by alexmurray on 2009-09-28
I've uploaded a patched version of xorg-server to my [PPA]("https://launchpad.net/~alexmurray/+archive/ppa") which should fix this.

---

