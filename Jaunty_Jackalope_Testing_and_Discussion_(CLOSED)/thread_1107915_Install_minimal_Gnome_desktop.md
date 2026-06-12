---
title: "Install minimal Gnome desktop?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by emendelson on 2009-03-27
I've been trying to set up a minimal Gnome desktop in Jaunty, but the methods that worked in earlier versions seem to have stopped working. Any advice would be welcome.  Here's what I've been doing:

I start with the alternate CD and install a command-line interface system. Then I use apt-get to install xorg, gdm, and gnome-core. This was always enough earlier; this time, the gdm login screen appears, but drops me to a terminal using X fonts, not the gnome-desktop.

If there's an obvious step that I'm leaving out, I'd be very glad to hear about it. Thanks.

---

### Post by taavikko on 2009-03-27
You also need drivers for GPU
xserver-xorg-video-* 

Then it should work.

---

### Post by emendelson on 2009-03-27
Thank you for that suggestion. Unfortunately, it didn't help. When I go to the Options in the GDM, it offers "Fail-safe gnome", but then tells me that Gnome is not installed. Gnome-core is installed (I reinstalled it). Possibly this won't work until the second beta, and I'll keep trying.

---

### Post by loomsen on 2009-03-27
Try with gnome-session and/or gnome-desktop-data pkges.

Oh, and what about ubuntu-minimal or ubuntu-standard? (not ubuntu-desktop)

---

### Post by emendelson on 2009-03-28
gnome-session solved it. Thank you!

---

### Post by loomsen on 2009-03-28
You're welcome

---

### Post by chuckyp on 2009-03-28
Yeah your .xsession had no way of knowing to start gnome. So when you logged in with GDM it just started X with no window manager.

---

