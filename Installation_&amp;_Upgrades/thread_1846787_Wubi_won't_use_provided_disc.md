---
title: "Wubi won't use provided disc"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by dakukuu on 2011-09-19
Ages ago I posted about a kernel panic problem. I thought I solved the issue and it turns out it didn't, so now im permanently downgrading to 10.10 and will upgrade to either 11.10 when it's out or if it still doesn't support my computer (even though older versions did) then i will use Mint instead.

The problem is i have the ubuntu 10.10 CD ISO in the same folder as wubi, however it doesn't pick up on it and wants to install 11.04, which kernel panics during install.

[IMG]http://i1207.photobucket.com/albums/bb466/amberflames/yhsjjie.png[/IMG]

This has worked before, does anyone know what im doing wrong? I want my ubuntu back :(

EDIT: Also, why do you need 50 posts to modify your profile? I've never seen that in a forum before...

EDIT2: Once again nevermind, i mounted the ISO and it just randomly popped up.

---

### Post by bcbc on 2011-09-19
Wubi.exe is release specific. The one within the ISO always is correct (as you saw when you mounted it) - but if you download one yourself then it will only work on the specified release.

You can find different releases of wubi.exe at releases.ubuntu.com, e.g. for maverick:
[http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

The one you get at [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer) is always the latest release (currently 11.04).

---

### Post by Frogs Hair on 2011-09-19
50 posts :[http://ubuntuforums.org/showthread.php?t=1836816](http://ubuntuforums.org/showthread.php?t=1836816)

---

