---
title: "No proprietary drivers show up as avaliable"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by adempewolff on 2009-10-16
I just installed the 64 bit version of the 9.10 beta (desktop edition) on a separate partition on my Dell Latitude D630.  I normally use a proprietary driver for my broadcom wireless chipset, and my nvidia graphics card.  When I installed the beta however, I clicked on hardware drivers to enable them and none showed up as available after the scan.

As a work around: I inserted the 9.10 live cd, went into software sources, checked the box in "installable from cdrom/dvd", went into synaptic, searched for "bcm" and installed "bcmwl-kernel-source", then restarted.

This made my wireless work, I'm not sure where to find my nvidia driver-but I can always download it now that the wireless is working.

Now that the wireless driver is installed it shows up in the "hardware drivers" list.  Why wasn't it there before?  I can see this regression as being a game-ender for users not accustomed to using synaptic.

---

### Post by nanog on 2009-10-16
Jockey did not work for me until I installed nvidia-common. You can also just install nvidia-glx-xxx manually which pulls in all the dependencies except for nvidia-settings.

---

### Post by terry_gardener on 2009-10-16
when i installed jaunty on a laptop this happened. the nvidia drivers didn't show. i used envyng to install and setup you even get the nvidia-settings.

---

### Post by adempewolff on 2009-10-16
I updated my package list, opening up Update Manager, held my breath and agreed to the partial upgrade it proposed (this instance of Karmic is on a partition purely meant for testing OS' before I use them for anything important, so I wasn't too worried about a disastrous partial upgrade), and let it download and install ~300MB worth of packages.

After I restarted (and edited my menu.lst on my main partition to point to the new kernel) nVidia drivers showed up.

Who knows what the matter was.  Maybe the install didn't get finished (I did get impatient with 10 minutes of an unresponsive black screen when it did the final restart and powered off the computer).

---

