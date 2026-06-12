---
title: "Configuring apt preferences"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by jpoRS on 2007-04-22
My current default media player is amarok, however whenever i do a dist-upgrade and the metapackage ubuntu-desktop is selected, rhythmbox is selected for install. I have no desire to use rhythmbox whatsoever. How would I go about configuring apt preferences in order to not install rhythmbox (or other unwanted programs) ever, upgrade after upgrade? Is there another way to prevent it from being installed ever, without having to type something along the lines of "sudo apt-get -y install ubuntu-destkop && sudo apt-get remove -y rhythmbox" every time i wish to install something?

Thanks for any help, Jim

---

### Post by jpeddicord on 2007-04-23
I think you can lock the package when it is uninstalled in Synaptic, then you can install ubuntu-desktop again. It will probably complain about dependency problems the whole time, but it should keep it off.


Jacob

---

