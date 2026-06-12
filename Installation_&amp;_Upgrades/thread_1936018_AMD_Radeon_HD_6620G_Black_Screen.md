---
title: "AMD Radeon HD 6620G Black Screen"
date: 2012-03-05
forum: Installation &amp; Upgrades
---

### Post by ajdrew06 on 2012-03-05
Hi All,

I just purchased a new laptop with an AMD Radeon HD 6620G video card. When I try to boot 11.10 liveCD from a USB stick, I get the purple boot screen for about 5 seconds, then I get a black screen (as if the screen were turned off). Eventually, I hear the Ubuntu sounds prompting input, but I can't see them. Any idea how to get the video to work? I appreciate your help.

Thank you all!
-Drew

---

### Post by 2F4U on 2012-03-05
Did you try adding nomodeset to the grub kernel parameters?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ajdrew06 on 2012-03-07
I got the purple screen, pressed escape, pressed F6, "x"ed out Nomodeset, selected "Try without installing", I got the purple screen with 11.10 and the four dots, the dots cycled through from orange to white to orange again a few times, then I got a black screen with a blinking cursor in the upper left corner. It never booted. Any ideas? I'm getting closer it seems lol

---

### Post by Vms100 on 2012-03-08
Try to boot with "Safe graphics" (Ie vesa graphics).

---

### Post by tuanita on 2012-03-08
Ubuntu 12.04, supports AMD Radeon graphics, I've installed myself and works but it's still Beta version.

---

### Post by ajdrew06 on 2012-03-08
I'll probably just wait until 12.04 comes out then. Incidentally, if I install the beta version, what happens when the final release comes out? do I have to reinstall, or will I be able to upgrade from beta to the release version?

---

