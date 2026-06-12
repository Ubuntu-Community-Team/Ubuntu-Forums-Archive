---
title: "[SOLVED] update gunshy"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by caro on 2007-06-02
I bought a new laptop and loaded up Ubuntu on it yesterday.  Everything was working great until I decide to run all the updates in the Update Manager.  I couldn't boot (GRUB error) with the updated kernel, but since it was a new install, I just blew it away and started over.  No great loss.

Since then I have only loaded a few updates I needed.  However, this leads me to a couple of questions:

1.  Should I keep everything updated that I see in the Update Manager?   If not, what are the important updates to watch for?  (I assume the updated kernel error doesn't happen everyday.)

2.  When Ubuntu has a new release, and I decide to update, will I lose what I've customized like updated graphics drivers for my widescreen laptop or restricted drivers for my Intel wireless?

Thanks

---

### Post by jack_teagarden on 2007-06-03
Hey!

It's generally a good idea to keep everything updated, and the error you talked about often happens when a new kernel messes with /boot/grub/menu.lst (partitions not in the order it wants, sometimes)
  When a new release comes out, you keep everything, it's almost like just another update....
Good luck in Ubuntu!

---

### Post by kevinlyfellow on 2007-06-03
If the new kernel is broken, the old ones are kept, just choose to use a different kernel when you boot.

---

### Post by caro on 2007-06-03
***A quick update:***

Found out this was an issue with Dell e1505 laptops.  The update redirected the boot to the wrong partition.  I changed it and was able to load the updated kernel and all other updates with no problem.  

Thanks, everybody!

---

