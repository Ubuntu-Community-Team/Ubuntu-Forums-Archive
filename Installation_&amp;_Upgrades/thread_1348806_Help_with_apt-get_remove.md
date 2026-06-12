---
title: "Help with apt-get remove"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by manjestic on 2009-12-07
I have two Karmic Koala kernels 2.6.31-14 and 2.6.31-15 on my system.  The -15 kernel does not boot on my system so, I want to remove the package and it's dependencies, reverting to the prior version with
```
sudo apt-get remove linux-image-2.6.31-15-generic-pae
```but when I simulate this, it wants to install 2.6.31-16.

How can I both remove and prevent a new version from being installed?

Thanks.

---

### Post by starcraft.man on 2009-12-07
> **manjestic said:**
> I have two Karmic Koala kernels 2.6.31-14 and 2.6.31-15 on my system.  The -15 kernel does not boot on my system so, I want to remove the package and it's dependencies, reverting to the prior version with
```
sudo apt-get remove linux-image-2.6.31-15-generic-pae
```but when I simulate this, it wants to install 2.6.31-16.

How can I both remove and prevent a new version from being installed?

Thanks.

[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

^ Please see gui section.

Gist of it is easily done with Synaptic. Open it up, search for kernels you want to remove and mark for removal. The packages you want to remain 14 will need locking (prevent updates). Mark the packages (check) that you want to preserve (i.e. the 14 image/header files) and then go to menu Package > lock version. This will prevent all updates to kernel files.

I advise against this and suggest trying 16, kernel updates are important providing security and new/improved features. You can always fall back to 14 if the newest version fails as well.

---

### Post by manjestic on 2009-12-07
Thanks for the advice.  I don't have a GUI installed; perhaps it's time to do so.  I notice that linux images are not auto removed on upgrade allowing me to boot older kernels.  So I will consider allowing apt to install -16 kernel.

---

### Post by starcraft.man on 2009-12-07
> **manjestic said:**
> Thanks for the advice.  I don't have a GUI installed; perhaps it's time to do so.  I notice that linux images are not auto removed on upgrade allowing me to boot older kernels.  So I will consider allowing apt to install -16 kernel.

If you don't have a gui see the cli section of my guide. You can use commands to put a hold on packages. Or else, use the aptitude ncurses gui to di it. Curses gui as ya prolly know is built for console, nifty stuff. Always liked it's look, reminds me of old days.

---

