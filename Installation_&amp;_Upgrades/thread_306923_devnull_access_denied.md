---
title: "/dev/null access denied"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by gasolino on 2006-11-25
I just manually edited my sources and apt-get dist-upgraded from Dapper to Edgy. I know I should have used the "official" method, but I thought this would be just as easy, and educational too. Apparently, I messed something up. However, I am almost positive that I edited my sources.list correctly.
First of all, my video driver is broken, and I can't get into X. I think I may know how to fix this, just by reinstalling the driver and editing xorg.conf, but I am having another problem. When I try to login, an error message pops up:
bash: permission to access /dev/null denied
That might not be exactly it, but it is almost the exact message. This message scrolls down the screen until it fills up the whole thing, and won't let me do anything else.
Is my install dead? Or is there something I can do?

---

### Post by gasolino on 2006-11-25
by the way, I am trying to login using my user name. I haven't tried to log in as root yet, will try that now.

---

### Post by gasolino on 2006-11-27
well, i don't know my root password, so I can't do that. I don't think I ever gave one.
Any ideas?

EDIT: The exact error message is:
bash: /dev/null: access denied

---

### Post by NeoFax on 2007-02-12
I just started receiving this error as well.  Does anyone know what could be the problem?  I just started receiving it after a month of no problems.

---

