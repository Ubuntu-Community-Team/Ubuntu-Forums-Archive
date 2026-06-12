---
title: "No ATI KMS for Kubuntu Karmic Alpha 3?"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by snargfish on 2009-07-23
My laptop has an X1250. I thought 2.6.31 had KMS for ATI. Was I wrong?

---

### Post by RAOF on 2009-07-23
No, you're right.  The current 2.6.31 has KMS available for ATI users, should you choose to turn it on.  An earlier 2.6.31 kernel even had a bug where KMS was enabled by default for ATI.

However, the userspace xserver-xorg-video-radeon and mesa components don't handle KMS very well at the moment (and rely on a host of unreleased stuff - this is still in development).  So, you can turn on ATI KMS, but you won't get 3D, and I'm not sure about accelerated 2D, either.  This makes it a pretty bad deal :).

If you want to try it out, the xorg-edgers team has a radeon-kms PPA with the various userspace components needed.

---

### Post by snargfish on 2009-07-23
> **RAOF said:**
> No, you're right.  The current 2.6.31 has KMS available for ATI users, should you choose to turn it on.  An earlier 2.6.31 kernel even had a bug where KMS was enabled by default for ATI.

However, the userspace xserver-xorg-video-radeon and mesa components don't handle KMS very well at the moment (and rely on a host of unreleased stuff - this is still in development).  So, you can turn on ATI KMS, but you won't get 3D, and I'm not sure about accelerated 2D, either.  This makes it a pretty bad deal :).

If you want to try it out, the xorg-edgers team has a radeon-kms PPA with the various userspace components needed.

Oh I see. Thank you for the explanation. I'll just wait for my KMS goodness ^^

---

