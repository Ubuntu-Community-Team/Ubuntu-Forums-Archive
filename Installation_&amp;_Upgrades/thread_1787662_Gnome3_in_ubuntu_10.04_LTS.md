---
title: "Gnome3 in ubuntu 10.04 LTS"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by viggu1990 on 2011-06-21
Can anyone please tell me how to install Gnome 3 in ubuntu 10,04?

I tried 'sudo apt-get install gnome-shell'

but there is a dependency problem with libgjs0 and xulrunner. Is there a way to fix it?

And I dont want to build Gnome3 from source..sorry..

Thanks for the help.:)

---

### Post by uRock on 2011-06-21
Installing gnome shell will not install Gnome3.

---

### Post by tgalati4 on 2011-06-21
Building from scratch builds character, and it might result in a working system.  You could request a backport and enable backport repositories or you could add the gnome3 PPA and try installing it directly and see what breaks.  Be sure you have your important data backed up because I see breakage in this situation.

---

