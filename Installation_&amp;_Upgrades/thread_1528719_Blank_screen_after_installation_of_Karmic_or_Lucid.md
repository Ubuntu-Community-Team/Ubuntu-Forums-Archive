---
title: "Blank screen after installation of Karmic or Lucid"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by jayemee on 2010-07-11
Hi,

Wondering if anyone could shed any insight into the problem I'm having. Had been running Jaunty for a while, but thought I'd go for a clean install of Lucid. After stumbling over an I/O error before installation (solved by burning live cd to a CD-R instead of RW), I finally managed to the installer, and everything seems to go through ok, but then after ejecting and rebooting I'm always brought to a blank, black screen, with a flashing white cursor. 

I've tried installing Karmic instead, but to no avail. I've tried various nomodeset/ i915 modeset changes that some people seem to have success with. Truth be told I'm very new to all this, and I'm really at a loss to what to do. I didn't even have the "ro" before the "quiet splash" in the command line that most other posts mention.

Cheers!

Edit; just tried to install my original copy of Jaunty, which now has the same problem!

---

### Post by jayemee on 2010-07-11
Just tried Lucid alternate install, to no success.

---

### Post by jayemee on 2010-07-11
OK, so further info - I'm using an Nvidia graphics card. If I f6 and select nomodeset it now just goes to a ubuntu loading screen, 5 white dots turn red, then it freezes. If I enter "nomodeset" into cmd line it brings up an unexpected error, which gives me the chance to load a test terminal, where I can install, but then it still brings me back to the blank screen. This is soo frustrating, especially as I had a working ubuntu running before!

---

### Post by tmack2 on 2010-07-11
This is going to sound dumb. I to experienced this at times with different computers.
I made sure there was n't a cd in my drive and set my bios to boot from hard drive first..
It will go t a blank/black screen with a white blinking curser for a time and then boot. 
worked for me. perhaps?

---

### Post by jayemee on 2010-07-11
That's not as dumb a suggestion at all - I actually fixed the problem by unplugging my second hard drive, which I thought might be causing some problems, and now I can install and boot in Lucid no problem. Thanks for the inspiration!

---

