---
title: "Program lockups (fle dialogs)"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Master Chief on 2009-04-21
I upgraded my hardy 8.10 installation earlier today to 9.04 and just noticed that all file dialogs (to open or safe files) freeze the used program so something is obviously wrong, but I don't know what that might be.

Anyone else here experiencing the same kind of lock ups?

Update: Apparently I am not the only one seeing this problem:  [http://multizilla.mozdev.org/weblog/weblog.html#1240342327](http://multizilla.mozdev.org/weblog/weblog.html#1240342327)

---

### Post by manuelb on 2009-04-21
It happened to me back in the alpha days, then the problem went away with next-day updates: are you sure you have the latest updates? Tried switching to "Master server" in sources and "Check" for updates?
Here we are wondering what's happening with random and voluntary lookups via "strace gedit", you may want to read it, it's all about lockups ;)

[http://ubuntuforums.org/showthread.php?t=1129414]("http://ubuntuforums.org/showthread.php?t=1129414")

If you can, could you ssh into your hanged machine and see if you can restart the whole gdm remotely? It may be a similar problem but we can't get why strace'ing locks the machine up.

---

### Post by Master Chief on 2009-04-22
Let me add that I am using the 64 bit edition, installed with the downloaded alternate-rc iso, and the installer downloaded another 1200 files so it better work (update manager says I'm up-to-date) or people will complain, like me.

---

