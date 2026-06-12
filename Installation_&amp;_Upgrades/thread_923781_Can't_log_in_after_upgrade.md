---
title: "Can't log in after upgrade"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by kvalis on 2008-09-18
A friend had problem after problem with an Packard Bell and Xp.  I said I would try Ubuntu  for him.  Installed 8.04 Alpha 3 tonight, and it even found the Linksys USB adapter.  I sent my friend a text message and told him the good news. Then, I thought I would update the system for him, and chose install of 500 plus packages.

However, after the update I can't log in, the Logitech wireless keyboard and mouse does no longer respond.

Any, suggestions??

Should I just reinstall 8.04, and turn off updates - since everthing was working fine?

I thought updates were meant to improve things!!!!???

Hopeful as ever

Tore

---

### Post by Partyboi2 on 2008-09-18
> Installed 8.04 Alpha 3 tonight, and it even found the Linksys USB adapter. I sent my friend a text message and told him the good news. Then, I thought I would update the system for him, and chose install of 500 plus packages.Hardy 8.04 is now the current stable release, I would suggest checking what version you have installed. maybe you have installed Intrepid 8.10 which is the next release which is still in development and could cause possible breakages.
If you are able to get to a terminal (Ctrl+Alt+F2) after you have started ubuntu, check what version you have by typing:
```
lsb_release -a  
```You can download hardy 8.04.1 (stable) from [[COLOR=Blue]here[/COLOR]]("http://releases.ubuntu.com/8.04.1/")

---

### Post by jack frost on 2008-09-18
I am running 8.04 now.. once the stable release of 8.10 comes out and I do an upgrade.. will it wipe all my settings etc.. like seamless desktop?  I have always just done fresh installs and not upgrade . (wondering about that)

---

### Post by Partyboi2 on 2008-09-19
> **jack frost said:**
> I am running 8.04 now.. once the stable release of 8.10 comes out and I do an upgrade.. will it wipe all my settings etc.. like seamless desktop?  I have always just done fresh installs and not upgrade . (wondering about that)
Doing an upgrade should not wipe out your current settings. Or you could do a fresh install and make sure that you have your /home folder already on its own partition.

---

### Post by kvalis on 2008-09-19
Thanks partyboi2.

Downloaded Hardy 8.04.1 and we were back to a running system.


Tore

---

