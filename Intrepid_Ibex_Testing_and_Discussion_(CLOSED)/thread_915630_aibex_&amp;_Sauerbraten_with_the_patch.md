---
title: "aibex &amp; Sauerbraten with the patch"
date: 2008-09-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Col-1023 on 2008-09-10
will the games in the ibex repositories, such as Sauerbraten have the latest patches.

I looked at the packages for Ibex and it has Sauerbraten 2008-06-20, which is the latest version of the game.

However, there is also a later patch available on sourceforge, dated about a month after the release of the game.

Is the patch going to be rolled into the Sauerbraten package?

If games such as Alien Arena 2008, Tremulous, World Of Padman, or Urban Terror have patches, will these be rolled into their respective packages?

TIA

---

### Post by RAOF on 2008-09-10
Generally, no.  I wouldn't expect upstream patches to be applied to the packages.

If there are particular reasons why these patches should be applied (bugs that they fix, or that multiplayer only works with the new patch, or somesuch) then filing a bug report against the package on launchpad.net, pointing to the patch, with the justification as to why they should be applied to the package.

Note that we're currently in Feature Freeze; if these patches add new features you'll need to separately justify why they should be granted an exception.

---

