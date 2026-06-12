---
title: "HELP Quake 2 was uninstalled during upgrade"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by webtaster on 2008-04-26
I was in the middle of a game of Quake 2 which was working on Gutsy. Since I upgraded to Hardy today the package quake2 has been removed although quake2-data is still installed. For some reason I can't re-install. I get this message from synaptic:-

"quake2:

Package quake2 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list"
I have tried re-enabling the apt-repositories that were disabled and reloading apt but no luck !
can anyone help ?? Luckily I still have my save games :-)

Thanks

Phil

---

### Post by Phil Urich on 2008-05-04
Strangely enough, on my AMD64 machine it was not uninstalled, but on my i386 machine it was.

However, I just got the [package from Gutsy](http://packages.ubuntu.com/games/gutsy/quake2) and re-installed with *that*, and things seem fine.  Well, emphasis on "seem", it doesn't start but that's because the NVIDIA setup is broken on my i386 machine because of silliness with the NVIDIA drivers refusing to go to a decent refresh rate on that machine at any resolution above a paltry 1024x768 so I'm using the open source but 2d-only "nv" drivers.  Get the package from the Gutsy download link and you should be fine!  

I'm going to try to fix the NVIDIA issues on my i386-arch machine soon, so if that one doesn't work then I'll be back with a solution that actually does ;) but I'm pretty sure the gutsy .deb will install and work just fine (although the GDebi installer seems broken on that older comp of mine, but dpkg -i did the trick as always).

P.S. I've thanked you because until I found your post I was writing off this problem as something broken with my older computer's install, and I only went ahead with installing the Gutsy .deb once I read your post and realized "aha, others also find quake2 sadly removed!"

---

