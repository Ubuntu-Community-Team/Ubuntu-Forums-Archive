---
title: "grub installation + revert to windows bootloader"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by gonintendo on 2010-02-22
i've been using ubuntu with wubi, and I'd like to install it on my new hard drive (so windows is on one hdd and ubuntu is on another). afaik, grub will be installed on the hdd w/ ubuntu, and i have to set it to recognize the other (windows) hdd. assuming that i want to get rid of ubuntu and just use windows, what steps do I have to take to do so? (if grub is only on the ubuntu hdd, then would I just have to format it?)

---

### Post by darkod on 2010-02-22
You would have to restore windows mbr on the ubuntu disk, but you could also simply boot from the windows disk which will still keep its windows bootloader if you set grub to install on the ubuntu disk.
Also there is nothing special in making grub see the windows OS, it will do it automatically unless you unplug the windows disk during ubuntu install.

---

### Post by gonintendo on 2010-02-22
cool, thanks, i really don't care much about the ubuntu disk, i just bought a new backup hdd, so the ubuntu one was sitting useless in my system.

---

