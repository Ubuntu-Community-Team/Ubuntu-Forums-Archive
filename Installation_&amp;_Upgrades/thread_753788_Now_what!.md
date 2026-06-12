---
title: "Now what!?"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by unknown03 on 2008-04-13
I've installed Ubuntu 7.10 on my friends computer, as my own, several times.. But recently I tried installing Hardy and decided to format and go back to Gutsy, atleast until the final release is out..

Nothing has changed with my hardware or BIOS.. But now I cannot boot/install from the liveCD as it just hangs on a blank screen.. I've tried the noapic nolapic boot options to no avail (when its worked before, but usually I never needed to use them) .. I tried the alternate cd as well, installed fine, but when booting up it loads everything and then hangs at a blank screen.. I tried recovery mode and it wont startx 

what gives? Im going crazy having to boot into Windows!!

---

### Post by kellemes on 2008-04-13
From recovery mode try the following..
```
dpkg-reconfigure xserver-xorg
```

now startx

---

### Post by unknown03 on 2008-04-13
Thanks for your speedy reply..

I've already tried sudo dpkg-reconfigure xserver-xorg and I still get the same error message when I startx:

XIO: fatal IO error 104 on xserver ":0.0"

---

### Post by kellemes on 2008-04-13
What's your videocard?

Please post (using code-tags):
/etc/X11/xorg.conf
/var/log/Xorg.0.log

---

### Post by unknown03 on 2008-04-13
phew, I'm back into 7.10

I have 2 x Nvidia GeForce 8600GT's setup for SLI, and that was causing its problems. I removed a card, and here I am!

QUESTION:

Why is it that you cant have, or at least initially boot, an SLI setup?

---

