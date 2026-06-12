---
title: "Sound card is the last thing to get working"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by Caps18 on 2010-02-03
One more thing to fix now...


I have tried to download the soundcard drivers from ASUS's website (M4N78 Pro motherboard running 7.10).  I will say that I'm unsure if the drivers would work for 7.10, but I guess they would.

I run the install.sh script, and I get this error message.

You haven't installed the kernel source.

nVidia didn't seem to have a problem locating the source. Is it looking for a newer source/kernel version than the one I have? Or is it looking in the wrong place? The source code is in /usr/src, the install script is looking in /lib/modules/$KERNEL_VER/source and /lib/modules/$KERNEL_VER/build

I may still have the previous sound card drivers installed, and I'm not sure how to remove them.  However when I run "aplay -l" I get nothing.

Thanks

---

