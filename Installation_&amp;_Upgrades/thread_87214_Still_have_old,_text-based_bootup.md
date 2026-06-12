---
title: "Still have old, text-based bootup"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by gk_jam on 2005-11-07
I had an Ubuntu 5.04 CD in the house and used it to install Ubuntu on my computer, and then immediately upgraded to 5.10 using apt and the instructions for upgrading in the wiki.

Everything is working fine in Breezy now, except I still see the old, text-based bootup of Hoary instead of the new Breezy graphical bootup screen that I've seen screenshots of. The splash screen and background are all the new Breezy ones.

Anyone know why I'd still be seeing the old bootup screen, and how to switch to the new one?

---

### Post by earobinson on 2005-11-07
no clue, i do know that a lot of people on the forums have been saying that a dist-upgrade is messy from 5.04 to 5.10. I would recomend dling the isos and doing a cleen install.

sorry I could not be more help.

You could manualy install usplash if it is not. or uninstall it and reinstall it using synaptic, that may fix the problem

---

### Post by az on 2005-11-07
Did you have ubuntu-desktop installed when you dist-upgraded?

If you just installed the base system, dist-upgraded and then installed ubuntu-desktop, you will have installed the kernel before usplash.

For usplash to work, it has to be part of your initrd.

What you can do right now is run

sudo apt-get install --reinstall linux-image-2.6.12-9-386 (if that is the flavour, 686 or k7)

That will reinstall the kernel and rebuild the initrd with usplash support.  Just make sure that you have the usplash package actually installed:
dpkg -l|grep usplash
if not, install it and everything else you are missing

sudo apt-get install ubuntu-desktop.

Cheers!

---

### Post by earobinson on 2005-11-07
and i learned something :)

---

### Post by gk_jam on 2005-11-07
That was exactly it (I had usplash installed, but needed to reinstall the kernel to include it in my initrd). Thanks for the help!

---

