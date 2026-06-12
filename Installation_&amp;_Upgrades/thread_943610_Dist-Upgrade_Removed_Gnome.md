---
title: "Dist-Upgrade Removed Gnome"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by carney1979 on 2008-10-10
I have Intrepid installed. As of last night none of my packages nor my system was "broken".

This morning it wanted to do a dist-upgrade (yes, I really meant "dist-upgrade").

I sent it on it's merry way and it updated some packages, then it said it wanted to remove a bunch of packages all relating to Gnome, such as gnome-session, gnome-panel, etc.

I thought that these vital looking packages must be included in some new package(s) so I told it to go ahead.

I later did a reboot and I have no desktop whatsoever. From a tty I tried the dist-upgrade again, it was finished. I tried "apt-get install -f", nothing happened. I tried installing gnome-session, no go, lots of broken dependencies.

How do I get Gnome back??

David

---

### Post by mlentink on 2008-10-10
Known issue. Please remember it's a beta...
You might want to read several threads on this issue [here]("http://ubuntuforums.org/forumdisplay.php?f=346").

---

