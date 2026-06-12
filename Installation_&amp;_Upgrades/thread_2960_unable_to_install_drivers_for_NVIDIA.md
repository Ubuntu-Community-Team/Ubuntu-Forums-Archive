---
title: "unable to install drivers for NVIDIA"
date: 2004-11-02
forum: Installation &amp; Upgrades
---

### Post by Dennis_k on 2004-11-02
I tried to install the drivers for my FX5700LE using the wiki howto.
But when i give the commant sudo apt-get install nvidia-fx i get a message that the driver is a part of an other package.

How can i install this driver?

---

### Post by mercurus on 2004-11-02
[QUOTE=Dennis_k]I tried to install the drivers for my FX5700LE using the wiki howto.
But when i give the commant sudo apt-get install nvidia-fx i get a message that the driver is a part of an other package.

How can i install this driver?[/QUOTE]

I have an nVidia GeForce 2MX chipsetted card, I'm assuming that they use the same Ubuntu packaged driver, since nVidia supply the same drivers for the two different cards. The package isn't called nvidia-fx as far as I can ascertain (I don't have the universal package repository enabled at present) it is nvidia-glx and has nvidia-settings to help configure it.

Try the HOW-TO on the Wiki:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

Cheers
mercurus

---

