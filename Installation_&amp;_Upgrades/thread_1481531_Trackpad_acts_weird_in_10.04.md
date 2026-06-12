---
title: "Trackpad acts weird in 10.04"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by EamonSloane on 2010-05-12
I upgraded yesterday, and I've noticed that my trackpad acts strangely now.  It's as if the resolution is wrong or something.  In comparison to each other, the horizontal response is much faster than the vertical response.  This is annoying as you can imagine.

I don't think it's an upgrade vs. clean-install issue because when I tried it out from a live cd, it did the same thing.

---

### Post by EamonSloane on 2010-05-13
bump?

---

### Post by efflandt on 2010-05-13
I really have no idea if it is related to the new kernel mode (KMS) video.  But my video was slow enough that in Solitaire, cards left multiple card trails (with no special effects).  I also could not suspend or hibernate.  glxgears did not rotate, but just occasionally jerked at a range of 130-200 in 6.1 seconds (really slow).  glxgears also caused system lag.

Using **nomodeset** kernel parameter (user space video) eliminated the card trails, glxgears smoothly averaged about 9600 in 5 seconds (similar to Karmic), and suspend and hibernate worked.

---

