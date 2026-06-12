---
title: "Can't find were to uninstall a .deb install"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by flatlinecoder on 2008-11-09
I install a program called Demorecorder from a .deb file I downloaded. How do I remove it? I cant find it in add/remove?

---

### Post by loko on 2008-11-09
take a look at synaptic, there you will find it.

you can start it from the start-menu or in the terminal by typing "sudo synaptic"

---

### Post by ajgreeny on 2008-11-09
You may also be able to uninstall it with ```
sudo dpkg -r demorecorder
```The actual name of the package will sometimes be less than obvious and usually does not include the version number, just the name.

---

