---
title: "I need help installing Firefox sorta..."
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by sourjax on 2007-07-28
As a learning experience I decide to build my own re-branded version of Firefox and It was a success for the most part.
here is the file: [http://jax.sourjax.net/firefox-2.0.0.5.en-US.linux-i686.tar.gz]("http://jax.sourjax.net/firefox-2.0.0.5.en-US.linux-i686.tar.gz")
I can use "SourJax Surfer" (Bon Echo) but only if I go it its folder and and start it from there. I want to it install it on my secondary "experimental" PC and have it run normally.

My second PC will run xorg, xdm, Fluxbox, Xfe, synaptic, gedit, gcalctool, and a few other programs. I want "SourJax Surfer" to be the default web browser and start from the menu just like if I "apt-get install"ed Firefox or Dillo.

Oh and a second question how do I rename all the "Firefox" files to reflect their new name? If I change the "Firefox" executable file the program won't run at all.

---

### Post by sourjax on 2007-07-29
I half solved this.

I un-tarred it, moved it to /usr/lib/surfer, created a symbolic link in usr/bin/, then gedited /etc/X11/fluxbox/fluxbox-menu to create a a launch point in the menu. 

Now the question is how do I do that on my regular Ubuntu? Is there a way to modify the menu?

---

### Post by sourjax on 2007-07-30
Ok I was wrong it didn't work as I thought it did, whenI rebooted my PC it deleted Surfer from the Menu, anybody else got an idea?

---

