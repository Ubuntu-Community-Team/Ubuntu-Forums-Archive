---
title: "Text Install for Manufacturer"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by mmendez on 2007-04-29
Well I have always preferred to install from the Alternate Cd and have seen the "Text Installation for Manufactures" but never done it, so I decided to try this option out to check out, because I will install Feisty on a few laptops and thought this would be a cool little thingamabob.

Well I breezed right through it and it asked me for a password to use, but no name. I thought nothing of it and kept going. After the installation I got to the login screen and well I had no user name. I tried nothing, "manufacturer", I tried manny to see if it will create one and I got nothing.

If I have to I will reinstall and pay more attention, but I would appreciate a little clarity thanks.

---

### Post by bapoumba on 2007-04-29
Your username should be **oem** and your password the one you gave during the install.
Once logged in, run **sudo oem-config-prepare** from a terminal. Next boot, a new user will be created (new login and password), with all the administrations privileges (will be in the admin group).

---

### Post by bodycoach2 on 2007-04-29
In the OEM installation, is there a way to get to the desktop, and use the add/remove or synaptic package manager to install packages? Also, I'd like to be able to prepare an OEM "Blubuntu" desktop for someone, and add all the packages they want.

Any OEM installation hints?

---

### Post by bapoumba on 2007-04-29
> **bodycoach2 said:**
> In the OEM installation, is there a way to get to the desktop, and use the add/remove or synaptic package manager to install packages? Also, I'd like to be able to prepare an OEM "Blubuntu" desktop for someone, and add all the packages they want.

Any OEM installation hints?
You can install packages, but any oem config on the desktop (themes ...) will be lost, as far as I remember. I only use oem install cd (the alternate ones) because it uses the debian installer, and not the graphical one.

---

### Post by mmendez on 2007-04-29
ok thanks for the info

---

