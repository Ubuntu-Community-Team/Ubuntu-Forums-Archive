---
title: "After upgrade the screen resolution is too small (ATI)"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by hena on 2007-11-05
I upgraded from 7.04 to 7.10 (kubuntu). And after upgrade the screen is way too small. After hunting around I found following in the Xorg.0.log

(II) RADEON(0): setting screen physical size to 48x228

My computer is Compaq N800c and display driver is ATI Mobility Radeon 7500.

Any help really needed.

---

### Post by phrostbyte on 2007-11-05
See if you can adjust the resolution using the included "Screen & Graphics" applet in the System -> Admin menu

---

### Post by hena on 2007-11-06
After some testing I find some interesting results.

If I boot to '(restricted)' kernel and give roots password I get to commandline. There typing startx will start the x nicely to roots account. But it can't be used by other unfortunately.

Also I boot normally and login as root on virtualconsole I get a commandline. Then I disable the xorg.conf by adding wrong parameter. Next I restart X with ctrl+alt+backspace it fails. Then back to virtualconsole and fix the xorg.conf and startx again gives me same result as above.

I'm confused ???.

---

