---
title: "How to uninstall resulted files from a .run file?"
date: 2014-12-28
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2014-12-28
I didn't see it in Synaptic, nor in the list of programs in the Terminal with "dpkg --list". So what's next?

Thanks guys,

JDL

---

### Post by steeldriver on 2014-12-28
What .run file specifically? In general, all bets are off if you install things outside of the dpkg package management system - so unless the .run file created/installed a .deb package OR it provides its own uninstaller, you are probably out of luck.

---

### Post by javierdl on 2014-12-28
Is called [JackHammer]("http://jackhammer.hlfx.ru/en/main.html"), a Quake & Half-Life editor. Inside its folder I didn't see any sign of an uninstaller :(
I suppose deleting its folder would not be enough, would it?

JDL

---

