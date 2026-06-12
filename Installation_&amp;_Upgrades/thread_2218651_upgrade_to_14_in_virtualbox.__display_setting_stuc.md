---
title: "upgrade to 14 in virtualbox.  display setting stuck at 640x480"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by airbornetrojan on 2014-04-21
Does anyone have a way to modify the display settings when they're stuck at 640x480.  the display setting panel cannot be navigated because the lower portions of the panel cannot be scrolled or tabbed.

Looks like i'm going back to 13.

---

### Post by airbornetrojan on 2014-04-22
I lost the reference--but, let it be known that when you upgrade Ubuntu in a virtualbox guest, you must run this script: sudo apt-get install virtualbox-guest-dkms

I agreed to upgrade something-something in that script.  shutdown the instance and brought it back up.  resolution came back to 1024x680 or so on my machine.

I'm coming from Microsoft stuff, so I forgot to clone my guest instance before all this.  please do.  this is brain surgery--not trivial.

Good luck,

---

