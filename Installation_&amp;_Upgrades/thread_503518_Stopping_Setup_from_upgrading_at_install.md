---
title: "Stopping Setup from upgrading at install"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by cholapoker on 2007-07-18
I am ready to install Ubuntu on a few people's pcs. However, I don't want the setup to update and upgrade while installing. Reason is, the internet may be 1.none existant 2.56k modem 3.Malaysian ubuntu servers are very slow. And I have the updates (*.deb) in another disk anyway.

Is there any way to stop the upgrade while installing?

---

### Post by Kobalt on 2007-07-18
To my knowledge Ubuntu doesn't update & upgrade package it installs from the CD while it install : after a reboot, once the install is complete, it prompts you with the available updates and asks you if you want to upgrade. Just discard these prompts and install your debs... And possibly disconnect the PC from the Internet during the install if you don't even want to be prompted with the updates.

---

### Post by cholapoker on 2007-07-18
feisty does update. 'hanging' at around 83% completion.  If internet is disconnected at this point, it gives a message. OTOH, if no internet connection was on at the beginning of install, it completes fast. I would prefer not to off the internet because:
1. i might forget to do so.
2. nice to surf (showing off!!)
3. at times, it is messy to disconnect ethernet wire or go search their dsl modem which might be elsewhere.

I found that 'ifdown' disconnects internet but not sure if the installation program will re-activate it. Have to check.

---

