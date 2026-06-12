---
title: "installing nvidia drivers"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by Refund on 2005-08-04
I need to know the basics of installing the nvidia drivers, they seem fairly straightforward, however it tells me that I'm required to boot out of my x environment (which would be gnome I'm assuming) before I can install the drivers, but i can't seem to figure out how to get out of gnome, I tried logging out (like in kde, where they have a terminal option) but my only option all lead back into gnome.

so I guess I have 2 things,

1) how do I get into the command line (and out the x environment)

2) is there anything else I should take note of before installing the drivers.

cheers in advance, I'm almost sure this would be a duplicate topic and even more likely in the wrong section, but I couldn't find anything in the search.

---

### Post by GavinX on 2005-08-04
Follow the instructions here and you're safe.

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

Cheers,
GavinX

---

### Post by obx-jdt on 2005-08-04
[QUOTE=GavinX]Follow the instructions here and you're safe.

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

Cheers,
GavinX[/QUOTE]
Just upgraded to "breezy" now I get this error while trying to install the nvidia driver;

"# nvidia-glx-config enable
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel."

any ideas?

---

### Post by zAo on 2005-08-05
[QUOTE=obx-jdt]Just upgraded to "breezy" now I get this error while trying to install the nvidia driver;

"# nvidia-glx-config enable
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel."

any ideas?[/QUOTE]
Well, Breezy is unstable after all. Try:
```
sudo apt-get install linux-restricted-modules-<your architecture>
```
Your architecture is something like 686 or k7

---

