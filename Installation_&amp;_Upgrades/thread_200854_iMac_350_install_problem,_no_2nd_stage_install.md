---
title: "iMac 350 install problem, no 2nd stage install"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by lokimon on 2006-06-20
trying to install ubuntu 6.06 PPC and after the initial install, all the way to the reboot, everything goes fine.

upon reboot i am asked for "linux" or "old" (old doesn't work) it defaults to "linux" and boots.  it even looks like it will go into Xwindows, but then the screen stays black for a bit and then drops back into text mode and asks me to log in.

once i do i get a shell, and i don't know where to go from here.

poking around it doensn't look like X11 is even installed (nothing in /etc for sure.)

sort of confused as to what to do at this point (this is going to be a public kiosk and without a GUI it's pointless.

any help is much appreciated

---

### Post by linear on 2006-06-20
I can't vouch for this personally, but you can try:

```
sudo apt-get install ubuntu-desktop
``` to install the missing bits.

Alternatively, install Breezy and do a dist-upgrade.

---

### Post by lokimon on 2006-06-20
well that at least got the install going, i'll let you know how it goes from there...

thanks a lot! i did try several things from apt-get install but none were the right one.

---

### Post by lokimon on 2006-06-21
that did the trick, thanks so much... this is the 3rd linux distro i have tried to put on this old imac and i'm happy that it not only works but provides the level of functionality i need.

next project will be getting DAAP music sharing working on it, and then replicate the install on an identical machine in the kitchen.

---

