---
title: "[SOLVED] Installing on a Laptop"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by dphoenixa on 2008-08-26
I have a HP with:

2.0ghz Centrino Duo
2gig ram
80gig hdd
nVidia Geforce Go 7400

i was going to install Ubuntu 8.04 but I just installed XUbuntu onto my desktop and thinking it may be a better match. But Maybe one of the others is even a better match...i am just trying to get what would be the best option to go with. I will be dual booting with Windows XP

---

### Post by iaculallad on 2008-08-26
> **dphoenixa said:**
> I have a HP with:

2.0ghz Centrino Duo
2gig ram
80gig hdd
nVidia Geforce Go 7400

i was going to install Ubuntu 8.04 but I just installed XUbuntu onto my desktop and thinking it may be a better match. But Maybe one of the others is even a better match...i am just trying to get what would be the best option to go with. I will be dual booting with Windows XP

With that spec, install Hardy instead to maximize the resources as it will be an overkill for (x)Ubuntu.

---

### Post by kspncr on 2008-08-26
I would just install regular ol' Ubuntu with those specs.

---

### Post by prshah on 2008-08-26
> **dphoenixa said:**
> 
2.0ghz Centrino Duo
2gig ram
80gig hdd
nVidia Geforce Go 7400


If you like/prefer the Xubuntu interface, you can stick with it; your machine is powerful enough to handle practically anything that you throw at it; but:

caveat 1)
XFCE's (the "X" in Xubuntu) Thunar file manager cannot handle UNC pathnames (Windows network file sharing) so you will have to use command line mounting and unmounting for Windows network shares. There is also no way (out-of-box) to browse windows networks for machines/shares. You will have to install pyNeighbourhood for windows network (samba) browsing; and even though there is a mount option in that, it will not work; you will still have to use the command line to mount.

caveat 2)
Bluetooth handling is not as transparent as in Ubuntu's Gnome, or Kubuntu's KDE. Eg., plugging in the bluetooth does not activate a suitable bluetooth icon/indicator, and obex:// style device browsing is not supported in the file manager.

Overall, I'd suggest you use either Ubuntu or Kubuntu 32-bit; after you gain familiarity with the gnu/linux interface, you can attempt a 64-bit version of one of these.

---

