---
title: "Intel and NO &quot;nomodeset&quot;"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-08-28
Somewhere along the way, I can now boot with KMS. I no longer need nomodeset. This happen before the latest kernel-8. I have an Intel i865 and needed both the old intel-2.4 driver and nomodeset in order to keep the system going without a freeze.

At some point I will try the newest intel driver. Last time I tried it took a long time to get back to normal.

---

### Post by jerrylamos on 2009-08-28
> **VMC said:**
> Somewhere along the way, I can now boot with KMS. I no longer need nomodeset. This happen before the latest kernel-8. I have an Intel i865 and needed both the old intel-2.4 driver and nomodeset in order to keep the system going without a freeze.

At some point I will try the newest intel driver. Last time I tried it took a long time to get back to normal.

i845 here will boot without nomodeset however it does require /etc/X11/xorg.conf to specify:
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "vesa"
EndSection

i830 here will not boot successfully without nomodeset.

ati radeon Mobility 7500 defaults to nomodeset but will run with radeon.modeset=1, slows down video noticeably.

ati radeon Xpress 200 defaults to nomodeset has had problems with radeon.modeset=1.  When it did run, video slows down noticeably.  I'll check it with karmic 2.6.31-8.

So out of four test pc's KMS isn't a star yet....

Jerry

---

### Post by VMC on 2009-08-28
I remember you once stated that you couldn't even boot alpha 3. You needed to use a2 and then work your way up.

There's some progress. I was just wondering what was changed that allowed i865 to use kms now. I think I remember seeing some xorg updates of late. I read what's being updated, but some of the files are meaningless to me.

---

