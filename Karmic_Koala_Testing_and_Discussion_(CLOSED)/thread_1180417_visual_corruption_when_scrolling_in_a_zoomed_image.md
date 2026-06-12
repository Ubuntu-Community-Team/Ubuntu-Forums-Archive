---
title: "visual corruption when scrolling in a zoomed image - eog"
date: 2009-06-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yoasif on 2009-06-06
running apt-cache policy eog
eog:
  Installed: 2.27.2-0ubuntu1
  Candidate: 2.27.2-0ubuntu1

if I zoom into [this image]("http://launchpadlibrarian.net/27221258/Artwork_F11_Betamockup1_std_right.png") and scroll up and down (most reproducible) I get visual corruption in Karmic.

Any help confirming this bug and commenting on the [launchpad]("https://bugs.launchpad.net/ubuntu/+source/eog/+bug/379221") and [gnome]("http://bugzilla.gnome.org/show_bug.cgi?id=584068") bug tracker would be very helpful!

---

### Post by psyke83 on 2009-06-06
> **yoasif said:**
> running apt-cache policy eog
eog:
  Installed: 2.27.2-0ubuntu1
  Candidate: 2.27.2-0ubuntu1

if I zoom into [this image]("http://launchpadlibrarian.net/27221258/Artwork_F11_Betamockup1_std_right.png") and scroll up and down (most reproducible) I get visual corruption in Karmic.

Any help confirming this bug and commenting on the [launchpad]("https://bugs.launchpad.net/ubuntu/+source/eog/+bug/379221") and [gnome]("http://bugzilla.gnome.org/show_bug.cgi?id=584068") bug tracker would be very helpful!

What video card/driver are you using? It's not necessarily a bug in eog (and I can't reproduce it). I also wouldn't recommend that you file bugs on the upstream tracker until you have determined that it's not a problem with Ubuntu itself (e.g. packaging issues, faulty Debian/Ubuntu patches, kernel, Xorg and various other issues). This is especially important during the development process, as there is a lot of activity with every aspect of the system.

---

### Post by yoasif on 2009-06-06
Nvidia 180 driver, GeForce 9100M G.

---

