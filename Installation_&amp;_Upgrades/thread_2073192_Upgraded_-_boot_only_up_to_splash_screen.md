---
title: "Upgraded - boot only up to splash screen"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by ricardisimo on 2012-10-19
This machine (32-bit) required a bit of a workaround: needed to log into unity once, then switch back to GNOME, and voila. That's fine...

My other machine (64-bit) cannot get past the Plymouth (?) splash screen. I have the mouse pointer, the purplish-orangish splash screen, but nothing else. If I tap the power button, I do get shutdown options (Sleep/Restart/Shutdown, etc...) and so I can get into recovery mode. But I have no idea where to start. I suspect that I might have to load lightdm momentarily, then later switch back to gdm later. I don't want to do any bashing, but Unity has been the source of most of my problems, one way or another, so...

I'm on a Intel® Core&#8482; i7-2600 CPU @ 3.40GHz × 8 with 7.7 GiB of RAM, 64-bit, as I stated. Any help would be greatly appreciated.

Oh, by the way, I can also remotely access my main drive by way of ssh from this computer, so as a worst case scenario I could do a fresh install after grabbing all of my files. I'd like to avoid this.

---

### Post by dino99 on 2012-10-19
first, remove "splash" when you boot, that will let you see the boot comments, and maybe let you know whats wrong.

---

### Post by ricardisimo on 2012-10-19
How? In the grub menu?

---

