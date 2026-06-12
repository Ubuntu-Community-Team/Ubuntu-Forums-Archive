---
title: "upgrade hardy 8.04 2.6.24-20-generic boot problems"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by piagent on 2008-07-25
The upgrade from 2.6.24-19 to 2.6.24-20 has presented a problem:
Sony laptop PCG-505ls: NG starting, assume bios, .......
Dell laptop Latitude  C610 or older (?): NG starting, ......
Dell laptop Latitude D800: OK
Dell laptop Latitude D600 x3: OK
ALtima AMD 800 custom desktop: OK

Logs did not show anything, at least the ones I looked at.  Going to try to see if grub -verbose gives any clues.  Any other ideas then stick with 19 until 21,lol.

---

### Post by avtolle on 2008-07-25
As has been reported on several other threads, this kernel upgrade has a known bug, and a bug report has been made to Launchpad. The current "fix" is to continue booting from the -19 kernel (you can remove the upgraded kernel, there's a how-to on one of the threads).

The update came from the proposed repository. Packages are placed there for testing, and often will have a bug (after all, that's the purpose of testing). I recommend that if you do not wish to be involved with testing and system breakage from bugs, you disable that repository, which is disabled by default. Good luck.

---

### Post by piagent on 2008-07-25
Thank you, I just found another post from 4 hours ago.

No problem with bleeding edge, I had already backed out the upgrade and changed the source on the older latitude.  The sony will stay as is.

What this has suggested to me is some "news" feed as part of the upgrade apps.  Is there such a feature, applet,app?  Other than these forums.

---

### Post by geezerone on 2008-07-25
> **avtolle said:**
> ...The update came from the proposed repository. Packages are placed there for testing, and often will have a bug (after all, that's the purpose of testing). I recommend that if you do not wish to be involved with testing and system breakage from bugs, you disable that repository, which is disabled by default. Good luck.

I was thinking the same after enabling the same repo to get the latest version of FF3. Already disabled the proposed repo and suggest others do the same like 'avtolle' says.

---

