---
title: "Usplash not working on shutdown and restart"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by exploder on 2008-10-03
The title says it all. Is this ever going to be fixed?

---

### Post by kansasnoob on 2008-10-04
Hmmm, mine's working OK.

I'm curious if it might be a uuid thing. Have you re-sized or moved the swap partition? I quite often run multiple Linux operating systems and share swap which requires fiddling with uuid.

---

### Post by exploder on 2008-10-04
The problem is happening on a fresh install. Hardy also had this problem but there was a work around. The fix that worked in Hardy does not work in Intrepid...

---

### Post by picpak on 2008-10-06
My usplash is broken after an upgrade. I think it only applies to certain themes. To restore the old one, run:

```
sudo update-alternatives --config usplash-artwork.so
```

And select "/usr/lib/usplash/usplash-theme-ubuntu.so".

Then run:

```
sudo update-initramfs -u -k `uname -r`
```

After that, run "sudo usplash" and Ctrl-Alt-F7 to get out of it.

However, this means I can't run [my favorite usplash theme](http://www.gnome-look.org/content/show.php/Blue+Hardy+Usplash?content=78833). :(

---

### Post by ronnielsen1 on 2008-10-06
Sorry - misread the problem

---

### Post by autocrosser on 2008-10-06
NO matter what I try, my usplash is broken about 90% of the time & I sometimes get BIOS warnings while it is starting---been mostly on "nosplash" for the last few months. [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)  has been there from June 1st & nothing so far has fixed it.

At least the priority has been moved to "high"

And this is with a almost new EVGA 750 SLI motherboard with the latest BIOS.

---

