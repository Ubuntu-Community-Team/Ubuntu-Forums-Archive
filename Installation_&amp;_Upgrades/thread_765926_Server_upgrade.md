---
title: "Server upgrade"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by bsharp on 2008-04-24
Is it possible to upgrade my server (currently Gutsy) to Hardy with an alternate install cd without breaking anything?  Or should I just wait till the download servers are less jammed and do it from them?  Alternate cd would be preferable since Ive already got it from all my other upgrades.

---

### Post by scragar on 2008-04-24
I'm almost possitve you can just run:
```
sudon apt-get dist-upgrade
```
which works fine on debian, ubuntu should support it.

---

### Post by Rocket2DMn on 2008-04-24
Have a look here:
[https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)

---

### Post by bsharp on 2008-04-24
I would rather upgrade from the alternate cd in order to avoid the traffic jam on the servers, but the upgrade page doesn't specifically say that the Server Edition can be upgraded using the Alternate CD.  I assume that it can't, since the Alternate CD installs and upgrades the desktop.

---

### Post by Rocket2DMn on 2008-04-24
Agh, my bad, I didn't read closely enough - looks like the alternate install cd requires a GUI.
I wonder what would happen if you did a dist-upgrade using the alternate install cd as a repository source.  That's just a thought, I haven't heard about anybody trying it.

---

### Post by bsharp on 2008-04-24
I'll just wait for the traffic to slow down, I would like to try using it as a repository, but I would rather break my desktop installation instead of my server. 

Thanks for the replies though :)

---

### Post by ptcbus on 2008-04-24
I upgraded a desktop from 7.10 to 8.04 and had no problems. I used torrents though since the servers are completely jammed. Torrents were extremely fast. See [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

