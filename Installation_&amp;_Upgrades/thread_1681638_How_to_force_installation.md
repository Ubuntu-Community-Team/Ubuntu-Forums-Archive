---
title: "How to force installation"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by Archaon59 on 2011-02-04
Hello, I have a problem with an old install of Wubi : I tried to install Kubuntu 10.10 from the .iso using a virtual drive (it wasn't intelligent, I know), the installation didn't finish (guess why ...).

So I uninstalled the broken ubuntu with the uninstaller, but when I try to lauch Wubi again, it is asking me to reboot, nothing else ... I deleted the registry keys, Wubi doesn't appear in the program list, I don't know what to do !

Thank you for your responses

---

### Post by bcbc on 2011-02-04
Strange... first follow the [manual uninstall]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?") instructions and make sure it is completely gone. Check Add/Remove programs and make sure it's gone too - double click and remove if nec.

If that doesn't help, then check the logfile in %temp%.

You could also try cleaning up the pyxxx.tmp folders in %temp% as well.

---

