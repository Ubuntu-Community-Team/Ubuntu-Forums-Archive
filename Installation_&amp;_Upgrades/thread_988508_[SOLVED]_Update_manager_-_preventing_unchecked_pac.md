---
title: "[SOLVED] Update manager - preventing unchecked packages reappearing"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by rednick on 2008-11-20
OK, I think this should be easy but I'm darned if I can work it out.
I installed the adobe flash plugin from the .deb on the Adobe site (running Intrepid btw, upgraded recently from Hardy) and it works very well.

Unfortunately, I now have a Distribution Update in my update manager - flashplugin-nonfree with the same version number as the flash plugin I've installed.

If I try to install the update it fails with a conflict between the packages adobe-flashplugin and flashplugin-nonfree.  But every time I boot, the orange tray icon is there, inviting me to update and always in the list is this same update.

Is there any way to stop this appearing - I've unchecked it, I don't want to install it. I just want it to go away! However, the only way I can think of is to start disabling repo's which will cause me to lose countless other updates.

With (ducks for cover) Windows Update, if you untick an update you get an option "Don't remind again about this update".  Do we have similar?

TIA
Nick

---

### Post by Partyboi2 on 2008-11-20
Have you tried to lock the package in Synaptic? You can lock the version by going to Package>Lock Version.

---

### Post by rednick on 2008-11-21
That did it. Cheers fella.

---

